---
title: "Complicated Ubuntu Install"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by jpg on 2005-12-18
I have a Shuttle PC (Nforce2 motherboard w/  integrated Ethernet, pretty sure it is an SK41G, but I can't find the receipt right now - I got it 18 months ago) that is failing in me. I am having problems with the CD and Ethernet. It won't even boot off of the DVD that I have in it, so I had to borrow a CD drive from work and plug that in instead. I cannot afford to replace this PC. The kids use it to watch movies, and surf the internet, so I am hoping to get a basic install and let them play with it until it dies.

Initially I had Debian installed, and everything worked perfectly, but gradually started to fail over the last year. The ethernet connection would fail (eth0 down, eth0 up messages in dmesg), and then it needed to have the dvd drive fixed by hand - /media/cdrom pointed to cdrom0, but that directory did not exist, so I had to create it using sudo every time we wanted to use the dvd drive. This may have been related to upgrading Debian.

I have tried installing both Ubuntu and RedHat Fedora (and WinXP Pro, even), to see if there is anything I can get on this system, and if there are kernel problems, or IRQ problems (which I suspect there are, since the boot process complains that the Nforce2 is not 100% native,etc., but I don't know for sure)

When doing an Ubuntu install, it works fine until it gets to "Install Base system", when it says that it cannot find the CD or the files. I have dropped into a shell, and the CD is mounted at /cdrom, and I mounted it by hand at /target/media/cdrom0 (linked from /target/media/cdrom), but it still fails. The ethernet is dead (in all three OSs). I have rigged an internet connection through the USB port, and Ubuntu detects and configures this fantastically. I know it works because i can use the Ubuntu Live CD to connect to the internet. I just can't get the base system to install. Once I do that, i can use Apt-get to install everything else. There is no floppy drive on this PC.

I have been able to get Fedora installed, but it cannot connect using the USB port, so that is a dead end (I guess I could transfer a bunch of rpm's via USB flash drive, but I really don't want RedHat on this computer).

So, my options: 

1. Boot and install of a USB flash drive (I have a 1GB SanDisk Cruzer, but I have not been able to get it to boot correctly - I do have the Ubuntu 5.10 install .iso on the flash drive).

2. Direct the Ubuntu install to find the iso on the USB flash drive, or on an external USB HDD (I have one of those as well).

3. Do a Net install by hand. I don't know how to intervene in the install process to do this, or even if it is possible. Any information?

4. Take out the hard drive and install on another computer. Due to the way this thing is put together, though, it would mean taking most of the computer apart.

If anyone has done one of the first three, any tips would be greatly appreciated. Also, any information on the install process and if, and to what extent, it can be modified would be a great help.

Thanks in advance!

JP

---

### Post by aysiu on 2005-12-18
I'm answering you not because I have any clue but because no one else has answered you. I'd say try doing a server install and then apt-getting the rest, but you may again run into the problem with installing the base system. It's worth a shot, though.

Just do a server install and then ```
sudo apt-get install ubuntu-desktop
```

If not, maybe consider using Damn Small Linux? The entire OS can fit on and boot from a USB drive.

---

### Post by MetalMusicAddict on 2005-12-18
[QUOTE=jpg]When doing an Ubuntu install, it works fine until it gets to "Install Base system", when it says that it cannot find the CD or the files.[/QUOTE]
Ive had this happen to me a re-burning the .iso fixed it for me. Dont know the real cause though.

---

### Post by ninotob on 2005-12-18
I too have had problems with the Breezy install discs.  Hoary works great though -- try installing Hoary and the upgrading by changing all the "hoary" references to "breezy" in synaptic.

---

### Post by jpg on 2005-12-18
[QUOTE=ninotob]I too have had problems with the Breezy install discs.  Hoary works great though -- try installing Hoary and the upgrading by changing all the "hoary" references to "breezy" in synaptic.[/QUOTE]

Thanks! I think I will try that. Ethernet decided to work this afternoon (and the only thing I did was knock something loose while cleaning up my desk :confused: ...). So, the worst case is to stick with RedHat. 

I hope Hoary works, though, because I originally installed an older Version of Debian, and that worked fine (of course, there is that hardware thing...).

Thanks!

---

### Post by jpg on 2005-12-18
[QUOTE=aysiu]I'm answering you not because I have any clue but because no one else has answered you. I'd say try doing a server install and then apt-getting the rest, but you may again run into the problem with installing the base system. It's worth a shot, though.

Just do a server install and then ```
sudo apt-get install ubuntu-desktop
```

If not, maybe consider using Damn Small Linux? The entire OS can fit on and boot from a USB drive.[/QUOTE]

Yeah, I need to get my USB mojo working. I just can't figure that one out. 

The server thing won't work, either, because it never gets past the "Install Base System" part. I am goign to try with an older version, and then punt and install RedHat.

---

### Post by jpg on 2005-12-18
[QUOTE=MetalMusicAddict]Ive had this happen to me a re-burning the .iso fixed it for me. Dont know the real cause though.[/QUOTE]

That is an idea. I might try that too, if the other stuff fails.

---

