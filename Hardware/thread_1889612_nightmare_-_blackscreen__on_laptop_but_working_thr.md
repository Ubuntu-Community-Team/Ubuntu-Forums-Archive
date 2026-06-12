---
title: "nightmare - blackscreen  on laptop but working through HDMI"
date: 2011-12-01
forum: Hardware
---

### Post by peter-123 on 2011-12-01
Hello Community

I explain my problem step-by-step, I hope We can solve it, thanks in advance

System Information

Model: HP Pavilion g6-1b74ca
Architecture: x64
Processor: Intel® Core&#8482; i3-370M 2.4 GHz, 3 MB L3 cache
Memory: 6 gb ddr3
Audio: IDT High Definition Audio CODEC
Wireless: Ralink RT5390 with Motorola BC8 Bluetooth 3.0 + HS Adapter
               (WITH THE NEWS 3.X KERNELS IT WORKS WITHOUT PROBLEM)
VIDEO CARD: Intel HD Graphics. Max Resolution 1366x768
VIDEO OUTPUT: One VGA port and one HDMI port

Ubuntu Version Used: Ubuntu 11.10 x86 and Ubuntu 11.10 x64

Problem:

Downloaded and recorded ubuntu perfectly no errors.
Turn on computer
Choose boot from CD
Ubuntu (x86 and x64) splash screen show UP
Check media for errors - no errors
Chose "Run Ubuntu"
Loading Kernel
Screen blink a few times
Screen turns black
Few second later start the Ubuntu Welcome sound
Blackscreen yet
I hardly noticed I can see a very very very very low gray window in the black screen
I press "Enter" key without knowing what windows is.
I wait at least 5 minutes still blackscreen
I close my display
I open my display
Ubuntu shows the command line window (restarting from sleep) and when it finish the screen turns black again
I can see my Ralink RT5390 wireless white light is ON and working
Thinking...
I connect my laptop through HDMI to my TV and MAGICALLY the Ubuntu Desktop appears on TV! My laptop screen is black but I can my desktop on TV throught HDMI.

Thinking now its working, I disconnect the HDMI cable and BLACKSCREEN again

I connect HDMI cable again and press the F4 display change button and now I can see both screens -tv and laptop (duplicate mode)-

With the good new I disconnect HDMI cable thinking now it will work but in the right moment when I disconnect HDMI the laptop screen turns BLACK again.

I repeat the same procedure but with VGA output and it works on TV but blackscreen on laptop.

With the Live CD my audio card works, my my webcam is detected (I couldnt use it because I cant install programs on live cd)

I turn off computer

I try again but using VESA video drivers and no video signal on laptop screen.

I try to use another linux distribution and download and burn the next distribution:

*opensuse GNOME and KDE latest version - only can see boot splash window
*puppy linux latest version - only can see boot splash window
*linux mint latest version - only can see boot splash window

finally I downloaded the SLAX pocket distribution and I cant believe it!

An old (2009) linux distribution CAN make my screen **work**!!!

But I **need** Ubuntu, I like Ubuntu, I have always used Ubuntu plus with the new Ubuntu 11.10 it includes the Linux Kernel 3.x version and I dont need to compile and install my Ralink RT5390 wireless card because the new 3.x Kernels have included my ralink driver by default.

Do you have any idea how can I make Ubuntu work in my laptop?

---

### Post by BC59 on 2011-12-01
It's an old problem the graphics card of your computer.

I found this old solution posted on the Bug #590504 report:

