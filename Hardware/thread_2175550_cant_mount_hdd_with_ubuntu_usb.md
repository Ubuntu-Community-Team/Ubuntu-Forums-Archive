---
title: "cant mount hdd with ubuntu usb"
date: 2013-09-19
forum: Hardware
---

### Post by ryan35 on 2013-09-19
I have old laptop and os is xp. I cant boot it so i tried run ubuntu from usb and i did it, but problem is i wanted to access hdd so i can save images but i cant, i have this error:

[http://imgur.com/EPG7i62](http://imgur.com/EPG7i62)

---

### Post by sudodus on 2013-09-20
Welcome to the Ubuntu Forums :-)

There can be several reasons why you can't read the HDD.

A.  It is physically broken. Let us hope this is not the case. You can check if the connections are good (move the plugs a little to make sure it is good electrical connection to the HDD).

B. The file system is damaged.

1. In this case it might help to run ```
chkdsk /f
``` from Windows. You can boot from a Windows install disk, from a Bart PE or Windows 7 PE  USB drive and run that command. If the damage is fairly small, it may work. (I have managed to repair Windows systems a few times that way.

2. If [FONT=courier new]**chkdsk /f**[/FONT] does not help 'enough' to make Windows run again, you might be able to read the partition and save your personal files after booting again from the Ubuntu pendrive.

-o-

If you post the output of the following commands, it will be easier to help.

I select advanced mode, mark the text and click the **#** icon at the top of the editing window in order to put the output text within

[noparse]```
sudo fdisk -lu
```[/noparse]

tags to make it look like this

```
sudo fdisk -lu
```
and this
```
sudo parted -l
```

Please do the same with the output from the commands :-)

---

