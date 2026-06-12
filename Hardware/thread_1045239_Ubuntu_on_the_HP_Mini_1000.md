---
title: "Ubuntu on the HP Mini 1000"
date: 2009-01-20
forum: Hardware
---

### Post by chud67 on 2009-01-20
I just purchased one of the new HP Mini 1000's with their version of Ubuntu Linux (called Mi, or Mobile Internet).  As you may have heard, this version comes with the command line disabled.  :( 

Story:  [Linux-based HP Mini Mi ships with command line disabled]("http://arstechnica.com/journals/linux.ars/2009/01/08/hp-introduces-command-line-free-linux-netbook") 

Since there is no command line this may be an unanswerable question, but how would I determine what my MAC address is?  I need to know the MAC addy so that I can get on the wireless network at my office.  
This would be easy to determine via command line, but since there is no command line on this version I am wondering if HP made some other way to determine system settings from within the GUI (which I believe is their own custom-made GUI).  

Alternatively, does anyone know a hack to unleash the command line on this netbook?  :D

---

### Post by chud67 on 2009-01-20
I scavenged this info from other threads, and will post it here for historical purposes.  

How to enable command line interface on the HP Mini Mi:  

1.)  Hold Alt-F2, then type "gnome-terminal" (without quotes).  

2.)  Or to get a full-blown root terminal:  In the upper right-hand corner, click Settings.  Under "Menus" on the left-hand side, click "Advanced".  Put a check in the checkbox for "Root Terminal".  Click "Close".  Root Terminal will now appear as an option under the Advanced tab.  You can do anything you need to do from the root terminal.  

:D

---

### Post by chud67 on 2009-01-20
To determine your MAC address, open the root terminal, and type **ifconfig** and then press enter.

---

### Post by Bailywolf on 2009-01-20
Yeah, what they said.

I don't know what HP was talking about with the disabled nonsense.  It's not even hard to find.  You can customize your Settings launcher to have your root terminal icon right there.  

I'm working on hacking the desktop so other things can be nested in the three panels (rather than mail/web/media), and adding applications to the launcher menu, with progress reported [here]("http://ubuntuforums.org/showthread.php?t=1042198").

-B

---

### Post by bobbyshoule on 2009-04-14
I also purchased the Mini 1000 (last week) with Linux and am wondering how to dual boot this with windows XP or similar (hopefully from a thumbdrive) since I need to access remote desktop to log into  Windows Server 2003 and a program called MochaSoft for work. here are my specs:
- HP Mini 1000 Mi Edition
- HP Mobile internet (Mi) software built on Linux
- Intel(R) Atom(TM) Processor N270 (1.60GHz)
- FREE Upgrade to 1GB DDR2 System Memory (1 Dimm)
- 16GB (Solid State Drive Flash Module)
- Intel(R) Graphics Media Accelerator 950
- 8.9" diagonal WSVGA LED BrightView Widescreen Display (1024 x 600)
- HP Mini Webcam with HP Imprint Finish (Swirl) - For 8.9" Display
- Wireless-G Card with Bluetooth

---

### Post by westvleteren on 2009-05-03
to bobbyshoule

It is possible to have a dual boot system on your HP Mini using the original XP installation as the first OS on the first partition and Mini Mi on a separate partition with a 1 gig swap. Here is how you do it:

1st - download the Mini Mi Linux image. and put on USB Stick
[ftp://ftp.hp.com/pub/softlib/software10/COL25940/dennis-stable-install-usb-gm-1.img](ftp://ftp.hp.com/pub/softlib/software10/COL25940/dennis-stable-install-usb-gm-1.img)

2nd - remove the XP hard drive from the HP Mini.

3rd - Insert another Hard disk into the HP Mini to install the Mini Mi Linux distro on a (previously partitioned) 10 gig partition via the same USB stick in the 1st step. Dont forget to enable USB to boot first in BIOS. Boot to the stick and do the recovery install.
If the installation removes your partitioning scheme (which it may) you can shrink it later to 10 gigs with Gparted in a Live CD or preinstalled Linux distro.
It will be important to have your source and destination partitions exactly the same size, because you cant copy/clone an 11 gig partition to a 10 gig partition.

4th - Partition the XP HardDisk with Gparted in a live distro like Knoppix. Shrink XP Partition and leave 10 gigs for Linux and 1 gig for swap. (this can be done on a desktop system (attached by USB, or on the HP Mini using external cdrom drive to run the live distro)

5th - Clone (copy/Paste) the Freshly installed Linux partition to the 10 gig partition on the XP HardDrive within Gparted. Both Drives must obviously be plugged in via USB for this and unmounted during the clone.

6th Use Super GRUB Disk or Debian Rescue to install GRUB to the MBR. Grub will recognize the OS's installed and create entries for them in the Grub Menu. The OS's should boot from the GRUB menu, if not the GRUB boot entries may need to be edited more precisely. The Windows Entry is simple: boot chainloader +1
Linux's partition may need to find the image in /boot/image-2.6.27-i386 to boot or whatever it is on your machine.

Thats how you get the best of both worlds on the HP Mini.

This method has been tried by myself on several different systems where installations dont offer you options to install on a specific partitions, and just wipe the HD clean to do a fresh install.

---

### Post by namluc on 2009-05-03
My mini 1000 came with xp preinstalled. Following advice from the internet, I used the ubuntu live cd's ntfsresize tool to try and set up a dual boot system. I made the partition slightly larger than the resize as recommended, and then installed ubuntu on the rest of the system.

When I tried to boot into windows however, a black screen of death appeared, saying something like windows has had a major problem, or there has been some kind of hard disk failure etc. ubuntu is working fine (almost!), but I was wondering if i could save the windows part, or if it is now dead space. 

Also, the microphone and sound are not working in either skype or ekiga, i've done a few searches but haven't found anything that has helped me, any suggestions anyone??

---

### Post by Hal Story on 2009-07-18
I just bought a new HP 1000 series with XP installed. It eats 8 GB of the 16 GB sold state mass storage, so there is no room for a 10 GB partition with XP still in place. I want to boot from a USB memory stick but have not succeeded. Perhaps I have downloaded the wrong image file. The best I can get is BOOT ERROR before the computer proceeds to launch Windows XP. Any thoughts?

---

### Post by bopomofo on 2009-11-04
> **chud67 said:**
> 
Alternatively, does anyone know a hack to unleash the command line on this netbook?  :D

The following trick works on the version of MI that comes pre-installed with the Mini HP 110. Try it out the 1000.

There is a keyboard shortcut for Run a Terminal, but it is disabled.

Go Settings > Advanced > Keyboard Shortcuts

The last item under Desktop is called **Run a Terminal**.

Click the word *Disabled* and set a new Shortcut. Instant terminal!

---

### Post by Blasco68 on 2010-03-10
Hi guys
Im seing on this forum that a lot of you know a lot of this HO Mini, I had 1 and it was stolen, they broke my car window, so talking with some frinds they told me that if I can get the MAC address I will be able to track it, I Have the box, serial numbers, product ID and all the info that cames in the box, I dont Know if one of you might be able to help me getting this MAC ID with out the computer and using the above info.
 
Thanks A lot
Alex B

---

