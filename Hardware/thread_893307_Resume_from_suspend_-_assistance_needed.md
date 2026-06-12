---
title: "Resume from suspend - assistance needed"
date: 2008-08-18
forum: Hardware
---

### Post by toshwriter on 2008-08-18
Hi all,

I've spent a long time struggling with the suspend on my laptop - a Sony Vaio VGN-AR51E (specs: [http://support.vaio.sony.co.uk/specifications/specifications.asp?site=voe_en_GB_cons&c=0&s=VGN-AR&m=2873](http://support.vaio.sony.co.uk/specifications/specifications.asp?site=voe_en_GB_cons&c=0&s=VGN-AR&m=2873)). 

The machine seems to go into suspend ok, but when it wakes up all I get is a black screen with a blinking cursor. If I go to TTY1 I can see the normal text, but then the keyboard stops responding immediately and I have to reboot.

I was running the nvidia driver, and since I heard it can cause problems with suspend I uninstalled it. When I try to resume now the screen doesn't come on at all! I just get a bit of HDD activity then nothing happens. I've left the driver uninstalled for all my testing to ensure that it wasn't that causing the problem.

I'm running an up-to-date 64-bit hardy installation. I happened to have the live cd of the 32-bit version, so I tried that (to ensure it wasn't happening as a result of something I'd installed, or it being a 64-bit install). I had the same problem, with the screen not coming on.

I've tried many things to narrow down what's happening - too much to go into in detail here, but I'll mention the bits which seem most promising. 

I followed the instructions on [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend), and I got (in the dmesg):

[   13.590875]   Magic number: 0:731:42
[   13.590877]   hash matches /build/buildd/linux-2.6.24/drivers/base/power/main.c:76
[   13.590881]   hash matches device ttyeb

Apparently, ttyeb is the device that is likely to be causing the problems. The instructions say: "The only way to prove this [is what's causing the problem] is to remove the module prior to initiating suspend."

I'm fairly new to linux, so I really have no idea how to do that for this device, or even what the device is! I tried:

ls /dev -l | grep ttyeb

which gave me:

crw-rw-rw-  1 root   tty       3, 251 2008-08-18 09:18 ttyeb

although I can't really work out any more!

My questions are:

a) What is ttyeb? (the major number of 3 suggests it's related to a hdd according to something I read)
b) Could it be this that is causing the problems?
c) If it is, does anyone have any suggestions on how I can go about fixing it?
d) If it's not, are there any further investigations that I can do to work out what's going on?

Other things I've tried are various quirks ([http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-explain.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-explain.html)) which I thought might be appropriate. None worked.

I also tried installing uswsusp but I couldn't get it working due to some problems with my swap. I can't see any problems with it - the command free gives the expected output. However, my swap never gets used because I've got 2GB of ram (I don't even max it out on Vista!) so if there were any problems I wouldn't know.

Many thanks for your help.

---

