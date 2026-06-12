---
title: "How can I use Ubuntu to recover Windows files?"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by vivek2009 on 2009-07-03
I have laptop loaded with Windows XP. The windows dll file is corrupted and can't let me log in. Can I use ubuntu boot CD to backup the files stored in windows partition?
 
I did some research. Based on what I understand, I downloaded iso file from [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download). Now, I need to burn this into DVD and use that DVD to boot my windows-screwed-up laptop. Burning instructions are at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
Good documentation on installing ubuntu is here -> [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
 
I haven't done any of these yet. I want to understand the whole process first before I venture into this. 
 
Once I install, how do I see files in windows? [http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/](http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/) and [http://www.wikihow.com/Access-Windows-Files-in-Ubuntu](http://www.wikihow.com/Access-Windows-Files-in-Ubuntu) give useful information about that.
 
Great. Now, the unanswered question is: How do I copy all these windows files into DVD for the backup? I understand that you can view the windows files from ubuntu. Is there any software in ubuntu that takes any file (ubuntu or windows) and burn it in the CD/DVD drive? 
 
I put in all the steps here so that it will be useful for someone that lose all his/her windows file. It may even encourage people like me to switch to Ubuntu.
 
Thank you.

---

### Post by Joe88 on 2009-07-03
You can use the Ubuntu boot CD to access your Windows files and then copy/write them to a DVD,CD,USB stick,SD card etc.

**You don't need to install Ubuntu on your hard drive.**

_**Steps:**_

**NOTE: There are many typing and grammar mistakes in the following guide.**

Make an Ubuntu boot DVD
-----------------------
1.Download a disc image file (.iso) from ubuntu.com
2.Burn this file to a DVD using CD/DVD burning software like this free software:_[Active ISO Burner]("http://download.cnet.com/Active-ISO-Burner/3000-2646_4-10602452.html?tag=mncol")_

Boot Ubuntu from the boot DVD
-----------------------------
3.Start your computer, when its starts your will see a screen wich tell you to press a particular key if you want to access your BIOS/Setup - press this key before the screen stops being displayed
4.You will then be presented with a simple menu screen, which you can navigate through and interact with using your keyboard; find the menu allowing you to configure your computers boot order
5.Set it to boot from your CD/DVD drive before it tries to boot from your hard drive
6.if you haven't done so already, put your boot DVD into your drive
7.Quit your BIOS and save the changes
8.Your computer will restart and it will then start your Ubuntu boot DVD
9.From the opening menu, use your keyboard to choose the option called **"Try Ubuntu without making any changes to your computer"**

The Ubuntu operating system will now boot up.

**I don't explain everything you need to know about using the following Ubuntu software, but this software is similar to Windows software, so you should be able to work out how to them it your self. For example, the left mouse button is used to create selection boxes, in the same way that its used in Windows.**

Finding and accessing your Windows Files
----------------------------------------
10.Look at the menu bar at the top of your screen, it will have 3 drop down menus called applications,places,system - click on "places"
11.From the presented drop down menu click "computer"
12.The ubuntu equivalent of Window explorer will now be started, and you will see the drives,removable memory and hard drive partitions detected on your computer - click on partition icon for your windows hard drive partition

The Ubuntu "Explorer" program will now show all the folders  and files from your Windows partition - you can now access them.

Its up to you, which method you use for backing up your files.


Backing Up your Windows files to a CD/DVD
-----------------------------------------
a.In the menu bar mentioned in step 10 click on "applications"
b.The drop down menu will give you access to all the applications installed on the boot disc under categories; the disc burning software is "under the Sound & Video category" move your mouse over this
c.From the menu displayed, you will see the disc burning program called "Brasero Disc Burning"; left click on it
d.When its opening screen is display click on the "Data project" button
e.Insert a blank DVD/CD into your computer disc writing drive

You can now use this software to queue up Windows folders and files to be burnt to the blank DVD/CD - after you have added a folder/file to the queue the displayed remaining CD/DVD space will be updated.

To do this:

f.Under "Places" click on the picture which represents your Windows partition accessed in step 12 - all the files and folders on your window partition will now be displayed in the disc burning program
g.Use your mouse to navigate to the directory containing the folders and/or files you want to add to the disc burning queue
h.Left click on a folder or file to select it, if you hold shift and click on another folder file displayed above or below it, you will see that all the folder and files in between will be selected.
i.With the folder(s) and/or files(s) selected, click the add button

Repeat these steps for all your other files, when you have finished or cannot queue up any more files and folders for a disc because it has no more space - you can burn these to the disc by clicking the burn button.
 
Backing Up your Windows files to a USB / any other removable memory
-------------------------------------------------------------------
The Ubuntu "Explorer" program will have a "places" column displaying all the memory related stuff you saw when you first started it - from here you will be able to navigate straight to your USB stick / SD card / any other removable memory attached to your computer.

a. Select file/folder(s) you want to backup by left clicking on the file/folders or holding it down to make a selection box (like in Windows) 
b. from the file menu shown at the top of the Ubuntu "explorer" left click edit
c. then left click copy
d. under places, left click on the picture representing the USB stick you want to back up to
e. from the file menu shown at the top of the Ubuntu "explorer" left click edit
f. then left click paste

The windows file will now be saved onto your USB stick, when this is completed it will appear there. You can use the back arrow to go back to the Windows partition you were in, before step c. 

Repeat these steps for all of the files and folder you want to back up to your removable memory.

Shutdown
----------------------
When your finished you should be able to work out how to close down the programs your self, to display the shutdown menu click on the red button on the right side of the program bar (the bar with the drop down menus mentioned in step 10).

---

### Post by vivek2009 on 2009-07-03
Thank you Joe. I bought a external hard drive and transferred all content to that. Because I was "trying" the ubuntu, it was accessing the software components from the ubuntu DVD. So, I couldn't write the data to the DVD writer. I wanted to keep the external hard drive anyway just to be safe to handle future accidents.
 
So far it's working. I am still transferring all the data to external hard drive, there is 60+GB data, DVDs wouldn't have worked for all data. External hard drive is the good solution, but it's expensive. If you want to take backup for less than 10GB, best option is to install Ubuntu (insteadof just trying it). By then, your DVD drive is free for you to write backup DVDs.

---

