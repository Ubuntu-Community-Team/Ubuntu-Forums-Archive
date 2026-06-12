---
title: "Force mounting external drive"
date: 2009-04-18
forum: Hardware
---

### Post by Vostrocity on 2009-04-18
I have an USB HDD that I haven't used since a couple months ago with Windows. Usually I just wait til the drive doesn't sound like it's clicking anymore and then power it off (no safe removal). Nothing bad happend to either Windows or the drive so that's how I always removed it. Well now it won't mount in Ubuntu obviously. I have plenty of Windows computers around but just for future reference I want to know how safe it is to force mount it. 
"Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility." Very sloppy grammar btw. ;)

---

### Post by Vostrocity on 2009-04-23
Any responses here?

---

### Post by SuperSonic4 on 2009-04-23
```
sudo mount -t [COLOR="Red"]ntfs-3g[/COLOR] /dev/sd[COLOR="Red"]XX[/COLOR] /media/[COLOR="Red"]disk[/COLOR] -o force
```

note that red text means you'll have to put your drive specific details in: ntfs-3g is for ntfs devices, vfat is for fat devices.

sdXX is where the external drive is mounted, you can always check it's location (and filesystem) with ```
sudo fdisk -l
```

/media/disk is where the drive will be mounted to. You may need to do ```
sudo mkdir /media/[COLOR="Red"]disk[/COLOR]
``` if the mount directory does not exist.

---

### Post by Vostrocity on 2009-04-23
Ok but what's the chance of corrupting data on the disk? It says to force mount "for your own responsibility".

---

### Post by SuperSonic4 on 2009-04-24
I've done it a few times (about 3-5) and nothing has happened to my data. I can't say whether you'll be unlucky or not but I believe it's a small chance

---

### Post by Vostrocity on 2009-04-25
Ok so the dialog box says that I should use mount -t ntfs-3g/dev/sdb1/media/Lacie Files -o force, which is basically what you said. And then it says to run as root so I add in sudo. Well then it asks for my password. I type it in perfectly but it keeps saying that it's wrong. :confused:

---

### Post by Poleh on 2009-04-26
does your folder /media/Lacie Files exist? you should have that folder before mounting to it.

---

### Post by Vostrocity on 2009-04-26
Idk, where is it supposed to be? But I doubt that has something to do with the password being wrong.

---

### Post by KhurramM on 2009-04-26
Try reformatting your hard using FAT32, u will never, hopefully, get to use force.

It can be used both for linux and windows machines.

Hope this can be of help.

---

### Post by thatcooldude on 2009-04-26
> **Vostrocity said:**
> Ok so the dialog box says that I should use mount -t ntfs-3g/dev/sdb1/media/Lacie Files -o force, which is basically what you said. And then it says to run as root so I add in sudo. Well then it asks for my password. I type it in perfectly but it keeps saying that it's wrong. :confused:

Have you set a root password before?  Try issuing the following command in your Terminal:

```
sudo passwd
```

Type in a desired root password, then confirm it.

Then try the sudo command you were attempting before and you should be able to mount the drive successfully.  You're correct - the error you're receiving has to do with the password and not the command.  I would hold off on reformatting until you've exhausted your other options!

Please post back and let me know if setting the password works!

---

### Post by Vostrocity on 2009-04-28
> **KhurramM said:**
> Try reformatting your hard using FAT32, u will never, hopefully, get to use force.

It can be used both for linux and windows machines.

Hope this can be of help.

Lol why would I want to use FAT32, it's a 750GB hard drive.


> **thatcooldude said:**
> Have you set a root password before?  Try issuing the following command in your Terminal:

```
sudo passwd
```

Type in a desired root password, then confirm it.

Then try the sudo command you were attempting before and you should be able to mount the drive successfully.  You're correct - the error you're receiving has to do with the password and not the command.  I would hold off on reformatting until you've exhausted your other options!

Please post back and let me know if setting the password works!

Here's what I get.
```

