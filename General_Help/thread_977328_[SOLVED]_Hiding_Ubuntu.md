---
title: "[SOLVED] Hiding Ubuntu"
date: 2008-11-10
forum: General Help
---

### Post by jesuisbenjamin on 2008-11-10
Hey Forum!

Ubuntu and Vista are running in dual boot on a Vostro, because the fan is defect a technician is going to pass by tomorrow and repair that. I'm afraid that if he sees i am using Ubuntu that i am going to get in conflict with Dell's support policy (although BIOS is taking care of my fan, not Ubuntu).
How can i let this computer start automatically in Vista and hide Ubuntu's presence at start up?

Thanks :)

---

### Post by CLomax on 2008-11-10
You could overwrite the MBR with EasyBCD if you're using the Windows MBR.

It might overwrite GRUB too if you happen to use that.

I wouldn't do this unless you know how to reinstall GRUB or add Ubuntu back to the MBR.

---

### Post by jesuisbenjamin on 2008-11-10
Ok and what if i uninstall Ubuntu?

---

### Post by ciscosurfer on 2008-11-10
Careful with that axe, Eugene!

Uncomment #hiddenmenu in your /boot/grub/menu.lst to make the GRUB menu "hidden".  Also, set your default value in your menu.lst to the number corresponding to your Vista drive/partition.  Just remember that the numbering scheme begins with "0".  Experiment with this if you're unsure.  You could also set the timeout option to something miniscule, or even set to "0" as well.

You can do this manually or you can use SUM (startupmanager) if you want a GUI to aid you.

---

### Post by ratmandall on 2008-11-10
If you overwrite the grub MBR with windows MBR, 
Ubuntu still installed so you just have to recover grub which is pretty easy with super grub disk [http://supergrubdisk.org](http://supergrubdisk.org).

so unless the tech looks at your hard drives partition's(which he shouldn't seeing as it's go to do with the fan) you will be fine.

---

### Post by jesuisbenjamin on 2008-11-10
> **ciscosurfer said:**
> 
  You could also set the timeout option to something miniscule, or even set to "0" as well.


If i set the timeout option so short, how would i be able to get back to ubuntu when needed?

---

### Post by ciscosurfer on 2008-11-10
By hitting ESC really, really fast! ;-) You don't necessarily need to change it...was just a suggestion as far as speeding up the bootup process...change it to 5 or something, or no change at all.  But to get your menu to show again, you do need to press ESC to see it...change the settings back to what they were before after the fan guy goes away.

---

### Post by jakupl on 2008-11-10
> **jesuisbenjamin said:**
> If i set the timeout option so short, how would i be able to get back to ubuntu when needed?

You can easily use the live cd to boot up with, and then change /boot/grub/menu.lst from there.

---

### Post by jesuisbenjamin on 2008-11-10
> **ciscosurfer said:**
> 
Also, set your default value in your menu.lst to the number corresponding to your Vista drive/partition.  Just remember that the numbering scheme begins with "0".  


Is this the place i should change the partition number?
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)
```

According to the comments i should not uncomment this, but rather change the value (to 2 in this case i think).

(This is unknown terrain to me, i don't want to mess up...)

Cheers :)

---

### Post by ciscosurfer on 2008-11-10
The other option would be to simply unplug the monitor and move it to a different room.  This involves the least amount of effort and when the guy wants to power on the machine, all he cares about is whether the fan is working.

And no, that's not the correct place.  Check out these tutorials ([https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)) and ([https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)) on modifying GRUB options if you want to.  But I still like my 'remove the monitor' idea.

EDIT: a very [thorough tutorial on GRUB options]("http://users.bigpond.net.au/hermanzone/p15.htm"), etc.
.
.
.
.

---

### Post by jesuisbenjamin on 2008-11-10
haha that would not be the best option on a laptop i guess ;)

---

### Post by ciscosurfer on 2008-11-10
Indeed.  Follow my last link in the EDIT of my previous post.  Scroll down to this section:                          **Editing GRUB's menu.lst file**

---

### Post by ratmandall on 2008-11-10
You could change the default Value in /boot/grub/menu.lst to the windows partition number and then set the timeout to 0

In terminal [php]sudo gedit /boot/grub/menu.lst[/php]

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic #THIS = 0
#THE COMPUTER COUNTS FROM 0 ONWARDS
uuid		8e06a18d-7f5e-4fde-be4e-7ff47b934aa3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8e06a18d-7f5e-4fde-be4e-7ff47b934aa3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)#THIS = 1
uuid		8e06a18d-7f5e-4fde-be4e-7ff47b934aa3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8e06a18d-7f5e-4fde-be4e-7ff47b934aa3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+ #DO THE MATH
uuid		8e06a18d-7f5e-4fde-be4e-7ff47b934aa3
kernel		/boot/memtest86+.bin
quiet
```
So get the number where the windows entry is then change the default value(Near the top of the file) to that number.
```

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0 <<CHANGE THIS TO THE NUMBER
```
Edit: AWW SHUCKS

