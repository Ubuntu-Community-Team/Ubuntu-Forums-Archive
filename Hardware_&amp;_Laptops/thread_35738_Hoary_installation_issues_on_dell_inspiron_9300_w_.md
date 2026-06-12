---
title: "Hoary installation issues on dell inspiron 9300 w/ solution"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by malliemcg on 2005-05-20
Hello everyone.

I thought that I might post the solution to the problem that I have been having on the Dell Inspiron 9300 trying to install Hoary (2005.4) as I was unable to find a solution to it when it was making my life unhappy, it might help somoene else out there.

I have a Dell Inspiron 9300 with the ATI X300 graphics card. (1440x900, 64MB RAM) The installer would lock up after selecting the appropriate boot image with a very pretty, changing but strange video problem, it did not appear that the laptop had crashed.

After several hours of googling and playing around, I came to the idea of connecting an external (CRT in this case) monitor to see what would happen, after using the Fn-F8 key the external monitor displayed the Ubuntu installation screen  \\:D/ . Once it was all installed I was able to disconnect the monitor and boot into hoary no issues at all, even sound works off the bat  :grin: .

Well I hope this helps someone enjoy!

M

---

### Post by emperor on 2005-05-20
I just ordered a Dell Inspiron 9300 last night during the $450 off, free dvd/cdrw and free accessory sale. I have one question concerning a Ubuntu Hoary install:

Were you able to turn on DMA for the DVD optical drive? Apparently there is a known issue with the 2nd drive controller being unable to use DMA. This appears to be a kernel issue that has been fixed in 2.6.12 series kernels. So I am curious if Hoary has a patch to fix this!

---

### Post by Strife on 2005-05-20
I have a Dell Inspiron 6000, and I had similar video issue when I was installing it. However, I had found somewhere that passing the vga=771 option would solve it, and sure enough it did.

I would like to see if I could remove that option now, though, because I have problems returning from suspend (the screen refuses to show up), and I hear that supposedly the problem is having the vga=771 option set.

We'll see how it works...

---

### Post by Strife on 2005-05-20
Oh, one more thing. You say you have an X300 video card, as I do too. Thus far, I haven't been able to get hardware acceleration working, but if you can, please let me know how you did it.  :)

---

### Post by malliemcg on 2005-05-21
I have not had a chance to get any further with this.

I'll report progress/issues as they happen when I get back to work next week. (Work laptop for a Development project).

