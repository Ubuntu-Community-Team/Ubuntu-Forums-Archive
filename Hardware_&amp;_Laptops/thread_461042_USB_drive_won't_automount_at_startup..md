---
title: "USB drive won't automount at startup."
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by kevin79 on 2007-06-01
I have an external Seagate usb hard drive connected to my laptop. The drive is formatted as ext3. When I start up my laptop with the drive connected, the drive isn't automatically mounted. The only way that I can get the drive to mount is to turn the hard drvie off and back on. Once I do that, Kubuntu automatically mounts it. How do I get it so that the drive will mount automatically at boot?

---

### Post by kevin79 on 2007-06-19
Anyone???

---

### Post by ukripper on 2007-06-21
to mount automatically during boot you need to add your drive to fstab to add it using UUID :

First issue following command in terminal:

```
ls -al /dev/disk/by-uuid
```

and now add the uuid listed in front your drive you want to mount to fstab like other drives there.

---

### Post by lifestream on 2008-05-08
Sorry to revive this thread but....

I tried ls -al /dev/disk/by-uuid  
Got:
lrwxrwxrwx 1 root root  10 2008-05-08 15:05 55D123D9E79ABF54 -> ../../sdb1

So I went in fstab and added:
#UUID=55D123D9E79ABF54 /media/USB\040Drive ntfs-3g defaults,force,users 0 0

But it still won't mount. 


I've been trying to get this done for almost a *week* now. Can anyone help?

---

### Post by lifestream on 2008-05-08
I've tried to have the USB drive mount at boot time but that doesn't work.
The other option I have thought about is to add that gnome command that automagically mounts the drive at the session start.

Could you tell me what's the command that nautilus uses when you right click a drive and select mount? Thanks you.....

---

### Post by dryder on 2008-05-09
There is a known problem with Seagate FreeAgent Drives ... I have lost the link but there is quite a bit reported about them in Launchpad. It is the drive, not linux. The drive only wakes up (which is what you need if you want to mount it when booting) in Windows.

The kernel developers have, I believe, agreed 'it needs addressing'.

Google for linux freeagent wake-up .. or whatever


