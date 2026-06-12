---
title: "Not booting properly on an Asus X56SE-AP111C"
date: 2008-12-21
forum: Hardware
---

### Post by kuja605 on 2008-12-21
[FONT="Arial"]Hey there,

I've just got my hands on my new asus laptop. Here are the specs:

American Megatrends BIOS
Intel Duo T5750 (2Ghz Dual Core 64-bit)
ATI Mobility Radeon HD3470
3BG RAM
A 250GB S-ATA
USB 2.0
An E-SATA port?
Vista Home Premium Dx
Webcam
Thumb scanner

So anyway, with all the "bells and whistles" and plenty of resorces to run linux, im stumped... I've got the 8.10 Live installer CD from the official site, which ive MD5 checked and have booted up on a desktop, so i know it's not a fault on the disc. When i put the disc into the laptop and power up, the ubuntu splash pops up, i select my language, and select "Try Ubuntu without damaging your system". The Ubuntu logo sits there with an orange bar that starts on the left, scrolls to the right and disapears. This repeats for about 90 seconds. Then the bar fills from left to right like an ordinary loading bar. Here's where the problem starts.

Normally at this point the Ubuntu logo and loading-bar disappear, and the mouse pointer and GUI kick in as the OS starts up. However, on my laptop, when the Loading-bar disapears, all im left with is a command line based interface. Being a complete Linux novice i don't know what to do.

Any help? (Happy to answer any questions)[/FONT]

---

### Post by DieB on 2008-12-22
tried it with the 64-bit version of live-cd?

---

### Post by kuja605 on 2008-12-22
Right, so i've now (thanks DieB for the idea :D) tryed the 64bit live disc too.

So again, ive selected "try ubuntu without... blah blah" and there is no Ubuntu logo with loading bar. However there is a cursor for typing stuff in (the kernel CLI?) which randomly appears at different points on the screen. And then i get random colours on the top quarter of the screen and hear the Ubuntu start up music (YAY!) but still no gui.. just funny colours on top quarter of the screen followed by black.

Any more ideas? :lolflag:

---

### Post by robbiegregg on 2008-12-31
Hi
I have exactly the same laptop and trying to do the same thing (install Ubuntu 8.10 64 bit).  This has completely stumped me however I reckon the reason why we see the command line prompt rather than the nice GUI is because the XServer fails to start - presumably because the graphics driver is not compatible.  

I have read other posts which point to the fact that because the laptop has two different RAM modules installed, Ubuntu can't handle this so removing one will help matters.  However I don't think this is the problem (and have not tried to remove the additional RAM module) since otherwise we would not hear the "jungle sounds" when Ubuntu first starts up?

If you manage to find a fix for this problem, please post your findings.  I'll do the same.

Cheers
Robbie

---

### Post by kuja605 on 2008-12-31
Just tryed the 9.04 developer ALPHA as it has an updated version of X.org server. (Thanks for the idea robbiegregg :D). This STILL doesn't fix the problem. Same thing as before with the 64-bit live disc. The GUI scrambles after the kernal loads and the Ubuntu "loading bar" finishes. I've tryed both the normal "Try ubuntu" and the "Try Ubuntu" with the safe boot option enabled. Still no cigar :confused:

This seems to be a real problem for the developers as alot of Asus users are all having the same/simalar problems :(

Thanks so far guys :D and has anyone else got any more ideas on the matter?

---

### Post by robbiegregg on 2009-01-02
Hi
Yesterday I tried to install Ubuntu again on my x56se laptop.  

First, I installed Ubuntu whilst logged on through Windows Vista and then rebooted.  Limiting the memory usage to 900M (adding the line mem=900M) from Grub and choosing the safe graphics mode, I managed to get to a command line (since XServer failed to start). I managed to hook Ubuntu up to the internet and managed to install the RadeonHD drivers (you'll need to enable "universe" in aptitude if you would rather not compile from source) and then edited my /etc/X11/xorg.conf file to use the new radeonhd driver.  Although the XServer started and I could hear the Ubuntu music, the screen was completely dark (as opposed to the random colours I used to get in the top 1/5 of the screen).

Reading more on the Xorg website, it stated there are known bugs with Asus laptops using the radeonhd driver and more than 2gig of memory.  I therefore bit the bullet and removed one of the RAM modules (the laptop has a 2gig and a 1gig RAM module - i removed the 2 gig module).  To my surprise when I booted from the Ubuntu 8.10 64bit CD and chose the first option (try Ubuntu without installing), the Ubuntu desktop appeared, the Ubuntu sounds could be heard and presumably I could if I wanted to install Ubuntu.

Therefore I reckon it is not possible to install Ubuntu on the Asus laptops without removing some of the RAM.  I reckon there is an issue with X.org (Xserver) which makes it incompatible with the memory configuration the laptop is in when both RAM modules are installed.  According to the POST screen (press ESC and then pause when the computer first starts), "the MCH is operating with DDR2-667/CL5 in Dual-Channel L-Shaped Mode" and it is this that XServer can't handle.

Personally I am going to wait until a new version of Ubuntu or Xserver is published before trying to install Ubuntu.  However if anyone else has better luck than me, please post on this website.

Thanks
Robbie

---

### Post by robbiegregg on 2009-01-02
Kuja,
I recommend you contact Asus support and make an inquiry regarding a potential BIOS update.  Other websites ([http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=2)) indicate there might a problem/bug with the BIOS (website does not explicitly state the X56se is affected) and that a BIOS update is required.

---

### Post by robbiegregg on 2009-01-03
It looks also that x-org are aware of this bug:
[https://bugs.freedesktop.org/show_bug.cgi?id=16263](https://bugs.freedesktop.org/show_bug.cgi?id=16263)

---

### Post by kuja605 on 2009-01-06
hmmm... there are *NO* bios updates for the X56Se models.

[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

Is that even the right place to look? :popcorn:

---

### Post by kuja605 on 2009-02-14
has anyone acutally found a fix yet? i was really hoping that id be able to use a FOSS Laptop :(

---

### Post by souljacker on 2009-02-21
Hi guys. It looks like a BIOS bug. The patch below worked for me (Ubuntu Intrepid 64bit).
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/316079/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/316079/)

(Specs: Asus X56SE-AP049C, 4GB RAM, ATI Mobility Radeon HD3470)

---

### Post by kuja605 on 2009-02-22
hey there! Thanks for finding this, the only problem is that im completely new to UNIX systems and don't know how to go about "patching then kernal". Can anyone look at this fix at write a quick "walkthrough" post on how to get this running?

Thanks :popcorn:

---

### Post by souljacker on 2009-02-23
No prob. Just follow the instructions either here
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
or here 
[http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid/](http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid/)
Before compiling the new kernel, remember to copy the content of the patch at the end of this file (in the kernel source tree) arch/x86/pci/fixup.c or this arch/ia64/pci/fixup.c (depending on your architecture) and to add "asus-m51se-pci-quirk" to the kernel boot arguments in /boot/grub/menu.lst
Cheers ;)

---

### Post by robbiegregg on 2009-02-25
Kuja
Did you manage to get your laptop running under Ubuntu?

---

### Post by robbiegregg on 2009-03-03
Hi all
I've managed to follow the instructions given above and installed Ubuntu on my X56se laptop (with all 3 gigs installed!!).  Here's some additional steps I took:
1/. Remove one of the memory modules from the back of the laptop - I removed the 1gig module however with hindsight it is alot easier to remove the 2gig one
2/. Install Ubuntu - there should be no problem doing this since the total installed memory is less than 2gig.
3/. By default, the wireless card installed in the M51se laptop should be found by Intrepid Ipex (Ubuntu 8.10).  Set this up to connect to the internet.
5/. You'll also need to install the ncurses library:
  sudo apt-get install ncurses-dev
6/. Once you have compiled the new kernels and used dpkg to actually install them, edit the file /boot/grub/menu.lst and make a change to the kernel boot options by adding the line "asus-m51-pci-quirk".  For me the boot options for Ubuntu are the following:

title           Ubuntu 8.10, kernel 2.6.27-11-generic (with Asus M51se PCI quick enabled)
uuid            019b3fae-270a-4881-9924-c04ca7c33a17
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=019b3fae-270a-4881-9924-c04ca7c33a17 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M asus-m51se-pci-quirk
initrd          /boot/initrd.img-2.6.27-11-generic
quiet

7/. Turn your machine off and put the other memory module back in.  Choosing the correct option at boot should then work!

---

