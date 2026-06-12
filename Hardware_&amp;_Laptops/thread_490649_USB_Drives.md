---
title: "USB Drives"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by screenname on 2007-07-02
Currently I am using Fiesty Fawn, though presumably this persists nomatter the version.

My issue is that when I plug in my USB drive, the icon appears on my desktop, but I can't write files to it, and when I delete files, they're automatically sent to a folder called "trash.username". Additionally, when I want to remove the usb drive, I have to right click and select "eject".

I have a suspicion that this has something to do with mounting. This is a very cumbersome process considering that I don't have this issue with Windows - I can just plug it in, write files to it, and remove it. Can anyone provide a simple solution to this issue?

edit: Solved. Thanks everyone.

---

### Post by kyphi on 2007-07-02
USB devices mount automatically in Feisty.

I wonder if you have formatted your USB stick in Windows as NTFS.

When you see the icon on the desktop, right click it and go to Permissions.  What is ticked there?

To remove (eject or unmount), yes you have to do that in Ubuntu but you also have to do that in Windows, except in Windows it takes about three submenus to achieve the same thing.

---

### Post by screenname on 2007-07-03
Owner: (me)
Folder access: Create and delete files
File access: ---

Group: root
Folder access: None
File access: ---

Others: 
Folder access: None
File access: ---

Execute: (checked) Allow executing file as program

SELinux context: unknown
Last changed: unknown

Also, it may take more for Windows to achieve the what Linux is doing with my drive currently, but it is clearly not what I want - when I remove the drive from Windows it automatically adjusts to that, while this is not so in Linux.

---

### Post by kyphi on 2007-07-03
My properties file apparently looks quite different to yours.  Mine states under permissions:

Owner: Read - Write - Execute with check boxes next to each entry.  Perhaps it is different for Feisty.

As for your comment:

"Also, it may take more for Windows to achieve the what Linux is doing with my drive currently, but it is clearly not what I want - when I remove the drive from Windows it automatically adjusts to that, while this is not so in Linux."

Just a piece of advice - it is free:  you do NOT yank out USB peripherals whether it is Windows or Linux.  In Windows you 'Stop' your peripherals, using three screens and in Ubuntu you eject (unmount) using a right mouse click.  Next time you are in Windows look at the icon that appears in the bottom right hand corner after you have plugged in your USB peripheral.  I think that the main reason for following this procedure is to give the system time to write to and from the device.

You may find the answer you seek in the following URL:

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

If there is nothing there to ease your pain, you might use the search function at the top of the page.

---

### Post by dabl on 2007-07-03
Here's the Kubuntu version of how I got a working USB drive formatted as NTFS.  I'm sure there is a Gnome way to add yourself to the "fuse" group, I just haven't needed to do that.

[http://kubuntuforums.net/forums/index.php?topic=3084679.0](http://kubuntuforums.net/forums/index.php?topic=3084679.0)

Note the caution regarding NTFS as a journalling file system -- kyphi is correct, you cannot simply yank out the NTFS drive without inducing file corruption.  Use the "eject" or "safely remove" command from the right-click menu on the device icon.  :)

---

### Post by screenname on 2007-07-03
I definitely learned something new from your posts. Thanks to both of you for your assistance!

---

### Post by screenname on 2007-07-03
Alright, update:

I can definitely write files to it. Unfortunately, the problem with deleting still persists - every file that I delete when the USB drive is on my Ubuntu machine is not truly deleted, but in a folder called ".Trash-(myusername)". I have to delete files from it on my Windows machine in order to successfully delete it from the USB drive.

I'm not sure why I would need to format my drive to NTFS or why I would need to add myself to a "fuse" group as I don't know entirely what either of those do.

---

### Post by Rocketmac on 2007-07-03
I ran into this.  You should check to make sure that you have the newest version of ntfs-3g installed for those pesky NTFS-formatted disks.   


Ctrl+H and delete the .Trash*  is what I typically do.  It's not the best solution, but it works.

---

### Post by kyphi on 2007-07-04
Could I enlist your co-operation in a little experiment?

Create a file in Ubuntu - save it to your USB stick - eject the USB stick and remove it.
Then reinsert the USB stick - find the newly created file and delete it.

The reason I am asking this is to eliminate the possibility that you cannot delete because of file name corruption.

Would you try it please.

Also, forget about the NTFS formatting for the moment - that related to establishing permissions.

Also, where is this folder called .Trash-<username>.  Is it in your Home folder?

---

### Post by screenname on 2007-07-04
Kyphi, I followed your instructions, and the newly created file acted as other files did when deleted; it was moved to the ".Trash-<username>" folder. 

.Trash-<username> is in the USB drive itself. This folder invisible when using Ubuntu; I can only see it when looking at the drive on Windows. However, it's indeed there and not specific to Windows - I've looked at the difference in size, and the available space on the USB drive when using Ubuntu does not decrease after deleting files, while it does when doing so on Windows.

---

### Post by kyphi on 2007-07-04
In Ubuntu, after you have inserted your USB stick and the icon appears on your desktop, open the USB folder.

Go to 'View' at the top of the screen and scroll to 'Show Hidden Files' or press Ctrl+H.  That will reveal the .Trash-<username> file.  All it does, is show you what you have deleted from your USB stick.  The deleted file shows also in the recycle bin in the bottom right corner of your desktop.  Once you empty your main recycle bin, the  trash file on your USB stick will also be empty.  Alternatively, you can empty the recycle bin on your USB stick........now that you know where it is.

Enjoy Ubuntu.

---

### Post by Jose Catre-Vandis on 2007-07-04
Alternatively, in Nautilus, go to Edit -> Preferences and select the Behaviour tab

Put a tick in the "Include a Delete Command that bypasses Trash" box

You can now right click, select "Delete" from the sub-menu, and completely delete files on your stick
(or anywhere for that matter)

Warning - use with caution, once they're gone, they're really gone!  :)

---

