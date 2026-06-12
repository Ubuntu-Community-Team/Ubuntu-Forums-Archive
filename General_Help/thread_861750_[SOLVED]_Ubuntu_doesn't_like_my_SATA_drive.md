---
title: "[SOLVED] Ubuntu doesn't like my SATA drive"
date: 2008-07-16
forum: General Help
---

### Post by solwic on 2008-07-16
I just bought a new 500Gb SATA hdd today and tried to dual boot Windows XP and Ubuntu the way I always do:  Install XP on the whole drive, then use Ubuntu to resize the partition.  

All that went OK, except GRUB didn't get written to the MBR.  When I used a livecd to manually install GRUB, I kept getting errors such as "Cannot mount device" or "No partition found".  

I'm running:

500Gb SATA HDD as Primary Master

80Gb IDE HDD as Slave.  It's jumper is set to slave, and it's using the slave plug on the IDE cable.

The installer finds all my drives fine, partitions them perfectly, and finishes setup with no trouble.  But when I reboot it doesn't even give me an option, it just goes straight to Windows.  

Any ideas?  I'm using the graphical installer for 8.04 if it matters.  I've also dual-booted Windows and Ubuntu on the 80Gb drive that's now a slave, and everything worked perfectly.  I assume this is a SATA issue.

Any help would be awesome!  I'm running XP by itself now, and I'm missing my Ubuntu!  Help!  :P

---

### Post by logos34 on 2008-07-17
> **jrock612 said:**
> All that went OK, except GRUB didn't get written to the MBR.  When I used a livecd to manually install GRUB, I kept getting errors such as "Cannot mount device" or "No partition found".  

...

But when I reboot it doesn't even give me an option, it just goes straight to Windows.

You ran this from the live cd:

> sudo grub

**find /boot/grub/stage1**
(enter output in next command)
[B]root (hdx,y)
setup (hd0)
quit[/B]?

