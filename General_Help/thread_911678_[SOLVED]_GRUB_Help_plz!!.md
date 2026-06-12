---
title: "[SOLVED] GRUB Help plz!!"
date: 2008-09-05
forum: General Help
---

### Post by Gabix on 2008-09-05
Hi! I'm having trouble with GRUB and cant find the right answer in the forum, I'll explain my problem: 
I tried for 2 day installing win xp in my new HP 530 notebook with problems (the sys never logs off (desktop + mouse for ever right after I install all drivers, reboot, and install Firefox, thunderbird and winamp). I HATE XP!. Never mind... 
I also installed Ubu Hardy with ABSOLUTELY NO PROBLEM AT ALL (everything running perfectly at once).
So I said "screw XP", and left Ubu only. The thing is that after a week I thought of something that might correct my XP problem, so I backed up my Ubu only system by making a tgz of the entire hd, and placed it on another computer. After that I Installed XP which made me erase everything (I had only 1 primary partition for / and an extended for /home and swap, that after being resized the free space gained remained extended, and I didn't know how to make it primary). 
So... Installed XP and guess what, I didn't solve the problem :(.
Well, after crying out loud lots of unpublishable things to Microsoft, Bill Puertas and Ventanas (gates and windows for non-Spanish talkers) I reinstalled Ubu from scratch in a new partition table (again, I didn't know how to re-set the / and /home with gparted) and then unpacked the backup.tgz on / overwriting everything and hopping GRUB would magically reconfigure itself. Of course that didn't happened, so I'm here to find the way to do it. It's obvious that after grub loads the Ubuntu logo bar stays bouncing from one side to the other.

My new partition table is:

```
Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros, 234441648 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x31a431a3

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63    39070079    19535008+  83  Linux
/dev/sda2        39070080   234436544    97683232+   5  Extendida
/dev/sda5       231512715   234436544     1461915   82  Linux swap / Solaris
/dev/sda6        39070206   231512714    96221254+  83  Linux

Las entradas de la tabla de particiones no están en el orden del disco
```


This is my grub/menu.lst with everything else in there commented:

```
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3890f1fd-cb80-44d6-a51c-4203594a9139 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3890f1fd-cb80-44d6-a51c-4203594a9139 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3890f1fd-cb80-44d6-a51c-4203594a9139 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3890f1fd-cb80-44d6-a51c-4203594a9139 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3890f1fd-cb80-44d6-a51c-4203594a9139 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3890f1fd-cb80-44d6-a51c-4203594a9139 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

And (I'dont know what this is, but might come handy):

```
/dev/sda1: UUID="7f1c2d63-49bf-40b6-8c62-19e87899bab6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="ad6e8a94-2bef-4fdf-bd4e-f5f7b3de1bfa" 
/dev/sda6: UUID="98a66dc9-bf00-4219-9ec1-266ed12fce8b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

```

So well, If something else is needed, please tell me...
Thanks a lot!!

PD: Where is the SOLVED btn to show the tread as SOLVED?? :P

---

### Post by elmer_42 on 2008-09-05
I found a [link]("http://ubuntuforums.org/showthread.php?t=224351") that may help you. When I had to reinstall Windows, it rewrote my MBR with the Windows boot loader, which I promptly replaced again with GRUB. I used a guide that was in the Ubuntu wiki, but I can't quite remember the link for it right now. The post I linked you to seems to be the same instructions, though.

---

### Post by falcon61102 on 2008-09-05
Well the easiest answer is your last one.  The SOLVED button is under the Thread Tools Menu near the top of the page.

As far as your GRUB goes, it looks like all you need to do is change the UUID for your menu.lst entries.  Currently it is this:
```
/boot/vmlinuz-2.6.24-21-generic root=UUID=3890f1fd-cb80-44d6-a51c-4203594a9139 ro quiet splash
```

Change it to this:
```
/boot/vmlinuz-2.6.24-21-generic root=UUID=7f1c2d63-49bf-40b6-8c62-19e87899bab6 ro quiet splash
```

---

### Post by sml on 2008-09-05
Why do you need XP? Maybe we can help sort your problems in Ubuntu? What do you need to do?

---

### Post by Gabix on 2008-09-05
I need it to work with Visual Studio.Net and SQL Server I don't really understand Monodevelop...
Anyway, I love working with PHP in Ubuntu!

---

### Post by falcon61102 on 2008-09-05
Did that take care of your issue?

---

### Post by Gabix on 2008-09-05
No... Just a little :D
Actually, now Ubuntu loaded after grub and detected the / directory, but it lost the /home (which is on another partition). 
I got stuck in a console outside of the GUI (didn't load GNOME) and typed reboot (why? I don't know, just testing).
Then Ubu entered to the log screen, but every time I tried to log in a message said something like if I wanted to load in safe mode... I clicked on "yes", and after a second another message appeared saying that my session lasted less than 10 seconds...
(the "..." is because I don't remember all the msg) But I have 2 computers. falcon61102, if you need to know exactly what it says I can post it.
HELP!

---

### Post by Gabix on 2008-09-05
Is there an auto way of solving the problem?, something like sudo reset menu.lst.
If exists I'd like to know the coded way also!

---

### Post by Gabix on 2008-09-05
Maybe I screwed thing up when I overwritten everything in root, I remember that I didn't delete everything on drive before unpacking.

---

### Post by falcon61102 on 2008-09-05
The GRUB only deals with booting your system but once it boots it no longer has anything to do with what goes on.  It sounds like you may be having some graphics issues.  

As far as it not finding you /home parition, it could be that your fstab needs to be edited to actually use the parition that you want it to.

Make sure you change the UUID in the menu.lst for the other kernal versions listed.  That way you can go back and use them if necessary.

Boot back up with the LiveCD and we'll see about your fstab.
You can view it with:
```
gksude gedit /etc/fstab
```

EDIT: If you could post the fstab and the results of:
```
sudo blkid
```

---

### Post by Gabix on 2008-09-05
the one for the live cd says this:

```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

```

the one for /media/disk/etc... cd says this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3890f1fd-cb80-44d6-a51c-4203594a9139 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=c23061d8-9d9e-425d-bbe7-408385782874 /home           ext3    relatime        0       2
# /dev/sda5
UUID=e81711ea-a76d-4091-9c5e-2dedf7424759 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by Gabix on 2008-09-05
Damn! I can't find the thread in witch there was the command to list my uuids... What was it?

:D sudo blkid!

```

/dev/sda1: UUID="7f1c2d63-49bf-40b6-8c62-19e87899bab6" TYPE="ext3" 
/dev/sda5: UUID="ad6e8a94-2bef-4fdf-bd4e-f5f7b3de1bfa" TYPE="swap" 
/dev/sda6: UUID="98a66dc9-bf00-4219-9ec1-266ed12fce8b" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

```

I have to replae the uuids in fstab too?
What is the fstab?, just want to learn...

---

### Post by falcon61102 on 2008-09-06
```
sudo blkid
```

Sorry, I must have updated my last post too slow.

---

### Post by falcon61102 on 2008-09-06
The fstab, in short, is what automounts your HDs when you boot your computer.

Yeah, you need to change the UUIDs for all three of your partitions in the fstab.  Then try rebooting.

---

### Post by Gabix on 2008-09-06
GREAT!!! Everything works marvelous now!

Just a comment:
I remember my .Net teacher (windows lover) said: "Ah! Linux is not prepared for the final user" And also: "I love Vista, everything works so great!". Two things, I think I can call myself an intermediate Xp user, that knows some things or two about configuring Microsoft opp systems, I tried Vista and besides of it's low low low performance (rated in relation with the Ubuntu Hardy with lots of compiz and indexing enabled in the same computer), It is really much worse prepared for the final user than Ubuntu, and Xp may win only because It's the Opp Sys that everyone uses since childhood. The possibilities and advantages you have with Ubuntu are endless. And I only started using It this year! Something as basic as packing your entire drive to backup you system can't be done with windows, you always have to look for (always paid) software to make it for you AND LEARN HOW TO USE THAT SOFTWARE. And I can't even think of what would happen to you If you tried what I did, overwriting everything in you C drive! :lolflag: BLUE SCREENS EVERYWHERE!
The only thing that keeps you from completely changing are the freaking corporations that don't like Ubu's and Linux philosophy, and don't want to release their version for Ubuntu/Linux, LIKE ADOBE!!! I think it can't be really hard to do it, all their products are available for mac, AND MAC IS LINUX BASED!!

falcon61102: Thanks again for you immediate help. 

PD: I tried posting a question in Windows forum about my problem (with XP above), but when neither Firefox nor IExplorer acceded the log in page in the there, I took a deep breath and postponed for later, when I had the courage to lead with that problem...

---

### Post by falcon61102 on 2008-09-06
No problem.  Glad you got it working.

---

### Post by Gabix on 2008-09-07
How can I make the code lines shown on boot print to a file?

---

