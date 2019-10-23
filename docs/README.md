---
sidebar: auto
---

# On/Off Boarding notes

## Some housekeeping...

This site is being used to capture notes for the On Off Boarding project.

This is a VuePress site... but I think that all editors need to know is that it is
a directory of Markdown files in a GitHub repository.  Pull the repository down to your machine, edit it and push it back to the repo.  Pushing to the repository will automatically cause the online site (on Netlify) to get regenerated.

If all of this turns out to be to much trouble, we'll do something else.

## Purpose

The On/Off Boarding application is used to organize lists of tasks that need to be done when employees are onboarded, offboarded, or transferred.  The app manages template lists of tasks that can be copied and edited for each on/offboarding event.  The application tracks who completed a task, when it was done, and who verified the completion.

## Features

* editor for tasks and lists of tasks
* assignment of lists of tasks to "executors"
* dashboard reporting of tasks assigned, progress, overdue tasks, etc.

## Data

This section will contain notes on the data which the On/Off Boarding application
is using

### Task

A task has the following data:

| Field | Description |
| :---- | :---------- |
| title | plain text name of the task |
| description | rich text description of the task.  May include links to additional information, policy documents, or other resources |
| done | a boolean value indicating whether the task is complete.  Generally rendered as a checkbox |
| sequence | an integer used for sorting a group of tasks |
|  tasklist_id|   a pointer to a tasklist that contains this task
| due_date | date when a task should be completed.   **Note**: we are not specifying a specific time |
|  done_by|  user id of the person who completed the task
|  done_at|  timestamp, when the task was completed
|  tags|  zero or more tags used to identify or group tasks
|  created_at|  timestamp, when this task was created. Tasks may be created when a tasklist is created (by copying a template of tasks), or later by inserting a new task in an existing tasklist.

* There are comments associated with tasks.  Right now we are supporting only one comment.

### Tasklist

| Field | Description |
| :---- | :---------- |
|title | plain text title of the tasklist |
|description | rich text description of the tasklist.  May include links to additional information, policy documents, or other resources. |
|assignee |  a user id (entry in the user table) indicating who is responsible for completing the tasklist |

* there are comments associated with tasklists.  Right now we are only supporting one comment. 

### TaskComment

| Field | Description |
| :---- | :---------- |
| task_id | id of the task that this is a comment for |
| comment | rich text comment |
| user_id | user id of the (last) person editing the comment |
| updated_at | timestamp of the last edit for this comment |

This is implemented in a separate table so the database would be ready if we wanted to support multiple comments on tasks in the furture. 


### TasklistComment

| Field | Description |
| :---- | :---------- |
| tasklist_id | id of the tasklist that this is a comment for |
| comment | rich text comment |
| user_id | user id of the (last) person editing the comment |
| updated_at | timestamp of the last edit for this comment |

### User

These fields are relevant to the application.  Additional fields are used for authentication.

| Field | Description |
| :---- | :---------- |
| name | first and last name |
| email | email address |
| netid | Cornell NetID |

### Administrator

| Field | Description |
| :---- | :---------- |
|  |  |

### Unit Manager

| Field | Description |
| :---- | :---------- |
|  |  |

### Section Manager

| Field | Description |
| :---- | :---------- |
|  |  |

## Field notes

* It may be good to suggest a maximium length for a title, so that it fits into rendered components.

## Pages


### My Tasks

The My Tasks page will contain a list of task list titles in the left sidebar. Task list titles which contain tasks due today (or soon) should be highlighted.

Clicking on the task list title will display the list of tasks in the main content area.  

### Edit Tasks

(How will this work?)



