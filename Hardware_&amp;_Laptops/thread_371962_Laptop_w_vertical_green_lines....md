---
title: "Laptop w/ vertical green lines..."
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2007-02-27
I've got an HP laptop with an nVidia GeForce Go 7200, and this started happening *after* I sent my laptop back to HP for a malfunctioning wireless card...

My laptop is like example two on this page...
[http://www.laptoprepairguy.com/laptop/2006/08/17/bad-video-on-lcd-screen/comment-page-15/](http://www.laptoprepairguy.com/laptop/2006/08/17/bad-video-on-lcd-screen/comment-page-15/)

However, I do not get this when running Windows, only Linux.

I am running stock drivers and whatnot in Windows, and latest nVidia drivers in Linux. The problem doesn't seem to occur until I get the nVidia drivers.

Can anyone help me out with this?

---

### Post by tgalati4 on 2007-02-27
Sounds like a video syncronization problem.  Try in a shell:

dpkg-reconfigure xserver-xorg

then reboot.

If that doesn't fix it, they start marching through the resolutions:

640 by 480 up until you get to your native screen resolution.  Take note of the results.

Good luck.

---

### Post by enigma_0Z on 2007-02-28
Well, the nvidia installer didn't have any issues before, and my laptop has a native resolution of 1280x800 so..... I'm not sure how that's going to help.

Also, I reinstalled windows (ick!) so that I can send it back to HP again... funny thing is that I never had this problem untill HP "fixed" my wireless card...

---

### Post by tgalati4 on 2007-03-01
It's possible that they damaged the ribbon cable when disassembling the laptop.  But the damage is subtle such that the windows nvidia driver does not cause a problem.  

Did you try several different resolutions in Windows?  Perhaps there is a syncronization problem.  If you find it in Windows then you might be able to back out the vertical and horizontal refresh rates that cause it.

It could also be a video memory problem.  Ubuntu is not detecting the correct amount of video memory and overwrites it resulting in a garbled screen.  

Do a search in the forums for how to hardcode the memory in xorg.conf.

Good luck.

---

### Post by mormegil on 2007-03-01
I also am experiencing this problem, also after sending my machine to hp for repairs.  

I get the problem in windows when not connected to ac power.  Do you?

I get the problem using the latest nvidia drivers in linux when using kubuntu feisty herd 4 for amd64.  Have not tried earlier or i386 installs yet (takes so much time to keep changing OS.  At least its faster then gentoo installs...)  What distro are you running when you get the errors?  When you run with open-source drivers, are you using "vesa" or "nv"  nv doesnt get screen resolution correct on feisty, but it does on edgy.  vesa is horribly slow.  

I'm stuck, thinking of trying to have hp refund or replace the whole thing if I can...

---

### Post by hardyn on 2007-03-01
are the lines present when drivers are not loaded?  during post? etc.

it looks alot like a dammaged video.

---

### Post by enigma_0Z on 2007-03-13
> **mormegil said:**
> I also am experiencing this problem, also after sending my machine to hp for repairs.  

I get the problem in windows when not connected to ac power.  Do you?

I get the problem using the latest nvidia drivers in linux when using kubuntu feisty herd 4 for amd64.  Have not tried earlier or i386 installs yet (takes so much time to keep changing OS.  At least its faster then gentoo installs...)  What distro are you running when you get the errors?  When you run with open-source drivers, are you using "vesa" or "nv"  nv doesnt get screen resolution correct on feisty, but it does on edgy.  vesa is horribly slow.  

I'm stuck, thinking of trying to have hp refund or replace the whole thing if I can...

What kind of laptop do you have?

My problems are only after the nvidia binary driver has been loaded, but these problems bleed into windows after they start.

No lines in POST, usplash, etc...

Refresh rates not cause, color/resolution independant as well.

---

### Post by mormegil on 2007-03-17
I have an hp dv6000z with nvidia go 7200 graphics card.   I have no problems in kubuntu herd4 amd64 version until i install the nvidia proprietary drivers (nvidia-glx).  

Also, I cannot get the native nv driver to display any resolution above 800x600.  The install defaults to vesa which is very slow.  

ideas?

---

### Post by mormegil on 2007-03-17
I do not see geforce go 7200 listed as supported by nvidia drivers: [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

so that's probably part of the issue?  Any ideas why this one card is not supported?

---

### Post by enigma_0Z on 2007-03-17
Hrm... I noticed that too, but then why doesn't the driver fail to install/load when it doesn't find any valid hardware...

I never had this problem until HP "fixed" my laptop. Before all this mess, the binary drivers loaded just fine, and I had all of the advanced shaders & acceleration and everything.

---

### Post by mormegil on 2007-03-25
Any chance that you upgraded your driver after you got the machine back from hp?  Are you using the 64bit distro (amd64) or the i386 version?  I had no problems when running i386 edgy before, but experienced the green lines running amd64 version of feisty herd 4.  Am trying i386 version of feisty beta now.

---

### Post by enigma_0Z on 2007-03-27
It is possible... what version of the driver did you use that worked, and can you post a link?

I still don't have the laptop back from HP, I'm going to ask for a replacement today (it's been about two months for the whole ordeal).

---

### Post by mormegil on 2007-04-02
I was using the nvidia-glx edgy package, whatever was current/stable in november/december 2006.

Just received a restricted-modules update from apt-get this morning on Feisty.  Am trying again, so far is stable with no green lines, but sometimes they take a while to appear.  

(I'm running feisty beta i386 right now)

Surprising that they still haven't sent you your machine.  I assume the replacement will also be a dv6000z?

thanks.  I'll try to be better on the reply-time.

---

### Post by mormegil on 2007-04-02
nope, problem remains despite updates.

---

### Post by enigma_0Z on 2007-04-06
Hmm. I'd say send it in. Just got my replacement... I'm in windows right now, still need to install Linux.

---

### Post by mormegil on 2007-04-06
I actually am already using my replacement.  I sent my first dv6000z in hp when one day the video would not come on at all (no windows, bios, anything).  When I got it back I first experienced the green vertical lines problem.  Because this problem occurred in Windows XP when on battery (though not when on AC), they replaced it.  I think the problem in windows occured only after i installed nvidia-glx in linux.  The replacement is an almost identical dv6000z, (still with the nvidia go 7200) but has Vista instead of xp.  I installed linux (feisty beta, since it has alsa-13 so sound works out of the box).  I got wireless working, (ndiswrapper), smp support and everything (using the i386 version and booting with kernel option noapic).  The opensource nv driver worked fine (needed to manually adjust resolution and manually add synaptics touchpad to xorg.conf).  I install the binary driver nvidia-glx, switch my xorg.conf driver from nv to nvidia, and everything looks good for a little while running 3d acceleration, glxgears, etc.  After a little while (usually after opening and closing a 3d app like glxgears) I get the green lines on any black background (dvd window, konsole window, etc, on both ac or battery).  Unlike my earlier machine w/ XP, Vista does not show any green lines on battery power (or on ac). 

Let me know if you get the green lines when using the nvidia driver
What are the specs of your replacement?  dv6000z w/ Nvidia go 7200?  xp or vista?
what version of ubuntu?  (edgy or feisty, i386 or amd64)
On what grounds did hp replace your machine?  

Thanks!

---

### Post by enigma_0Z on 2007-04-10
No, I do not get the green lines anymore.

My system is basically the same, but with the following extras:

1. Vista Home Premium
2. Webcam
3. Hard Disk size upgrade

I don't get any green lines, been running the thing for hours at a time. Did the problem start rather immediately? I'm using the binary driver--but I downloaded it from nvidia's website, IMO the driver that comes with ubuntu is really screwed up anyway, as far as how the files are organized.

You needed to manually adjust the resolution & synaptics touchpad? that's odd--they were automatic for me.

wow, I've edited this like five times now.

IN answer to your questions:
No green lines
Almost identical specs, +vista home premium, +40 GB extra hdd, +webcam, +remote
Feisty i386
Basically, because I had sent it in three times, I said that I doubt the integrity of the PC from being disassembled and reassembled several times and asked for a replacement.

---

### Post by mormegil on 2007-04-16
still no luck.  maybe a clean install would help.  a few more questions:

1) are you using ndiswrapper? fw-cutter?
2) what boot options are you using?
3) have you tried amd64 version?
4) any other issues? 

(me: my wireless is working fine with ndiswrapper, never tried fw-cutter.  I boot with the option noapic.  haven't tried amd64 recently.  for some strange reason konqueror cannot connect but firefox works fine.).  

Thanks

---

### Post by tonyldo on 2007-05-02
I have a dv6000z Go 7200 with the same problem , The Green lines when i install the nvidia drivers from the nvidia site... with the nv driver the system has no problem.
i install the faisty fawn with boot option : noapic nolapic 
I think that this is a problem with all dv6000z laptop with the card Go 7200 :(
I tried Sabayon, OpenSuse too . And a lot of boot option like iommu=off , noirqdebug, NOIRQPOLL , NOSMP ... with no sucess 

I dont have more ideas to do nvidia driver work on my laptop. :(

Lets wait for futures kernels or bios updates or nvidia linux drivers :(

---

