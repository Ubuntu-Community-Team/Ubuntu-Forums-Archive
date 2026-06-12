---
title: "USB Fails After Suspend on Thinkpad"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by AClark on 2007-04-21
On my IBM A31 Thinkpad  the built in USB 1.1 ports fail on resuming from suspend to Ram

I have a PC Card with two USB 2.0 ports that works - I doesn't matter if I plug it in before suspending or plug it in after coming out of suspend - it works either way.

Rebooting always brings them back.

This started after the update to 2.6.20-11 generic kernel - I am now at 2.6.20-15 

If I boot into a kernel prior to -11 USB works correctly.

This is the yield from lsusb without the PC Card 

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

awc@Thinkpad-A31:~$ lsusb  with PC Card plugged in
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Same yield before and after suspend

I would like to continue to use the 1.1  ports for things that don't require 2.0 and also not tie up the card slots unnecessarily - especially since the end of the USB PC Card blocks off both slots.

Is there a way to restart the USB system that might redetect the built in ports without rebooting ??

I installed Herd 3 and have been using Fiesty ever since - This is about the worst problem I have had so I can't complain - still it would be nice to find a solution.

I have been able to solve most of my other (minor) problems by searching the forums but haven't found anybody else with this one so far.

---

### Post by mpvano on 2007-04-23
My T30 internal USB fails on every resume as well. This is a real show stopper. I'd like to know the answer to the same question. I'm hoping a proper update will be issued soon to fix it - it seems this has happened before with other releases....

Mario

PS

I also had trouble with my internal wireless, but I think that's because it's an orinoco chipset and I needed to add blacklist entries for several conflicting drivers being loaded all at once. I suspect you have a later chipset and didn't have this problem.


mv

---

### Post by AClark on 2007-04-23
" I'm hoping a proper update will be issued soon to fix it -"

There have been 4 updates to the kernel since the update that caused this so I've decided to stop holding my breath. :(

"I also had trouble with my internal wireless, but I think that's because it's an orinoco chipset and I needed to add blacklist entries for several conflicting drivers being loaded all at once. I suspect you have a later chipset and didn't have this problem."

My internal wireless is a Prism chipset and has been trouble free.  The wierd wireless problem I have is that with my USR 802.11G PC Card ( Internal is 802.11B) , I can't connect to my Buffalo router unless the router is configured for mixed mode which causes the throughput be too slow to stream video or even mp3s across the lan.

I originally thought this was because there was some kind of conflict with the internal driver.
However when I physically remove the internal card from the computer it still won't connect unless set for B & G, so I don't know if its the Linux driver for the TI chipset or something about the Router. (Works fine in WinXP)

---

### Post by mpvano on 2007-04-23
Sounds like the prism driver (which is being loaded for my internal card but does NOT work with it) is loaded last - good news for you and bad for me!

I wonder if you aren't having other multiple driver problems yourself. I don't know what chipset your USR card uses, but perhaps you should review what you see after you do an "lsmod" command if you haven't it yet - blacklisting something may help you out as well....

The fact that a kernel update started the USB problem is a good hint. Do you know which version of the kernel was the first one with the problem? I'm guessing it's not actually a problem in the kernel, but more likely a change to the kernel configuration they made at that time.

he kernel configurtaion file is stored for reference purposes in the /boot directory as well. You might try comparing the lsat one that worked with the first one that doesn't. The files are named "config-" follwed by whatever the kernel is called. They're text files and can be manually compared side-by-side, or the "diff" command in a shell window might be useful in finding the differences.

Sounds like time to try to figure out how to use launchpad again and see if there are any open bug reports on this....
(24-April-2007 edited:  I added my problem report on the USB issue to launchpad #99267 - mv)

Let me know if you are able to learn anything from the config files. In any event, thanks for the additional information.

Mario

---

### Post by airbornespent on 2007-04-30
Found this bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/37328]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/37328")

I'm having the exact same problem on my T30, but it doesnt seem limited to thinkpads. I'm gonna try some different kernels through synaptic.

---

### Post by airbornespent on 2007-04-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/37328](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/37328) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				My old 2.6.17 doesnt seem to work after the 7.04 update. Gonna try remove and reinstall, unless its not compatible with the feisty updates...

---

### Post by airbornespent on 2007-05-27
So, I don't know how to downgrade my kernel, I think I'm about to start a new thread asking this. Unless someone has a fix for this issue, **please**, having to reboot just to use USB after suspending is *annoying*...

---

### Post by Talon2 on 2007-05-30
> **mpvano said:**
> My T30 internal USB fails on every resume as well. This is a real show stopper.

Confirmed on my T23 as well.  This really is a show stopper as I run an external wireless device that pulls power from usb and I use a usb mouse.

Anyone got any ideas how to work around this until there is a fix?

---

### Post by mpvano on 2007-05-31
It's not as easy as you think -  kernels need to have patches to support features needed by Ubuntu's Fiesty boot and system utilities. You'd need to backport their new Fiesty patches to another kernel, and patches are NOT portable between versions.

It would probably be more productive to try to figure out how to get more priority attached to  fixing this issue.

