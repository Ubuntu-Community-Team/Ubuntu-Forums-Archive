---
title: "Installing on second harddisk?"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by Edho on 2005-12-29
Hello,

Playing with Breezy Live-cd... works..web,printing,usb-for-cam.
Like it. :D

A few questions,please.

-If i do a real install on my second disk(8 Gb).. can i reley on the Grub he will do the right things for dual booting with Xp home (= first(master) hd-30Gb)?
Or is it tricky?

I have to give permission to install the bootloader in the Mbr of the FIRST disk, this is where windows is.. am i right??

-It seems making a own partition for /home is the best.
So on a disk of 8 Gb... 3 partitions,
 3G     for Ubuntusystem
 500Mb  for Swap (256 Mb ram)
 Rest    for home-data.
Agree? or better other figures?

---

### Post by kevvyd on 2005-12-29
I am no expert on the topic, having just installed Ubuntu myself, but I can verify that Grub will allow you to run your XP as normal -> that's how mine is set up. 

There is only one MBR, regardless of the number of drives you have, and GRUB will find it without any intervention from you. You just have to make sure that you install the OS on the proper drive. I would write down the name and model number of the drives that you have in your machine and identify them. You will be asked where to put Ubuntu during the installation and you do not want to put it on the wrong one!

---

### Post by az on 2005-12-29
When in doubt, grub will ask where to install itself.  Pick the MBR on the first disk.

As for partitioning, I suggest everything on the same partition unless you have very specific needs for seperate partitions.

---

### Post by psusi on 2005-12-29
[QUOTE=kevvyd]
There is only one MBR, regardless of the number of drives you have, and GRUB will find it without any intervention from you. You just have to make sure that you install the OS on the proper drive. I would write down the name and model number of the drives that you have in your machine and identify them. You will be asked where to put Ubuntu during the installation and you do not want to put it on the wrong one![/QUOTE]

There is one MBR on every hard disk.  Older systems would only load the MBR from the first detected disk.  More modern bioses have an option allowing you to specify which disk should be booted, but it is easier and works for more people to just install grub to the MBR of the first drive.  

Let it install to the first drive and you should have no problem dual booting.

---

### Post by kevvyd on 2005-12-29
[QUOTE=psusi]There is one MBR on every hard disk.  Older systems would only load the MBR from the first detected disk.  More modern bioses have an option allowing you to specify which disk should be booted, but it is easier and works for more people to just install grub to the MBR of the first drive.  

Let it install to the first drive and you should have no problem dual booting.[/QUOTE]
Thanks for the correction. I'm just learning by feel here, too.

---

### Post by Edho on 2005-12-29
Thanks!

So.. bootloader install to MBR of masterdisk.
-------------------

I have readed somewhere, it's a good idea to create a partition for /home.
When one later do a major-update of the system, the userdata are safer.
Is that correct?

How would a mature linuxer partitioning his 8 Gbyte disk for Ubuntu-install?

In that context...
Later , when i decide to keep going with Linux, i will make on my 30Gb(ntfs) a room for Fat32.
(reachable RW with both OS)

Again thanks.

---

### Post by dbeckham32 on 2005-12-29
You can also use Grub off the primary hard drive to boot an OS that's physically stored on another disk.

I have a dual hard drive system with three operating systems - two on the first disk and Fedora Core on the second. You must edit the Grub menu.lst file and observe the HD number. In this sample, "hd0,4" refers to my first hard disk, partition 4 (which is where I have Ubuntu installed):

title           Ubuntu, kernel 2.6.12-9-686-smp
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.12-9-686-smp root=/dev/hda5 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-686-smp
savedefault
boot

---

### Post by lha on 2005-12-30
Grub can be used to boot Windows even if Windows isn't installed on your primary master. This allows you to leave your 30GB drive, including its mbr, untouched.

I have Windows 98 on secondary master and Grub installed on primary master. Using map (a grub command) I trick Windows into believing it is on primary master. This is easy to do, my /boot/grub/menu.lst lines that allow me to boot Windows are below:

```
title Windows
map (hd0) (hd2)
map (hd2) (hd0)
root (hd2,0)
makeactive
chainloader +1
```

You can make your 8GB drive primary slave and 30GB drive primary slave (or something else). Then install Ubuntu to 8GB'er with Grub on its mbr. Installer will probably recognize Windows on the second hd and add it to grub's menu and it will work out of the box. If Windows isn't detected during install, just append similar lines to your menu.lst as described above.

N.B. I have not tested this with Windows XP but I see no reason why it wouldn't work. Even if it didn't work out you can revert to your old setup and install grub on the mbr of your 30GB drive.

---

### Post by Thanatos10 on 2005-12-30
If you already have windows loaded you can simply use XP's NTLDR instead of GRUB.  It's easy and painless just follow the simple step-by-step instructions found here [http://www.aboutdebian.com/dualboot.htm](http://www.aboutdebian.com/dualboot.htm).  Which ever method you decide on good luck.

---

### Post by Edho on 2005-12-30
Thank You..but...
Just did the install.

Not without problems.
Error.. base system not installed good...go back..
Again erased the partition...try again forward...
To my surprise it asked for installing Lilo?? and not Grub!!!
Yes
System asks first time to reboot... black scr...msg. "can't find tty or something."
No menu... Pc death.(No Windows, no Ubuntu)

All over again with an other install-cd.(recieved #5)
Now installing Grub..(did not asked for Lilo anymore)

Finaly it looks OK.
Booting give me the choise     Ubuntu --- Windows.
Thank God.:D

But i am not sure about the swap-thing.
How can i check it's there?

Edit:
Found!
In system Monitor.

Edho happy :D

B T W...
Firefox + sys.mon    takes a cpu-load 9 %

---

