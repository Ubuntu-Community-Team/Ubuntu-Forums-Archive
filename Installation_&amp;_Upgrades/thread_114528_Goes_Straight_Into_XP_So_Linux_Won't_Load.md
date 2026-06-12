---
title: "Goes Straight Into XP So Linux Won't Load"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by Glass Casket on 2006-01-08
I know I made a thread about this already, but thought that this section would be more appropriate.

**So here is my problem:**

So I just finished trying to dual boot XP with Ubuntu for the tenth time. I set up my first linux partition as the primary and all other partitions logical. Then it asked me if I wanted to load the bootstrap loader in the MBR, I didnt know exactly what to do, so I checked yes.

Then when my system finished rebooting to finish the instalation, it goes straight to XP. So i'm now begining to think that I wasen't supposed to put the bootstrap loader in the MBR.

If that's what stopped me from dual booting, is there a way I can move the bootstrap loader? Or do I have to redo the whole instalation and pick not put the bootstrap loader in the MBR?

**My system is as follows:**

I have three hardrives.

Drive #1: One partition with all my music in NTFS.
Drive #2: Windows XP with 5 partitions.
Drive #3: Trying to get Linux on it.

The bootloader was GRUB.

Also, when I was setting up al my partitions on the third disk, I put it as type '/' (root). But there was also an option to put it as type boot.

I set up XP first.

And for some reason, the drive with Linux dosen't show up in the BIOS.

Any help would be greatly appreciated.

Thanks.

---

### Post by DoorGunner on 2006-01-08
I have a dual boot as well.....so do many others here.... Most of the time grub is set for a very fast start.....

When i start up....right in the first few seconds of the start up I see the following:
1  I Get compaq screen that comes up 3-5 seconds. 
2 the screen goes blank for 1 second.
3 you should see an ubuntu screen or a little flash of grub in the upper left corner for 3 seconds then windows boots.

Pay close attention to the abunutu part or what ever image you get. It may just say grub really quickly then start booting window.

What you need to do is press enter at any indication of grub or ubuntu. 

Then you should see some options. Once you get in you can edit your grub to give you say 30 seconds. If you can get to that part or discribe the first few seconds we can help.

---

### Post by Glass Casket on 2006-01-08
[QUOTE=DoorGunner]I have a dual boot as well.....so do many others here.... Most of the time grub is set for a very fast start.....

When i start up....right in the first few seconds of the start up I see the following:
1  I Get compaq screen that comes up 3-5 seconds. 
2 the screen goes blank for 1 second.
3 you should see an ubuntu screen or a little flash of grub in the upper left corner for 3 seconds then windows boots.

Pay close attention to the abunutu part or what ever image you get. It may just say grub really quickly then start booting window.

What you need to do is press enter at any indication of grub or ubuntu. 

Then you should see some options. Once you get in you can edit your grub to give you say 30 seconds. If you can get to that part or discribe the first few seconds we can help.[/QUOTE]

Thanks for the quick reply!

I'm going to try that now and i'll post back in a few minutes.

---

### Post by Glass Casket on 2006-01-08
I don't see anything related to GRUB or Ubuntu...

---

### Post by DoorGunner on 2006-01-08
what kind of computer do you have?? just out of interest?

You have done the right thing by loading to the mbr...... so we need to get you into ubuntu.

can you describe your start up sequence??

---

### Post by Glass Casket on 2006-01-08
It's an MDG, with an Intel motherboard.

I'm thinking maybe I didnt make the right type of partition or something.

---

### Post by DoorGunner on 2006-01-08
Ok..... when the computer starts do this....try to press enter every couple of seconds or so.....Grub may show itself...... just be aware you need to stop pressing enter when it does.

What should happen is a new page with some options will appear....Similar to if you were going into your bios.:)  If you do get a new page select ubuntu

---

### Post by Glass Casket on 2006-01-08
**My boot up sequence is as follows:**

1. Intel splash screen
2. Blank screen for a second or two
3. Windows XP splash screen

And i've tried pressing 'Enter' during the blank screen and it did nothing.

Is there any way we could talk on Msn? It would be much faster.

---

### Post by DoorGunner on 2006-01-08
try what i just said during between the intel splash and xp splash.....every second or so


my msn is [email]door_gunner_2@hotmail.com[/email]

---

### Post by DoorGunner on 2006-01-08
It sounds as though you have done everything correctly.....Does anyone else have any Ideas for Glass Casket.

---

