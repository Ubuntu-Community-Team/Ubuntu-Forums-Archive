---
title: "More dv9000 fun..."
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by velozoom on 2006-10-28
My last post was probably too broad in scale so I'll focus on specific issues this time...  ;)  

I have an HP dv9000 laptop that I am trying to sort out how to load drivers for.  (I'm a linux noob, btw)  I downloaded the nvidia driver package (a .run file) and tried to run it from gnome.  It needed to stop the xserver so I logged out and ran it from a command line with root priveleges.  Then it said I needed the gcc package.  (rolls eyes) ok, I so I found out how to get that package and install it.  that worked well.  

Now, I've got the gcc C compiler loaded and when I go back into the coammand line and run the driver package it says it can't find a kernel interface and needs to compile one.  Ok. THen it says it can't find a kernel interface on the nvidia ftp site.  Ok. The is says it can't find the kernel source tree for the currently running kernel.  it then says I can specify the kernel source path with the -kernel -source -path command line option.  

Well, this all seems a bit scary for someone with my exceptionally minimal linux skills so I thought I would ask.  A) is this something I should do?  B) how do I find the kernel path?  and C) how do I use the source path option to set it?  

Thanks!!!!!

---

### Post by velozoom on 2006-10-28
Argh!  I am getting more and more lost....

So...I found out how to use apt-get to install the kernel source.  I used uname -r to determine the kernel version and then ran the following

sudo apt-get install build-essential linux-headers-[linux kernel version]

the NVIDIA driver would now run from the command line and everything seemed to go fine.  But it fregged my xserver.  Now x will not run.  WHen I try to start X the error message says there is an API mismatch.  DId I install the wrong kernel source?  Or is the driver installer wrong?

---

### Post by AlReece45 on 2006-10-28
First, "Step 2" of [this thread]("http://ubuntuforums.org/showthread.php?t=263851") worked for me. But since you've seemed to have gotten so far now. You need to  uninstall linux-restricted-modules, nvidia-glx, nvidia-settings, and nvidia-kernel-common.

This code should do it:

```
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
```

After that, if X still doesn't work (it probably won't). Recomile the drivers again using the .run file.

Edit: I'm assuming you're trying to install beta drivers.

---

### Post by velozoom on 2006-10-29
Thank you, AlReece, i used step 2 and it appears that the drivers installed.  However, I'm searching on a fix to the new problem....when I reboot I get nothing but a black screen.  I hear that the login screen is reached, and I even log in and hear the start up sound.....but nothing on the monitor.  Can't seem to find a solution to this extact issue......

---

### Post by velozoom on 2006-10-29
I've looked and researched and tried everything that seemed to apply and I still have a broken xserver.  I've looked at xorg.conf but don't know enough to mess with it, although the available resolution modes do not seem to reflect the capabilities of my vid card.  

I can log into the command line but have nothing but a blank screen after the iniital splash screen.  Help?  I really don't want to reinstall Ubuntu.....again  ;)

[EDIT]  ACtually, I am using the 64bit version of Ubuntu, would my woes be lessened if I reinstalled using the 32-bit version?

---

### Post by byroncoughlin on 2006-12-02
I know that it has been a while since you posted this problem. Have you had any success. If not are you using an AMD processor or an intel. I have the hp dv9035 which is the amd 64  so therefore I am using the 64 bit Ubuntu. Which Kernel version do you have. I see the same problem with 2.6.15-27. But not with 2.6.15-23. Try removing all network cables and USB items. Connect them after you restart.

---

### Post by teh.element on 2007-04-30
Best thing ever: RESTRICTED DRIVER MANAGER and AUTOMATIX2! They both will take care of everything and install the driver for you! Restricted Driver Manager is only for Fiesty in GNOME however...

---