> 1. Install new versions of libdrm*, lib*mesa* and xserver-xorg-video-intel packages from ppa:ubuntu-fi or ppa:baltix (see [https://launchpad.net/~baltix/+archive](https://launchpad.net/~baltix/+archive) ) repository
2. Install new Linux kernel 2.6.38 image (linux-image-generic-lts-backport-natty) from ppa:baltix-members (see [https://launchpad.net/~baltix-members/+archive](https://launchpad.net/~baltix-members/+archive) ) or ppa:kernel-ppa
3. restart Ubuntu 10.04 operating system :)

I've updated xserver-xorg-video-intel and libdrm* packages from these repositories and can confirm that this solution fixed *all* video driver problems on my Dell Latitude E5520 notebook with Intel(R) Core(TM) i5-2410M CPU and integrated Intel HD Graphics second generation (VGA controller: Intel Corporation Device 0116 (rev 09) )!
I'm using new libdrm*, lib*mesa* and xserver-xorg-video-intel packages from ppa:ubuntu-fi (or ppa:baltix) repository for 2 days and haven't noticed any problems :)

I don't know if you can do something according to the solution.

---

### Post by peter-123 on 2011-12-01
> **BC59 said:**
> It's an old problem the graphics card of your computer.

I don't know if you can do something according to the solution.

Hi

I will try one of the solution but Im not sure if it will work.

I have understood that in each new ubuntu version it includes the newest updates, drivers and kernels. So everything is the latest including compiz, unity, gnome, python, upstart, xserver and so on

Ubuntu will be going back instead going forward.

> 2. Install new Linux kernel 2.6.38 image (linux-image-generic-lts-backport-natty) from ppa:baltix-members (see [https://launchpad.net/~baltix-members/+archive](https://launchpad.net/~baltix-members/+archive) ) or ppa:kernel-ppa

Ubuntu 11.10 includes 3.0.0-12.20 kernel so do I need to downgrade?

> 3. restart Ubuntu 10.04 operating system

The first Core i3 330UM was launched on January 7, 2010
Ubuntu 10.04: launched April 19 2010

This HP computer is a new model even the Intel i3 processor and Intel HD Graphics are newest models, versions and revisions.

How can an April 2010 Ubuntu have support for a future 2011 chipset when the chipsets wasnt created? Maybe I understand wrong :S

Do I need to wait an update from Ubuntu and/or kernel to get work my screen?

In 2.x linux kernels and olders my ralink wireless card doesnt work and in the new 3.x kernel it is compile in the kernel so no more headaches

---

### Post by foresthill on 2011-12-01
Sounds like it's your backlight. If you shine a flashlight or lamp onto the screen when the computer is on, and you can just barely make out the log in screen and cursor moving around, then it's your laptop's backlight not turning on.

I went through this with 11.04 and 11.10 on my Intel 4500 MHD graphics. There is a fix in this thread, though you might still have problems using your brightness keys and resuming from hibernation keys like I do:

[http://ubuntuforums.org/showthread.php?t=1741556&page=4](http://ubuntuforums.org/showthread.php?t=1741556&page=4)

Have you tried installing 10.10? See if the live CD works.  That's what I'm currently using until this backlight mess gets straightened out.

---

### Post by peter-123 on 2011-12-06
> **foresthill said:**
> Sounds like it's your backlight. If you shine a flashlight or lamp onto the screen when the computer is on, and you can just barely make out the log in screen and cursor moving around, then it's your laptop's backlight not turning on.

I went through this with 11.04 and 11.10 on my Intel 4500 MHD graphics. There is a fix in this thread, though you might still have problems using your brightness keys and resuming from hibernation keys like I do:

[http://ubuntuforums.org/showthread.php?t=1741556&page=4](http://ubuntuforums.org/showthread.php?t=1741556&page=4)

Have you tried installing 10.10? See if the live CD works.  That's what I'm currently using until this backlight mess gets straightened out.

Hi everybody

I cant believe it... this time Ubuntu cheated me very well...

I have never tried to use my brightness key before and I used it now...

Its working and posting from Ubuntu with Hp Pavilion g6

Its solved thanks to everybody

---

### Post by mlhudson on 2013-04-01
Had this exact same issue. Thankful for this thread. Weird that it would launch each time with brightness to minimum.

---