andrew@Vostrocity:~$ sudo passwd
[sudo] password for andrew: 
testingSorry, try again.
[sudo] password for andrew: 
testtestSorry, try again.
[sudo] password for andrew: 
testing againSorry, try again.
sudo: 3 incorrect password attempts
andrew@Vostrocity:~$ testing again

```
And that's the exactly what happens when I get the problem in the first place. :confused:

---

### Post by thatcooldude on 2009-04-28
Then it looks like the problem is your root password has been set to something you no longer know :/

Try [resetting your root password]("http://www.wallpaperama.com/forums/how-to-reset-linux-root-forgotten-passwords-get-retrieve-root-password-t956.html") then retry your previous commands

```
sudo mount -t ntfs-3g/dev/sdb1 '/media/Lacie Files' -o force
```

**NOTE: **I've added 'single quotes' around the mount point which is new (compared to your previous post).  You have a space in the name of your mount point (Lacie Files) which Ubuntu will cut off at Lacie without the quotes.

Enter the password (if it's needed) and your drive should mount.

If you get an error like:

```
mount: mount point /media/Lacie Files does not exist
```

You first need to create the folder or "mount point" for Ubuntu to mount the drive.

Type:

```
sudo mkdir 'media/Lacie Files'
```

**NOTE: **Once again - the quotes are important! :D

To create the mount point, then try the sudo mount command one more time - you should be good to go!

---

### Post by Vostrocity on 2009-04-29
Weird, I still can't change the root password. Maybe I'm not following the instructions correctly. When I'm booting using the instructions in the link I first hit one of those old-looking 8 bit text only dialogs. There were a couple options like "repair", "clean", and one that was "root". The description for it was "drop down to root terminal" or something. I'm not sure if that's where I was supposed to go. But anyways I couldn't figure out how to select it so I just canceled and let it boot up. And then I typed the following into Terminal.

```

andrew@Vostrocity:~$ passwd
Changing password for andrew.
(current) UNIX password: 
pass
passwd: Authentication token manipulation error
passwd: password unchanged

```

I'm thinking that maybe I'll just uninstall 8.10 and then do a clean install of Jaunty since I haven't upgraded yet (due to me needing to move things onto this external drive that I'm having problems with to free up space). Thanks for your help so far anyways.

---

### Post by thatcooldude on 2009-04-29
Reboot one more time and go into the "root" terminal option that you saw.

Follow the previous steps and you should be able to get up and running.

Ubuntu has different privilege levels and "root" is the equivalent of god :D When you type in "sudo" you're performing commands at a "root user" permission level.

---

### Post by Vostrocity on 2009-04-29
Ok I'll try again in a couple minutes. I've tried getting into that menu, but since it's all text-based I had a hard time figuring out how it works. I typed "root" and it did highlight that menu option but then typing "ok" or "<ok>" doesn't do anything.

---

### Post by Vostrocity on 2009-04-30
Stupiiid.. I can't figure it out. I can select any menu option by typing the name but I can't get it to actually execute anything! :-x

---

### Post by thatcooldude on 2009-04-30
[http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu](http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu)

That's all I can recommend.  I'm not sure if anyone else can chime in on how to force a reset if you're not sure of your current password :/  I think I've reached my limits as far as my knowledge goes...sorry!

---

### Post by Vostrocity on 2009-04-30
Ok well thanks. I'll just be using 8.10 for a week or so until I have time to wipe my HDD and install a triple boot between Vista/7 RC 1/Jaunty. :)

---

### Post by SuperSonic4 on 2009-04-30
You can mount your external drive via the root prompt shell that you go to in recovery mode using the command in post 6. From there you can use mv or cp to move/copy your files to the external. Something like

```
mv -v ~/.mozilla /media/Lacie\ Files
```

You can use tab completion to help

---

### Post by Vostrocity on 2009-04-30
Actually the reason why I couldn't change my root passwd in the first place was because I couldn't access the root prompt.

---

