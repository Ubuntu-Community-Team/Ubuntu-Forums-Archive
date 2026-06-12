---
title: "Suspend/Resume issues with Sony Vaio FE"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by gregorygreg on 2007-06-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/116553](https://bugs.launchpad.net/ubuntu/+bug/116553) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a Sony Vaio FE series (VGN-FE590P) laptop that I am having difficulties with. I am running Ubuntu 7.04.

My problem is this, I can enter into suspend mode fine.  However, when I try to resume, the computer seems to do everything BUT enable the screen.  I cannot tell if the screen is dark, or if it is just not on at all.  At this point I am forced to perform a hard reset, and my computer is not happy (fsck)...

Where can I get started on fixing this issue?


Thanks for everyone's support,
Greg

---

### Post by hardyn on 2007-06-20
what video card?

---

### Post by IntuitiveNipple on 2007-06-20
Yes, since I reported that bug I have been investigating. The core of the issue is the backlight not being switched back on. It appears to be related to the nvidia chip-set and possibly the BIOS ACPI functionality not being used.

If you have another PC you'll find you can ssh into the laptop and it is working (mostly) okay.

If you watch the thread on the [sony-laptop kernel platform driver](http://ubuntuforums.org/showthread.php?t=465491) you will see many Vaio issues are being actively worked on.

---

### Post by hardyn on 2007-06-20
I have an Asus z71vp which shares alot of the problems the sony's... try adding VGA=791 to the grub boot parameters.

..... quiet splash vga=791

this is required to get my nvidia based notebook to fire back up.

---

### Post by gregorygreg on 2007-06-20
I have a nvidia card.  I realized that my problem now is a little bit different than I first thought.  When I resume from standby, everything starts up but all I see on my desktop is a pointer with a small box around it.  Besides that, everything around the pointer is black.  It seems like the gui is not initializing properly. 
Any ideas?

---

### Post by IntuitiveNipple on 2007-06-20
> **hardyn said:**
> 
..... quiet splash vga=791
That is for resuming from hibernate when the PC has to completely boot, rather than resume from suspend where the state of the PC is frozen in RAM. I'll try that same mode using vbetool see what it does.

**gregorygreg**: I am currently debugging this issue. I'm working outside of Gnome with console-mode to reduce complications.

I'm connected over the network using ssh and issuing commands to control the backlight successfully. I can turn the backlight on/off remotely using:
```
$ sudo vbetool dpms off
$ sudo vbetool dpms on
```
After the PC resumes from suspend however the network doesn't reactivate. I can start another terminal blind by pressing Ctrl+Alt+F2 and logging in and issuing commands and seeing disk activity as a result of running commands, and I can force a restart by typing blind:
```
$ sudo su
Password: *******
$ shutdown -r now
```
The PC then restarts.

I'm going to work on getting the network back up, and then I can do some remote post-resume debugging.

At the moment it looks like the nvidia driver isn't correctly restoring the hardware configuration.

---

### Post by Kingsley on 2007-06-20
> **hardyn said:**
> I have an Asus z71vp which shares alot of the problems the sony's... try adding VGA=791 to the grub boot parameters.

..... quiet splash vga=791

this is required to get my nvidia based notebook to fire back up.
Thanks. That fixed the problem with suspend on my HP dv6000.

---

### Post by Bluecircle on 2007-06-21
Try my suspend/hibernate fix, it works fine on my Vaio TX.

[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by hardyn on 2007-06-21
> **gregorygreg said:**
> I have a nvidia card.  I realized that my problem now is a little bit different than I first thought.  When I resume from standby, everything starts up but all I see on my desktop is a pointer with a small box around it.  Besides that, everything around the pointer is black.  It seems like the gui is not initializing properly. 
Any ideas?

are you running desktop effects?

---

### Post by hardyn on 2007-06-21
> **IntuitiveNipple said:**
> That is for resuming from hibernate when the PC has to completely boot, rather than resume from suspend where the state of the PC is frozen in RAM. I'll try that same mode using vbetool see what it does.


I need that switch to resume from memory suspend, i had to do this with both an nvidia 6600 and an ATI X700

---

### Post by gregorygreg on 2007-06-21
yes I am running desktop effects.  I will try it w/o

---

### Post by gregorygreg on 2007-06-21
okay I disabled desktop effects and my computer can now return from sleep mode.

However, I have a problem with my sound after resuming.  It "crackles" and sometimes doesn't work at all..

what's up with this?

---

### Post by hardyn on 2007-06-21
lots of threads on this, you might have look into compiling and installing the new ALSA

---

### Post by wvengen on 2007-06-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/100114](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/100114) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I recognize this problem on my Sony VAIO VGN-FE41E (see [bug 100114]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/100114")) and added snd-hda-intel to my modules to unload on suspend + removed volume control.

---

### Post by gregorygreg on 2007-06-23
can you explain to me how to fix this?

---

### Post by namityadav on 2007-07-07
> **gregorygreg said:**
> okay I disabled desktop effects and my computer can now return from sleep mode.

However, I have a problem with my sound after resuming.  It "crackles" and sometimes doesn't work at all..

what's up with this?

I have a similar problem. Disabling desktop effects makes the "standby" feature working. Any suggestions on how I can have the desktop effects enabled and still use standby?

---

### Post by Depressed Man on 2007-07-07
I forget where it was, but there was a specific method to fit suspend/hibernate for Beryl users. Not sure for Compiz or Compiz fusion though.

---

### Post by lorenzogrespan on 2007-07-22
> **gregorygreg said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/116553](https://bugs.launchpad.net/ubuntu/+bug/116553) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a Sony Vaio FE series (VGN-FE590P) laptop that I am having difficulties with. I am running Ubuntu 7.04.

My problem is this, I can enter into suspend mode fine.  However, when I try to resume, the computer seems to do everything BUT enable the screen.  I cannot tell if the screen is dark, or if it is just not on at all.  At this point I am forced to perform a hard reset, and my computer is not happy (fsck)...

Where can I get started on fixing this issue?
Greg

I solved this problem (although on an Asus) with

```
vbetool vbestate save > /tmp/vbestate
[...]
/bin/sync
chvt 1
echo mem > /sys/power/state
vbetool vbestate restore < /tmp/vbestate
[...]
```

but your mileage might vary.

---

### Post by 0live on 2007-08-07
> **gregorygreg said:**
> I can enter into suspend mode fine.  However, when I try to resume, the computer seems to do everything BUT enable the screen.
I think I had the same problem, but it's fixed now. Actually I had a rather hard time getting the screen back to life in opensuse, so I didn't bother and used the same method when I switched to Ubuntu and realized that resume wouldn't work 'out of the box' either.
Basically, **s2ram -f -a 2** works for me (VGN-FS115Z) **BUT** not with *any* nvidia drivers:
- I didn't even try with the non-proprietary ones
- it worked with the legacy ones (7185)
- it did not work with nvidia-glx-new (9755) which actually is old.
- it is working with the newer ones (100.14.11)
That said I sometimes have the x server crashing when I log out (just log out, not reboot or anything) so I wouldn't highly recommend you to install v. 100.14.11, which is not officially supported by Feisty at this time.

---

