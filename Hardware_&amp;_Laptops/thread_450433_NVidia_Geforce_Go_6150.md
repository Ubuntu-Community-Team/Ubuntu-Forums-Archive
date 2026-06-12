---
title: "NVidia Geforce Go 6150"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by Elliot.strumlauf on 2007-05-21
I recently bought a brand new laptop with a Geforce Go 6150. Any and every attempt I have had at installing the NVidia driver has crashed my XOrg, whatever that it, and it gives me a crapy message when i start Ubuntu. I have tried IRC ubuntu nvidia and effects, no one out of the 90 something people there responded to me.... If someone could help me it would be awesome. Thanks

---

### Post by EXCiD3 on 2007-05-21
Which Ubuntu release are you using? If you are using feisty, you can enable the driver through Restricted Drivers Manager. Another route that works on ALL releases is using Automatix. Download it, and then choose to install the Nvidia driver. You could also use the ENVY script to install it for you. Just google "Automatix" or "Envy Ubuntu" and you will get results for the software. This ought to take care of your problem.

---

### Post by Kobalt on 2007-05-21
If you are new to linux/ubuntu, I'd advise you at first not to try either Automatix or Envy : it can work, yes, but Automatix also can brake your system heavily while Envy may require more skills to get your X server going on in case of a crash. Have you tried the Restricted Drivers Manager yet ? Can you please post us you xorg.conf file : ```
cat /etc/X11/xorg.conf
```

---

### Post by wooxy on 2007-07-12
I also have a GeForce 6150 in my laptop, and (I'm a beginner) it will only boot Feisty Fawn when using kernel option vga-771 ... when I turn off this option, it just never can finish booting.

Some of my research turned up this list from Nvidia, 
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)
and I don't like the look of it.  While "GeForce Go 6100" and "GeForce 6150" are on the list, our "GeForce Go 6150" is not!!

As for the "Restricted Drivers Manager", it shows the Nvidia driver as existing and OFF, and it cannot be turned on by clicking in the "on" checkbox.  Attempting to change the display properties gives me a dialog to click and says it will be enabled on the next boot.  It never does.  I even have tried switching off the boot option "vga=771", no go.  

Well, at least Vista still runs on the thing :)

update:  I found another list at Nvidia which does include the GeForce Go 6150.  The version numbers aren't in the same order of magnitude, though, so I have no idea what's new or old, but this is more likely than not good news.

[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html)

---

### Post by Elliot.strumlauf on 2007-08-09
Any new observations? I have just switched back to Ubuntu from Vista/XP and I am trying to get into CompizFusion. I am a little afraid, because everytime I install the retricted driver from NVidia XOrg crashes, and I just got wireless up so I don't want to reinstall and have to do that again. Any new voices?

---

### Post by mjwhitfield on 2007-10-08
I there a any update on this? I'm planning on buying a COMPAQ F560EM, which has this card and I'd like the shiny desktop effects.

---

### Post by dabl on 2007-10-08
> **Kobalt said:**
> 
Envy may require more skills to get your X server going on in case of a crash.



Not to be argumentative, but who can't remember ```
sudo envy -t
``` ?

That's the only skill you need, to recover the GUI after a kernel upgrade.  If necessary, tape a note to your monitor!

:)

---

### Post by Elliot.strumlauf on 2007-10-08
Well, not to be argumentative, but read before you post! This isn't about upgrading kernels. I install the NVidia driver by Automatix, Enable Restricted, what have you, and it crashes next time it loads. Hopefully 7.10 won't be garbage

---

### Post by cubeist on 2007-10-08
The 6150 should work fine with just the restricted driver (system/admin/restricted driver).  My 6150 works great in feisty with the 100.10.xx driver and perfectly in gutsy with the 100.14.xx driver.  Beryl in FF works very smoothly and compiz is also very smooth in gutsy.

---

### Post by MikaelHolber on 2007-10-18
This problem seems to be with Gutsy as well. I took a look at my friends computer today which has a Nvidia Geforce Go 6150. I tried to load the driver from nvidia-xconfig into the xorg.conf-file, doing it manually and using Gutsy's fancy new screen-utility. The card is detected and listen in lspci but no luck with making it work with the nvidia-proprietary driver. Using envy or automatix will most likely end up with the same result.

---

### Post by Shannon_VanWagner on 2007-10-21
Hi there,

I installed Ubuntu 7.10 on my Dell Inspiron 2650 and enabled Nvidia GeForce Go proprietary drivers and after rebooting the screen either was blank, frozen, or sometimes would show some garbled output.

Here's what I did to fix it:

On bootup, hit F2 to enter the Dell BIOS
For the section marked "Video Display Device", switched the setting from "Simul Mode" to "LCD Mode"

Saved the setting with F10 and then exited and rebooted.


On reboot everything came up normal.

Go Linux!!

Hope this helps!

Shannon VanWagner

---

### Post by CaptBill on 2007-10-21
I have an Hp 9000 with a 6150 nvidia card. THE ONLY WAY I got it working was to download ENVY and run it. I is a long download but it worked perfectly. I tried every other method on this list. I worked at it for over a week. Alberto Milone website is very good and you can download envy there [http://albertomilone.com/](http://albertomilone.com/)

---

### Post by mrgordonz on 2007-12-12
I scoured the Net for ways to install drivers for my NVidia Geforce Go6150.  I eventually decided to use Envy - and it worked perfectly.  No errors, super easy to use, screen resolution is great.

---

### Post by sowelie on 2007-12-12
I also have a geforce go 6150, and I only experienced minor problems.  I had to disable APIC to get the live cd working and also to boot for the first time before installing my graphic drivers.  Once I installed the restricted drivers, everything worked fine.  I just installed the drivers right out of the repositories, which is the safest way to do it because if the kernel is upgraded you don't have to manually rebuild the kernel modules.

---

### Post by DraQla on 2008-02-01
Hi. Got the same card and Ubuntu 7.1 - and quite some problems with it.
Main problem is that the screen resolution won't go above 1024x768. I used to run 1280x800 under XP.
I tried to activate the diver in the restricted driver section but I just got the message:
"Software source for the package nvidia-glx-new is not enabled."

I looked up what nvidia-glx-new was and found out that "sudo nvidia-glx-config enable" should enable it.
Either I'm stupid or I'm stupid, but the terminal tells me:
"sudo: nvidia-glx-config: command not found"

A friend recommended changing the modes in xorg.conf, but there was nothing to be changed...

So. I'm new to this. I have hardly any experience with Linux. I feel totally stupid.:confused:

---

### Post by qhimq on 2008-02-01
are you running 64bit gusty?

i had a big problem installing the nvidia driver too.

envy didn't even work for me installing the driver.  How i solved it was install run envy and use the clean any installation option.

Then i went to [http://www.nvidia.com/object/linux_display_amd64_169.09.html](http://www.nvidia.com/object/linux_display_amd64_169.09.html)

Downloaded that thang, then ran it after killing gdm.

Need more specific information on how to do that, then ask.

---

### Post by DraQla on 2008-02-01
Thanks for your help and the links, however I can't make head or tail of it.
This started when I tried to install envy and it didn't work and it goes on with me having no idea what the nvidia read-me tries to tell me.
So, I'm stuck at the point of downloading the driver from nvidia and a terminated installation due to the X Server running.

Oh, and yes. I'm running the 64Bit version.

EDIT:
After I ran some updates Ubuntu decided to let me run the restricted driver and upon reboot I saw my beautiful 1280x800 screen resolution. Main problem 1 resolved - if I manage to get my wlan device running I'm all happy and set... :D

---

