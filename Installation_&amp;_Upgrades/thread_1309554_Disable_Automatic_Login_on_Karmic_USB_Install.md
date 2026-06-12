---
title: "Disable Automatic Login on Karmic USB Install"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by sockets on 2009-11-01
Dear All,

I have installed Ubuntu 9.10 to a USB stick, using the "USB Startup Disk Creator". The problem that I have is that when I boot from my USB stick I am automatically logged in, just as when booting from the Live CD.

I have created my user accounts, using System->Administration->Users and Groups->, then I have tried to disable automatic login using the System->Administration->Login Screen-> graphical interface, and I have also tried to disable auto login by editing the /etc/gdm/custom.conf file. But I have had no success, both appear to be reset when I boot the USB stick.

All other changes that I make remain, such as files I have created or the user accounts that I have created. And if I "Log Out..." from the default live user account, the login screen is displayed with the user accounts that I have created.

I have really run out of ideas now, so if anyone knows how I can solve this I would be greatly appreciative.


Thank you in advance,

- Sockets

---

### Post by Haywood on 2009-11-05
I hear ya sockets... I have beat my heat against the wall on this one.  If anyone can provide guidance it would be appreciated. ~H

---

### Post by Mighty_Joe on 2009-11-05
Personally, I prefer a full install to a USB flash drive.  It has it's drawbacks:  it takes up more space (2+GB vs 700Mb for the Live) and it may not work between different computers (though mine's worked on every computer I've tested) but it also is much faster than the Live USB install.  And you can configure it to require a user to log in.

---

### Post by wolfganggold on 2009-11-05
I'm having the same problem.  I was able to do this on another thumb drive with Jaunty with no issues.  I wonder what's up! :)

---

### Post by Haywood on 2009-11-06
> **Mighty_Joe said:**
> Personally, I prefer a full install to a USB flash drive.  It has it's drawbacks:  it takes up more space (2+GB vs 700Mb for the Live) and it may not work between different computers (though mine's worked on every computer I've tested) but it also is much faster than the Live USB install.  And you can configure it to require a user to log in.

Other than selecting the USB thumb drive as the root... are there any instructions on this?

---

### Post by juliopjuliop on 2009-11-06
Hi, after many hours of pacience i have managed to come up with a solution to this problem. First i found out the root of the issue is that a script in initrd.lz actually creates the autologin instance(/etc/gdm/custom.conf) for ubuntu user in a livecd, this script is called "15autologin" and is located in the livecd, in the directory "/usr/share/initramfs-tools/scripts/casper-bottom/" the way i fixed this was i unpacked the squashfs file and chrooted in, then edited 15autologin file to set automaticlogin=true to false and i also changed the timeout option to false. Then i went ahead and rebuilt the initrd.lz with this command "mkinitramfs -o /initrd.lz 2.6.31-11-generic" wich made a new file called initrd.lz in the root of the squashfs, then i proceded to close the chroot and overwrite the /casper/initrd.lz in my liveusb with the newly generated one, and booted it up and vuala it showed me the login screen. hope this helped.

Also in theory this could work from within your liveusb just modifying the file 15autologin temporarily in the live environement and using "mkinitramfs -o /initrd.lz 2.6.31-11-generic" then you will have too copy it too another usb or onto your harddrive and then bootup into another os and overwrite it as you cannot overwrite your initrd.lz in your usb as its mounted as a cd.

PS: i would gladly upload the modified initrd.lz so you wont have to go through all this hassle, but im not sure if i can.

---

### Post by Mighty_Joe on 2009-11-09
> **Haywood said:**
> Other than selecting the USB thumb drive as the root... are there any instructions on this?

I posted links to some instructions [here]("http://ubuntuforums.org/showthread.php?t=1193680").  The thing you have to watch in on the last step of the install you have to choose to install Grub on the thumb drive rather than the hard drive.

---

### Post by LoneSt4r on 2009-11-15
> **juliopjuliop said:**
> Hi, after many hours of pacience i have managed to come up with a solution to this problem. First i found out the root of the issue is that a script in initrd.lz actually creates the autologin instance(/etc/gdm/custom.conf) for ubuntu user in a livecd, this script is called "15autologin" and is located in the livecd, in the directory "/usr/share/initramfs-tools/scripts/casper-bottom/" the way i fixed this was i unpacked the squashfs file and chrooted in, then edited 15autologin file to set automaticlogin=true to false and i also changed the timeout option to false. Then i went ahead and rebuilt the initrd.lz with this command "mkinitramfs -o /initrd.lz 2.6.31-11-generic" wich made a new file called initrd.lz in the root of the squashfs, then i proceded to close the chroot and overwrite the /casper/initrd.lz in my liveusb with the newly generated one, and booted it up and vuala it showed me the login screen. hope this helped.

Also in theory this could work from within your liveusb just modifying the file 15autologin temporarily in the live environement and using "mkinitramfs -o /initrd.lz 2.6.31-11-generic" then you will have too copy it too another usb or onto your harddrive and then bootup into another os and overwrite it as you cannot overwrite your initrd.lz in your usb as its mounted as a cd.

PS: i would gladly upload the modified initrd.lz so you wont have to go through all this hassle, but im not sure if i can.

Hello!

This is exactly what I am trying to do.  However, after 2 attempts, I did not succeed.  Could you please post a more detailed (step by step) procedure of what you did?

Thanks!

---

### Post by BeHive on 2009-11-18
I've been trying to make this work but to no avail.

Would be very helpful if a step by step was provided.

cheers

---

### Post by Fran89 on 2009-11-20
> **juliopjuliop said:**
> 

Also in theory this could work from within your liveusb just modifying the file 15autologin temporarily in the live environement and using "mkinitramfs -o /initrd.lz 2.6.31-11-generic" then you will have too copy it too another usb or onto your harddrive and then bootup into another os and overwrite it as you cannot overwrite your initrd.lz in your usb as its mounted as a cd.

PS: i would gladly upload the modified initrd.lz so you wont have to go through all this hassle, but im not sure if i can.

This worked, while in the USB Live mode, I went to "/usr/share/initramfs-tools/scripts/casper-bottom/" and sudo gedit'ed the file "autologin15" after I edited it I used mkinitramfs -o /initrd.lz 2.6.31-11-generic (mine is actually -14 at the end) and it creates a initrd.lz in the root of the filesystem. Then i sudo nautilus'ed and made a copy paste (into the USB which is mounted as a CDROM) and after that it worked, although I don't see autologin15 anymore in the casper-bottom folder...

still if anybody wants to try... ;)

---

### Post by BeHive on 2009-11-20
I actually did the same thing yesterday night and it worked pretty good


edited my 15autologin, created the new initrd.lz (14 here also on the kernel) and then copied it into sdb1's casper folder.

rebooted

worked as a charm

everything as root obviously because of file permissions 

if someone needs any more help with this, just post :)

cheers

---

### Post by dannyboy79 on 2010-01-13
I don't care so much that live session user is auto logged in as much as the fact that after i logout of the live user, then log into the account i created, i use sudo to change various settings, like /etc/hostname, /etc/fstab to auto mount my nfs shares, change /etc/network/interfaces, those changes don't save but changes like adding new apps save just fine. VERY WIERD. anyone else experiencing these problems?

---

### Post by romerotek on 2011-12-24
1. $ sudo gedit /etc/gdm/custom.conf
2. change AutomaticLoginEnable to false

---

