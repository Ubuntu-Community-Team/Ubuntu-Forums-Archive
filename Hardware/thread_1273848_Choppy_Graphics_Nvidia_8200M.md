---
title: "Choppy Graphics Nvidia 8200M"
date: 2009-09-23
forum: Hardware
---

### Post by scanzano on 2009-09-23
This is not a problem that I currently have, but a guide to help other people fix a problem with there Nvidia 8200m Video Card on Ubuntu. I got so frustrated with doing this that I figured I should post a guide on what to do. This guide to fixing choppy graphics is as far as I know for only the 8200m but I doubt that it will not work for anyone other Nvidia video cards.

For the whole process of the things I am going to guide you through here will require you to deal with the choppy graphics so try to be patient.

First and foremost.

There are 2 ways of doing this. One way is the easy way which is not always an option. The second way is more command line involved, which is what I had to go through originally.

        [COLOR=Blue]_**The Easy Way (If your lucky enough):**_[/COLOR]
   **1) Allow Ubuntu to update itself (including updated packages for Synaptic). You can do this by:**
a- Clicking on System >> Administration >> Update Manager (this is located in the task-bar at the top of your screen. It is important that you do this first.)
b- And also for Synaptic. System >> Administration >> Synaptic Package Manager (List of programs will update automatically)
[B]
2) Installing the right software:[/B]
        a- If you exited Synaptic Package Manager just re-open it.
        b- In the "Quick Search" bar at the top right of the Synaptic Package Manager window type in "envyng".
c- Now assuming that this will work for you, there will be three specific software packages listed; these are: envyng-gtk , envyng-core and envyng-qt. The only thing you have to do is click the little checkmark box-like buttons just to the left of the package names and then click on "Apply" at the top of the Synaptic Package Manager Window. Just click next/ok/accept on all the windows that pop-up after clicking apply.
        d- Exit Synaptic Package Manager
[B]
3) Updating the Video Card's Driver:[/B]
 a- Click on Applications >> System Tools >> EnvyNG (This will all be located in the taskbar at the top of your screen)
b- Search through the list of drivers that comes up for a driver that has both the checkmarks for compatible and recommended. If there is no driver that is both recommended and compatible then just use one that is only compatible and of the newest version (For example version 2.81.2 compared to version 3.81.2). Click on the checkmark box just to the very right of the appropriate driver.

**4) The simplest of parts:**

      a- Restart your computer and boot into Ubuntu.

      [U][B][COLOR=Blue]Or The Hard Way (Which isn't as hard as I make it out to be):
[/COLOR][/B][/U] 
**1) Open up a terminal/command line. If you do not know how then I pity the fool.....**
Just kidding. Go to Applications >> Accessories >> Terminal (This is all in the taskbar at the top of your screen).

**2) In the terminal/command line that you just opened up type:**
     ```
sudo apt-get install envyng-gtk 
```Now you WILL be asked for a password. The password is the same as the password you login with. When you type in the password you will not see little star symbols (*). Don't worry it doesn't matter because you are still typing it in. Anywho, when you are done typing in your password hit enter.
But Pay attention! You will most likely be asked for conformation of some sort for something. All you have to do is hit the y button and then hit enter. When it is done you should DO NOT CLOSE THE TERMINAL. Just for the sake of not having to type in the sudo password again. I personally find that annoying.

By Default you should not have to install "envyng-core" because it is mandatory that it has to be installed with "envyng-gtk".

Next you are going to type in:
     ```
sudo apt-get install envyng-qt
```Again pay attention to if it asks you to confirm something or not.
When the install is done close the terminal by hitting the x button.

**3) Updating the Video Card's Driver:**
 a- Click on Applications >> System Tools >> EnvyNG (This will all be located in the taskbar at the top of your screen)
b- Search through the list of drivers that comes up for a driver that has both the checkmarks for compatible and recommended. If there is no driver that is both recommended and compatible then just use one that is only compatible and of the newest version (For example version 2.81.2 compared to version 3.81.2). Click on the checkmark box just to the very right of the appropriate driver.

**4) And Yet Again The Simplest of Parts:**

      a- Restart your computer and boot into Ubuntu.

If you are still experiencing problems private message me and I will do my best to reply with a solution as fast as possible.

---