### Post by ryan35 on 2013-09-20
I cant boot it with windows repair console or windows xp.
I tiped that 2 commands and i took 2 pictures:
[http://i.imgur.com/NDJ3CD7.jpg](http://i.imgur.com/NDJ3CD7.jpg)
[http://i.imgur.com/VE7d5R7.jpg](http://i.imgur.com/VE7d5R7.jpg)

---

### Post by sudodus on 2013-09-20
It is much easier to mark and paste text from the terminal window to the editing window of the Ubuntu Forums than to take photos and upload them. Mark the text pressing the left button and drag the mouse. Middle click to paste it.  But the information is there in the pictures, so here we go.

The pictures show four primary partitions on the internal hard disk drive /dev/sda. My guess is that the first one contains Windows XP. The second one might be a data partition, but the third hidden fat32 partition and the fourth EFI partition indicate an attempt to install Windows 7 or Windows 8. So the second partition might contain that second Windows. Do you know anything about the history of the computer?

It looks like it should  be possible to mount the partitions. If you can not do it automatically with the file browser, you should be able to do it manually with terminal window commands (when Ubuntu is booted from the USB drive).

Open a terminal window and run this command to mount the first partition

```
sudo mount -t auto /dev/sda1 /mnt
``` and use the file browser to explore it (in the directory /mnt).

Unmount it with ```
sudo umount /mnt
``` and run this command to mount the second partition

```
sudo mount -t auto /dev/sda2 /mnt
``` and use the file browser to explore it (in the directory /mnt).

---

### Post by ryan35 on 2013-09-20
its working but there is another problem, i cant move images to my usb. When i go right click to image or folder i can move it to Home or Desktop. How to move it to usb?

---

### Post by sudodus on 2013-09-20
I'm glad it works for you :-)

You need to mount your USB drive so that it has read and write permissions.

- What USB drive is it? The pendrive that you boot from or some other USB drive (pendrive or HDD)?

- Where and how is it mounted now (by automount I suppose)?

When the target USB drive is mounted (the one you want to copy to), run this command and post the output (mark and paste is easier than to take a photo). See my previous post.

```
cat /etc/mtab
```

---

### Post by ryan35 on 2013-09-20
Am on another computer, this is desktop pc. laptop is uber slow so making pictures is easier then login from laptop and upload it from there. (sry but its really easier).
I see it has automount option on. I have usb that i boot ubuntu and another usb with 4gb.
[http://i.imgur.com/fXgXDyL.jpg](http://i.imgur.com/fXgXDyL.jpg)

---

### Post by sudodus on 2013-09-20
On your boot drive

***/dev/sdb1*** is mounted on ***/cdrom*** with read/write permissions. The drive size is 16GB, and the image of the iso file is less than 1 GB, so there should be a lot of space to copy files to that place. You see it as ***/cdrom*** in the file browser.

And there is a ***fuse*** system which is also read/write (is it a Windows network)? Maybe you can copy a lot of files this way. Check how you see it in the file browser.

---

### Post by ryan35 on 2013-09-20
I mounted first partition and i did that command but doesnt work or i didnt understand what to do [http://i.imgur.com/V36ZIjS.jpg](http://i.imgur.com/V36ZIjS.jpg)

---

### Post by sudodus on 2013-09-20
/dev/sdb1 is already mounted and can been seen with the file browser. You need not mount it. Browse to the directory /cdrom. If you have two browser windows open, you can drag and drop files from the Windows directory to that /cdrom directory.

But let me ask you now: What do you want to do with the computer? (I mean after you have saved the most important personal files.)

- Do you want to make Windows work again?

- Do you want to wipe Windows and install some kind of Ubuntu flavour operating system?

- Or do you want both? (most complicated, but should be possible.)

---

### Post by ryan35 on 2013-09-20
Its my sisters computer and laptop is ruined. It droped several times and bottom of screen is black maybe she will buy new laptop i dont know.

I can access mnt (i guess thats file browser) and i found desktop, there are folders with pictures i need to save. But when i search for cdrom i cant nothing. It doesnt exist.

---

### Post by sudodus on 2013-09-20
OK, the main task is to save files from the computer. [COLOR=#696969]Maybe after that you can try something else, particularly if you have an external monitor, for example test how it works with an installed linux system.
[/COLOR]
-o-

The picture you uploaded indicated that /dev/sdb1 is already mounted to directory /cdrom, and it is on your USB boot drive.

Try these commands (and post the output). The first one is 'ell ess space minus ell space slash'

```
 ls -l /
```
```
ls -l /cdrom
```
```
df -h
```

The output will tell us if you can use /cdrom. (I think so, but I am confused because you cannot find it.)

---

### Post by ryan35 on 2013-09-20
[http://i.imgur.com/I1zxUHR.jpg](http://i.imgur.com/I1zxUHR.jpg)
[http://i.imgur.com/N5xXRGy.jpg](http://i.imgur.com/N5xXRGy.jpg)
[http://i.imgur.com/2wSYxfo.jpg](http://i.imgur.com/2wSYxfo.jpg)

---

### Post by sudodus on 2013-09-20
The directory is there and there are 11 GB free (for your files to be saved). But I cannot see if it is read/write, because the line for /cdrom was outside the screendump of the second picture.

Anyway. Open a new window of file browser and change directory to the 'computer' or 'root directory' '/' (slash). There you should find alongside for example /mnt also /cdrom. Change directory to /cdrom and then you have one browser window at /mnt and one browser window at /cdrom. Now you can drag and drop files (or even directories, but beware, the limit is around 11 GB).

---

### Post by sudodus on 2013-09-20
And it will be slow, very slow, because USB drives are slow compared to an internal HDD. Do not unplug the pendrive until it has finished, maybe several minutes after you think it has finished.

If you have a terminal window open, you can run the command ```
sync
```

and when it returns to prompt, the files have been written to the pendrive.

---

### Post by ryan35 on 2013-09-20
I thought its over :p

[http://i.imgur.com/ohQB9u2.jpg](http://i.imgur.com/ohQB9u2.jpg)

---

### Post by sudodus on 2013-09-20
Please make a new attempt to show the permissions of the /cdrom directory:

ell ess space minus lower-case-ell upper-case-ell space slash space pipeline grep cdrom

```
ls -lL / | grep cdrom
```

and again (if something might have changed)

```
cat /etc/mtab
```

---

### Post by ryan35 on 2013-09-20
[http://i.imgur.com/vYMr9dJ.jpg](http://i.imgur.com/vYMr9dJ.jpg)

---

### Post by sudodus on 2013-09-20
I think the problem is that root owns /cdrom and has exclusive write access. We might be able to change that:

```
sudo chmod -R go+w /cdrom
```

Otherwise you need to copy with root (superuser) privileges, which is also possible. But let us try this first.

---

### Post by ryan35 on 2013-09-20
same error

---

### Post by sudodus on 2013-09-20
What flavour of Ubuntu are you running? If you are not sure, try

```
nautilus
```
```
thunar
```
```
pcmanfm
```

to find out which one is installed in your system. Use the one you have, I call it 'browser' here

Close your old browser windows. Start ***two new browser windows*** as superuser.

```
gksudo browser &
```
```
gksudo browser &
```

Change directory in one to /mnt and the files you want to copy.
Change directory in the other one to /cdrom which is to target, where you want to keep the copies.

Drag and drop files! I think it should work now :-)

---

### Post by ryan35 on 2013-09-20
I remember i installed 12.10 version. All commands for see ubuntu version do not work because it asking me to install something but it never install because ubuntu cant find some destination.

How to open 2 browser windows as superuser? I opet 2 windows and i tipe that in terminal then i go with first window to mnt and with second to cdrom and then i drag&drop?

---

### Post by ryan35 on 2013-09-20
I remember i installed 12.10 version. All commands for see ubuntu version do not work because it asking me to install something but it never install because ubuntu cant find some destination.

How to open 2 browser windows as superuser? I opet 2 windows and i tipe that in terminal then i go with first window to mnt and with second to cdrom and then i drag&drop? Because i did that and same thing.

---

### Post by sudodus on 2013-09-20
See post @21

1. Test which of the following commands that starts a browser: nautilus, thunar, pcmanfm. Probably only one of them starts a browser.
 
Use the commands  that I typed in post #21. You have to replace browser by the name of the browser that you use.

So one of these commands should work. Use it twice to get two browser windows!

```
gksudo  nautilus &
```
```
gksudo  thunar &
```
```
gksudo  pcmanfm &
```

(It seems that you should *not* use --no-desktop)

---

### Post by ryan35 on 2013-09-20
oh, sorry i didnt understand. I started moving images, i will let you know when am done.

---

### Post by sudodus on 2013-09-20
It seems to work for you now :-)

Remember that there are only 11 GB available on that /cdrom partition. Read again the advice in posts #14 and #15.

I will log out for tonight.

---

### Post by ryan35 on 2013-09-20
I did it! Thank you very much, i couldnt do this without you, thank you!

---

### Post by sudodus on 2013-09-21
You are welcome. It was nice to be able to help you :-)

---

