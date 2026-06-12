---
title: "How to copy files from USB drive"
date: 2008-11-05
forum: General Help
---

### Post by NitroBooster on 2008-11-05
I put in the USB drive into Ubuntu 8.10, it sees the drive, I see my files in it, but I can't copy them onto the main drive via the GUI. I get an error permission denied, although I'm logged in as root. I can't find the USB stick through the shell. Where does it automount to?  I tried using the find command to search for one of the .iso files that are on the USB stick, but it finds nothing.

---

### Post by qpieus on 2008-11-05
USB drives usually mount to /media. So look there and see if there's a subdirectory called "usbdisk" or perhaps the disk label.```
ls /media
```

As far as copying files from the usb drive - where are you trying to copy the files to? And you say you are logged on as root. Are you sure of that? By default the root account is disabled in ubuntu. If you are in fact not root, then that's why you can;t copy. A regular user can normally only copy files into your /home/username directory. (you can copy files elsewhere but you need to use the sudo command to do it)

---

### Post by nothingspecial on 2008-11-05
```
gksudo nautilus
``` will open your files as root.

You can then copy, delete, move to your hearts content.

Be wary though you can mess up big time if you`re not careful.

---

### Post by NitroBooster on 2008-11-06
I figured out how to copy, but the .iso I copy aren't reading right.

For example when I do

$cd /usr/src/
$cp /media/KINGSTON/some.iso .

The files move to the /usr/src/, but VirtualBox is unable to use them for some reason. Says the aren't registered right or something and gives an error.

However, I can use VirtualBox to boot off my .iso files if I point it directly to the USB stick just fine.

Anyone have any idea?

I'm gonna try the nautilus way...

---

### Post by qpieus on 2008-11-06
Try placing the iso somewhere in your /home directory and then have virtualbox boot from that iso. I run isos all the time from my hard drive inside virtualbox and it works just fine. But that's when the iso is in my home or some other directory that I own. /usr/src does not belong to you so maybe that's part or all of the problem. Is there a reason you are trying to put the iso in /usr/src? I guess I don't see the point in that...

My other suggestion is to note the exact error it gives and then search here or on google to see if other people have had that error.

---

### Post by NitroBooster on 2008-11-07
Moving it from /usr/src/ to home directory did not help :(


[IMG]http://i38.tinypic.com/15q2kqo.gif[/IMG]

---

### Post by qpieus on 2008-11-09
According to the virtualbox site, the VERR_ACCESS_DENIED error seems to be related to a permissions problem. 

So lets start over. 
I see from your error picture that the file resided in /home/adminuser. OK, dumb question, were you logged in as "adminuser" when you tried to have virtualbox load this iso? If not, that might explain the error since you probably wouldn't be able to go into another user's directories.

As far as getting virtualbox to use the iso, how did you do it? Here's how I do it:
open virtualbox
highlight the desired VM and click on "Settings"
In the setting window, click on CD/DVD-ROM
click on Mount CD/DVD drive and ISO image file
Use the folder icon next to the iso path area and browse to the desired iso file.
Click Ok when done and then start the VM.

Please list the permissions of the iso file, too.

---

### Post by scouser73 on 2008-11-10
To copy files in Root, use this command **gksudo nautilus** then go to your drive where you want to copy from, right click, select **Properties** then the **Permissions** tab and change the owner to you.

---