I am planning on applying patches/alterations as per [http://www.rtr.ca/dell_i9300/](http://www.rtr.ca/dell_i9300/) to the software install which I believe solves some of the issues mentioned.

M

---

### Post by mlord on 2005-05-25
I now have everything (!) working, except for the (Ricoh chipset) SD card slot.

Here's my website describing how I set it up:  [http://www.rtr.ca/dell_i9300/](http://www.rtr.ca/dell_i9300/)

Cheers

Mark

---

### Post by mlord on 2005-05-25
One user (emperor) asked about the kernel patch I'm using.

Most of it is from the upstream libata-dev patches that are already part of the stock (K)Ubuntu kernel from the install CD. 

To this, I've added a snapshot of my own Delkin Cardbus driver (not needed by most people), a snapshot of the libata suspend/resume support patches (currently making their way into libata-dev), and bug fixes for the "random lockups" that happen whenever the CD/DVD drive is empty (submitted for libata-dev).

EDIT: Oh, and plus the latest ALPS-Touchpad driver patch.

The "libata-dev" thingie is Jeff Garzik's private tree of stuff that will eventually be seen in the mainstream kernel, though possibly not for several months.  Most of it is NOT in 2.6.12-rc*, for example.

Jeff Garzik is the author and maintainer of the Linux "libata" driver subsystem.
(I am the original author and former maintainer of the Linux "IDE" driver subsystem).

I am not using 2.6.12-rc* on my i9300 yet because that kernel breaks VMWare, an application I use daily.

Cheers

Mark

---

### Post by emperor on 2005-05-31
Anybody got a fix for the "no sound" problem when playing movie trailers? Both mplayer-plugin and codeweaver solution does not resolve the problem. All sliders are up too!

Upgrading ipw2200 is a problem either compiling or installing on released 2.6.10 kernel in repo. Looks like I will have to download and compile a kernel afterall to get ipw2200 working right and DMA on drives.

Also, default Ubuntu install does not install fglrx drivers for X300 and installing the restricted drivers for 2.6.10 does not include a version of fglrx that supports the X300 chipset. Looks like the ati driver will have to be installed using newer driver on ati website.

Resume from suspend to ram does not work for me!

---

### Post by emperor on 2005-06-03
Trying to set DMA on the hard drive or the cdrom I get:

"HDIO_SET_DMA failed: Inappropriate ioctl for device"

Kernel is stock Ubuntu 2.6.10-5.

hd is /dev/sda8

cd/rw is /dev/scd0

Tried hdparm version 6.1 too but still did not work!
ran hdparm from home directory, did not install:
 ./hdparm -d1 /dev/scd0

Anyone get DMA set on cd or hd?????

---

### Post by dejitarob on 2005-06-04
> Upgrading ipw2200 is a problem either compiling or installing on released 2.6.10 kernel in repo.Works fine for me, see [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

> Also, default Ubuntu install does not install fglrx drivers for X300 and installing the restricted drivers for 2.6.10 does not include a version of fglrx that supports the X300 chipset.Works fine for me with the fglx package in the repos, see [http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

> Anyone get DMA set on cd or hd?????
Apparently mlord has some information on his website [http://www.rtr.ca/dell_i9300/](http://www.rtr.ca/dell_i9300/)

The most annoying problem I have which I cannot seem to fix is once I removed gnome and installed KDE I no longer have sound (see [my thread](http://ubuntuforums.org/showthread.php?t=39134)). That and the screen will not turn off when the lid is closed. Mlord did have on his website that a possible fix for random lockups was putting media in the dvd drive but mine won't stop spinning and its very loud. Anyone have any suggestions for this or getting [my sound working](http://ubuntuforums.org/showthread.php?t=39134)?

Update: I believe a broken headphone jack was the culprit. It is really loose and is not releasing the sound output to switch over to the external speakers. Be really gentle with those things, there are a bunch of people on Dell's forums with the same problem.

---

### Post by mlord on 2005-06-05
[QUOTE=emperor]Trying to set DMA on the hard drive or the cdrom I get:

"HDIO_SET_DMA failed: Inappropriate ioctl for device"

Kernel is stock Ubuntu 2.6.10-5.

hd is /dev/sda8

cd/rw is /dev/scd0[/QUOTE]

The libata "hdparm interface" does not implement the "-d" option.  For disks, "-d1" is always in effect;  for cdroms, it requires patching the kernel source code to get "DMA" turned on -- I think the Ubuntu kernels already have this by default.

-ml (hdparm author)

---

### Post by mlord on 2005-06-05
[QUOTE=emperor]Anybody got a fix for the "no sound" problem when playing movie trailers? Both mplayer-plugin and codeweaver solution does not resolve the problem. All sliders are up too![/QUOTE]

I have not experienced that problem, though I do use xine rather than mplayer etc.. for all videos.

> Resume from suspend to ram does not work for me!

Works for me, but not using the standard Ubuntu scripts -- see my website for *exact* details on getting this working (easy).

-ml

---

### Post by dejitarob on 2005-06-08
Mlord, thanks for your site its very helpful. I'm trying to compile my own kernel right now using your .config, in order to be able to use the synaptics drivers. I noticed that you have "Pentium M" selected as the Processor type instead of the correct "Pentium-4/Celeron(P4-based)/**Pentium-4 M**/Xeon". Just a heads up, thanks again.

---

### Post by dejitarob on 2005-06-08
Hey mlord, what method did you use to compile your 2.6.11.11 kernel? I used the vanilla sources from kernel.org + your patches using make-kpkg and it freezes at "Starting PCMCIA services". If I disable PCMCIA services it freezes at "Starting powernowd". I can boot up in recovery mode though, just a bit annoying to type kdm and login everytime.

---

### Post by emperor on 2005-06-11
My suspend problem is related to the ati fglrx driver. It may work with the standard xorg "ati" driver.

---

### Post by dejitarob on 2005-06-13
I got it working with a patched 2.6.10 kernel but the sensitivity is really low for some reason, even while using mlord's xorg.conf. Immediately after I log into and KDE loads, the touchpad stops working.

Update: I had to mess with the Corepointer option in the Serverlayout section via the Readme.

---

### Post by emperor on 2005-06-18
I was able to get the dma enabled on the cdrom/dvd drive today. I had to compile a kernel and decided to go with the latest kernel instead of the old 2.6.10 in Hoary.

1. **Downloaded pristine kernel** version 2.6.11.11 from kernel.org

2. Add your [b]userid rights to group "src".
[/b]
    sudo adduser username src

3.** Install kernel source** in /usr/src 

4. **Define "ATA_ENABLE_ATAPI in  .../include/linux/libata.h**
 
5. **Edit .../drivers/scsi/ata_piix.c**

[b]PIIX_COMB_PATA_P0  = (1 << 0).
PIIX_COMB                = (1 << 1),
[/b]
see: [http://www.mail-archive.com/linux-ide@vger.kernel.org/msg00910.html](http://www.mail-archive.com/linux-ide@vger.kernel.org/msg00910.html)

6. Followed "KernelHowto" in wiki to **build kernel** but had to build initrd.img as a separate step after installing the created kernel deb.

[https://wiki.ubuntu.com/KernelHowto#head-42da0e4c87e77bc99b48abdda0e93bbaf6e2f557](https://wiki.ubuntu.com/KernelHowto#head-42da0e4c87e77bc99b48abdda0e93bbaf6e2f557)
 
for example:
========
a, copy your current kernels /boot/config...." to the source directory as .config

b. make xconfig

<to create packages>
c. fakeroot make-kpkg --append-to-version=i9300 kernel_image binary

<to install when compile completed; debs in /usr/src >
d. sudo dpkg -i kernel-image-2.6.11.11.i9300_10.00.Custom_i386.deb

To make the missing "initrd.img..."
e. sudo mkinitrd -o /boot/initrd.img-2.6.11.11.i9300   2.6.11.11.i9300

f. Then you will have to edit /boot/grub/menu.lst to add initrd.

7. Reboot new custom kernel.

---