Grub could be seeing the sata as '(hd0)', even though the IDE drive is clearly the boot disk. (usually it's the other way round--grub thinks the IDE drive(s) come first despite actual boot order).  The way to tell is to change the BIOS **hard disk boot priority** (not to be confused with device boot order)--if you get the grub menu screen (or a grub error), then you're nearly home.  If the menu comes up but you get an error when you try to boot ubuntu, press 'e' to edit, 'e' again on the 'root' line and change from (hd**1**,x) to (hd**0**,x).

---

### Post by solwic on 2008-07-17
> **logos34 said:**
> You ran this from the live cd:

?

Grub could be seeing the sata as '(hd0)', even though the IDE drive is clearly the boot disk. (usually it's the other way round--grub thinks the IDE drive(s) come first despite actual boot order).  The way to tell is to change the BIOS **hard disk boot priority** (not to be confused with device boot order)--if you get the grub menu screen (or a grub error), then you're nearly home.  If the menu comes up but you get an error when you try to boot ubuntu, press 'e' to edit, 'e' again on the 'root' line and change from (hd**1**,x) to (hd**0**,x).

I reinstalled Ubuntu completely, making sure to set GRUB at /dev/sda/  

Now when I boot I select "Ubuntu" and it says, "Error 22: No such partition".  I try to load Windows XP, and it says it can't find NTLDR, and to press Ctrl+Alt+Del to reboot.  I ended up having to use fixmbr just to get Windows working again to log in here and post.

Would it help any if I just unhooked the IDE drive?  It's my backup drive, so I need to have it able to run with Ubuntu, but it doesn't have to be plugged in while I'm installing, I guess.

As of right now, here's my setup:

/dev/hda = NTFS 80Gb IDE Drive - Storage, drive set as slave

/dev/sda1 = NTFS 40Gb for Windows XP Home
/dev/sda2 = Swap space 3Gb
/dev/sda3 = Ext3 400Gb for Ubuntu

GRUB was installed at /dev/sda but I had to overwrite it with "fixmbr" from the Windows CD to get my system to boot.

Any ideas here?  I miss my Ubuntu, but I don't want to spend a week trying to get it to boot up...  :(

Thanks for any and all help.

---

### Post by solwic on 2008-07-17
> **logos34 said:**
> You ran this from the live cd:

?

Grub could be seeing the sata as '(hd0)', even though the IDE drive is clearly the boot disk. (usually it's the other way round--grub thinks the IDE drive(s) come first despite actual boot order).  The way to tell is to change the BIOS **hard disk boot priority** (not to be confused with device boot order)--if you get the grub menu screen (or a grub error), then you're nearly home.  If the menu comes up but you get an error when you try to boot ubuntu, press 'e' to edit, 'e' again on the 'root' line and change from (hd**1**,x) to (hd**0**,x).

Your little tip did the trick!  I got grub installed properly, tried to boot and got the missing partition error.  I pressed "e" on the first entry in the GRUB menu and edited it from hd(1,2) to hd(0,2) and it booted right up.

My last question is:  will that change be permanent, or will I have to redo it every time I boot?  

Thanks for the help!

---

### Post by jarrhed on 2008-07-17
Sometimes I find that after install I have the same problem. Heres what I do

First I boot into Ubuntu using grub (This is temporary Method) by:
Select Ubuntu X.XX 2.6.XX-XX
then push E
then go to top one where it says one of the following:
hd0,0
hd0,1
hd1,0
hd1,1
you get the idea

and change that to like from hd1,0 to hd0,0 or hd1,1
mess with that till you get it right

Then Permantent Method:
Theres two ways to do this
1. In Windows
First downloda the ext2/3 ifs driver (Lets you read/write Linux File System in windows)
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Then install it
Then select what letter you want it to be during the installer
Then open it
go to boot folder
then go to grub
and open menu.lst with notepad or any other text editor
change the lines that say
Ubuntu X.XX Hardy Heron/Gutsy Gibbon/ That Alpha Version
root hd0,0 or something like that
change that hd0,0 to what worked with the previous step
I dunno how to find it though

2. Another Windows Method
While in ubuntu go to accessories>terminal
Then in terminal type
cd /
cd boot
cd grub
sudo gedit menu.lst
type your password
then look for
Ubuntu X.XX Hardy Heron/Gutsy Gibbon/ That Alpha Version
root hd0,0 
change hd part to what you used before with grub and worked
save it
Done

---

### Post by logos34 on 2008-07-17
> **jrock612 said:**
> Your little tip did the trick!  I got grub installed properly, tried to boot and got the missing partition error.  I pressed "e" on the first entry in the GRUB menu and edited it from hd(1,2) to hd(0,2) and it booted right up.

** My last question is:  will that change be permanent, or will I have to redo it every time I boot?**  

Like jarrhead said, to make changes permanent:

gksudo gedit /boot/grub/menu.lst

change 'root' lines to match.  

Don't forget '**groot'** line too (which update-grub references).

Windows should be 'root (hd0,0)'

---

### Post by solwic on 2008-07-17
> **logos34 said:**
> Like jarrhead said, to make changes permanent:

gksudo gedit /boot/grub/menu.lst

change 'root' lines to match.  

Don't forget '**groot'** line too (which update-grub references).

Windows should be 'root (hd0,0)'

Well I did that and now Ubuntu boots like a charm.  Thank you so much for the help...this is the first time I've ran into trouble with GRUB crappin' out on me.  *phew*

Windows XP still won't boot up, though.  I select it in the GRUB menu and it says, "Starting up....NTLDR not found.  Press Ctrl+Alt+Del to restart"

Here's the section from my /boot/grub/menu.lst:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Root was set to (hd1,0) I believe.  I changed it to 0,0 on your recommendation.  Did I break something?  

Thanks again for all the help!

---

### Post by logos34 on 2008-07-17
you don;t need the 'map' lines--that's for booting windows on a another/non-first hard disk:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by solwic on 2008-07-17
> **logos34 said:**
> you don;t need the 'map' lines--that's for booting windows on a another/non-first hard disk:

So you now have my vote for Lord and Master of the Linux Universe.  :)

Thanks for the help...removing those two lines did the trick!

Cheers!

---

### Post by logos34 on 2008-07-17
thanks! glad to help in any way

have fun!

---