[http://hardware.slashdot.org/article.pl?sid=07/12/09/0651200]("http://hardware.slashdot.org/article.pl?sid=07/12/09/0651200")

[http://news.softpedia.com/news/The-Free-Agent-Gets-Repaired-Linux-Users-Rejoice-73520.shtml]("http://news.softpedia.com/news/The-Free-Agent-Gets-Repaired-Linux-Users-Rejoice-73520.shtml")

---

### Post by ukripper on 2008-05-09
> **lifestream said:**
> Sorry to revive this thread but....

I tried ls -al /dev/disk/by-uuid  
Got:
lrwxrwxrwx 1 root root  10 2008-05-08 15:05 55D123D9E79ABF54 -> ../../sdb1

So I went in fstab and added:
#UUID=55D123D9E79ABF54 /media/USB\040Drive ntfs-3g defaults,force,users 0 0

But it still won't mount. 


I've been trying to get this done for almost a *week* now. Can anyone help?

When you are logged in. Plug your usb drive and let it mount itself. once it has mounted then go to terminal and type following:

```
sudo mount
```
look for your usb drive something like /dev/sdb1 there and copy the whole mount details  for dev/sdb1 into your fstab. you can replace /dev/sdb1 to your UUID in fstab if you want to.

Just reboot then you all done.

---

### Post by lifestream on 2008-05-09
"It is the drive, not linux."
No way! /sarcasm/ That's why I just reformated it as ext3 and it now mounts at boot time, every time, without me having to do anything /endsarcasm/

Ukripper, I've tried it, no good. So I just backed up my drive and formmated it as ext3. It's all good now.

Thanks anyway.

---

### Post by dryder on 2008-05-09
> "It is the drive, not linux."
No way! /sarcasm/ That's why I just reformated it as ext3 and it now mounts at boot time, every time, without me having to do anything /endsarcasm/

Ukripper, I've tried it, no good. So I just backed up my drive and formmated it as ext3. It's all good now.

Thanks anyway. 

I'm glad it is working for you. But it shouldn't matter whether it is ext2/3 or ntfs.
If not the drive, and I have 6, how do you explain all the posts on the net and SeaGate saying it is the drive? I'd be interested to know because mine won't wake up in usb2 after going to sleep mode. And I don't want to disable sleep mode. Did you?
As a mater of interest, what is the date of manufacture of the drive?

---

### Post by dryder on 2008-05-09
lifestream
Having read my above post, it might come across as rude - it is not intended to be.

I am trying to understand the trouble others have and why it works for you - formatting to ext3 does not change the hardware parameters set in the drive. This can only be changed in Windows or, I have read, by using hpdarm or spdarm. I see from the date of your posts that your drive was not manufactured before any changes made be Seagate.

---

### Post by lifestream on 2008-05-09
> **dryder said:**
>  how do you explain all the posts on the net and SeaGate saying it is the drive?

I don't know, I'm not a pro... I've been trying for a while to get the drive to mount at boot, and as we both know, it didn't work, why would it work after formatting to ext3? *shrug* I really don't know :) 

> **dryder said:**
> 
And I don't want to disable sleep mode. Did you?
As a mater of interest, what is the date of manufacture of the drive?
No, I did not disable sleep mode, all the power saving features work great for me :/
I will put my computer to sleep after posting this, and I'll update here letting you know.

Sorry if I sounded upset, it's just I'm sick of having to explain my issue for half hour to every single person who tries to help me, and then they tell me to do stuff I've already told them I've tried.

Also, some people seem to like telling me random things (on irc) like: 
 - It's NOT possible to mount any USB drives at boot time.
 - You MUST buy a shorter USB cable for your usb drive.
Those are the only 2 silly things I remember. 

Mmm... I got the hard drive June .... 2005 or 2006 (it was my birthday, just don't remember which year :P 

Sorry, I also had no idea the problem was specific to SeaGate, no posts before dryders mentioned it was specific to seagate, so I assumed the mount problem was unrelated to the manufacturer... My drive is a maxtor. *shrug*



*EDIT*
Dryder,
The reason why mount at boot time is important to me, is because I log in to my computer very randomly; I can turn it on, look up a recipe online, go do the dishes, go back to the computer, check email, go sweep the floor, go to computer and send a message to a friend, go work on the garden outside for a few mins, come back to computer.

If I have to mount the drive every single time I do that, eek, thats a lot of time wasted. now that I think of it, my computer is set up to sleep at 11 secs of inactivity.... and I notice all of today my usb drive is mounted and ready to use when pc comes back from sleep mode.... (didnt really think about it before, so i dont know how it used to be)



wow that was a mouthful :)

---

### Post by dryder on 2008-05-09
kevin79's was the first post in the thread and he mentioned SeaGate FreeAgent. (It was ext3 also). Hence my post about these drives, not knowing yours is Maxtor (did I miss you saying which make it is?)

Seagate and Maxtor have problems in MAC-OS and linux, Maxtor to a lesser extent in that it is easier to 'work around it' - some have found by formatting to ext3 in Linux as changing the drive's sleep mode is not changeable only in Windows (without using hpdarm/spdarm).

I think that perhaps people advise not to leave them in all the time is because, as you may know, unless ejected, as opposed to unmounted, there is a risk of files not being closed before the drive is 'turned off'. Now Ubuntu can eject usb hdd's - before it could only unmount them - not sure if that means all makes though!

I can assure you (no rudeness) there are many more posts than mine on Ubuntu (archived?) and thousands more on the net re the FreeAgents - I was not trying to be a 'smart-****' :-)

Anyhow, the point is, the Maxtor is working for you, as you want it. :-)

---

### Post by ukripper on 2008-05-10
> **lifestream said:**
> "It is the drive, not linux."
No way! /sarcasm/ That's why I just reformated it as ext3 and it now mounts at boot time, every time, without me having to do anything /endsarcasm/

Ukripper, I've tried it, no good. So I just backed up my drive and formmated it as ext3. It's all good now.

Thanks anyway.

thats great it worked now. I personally have media server with ntfs-drive had the same problem initially. What i did was the above steps and added ```
mount -a 
```to rc.local as kernel sometimes fails to detect ntfs-drives at boot. mount -a command mounts all the entry in fstab for you after the boot process has finished.

---

### Post by dryder on 2008-05-21
lifestream

check this out:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/193154]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/193154")

---

### Post by 3rods on 2008-07-22
```
#UUID=55D123D9E79ABF54 /media/USB\040Drive ntfs-3g defaults,force,users 0 0
```

Not sure if this is relevant, but the original code contains the wrong slash as part of the mount location. ```
/media/USB\040Drive
``` should really be ```
/media/USB**/**040Drive
```. 

Also, the **#** in the front tells mount to skip the line. 

The code to mount the drive appears correct otherwise, just the wrong syntax. Not sure if anyone noticed that.

---

### Post by ukripper on 2008-07-23
> **3rods said:**
> ```
#UUID=55D123D9E79ABF54 /media/USB\040Drive ntfs-3g defaults,force,users 0 0
```

Not sure if this is relevant, but the original code contains the wrong slash as part of the mount location. ```
/media/USB\040Drive
``` should really be ```
/media/USB**/**040Drive
```. 

Also, the **#** in the front tells mount to skip the line. 

The code to mount the drive appears correct otherwise, just the wrong syntax. Not sure if anyone noticed that.

This ain't wrong syntax. "\" is used for parsing whitespace in command line if your directory or filename is something like USB DRIVE it will become -
**USB\ DRIVE**

---

