---
title: "[SOLVED] Would Ubuntu 7.10 Install on Thinkpad?"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by cmnorton on 2008-02-19
My new Thinkpad T61 has arrived at work. I've been asked to image the disk before blowing off all the Windows/Thinkpad software and installing Ubuntu 7.10. As part of imaging the hard drive, I've booted Knoppix; attempted to connect to the internet, and that does not work (not this forum's problem).

Given Knoppix and Ubuntu are both Debian derivitives, are there any known problems with T61's and Ubuntu? Before blowing away a perfectly good laptop, I am concerned the Ubuntu install will fail on the network piece. Is there a way I can test this? I will try the Ubuntu live disk as well.

---

### Post by shadowmaster79 on 2008-02-19
Yes , we have many IBM TP and any are witn ubuntu 7.10

---

### Post by shadowmaster79 on 2008-02-19
Do haven't CD drive? We have make with Dockingstation with CD rom.

difference in Knoppix and Ubuntu can be in drivers...

i have idea for you....

1. make installation of ubuntu on another pc.... on one partition (its better)

2. boot on another pc with live cd and tar all files and dirs on installed partition to usb flasj disk.

3. boot IBM TP with knoppix , partition hdd, reboot, boot with knoppix, format partition,
mount it and untar files to new partiotn....

4, check /etc/fstab and grub menu.lst for existing partitions

5. grub-install with hdd params

6. reboot a X finger

It should run....

:popcorn:

---

### Post by cmnorton on 2008-02-19
I went to check this hardware against a 7.10 live DVD before trying to install Ubuntu. I have checked the integrity of the DVD, having downloaded it with bittorrent. 

Now, a new problem is occurring. Basically, I am not able to boot with this DVD using either safe or regular mode and after tweaking VGA settings. I used the DVD to try to boot my Acer Travelmate laptop that is running Ubuntu 7.10. That boot worked.

If I leave the VGA settings at their default, the problems begin when the gnome display manager starts.  get a message indicating the display manager has shut down 6 times, a delay will occur before starting again, and then the installation hangs.

What should I be looking for in the hardware that is preventing the boot? If Ubuntu can boot an old Acer laptop, I am wondering if there's something up with the bios.

---

### Post by DDuong on 2008-02-19
I use to have 7.10 Xubuntu installed on my T61p (btw it worked beautifully).  Now I upgraded to Hardy Haron and it's awesome.

---

### Post by cmnorton on 2008-02-20
After looking at the thinkwiki site, I believe I can get over the graphics problems by installing in text mode. However, I am still worried that Knoppix could not configure eth0.

Edits:
--------------------------------------------
I have faith I can get Ubuntu to install; it has not failed me yet. My biggest concern has been the hardware in this T61, the graphics and ethernet controller. The ethernet device would not configure itself via DHCP under Knoppix 5.0. I pulled down Knoppix 5.1, and rebooted the T61. I can now get onto the network with Knoppix. 

BTW, Knoppix had to retry X a few times, before succeeding, just as the Run Ubuntu in SAFE MODE did.

---

### Post by eshallx on 2008-02-21
I've been having issues getting my install to work too... (T61P with Quadro FX570m)
only i can install just fine, but once I reboot I get no GUI, well, no G at all i guess.  Tried with ext monitor as well to no avail, blank screen where gui usually starts.  This problem is same with every distro i've tried (ubuntu studio, ubuntu, SUSE, also with kalyway leopard).  Pretty sure its the Graphics card, but not sure how to fix...

---

### Post by MiataMuc on 2008-02-21
I have a R61, and there were two problems to solve after installation with alternative DVD: first, in Grub I had to use "nosplash" option, because the splash screen don't likes my Nvidia, and then - after booting - I had to run dpkg-reconfigure xserver-xorg and set the adapter to "vesa". After a "startx" I installed the restricted Nvidia drivers and changed Grub to never use the splash-screen. 

Hope this helps,

Flo

P.S. on the R61, I got most of the FN-keys (and the touchpad) working by using the Hardy.kernel (link: [http://ubuntuforums.org/showthread.php?t=646755]("http://ubuntuforums.org/showthread.php?t=646755") - before the touchpad was recognised as a simple PS/2 mouse.

---

### Post by cmnorton on 2008-03-01
Thank you. This helped and is pretty much what I encountered. I would up disabling the nvidia drivers. I did not need the 3D graphics, and I wanted to use an external monitor, which I could not get to work without disabling the nvidia drivers.

---

