---
title: "Ubuntu doesn't work on my notebook hp"
date: 2009-04-08
forum: Hardware
---

### Post by elrull on 2009-04-08
hi everybody, this is my first post and i would be very happy if you could help me, i'm desperate.
well i just bought this notebook. it's a hp g60-125nr with
video: geforce go 8200m
hard disk: hitachi hts543225L9A300 ATA
processor: am turion Dual-Core RM x2 64

i have windows vista, but i doesn't fit my needs, so i've tried to install ubuntu 8.10, 8.04 and the beta 9.04 but all seems to fail with my computer.

when i'm in the ubuntu desktop, the video starts to fail, it's so slow, and y can't work because the windows appear too slow, like  ubuntu were to heavy for my pc. 

i think the problem is just that i have not installed the video driver(controller) but when i tried to do habilitate that, nothing happens.

the beta 9.04 tells me that there is no privative hardwares so it doesn't find any drivers to habilitate.

please help me!!!!! i need ubuntu i really need it.

thanks

---

### Post by Sam Lars on 2009-04-10
So you have Ubuntu installed and it's giving you the graphics problems?

---

### Post by avilella on 2009-06-02
Have you tried with the alternate CD?
[http://ubuntuforums.org/showpost.php?p=7253882&postcount=5](http://ubuntuforums.org/showpost.php?p=7253882&postcount=5)

> **elrull said:**
> hi everybody, this is my first post and i would be very happy if you could help me, i'm desperate.
well i just bought this notebook. it's a hp g60-125nr with
video: geforce go 8200m
hard disk: hitachi hts543225L9A300 ATA
processor: am turion Dual-Core RM x2 64

i have windows vista, but i doesn't fit my needs, so i've tried to install ubuntu 8.10, 8.04 and the beta 9.04 but all seems to fail with my computer.

when i'm in the ubuntu desktop, the video starts to fail, it's so slow, and y can't work because the windows appear too slow, like  ubuntu were to heavy for my pc. 

i think the problem is just that i have not installed the video driver(controller) but when i tried to do habilitate that, nothing happens.

the beta 9.04 tells me that there is no privative hardwares so it doesn't find any drivers to habilitate.

please help me!!!!! i need ubuntu i really need it.

thanks

---

### Post by scanzano on 2009-09-23
> hi everybody, this is my first post and i would be very happy if you could help me, i'm desperate.
well i just bought this notebook. it's a hp g60-125nr with
video: geforce go 8200m
hard disk: hitachi hts543225L9A300 ATA
processor: am turion Dual-Core RM x2 64

i have windows vista, but i doesn't fit my needs, so i've tried to install ubuntu 8.10, 8.04 and the beta 9.04 but all seems to fail with my computer.

when i'm in the ubuntu desktop, the video starts to fail, it's so slow, and y can't work because the windows appear too slow, like ubuntu were to heavy for my pc. 

i think the problem is just that i have not installed the video driver(controller) but when i tried to do habilitate that, nothing happens.

the beta 9.04 tells me that there is no privative hardwares so it doesn't find any drivers to habilitate.

please help me!!!!! i need ubuntu i really need it.

thanks

I know exactly what problem you have, but unlike other's relating to a problem of another without a solution I happen to have one.

For the majority of the things I am going to guide you through here will require you to deal with the choppy graphics so be patient.

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
```Now you WILL be asked for  a password. The password is the same as the password you login with. When you type in the password you will not see little star symbols (*). Don't worry it doesn't matter because you are still typing it in. Anywho, when you are done typing in your password hit enter.
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

Sorry if this is a late reply but only recently did i decide to take my time on figuring out how to fix this issue that i had. The only difference is that I have the HP G60 126CA and it isn't such a big difference.

Just a thought. This should be stickied considering that this seems to be a problem with most Nvidia Video Cards. Happened to my Desktop computer as well that is running an old Geforce.

Anyways if you are still experiencing problems private message me and I will do my best to reply with a solution as fast as possible.

---