It's listed in launchpad (and I added a report there myself), but has low priority to be fixed because the developers can't seem to grasp the importance of the problem. They've especially failed to grasp that it seems to affect a lot of other notebook vendors and models beside the ones that filed bug reports

Have you added a bug report, yourself? Perhaps more reports might convince them it's got to be fixed!

It would also help a lot if someone had pinned down exactly what the bug IS that's causing this. There might be a simple workaround, (or their might not!).

Unfortunately, I've had to switch to Debian Etch (which is more stable than fiesty) on my T30 because 6.06 is just too far out of date, so I need to swap in another disk drive to work on the Fiesty problem and I just don't have time to look into it any more.

It appears that something is failing to release the USB hardware driver, which makes it impossible to reload it cleanly when waking up from sleep. There seem to be other modules with this problem in Fiesty as well. I'm guessing it's a change to the driver interface specification breaking things. Does  anyone know how to force the driver to unload?

Hibernation seems to work around the problem, but on Ubuntu, (oddly unlike Debian Etch which has stuck with an older kernel), hibernation and restarting from it take almost as long as shutting down and rebooting, so that's no help at all. If your machine hibernates quickly, it might be a workaround for you.

still waiting as well.....

Mario

(p.s. Things are'nt all that rosy in the Debian Etch world either - they're currently at war with the Firefox/Thunderbird developers and constantly break these (and other) essential products in order to promote their ideology)

---

### Post by Talon2 on 2007-05-31
> **mpvano said:**
> 
Hibernation seems to work around the problem.


Hibernation isn't the work around for anything here.  Hibernation is broken.

Ubuntu needs to suck less quickly as far as power management is concerned or I'm going to decide I made a mistake and start looking elsewhere.

Let me see:

Fiesty on my T23 =

- Broken suspend (on second resume I get the black screen of death).  Power off, power on is the only way to recover that I can find.  Totally broken.

- Broken hibernate.  The system acts like it hibernates but the system boots normally instead of coming out of hibernation.  Totally non-functional.

- USB non-functional after suspend.

Did I mention that these are regressions?  This stuff used to work in Dapper.  Did mention that these issues seem to all carry a LOW priority in Launchpad?

---

### Post by ppkkss on 2007-05-31
> **Talon2 said:**
> Hibernation isn't the work around for anything here.  Hibernation is broken.

Ubuntu needs to suck less quickly as far as power management is concerned or I'm going to decide I made a mistake and start looking elsewhere.

Let me see:

Fiesty on my T23 =

- Broken suspend (on second resume I get the black screen of death).  Power off, power on is the only way to recover that I can find.  Totally broken.

- Broken hibernate.  The system acts like it hibernates but the system boots normally instead of coming out of hibernation.  Totally non-functional.

- USB non-functional after suspend.

Did I mention that these are regressions?  This stuff used to work in Dapper.  Did mention that these issues seem to all carry a LOW priority in Launchpad?

I have all the above problems with my T23 plus many of the networking issues discussed elsewhere.  The real show stopper that caused me to revert back to 6.10 was the loss of 3-D acceleration under feisty from my S3 Supersavage video card which meant Google Earth became unusable.

---

### Post by Talon2 on 2007-05-31
> **ppkkss said:**
> I have all the above problems with my T23 plus many of the networking issues discussed elsewhere.  The real show stopper that caused me to revert back to 6.10 was the loss of 3-D acceleration under feisty from my S3 Supersavage video card which meant Google Earth became unusable.

At least there is something a mere mortal can do about the S3 video breakage:

Problem:  Direct Rendering does not work.

Solution:  See:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905)

  See script in comment 46.  Use defaults for all questions.

---

I think I'm going to rename "Fiesty" to "Regression" as that more accurately describes what it is.

---

### Post by schlauf on 2007-06-02
This bug still remains unfixed on my Thinkpad X30. This is especially annoying since I use an external bluetooth dongle to connect to my phone for dial-in purposes ... and rebooting each time I'm changing trains is not my way to go - especially since software suspend works like a charm for the X30.

Ths filed bug report on launchpad doesn't reflect the particular side effects on USB, right? I've added my description, some more technically inclined people should file in a new, separate bug report, and not move it to the xserver directory.

---

### Post by iqag1060 on 2007-06-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99267](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99267) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				These bug reports would seem to be more directly relevant to this problem than the blank screen bug linked to before:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99267](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99267)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/44622](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/44622)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78634](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78634)
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/105563](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/105563)
[https://launchpad.net/ubuntu/+source/acpi-support/+bug/40397](https://launchpad.net/ubuntu/+source/acpi-support/+bug/40397)

There's a fix suggested in two of those Launchpad threads. Open a terminal before hibernating, and after resuming run:
```
sudo rmmod usbhid xpad ehci_hcd ohci_hdc usbcore
sudo modprobe usbcore usbhid xpad ehci_hcd ohci_hcd

```

This did not work for me (Feisty on X30) but it might for you. Another recommendation is a [patched kernel]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99267/comments/24"). You could also try [uswsusp]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/") (also did not help me with this problem.)

---