---

### Post by jesuisbenjamin on 2008-11-10
Ok i did that, changed the menu option and it loads Vista automatically.
Also i changed the timeout to 1 sec and uncommented #hiddenmenu

At startup though, i can still read LOADING GRUB etc...

Is there any way to get rid of this? It would be great. I imagine a technician would be used to see something else and may catch this. Else i would have to create some diversion, like breaking a glass each time he will start up :D

---

### Post by starcannon on 2008-11-10
> **ratmandall said:**
> If you overwrite the grub MBR with windows MBR, 
Ubuntu still installed so you just have to recover grub which is pretty easy with super grub disk [http://supergrubdisk.org](http://supergrubdisk.org).

so unless the tech looks at your hard drives partition's(which he shouldn't seeing as it's go to do with the fan) you will be fine.

+1 to this idea, read the documentation, and you should be able to restore windows mbr for the visit (no grub loading screen or anything) and then restore grub after the visit.

It's either that or hire one of your friends to dress up like a sasquatch and have him run by the window each reboot, and you can yell; "OMG did you see that!?! I think theres a friggen sasquatch in my yard!"; I think this is less obvious, messy, and over all less expensive than breaking glasses each reboot (remember he'll be working in windows so there will be lots and lots of reboots).

GL and have fun.

---

### Post by jesuisbenjamin on 2008-11-10
OK i didn't dare to put it down to 0 by fear of not having the opportunity of pressing ESC but changed it to 0.25 sec.
Would i put it on 0 am i not screwed then?

---

### Post by ratmandall on 2008-11-10
> **jesuisbenjamin said:**
> OK i didn't dare to put it down to 0 by fear of not having the opportunity of pressing ESC but changed it to 0.25 sec.
Would i put it on 0 am i not screwed then?

No if you put it to 0 all you have to do is boot into your live cd and edit the timeout in /boot/grub/menu.lst .
> **starcannon said:**
> 

It's either that or hire one of your friends to dress up like a sasquatch and have him run by the window each reboot, and you can yell; "OMG did you see that!?! I think theres a friggen sasquatch in my yard!"; I think this is less obvious, messy, and over all less expensive than breaking glasses each reboot 


I frigging lawled out loud.

---

### Post by jesuisbenjamin on 2008-11-10
> 
If you overwrite the grub MBR with windows MBR,
Ubuntu still installed so you just have to recover grub which is pretty easy with super grub disk [http://supergrubdisk.org](http://supergrubdisk.org).

So how would i go about doing that?

---

### Post by jesuisbenjamin on 2008-11-10
I've been browsing the forum to find how to restore Vista MBR and later on retrieve GRUB but found nothing relevant.
If anyone could guide me through this...

---

### Post by jesuisbenjamin on 2008-11-10
It's me again ):P

Is would [this procedure]("http://ubuntuforums.org/showthread.php?t=622828") be the answer to my issue?
Then i need to figure out how to restore GRUB after the fan-guy has gone?

Cheers.

---

### Post by snowpine on 2008-11-10
Dell sells computers with Ubuntu pre-installed; I really don't think dual booting Windows and Ubuntu will void your warranty. :)

---

### Post by jesuisbenjamin on 2008-11-10
WhaHAAAhahahaaaarg!:eek:

this is sooo cool :popcorn:

Vive l'Oubounetou

---

### Post by CLomax on 2008-11-10
> **jesuisbenjamin said:**
> WhaHAAAhahahaaaarg!:eek:

this is sooo cool :popcorn:

Vive l'Oubounetou

Calm down, dear. It's an operating system. ;)

---

### Post by ciscosurfer on 2008-11-10
This may be moot at this point, but here's the community documentation: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Otherwise, what type of diversionary tactics were employed? \\:D/

---

