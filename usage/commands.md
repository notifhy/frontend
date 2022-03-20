---
description: This page documents the available commands.
order: 2
---

# Commands

## Information
Click on a command to learn more about it.

+++ **/channel**
Modify the channel for the Defender or Friends Module

||| Cooldown
5 seconds
||| Requires Registration
Yes
||| Server Channel Only
Yes
|||


!!!warning
You must have the **Manage Channel(s)** or **Manage Webhook(s)** permission to use this command.
!!!
+++ **/data**
View or delete your data stored by this bot

||| Cooldown
10 seconds
||| Requires Registration
No
||| Server Channel Only
No
|||

!!!danger
**/data delete** will not remove everything. To also delete log files and similar, contact Attituding.
!!!
+++ **/help**
Displays helpful information and available commands

||| Cooldown
5 seconds
||| Requires Registration
No
||| Server Channel Only
No
|||
+++ **/language**
Override the language for this bot

||| Cooldown
10 seconds
||| Requires Registration
No
||| Server Channel Only
No
|||

!!!success
English is the only language currently supported
!!!
+++ **/modules**
Add or remove modules for your Minecraft account

||| Cooldown
5 seconds
||| Requires Registration
Yes
||| Server Channel Only
No
|||
+++ **/player**
View basic data on almost any Hypixel player

||| Cooldown
10 seconds
||| Requires Registration
No
||| Server Channel Only
No
|||

!!!warning
This command may be disabled in the future.
!!!
+++ **/register**
Link your Minecraft account to begin using the modules offered

||| Cooldown
5 seconds
||| Requires Registration
No
||| Server Channel Only
No
|||
+++

## Structures
The layouts of each command in the YAML format.

==- /channel
```yaml
name: channel
description: Configure a channel for the Defender or Friends Module
options:
    - name: defender
      description: Set or remove the channel from the Defender Module
      options:
          - name: set
            description: Set a channel for the Defender Module
            options:
                - name: channel
                  description: A channel to send alerts to
                  type: CHANNEL
                  channel_types: [ChannelTypes.GUILD_TEXT]
                  required: true
          - name: remove
            description: Remove the channel from the Defender Module and send alerts via DMs
    - name: friends
      description: Set a channel for the Friends Module
      options:
          - name: set
            description: Set a channel for the Friends Module
            options:
                - name: channel
                  description: A channel to send logins and logouts to
                  channel_types: [ChannelTypes.GUILD_TEXT]
                  required: true
```
==- /data
```yaml
name: data
description: View or delete your data stored by this bot
options:
    - name: delete
      type: SUB_COMMAND
      description: Delete your data - there is a confirmation step to prevent accidents
    - name: view
      description: View some or all of your player data
      type: SUB_COMMAND_GROUP
      options:
          - name: all
            type: SUB_COMMAND
            description: Returns a file with all of your player data
          - name: history
            type: SUB_COMMAND
            description: Returns an interface that shows your player history
```
==- /help
```yaml
name: help
description: Displays helpful information and available commands
options:
    - name: commands
      type: SUB_COMMAND
      description: Displays information about commands
      options:
          - name: command
            type: STRING
            description: A command to get info about. This parameter is completely optional
            required: false
            choices:
                - name: '/channel'
                  value: channel
                - name: '/data'
                  value: data
                - name: '/help'
                  value: help
                - name: '/language'
                  value: language
                - name: '/modules'
                  value: modules
                - name: '/player'
                  value: player
                - name: '/register'
                  value: register
    - name: information
      description: 'Returns information about this bot '
      type: SUB_COMMAND
```
==- /language
```yaml
name: language
description: Override the language for this bot
options:
    - name: language
      type: STRING
      description: The language to use for the override
      required: true
      choices:
          - name: Reset Override
            value: Auto
          - name: English (English)
            value: en-US
```
==- /modules
```yaml
name: modules
description: Add, remove, and configure modules for your Minecraft account
options:
    - name: defender
      type: SUB_COMMAND
      description:
          The replacement to HyGuard - get notified on logins, logouts, version
          changes, and more
    - name: friends
      description:
          Know when your friends are online by sharing logins and logouts with
          each other
      type: SUB_COMMAND
    - name: rewards
      description:
          Never miss a daily reward again - get notifications to claim your daily
          reward at your convenience
      type: SUB_COMMAND
```
==- /player
```yaml
name: player
description: View basic data on almost any Hypixel player
options:
    - name: status
      type: SUB_COMMAND
      description: Displays general information about the player
      options:
          - name: player
            type: STRING
            description: The UUID or username to search
            required: true
    - name: recentgames
      description: Displays the player's recently played games
      type: SUB_COMMAND
      options:
          - name: player
            type: STRING
            description: The UUID or username to search
            required: true
```
==- /register
```yaml
name: register
description: Link your Minecraft account to begin using the modules offered
options:
    - name: player
      type: STRING
      description: Your username or UUID
      required: true
```
===