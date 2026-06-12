---
title: "New Dual-boot Ubuntu User Experiencing Wireless and Resolution Problems"
date: 2013-10-15
forum: Hardware
---

### Post by barrings on 2013-10-15
Hello,
A couple months ago I assembled a new desktop computer with an Intel i7-3770K processor and a nVidia GTX 680 video card currently installed with Windows 7 Pro.  About a month or so ago I decided to install Maverick but instead of the expected 1080p HD I got a wondeful looking 800x600.  Just to be extra kind, Maverick decided to give me no internet functionality whatsoever.  I have a AR 8161 ethernet card on board and a AR5BWB222 PCI wireless/bluetooth adapter card.  Of course neither of these seem to be working.  (Perhaps a driver issue?  If so which should I try, and how do I get it?)  It goes without saying that ```
sudo apt-get install
``` is useless and I cannot install the official nVidia drivers, the absence of which is obviously causing the resolution issue.

Any help on this would be greatly appreciated.

Thanks a lot,
Stephen Barrington Leigh

---

### Post by coffeecat on 2013-10-15
> **barrings said:**
> Maverick

Maverick has been end-of-life (unsupported) for about 18 months now.

> **barrings said:**
> Perhaps a driver issue? 

Since both of those network devices appear to be quite recently released ones, and considering the kernel in Maverick is about 2 years old, it's likely that it's not so much a driver issue, but rather an absence of drivers for those new devices in that old kernel. You need to try a newer version of Ubuntu. I'd suggest going for even newer than the current LTS (12.04) because I see that your ethernet card is unlikely to work out of the box with 12.04:

[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

Try running the live session from a CD/USB of the current 13.04 and seeing if the network devices will work. Or, since 13.04 is only supported for another three months or so, wait a couple of days and then download the ISO for 13.10 when it is released on Thursday and try that live. 

A later version of Ubuntu will also give you a later version of the nouveau open source driver which might give you the correct resolution without having to use the proprietary nvidia driver.

---

### Post by barrings on 2013-10-16
Hello,
Thanks coffeecat for your quick reply.  Since posting, I have been thinking exactly the same thing.  I tried to upgrade with Maverick's upgrade utility (it's name escapes me at the moment) to 11.10 as starting point, but with a strange set of errors, which caused me to install Raring on top of Maverick.  Since then, I have encountered various other extreme stress-inducing troubles.  During install, the installer would hang whenever I would select the two checkboxes on the second step of the install process and eventually wound up unchecking them.  I then left the computer for several hours.  When I returned, I found that it threw an error something to the effect of "Cannot save new programs" but that sounds a lot worse than it was.  I selected OK and it then said that Ubuntu was installed successfully.  I then proceeded to reboot, but to my horror and shock, up came grub-rescue, saying "Error: Can't find file!"  I found some instructions that suggested I open the live CD and try to reinstall GRUB from there.  This only changed the error code to "'/boot/grub/i386-pc/normal.mod' not found".  The fix I found for this left the situation unchanged.  I then had the idea to boot directly from my Ubuntu HDD (I have Windows 7 and Raring on different HDDs) and for some inexplicable reason up came the "Starting Windows..." message!  Any ideas on what is going on here?  My only thought is that I installed GRUB on the wrong HDD, but that doesn't explain why it would boot into windows.  To add inconvenience to annoyance, my BIOS won't allow me to boot off the Ubuntu HDD as a boot order default (i.e. the HDD doesn't show up as an option), so I have to do it through the boot device menu.  Total pain.

If this should be in another section, I'm okay with that.  The only reason I put it here is because it had some relevance to this thread.

Any help would be greatly appreciated.

barrings

---

### Post by coffeecat on 2013-10-16
A few thoughts occur to me.

The hanging after checking the two checkboxes - would that have included connecting to the internet? It may be that you will still have issues with those network devices in the latest version of Ubuntu which is why I suggested trying the live session and testing them.

Some of what you describe sounds like an incomplete installation despite the successfully installed message, although I can't be sure. Did you check the md5sum of the downloaded ISO?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I suggest you test for internet connectivity from the live session. See if you can connect with both the ethernet and wireless devices and see what the monitor resolution is like with the default video driver. At least you'll know what you should be able to expect with those two issues once you do get Raring installed properly.

Turning to the boot issues, these may be repairable, but check you were using an installation medium with a good md5sum first. If you were, run [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") from the live session. This will collect information on the state of grub and may help to explain why Windows started up when it did. It would be better to start a new thread with a different title for this where you could post the boot info output.

We'll keep this thread open for the time being for you to report the result of testing your network devices, but it can be closed once you've got a thread going about your Raring installation problems.

---

