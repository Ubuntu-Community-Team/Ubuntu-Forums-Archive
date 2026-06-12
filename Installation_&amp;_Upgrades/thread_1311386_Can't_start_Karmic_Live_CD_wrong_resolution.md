---
title: "Can't start Karmic Live CD: wrong resolution"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Sciamano on 2009-11-02
Hi!
I've been trying to launch the Karmic live CD but it won't work.
I can choose all the language options and such, then the cd will start working, the white ubuntu symbol will appear in the middle of the screen.
Then, when the desktop should show up, the screen goes blank and my monitor tells me the system is trying to use a resolution which is out of range for my display (2048x1052 or something, when my monitor reaches up to 1280x1024 only).

I've tried selecting "safe graphic mode" at startup, but to no avail.
Anyone can tell me how to solve?

Thanks!

---

### Post by Sciamano on 2009-11-03
Anyone? :(

---

### Post by presence1960 on 2009-11-03
you could try the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by Sciamano on 2009-11-03
> **presence1960 said:**
> you could try the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

I know, but I'd like to try Karmic before installing it...
What if I install it with the alternate CD only to find out that the same problem shows up?

---

### Post by Suiname on 2009-11-03
I see you've already tried the safe graphics mode, but I think this only applies to installations and not the running of a live session (could be wrong). I believe there are other special options on the Live cd though, you should try one of these.  These options will be listed on the bottom of the splash screen when you boot from the CD the first time.

---

### Post by presence1960 on 2009-11-03
> **Sciamano said:**
> I know, but I'd like to try Karmic before installing it...
What if I install it with the alternate CD only to find out that the same problem shows up?

Unfortunately some machines can not run the Live CD. But check from the beginning maybe your CD is bad:

[MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you burned to CD
Burn the iso to CD as an image at no more than 4x-8x speed. If you need a burning program which will allow you to choose speed see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for InfraRecorder.
Boot the CD and choose "check CD for defects"
Try installing again. If it fails again for resolution try F4 again for Safe Graphics mode.

If all this still nets the same result then unfortunately you may have to use the alternate installer.

---

### Post by presence1960 on 2009-11-03
> **Suiname said:**
> I see you've already tried the safe graphics mode, but I think this only applies to installations and not the running of a live session (could be wrong). I believe there are other special options on the Live cd though, you should try one of these.  These options will be listed on the bottom of the splash screen when you boot from the CD the first time.
[Boot Options]("https://help.ubuntu.com/community/BootOptions")

Your specs would be of help to us also, please post them.

---

### Post by Sciamano on 2009-11-03
> **presence1960 said:**
> [Boot Options]("https://help.ubuntu.com/community/BootOptions")

Your specs would be of help to us also, please post them.

The linked page, unfortunately, does not help: I can't find any way to force a video resolution, and as I said, selecting "safe graphics mode" did not solve the issue.
The CD is fine, I've tried it on my laptop and it boots and I could also install it on a virtual machine.
Also, I've never had these problems, and I've been using Ubuntu since 6.06 Dapper Drake.

Some specs:
Intel P4 3.0 GHZ
Mainboard Intel PESV845
Video Card: NVidia 7600GT
Monitor: Benq FP791

Thanks!

---

### Post by Sciamano on 2009-11-04
no ideas? :(

---

### Post by t_e_r on 2009-11-04
Try with Free Software only option (under F6). I think that excludes any proprietary driver. On older machines, that should get you at least the basic graphic functionality, i.e., no compiz. However, although I was able to get X, I got random crashes. So I am not installing Koala yet.

---

### Post by RJ12 on 2009-11-04
About the boot options, did you try using the vga=xxx and check the chart for your resolution / colors

---

### Post by Sciamano on 2009-11-05
Thanks t_e_r, but it didn't work.
X still starts with a 2048x1536 which is out of range for my monitor.
I can hear the login sound from the speakers, therefore the only problem really looks like the monitor resolution.
If no one finds a solution, I guess I'll simply have to skip the Koala..

---

### Post by Sciamano on 2009-11-05
> **RJ12 said:**
> About the boot options, did you try using the vga=xxx and check the chart for your resolution / colors

If I'm not mistkaen, the vga=xxx option only sets the resolution for the framebuffer, and my problem only appears when X starts.

---

### Post by Sciamano on 2009-11-23
Any other ideas?
This happens with Kubuntu too. :(

---

### Post by xlv1000 on 2009-11-26
I have the same problem"out of scan range"
I want to run Karmic from live cd before installation
No solution untill now.
I will wait...........

---

### Post by Sciamano on 2009-11-26
The problem is related to the nvidia graphic card. Basically the driver that the livecd uses does not work.
I wonder if I could change the video card to a different one, install Karmic with that, then install the nvidia drivers even though the graphic card is not an nvidia, change graphic card back to my nvidia and launch karmic...
Who knows if this would work? :)

---

### Post by Sciamano on 2010-02-08
Still no solution? :(

---

### Post by imanewbie on 2010-02-09
I also have the same problem... but it doest say anything about screen resolution it just goes black... but my video card is an ATI radeon 9800(not really sure but i know its not below 9500)... my monitor doesn't start but the kernel is running coz when i press the POWER button it exits and displays the "Press Enter to shutdown" message thingy...

---

### Post by Sciamano on 2010-02-09
This is frustrating. :(

---

### Post by imanewbie on 2010-02-10
Try installing it in safe graphics mode... just press f4 and select the option... worked on mine... hope this helps

---

### Post by northrup on 2010-02-10
Press F6, then ESC, then tag "-xforcevesa -vga=xxx" (xxx being the appropriate resolution code) onto the end of the parameters.  The xforcevesa option might help, just because it forces a specific video driver.  You could see if tagging "-xsetup" works, but I don't see it listed in the [list of Ubuntu boot options]("https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options").

Otherwise, your video card swap plan would work, except that, instead of installing a driver, just alter the config file (xorg.conf?  I don't remember right now) and force X to use the lower resolution.  I don't remember how to do this, but I know I needed to when swtiching from a big CRT to a lower-res LCD when I moved an Ubuntu 8.04 machine.

---

### Post by Sciamano on 2010-02-11
> **imanewbie said:**
> Try installing it in safe graphics mode... just press f4 and select the option... worked on mine... hope this helps

Been there, done that. :)
Didn't work. :(

---

### Post by Sciamano on 2010-02-11
> **northrup said:**
> Press F6, then ESC, then tag "-xforcevesa -vga=xxx" (xxx being the appropriate resolution code) onto the end of the parameters.  The xforcevesa option might help, just because it forces a specific video driver.  You could see if tagging "-xsetup" works, but I don't see it listed in the [list of Ubuntu boot options]("https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options").

I'm going to try this afternoon. I will report back ASAP.

> Otherwise, your video card swap plan would work, except that, instead of installing a driver, just alter the config file (xorg.conf?  I don't remember right now) and force X to use the lower resolution.  I don't remember how to do this, but I know I needed to when swtiching from a big CRT to a lower-res LCD when I moved an Ubuntu 8.04 machine.

So you say, I change video card, install Karmic, boot with the "new" card, change the xorg.conf to force a lower resolution, swap cards, boot (it should then come up with the forced resolution) and only then install the nvidia driver?

Thanks

---

### Post by northrup on 2010-02-11
> So you say, I change video card, install Karmic, boot with the "new" card, change the xorg.conf to force a lower resolution, swap cards, boot (it should then come up with the forced resolution) and only then install the nvidia driver?

Exactly.  Let me know how either method works.  When I did it, my problem was that the login screen was scrolling, rather than just out of range.  Editing the config file fixed my problem.

---

### Post by Sciamano on 2010-02-12
> **northrup said:**
> Exactly.  Let me know how either method works.  When I did it, my problem was that the login screen was scrolling, rather than just out of range.  Editing the config file fixed my problem.

I'm very busy these days, and I couldn't find the time to try.
As soon as I find some free time I will.
Although I'd rather hope the -xforcevesa things works, so that swapping cards won't be necessary :)

---