### Post by Glass Casket on 2006-01-08
[QUOTE=DoorGunner]It sounds as though you have done everything correctly.....Does anyone else have any Ideas for Glass Casket.[/QUOTE]

Yeah!

I've tried it all. I've made the partioner make the partitions, i've made them manually, i've made the partitions of LVM or whatever that options is.

I'm litteraly on my 15th try and have run out of ideas.

If anyone has any help they can provide, it would be greatly appreciated.

Thanks.

---

### Post by benco on 2006-01-09
I think GRUB was installed on the MBR of your 3rd disk, so, as your boot disk is the 2nd (XP disk), it is normal that XP starts and not GRUB.
2 options :
#1 : change the boot order of your disks in the BIOS to boot disk #3 first.
#2 : install GRUB on the MBR of disk #2.
Todo that, you need to boot on a live CD and type 
> 
# mount -t ext3 -o rw /dev/hdc1 /mnt
# chroot /mnt
# grub-install /dev/hdb

(I assume that disk#1 is /dev/hda, disk#2 is /dev/hdb and disk#3 is /dev/hdc and your root partition is /dev/hdc1)
As I wrote in another post, I'm not sure the mount/chroot is mandatory but ... just in case !

---

### Post by Glass Casket on 2006-01-09
[QUOTE=benco]I think GRUB was installed on the MBR of your 3rd disk, so, as your boot disk is the 2nd (XP disk), it is normal that XP starts and not GRUB.
2 options :
#1 : change the boot order of your disks in the BIOS to boot disk #3 first.
#2 : install GRUB on the MBR of disk #2.
Todo that, you need to boot on a live CD and type 

(I assume that disk#1 is /dev/hda, disk#2 is /dev/hdb and disk#3 is /dev/hdc and your root partition is /dev/hdc1)
As I wrote in another post, I'm not sure the mount/chroot is mandatory but ... just in case ![/QUOTE]

Thanks man, i'll try that!

But is it normal for only one of the disks to show up in the boot order in the BOIS?

---

### Post by Glass Casket on 2006-01-09
So I managed to get GRUB going, but got an error.

---

### Post by Glass Casket on 2006-01-09
So I installed everything again, for about the 20th time! And got GRUB loading, but it gives me an error, ''Error 17'.

Any ideas?

---

### Post by Sef on 2006-01-09
From Gentoo, this is what it says  about GRUB Error 17:

> Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Be sure to check your root(x,y) settings in your grub.conf. 

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it.

[http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

---

### Post by Glass Casket on 2006-01-09
[QUOTE=Sef]From Gentoo, this is what it says  about GRUB Error 17:



[http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")[/QUOTE]

Thanks for the reply, but I still have no idea how to fix it.

---

### Post by Sef on 2006-01-09
> Thanks for the reply, but I still have no idea how to fix it.

Here's a thread that may help you:

[http://ubuntuforums.org/showthread.php?t=101316]("http://ubuntuforums.org/showthread.php?t=101316")

---

### Post by Glass Casket on 2006-01-09
[QUOTE=Sef]Here's a thread that may help you:

[http://ubuntuforums.org/showthread.php?t=101316]("http://ubuntuforums.org/showthread.php?t=101316")[/QUOTE]

That still didn't help :(

---

### Post by DoorGunner on 2006-01-09
ok We got him up and running.

What happened was he has an unusual setup.....

sd0 was a music drive
sd1 was windows
sd2 was Kubuntu

some of the trouble shooting established that grub was not in the right place. I think what may have happened origionally was grub installed on sd0 or his current drive. in any case we found it on sd2. Bios is now set to sd2 ...rebooted and kubuntu and Windows XP now works.........

after a couple of learning curve things with Kubuntu (no gedit or gnome edit) and finding Adept he is now on his way.

Congrats Glass Casket you are finally up and running.

---

### Post by Glass Casket on 2006-01-09
[QUOTE=DoorGunner]ok We got him up and running.

What happened was he has an unusual setup.....

sd0 was a music drive
sd1 was windows
sd2 was Kubuntu

some of the trouble shooting established that grub was not in the right place. I think what may have happened origionally was grub installed on sd0 or his current drive. in any case we found it on sd2. Bios is now set to sd2 ...rebooted and kubuntu and Windows XP now works.........

after a couple of learning curve things with Kubuntu (no gedit or gnome edit) and finding Adept he is now on his way.

Congrats Glass Casket you are finally up and running.[/QUOTE]

Thanks again man!

---

