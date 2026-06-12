---
title: "Acer Aspire Timeline AS4810TZ-4508"
date: 2010-03-17
forum: Hardware
---

### Post by itcave on 2010-03-17
I'm looking at getting a Acer Aspire Timeline AS4810TZ-4508.  I will be running Ubuntu as my only OS.  Has any one put Ubuntu on this laptop?  Did everything work, (web cam, card reader, hdmi output, accelerated video, wireless)?

Thanks!

---

### Post by Foxcow on 2010-04-29
9.10 runs beautifully for me.  The only thing that does not work properly is the touch pad disable button.  You can disable it but to re-enable it, you have to reboot.  I can't figure it out and its not that big a deal.

---

### Post by soepstad on 2010-04-30
Touchpad button works perfectly in 10.04, as does most everything else. Only problem I have is the CD eject button doesn't work (need to do 'eject /dev/cdrom' from command line)

---

### Post by eBalut on 2010-04-30
New to Ubuntu.  Installed 10.04 today along with Restricted Extras, Adobe Reader, and Cairo-Dock.  Using Launcher work-around to mount/unmount CD/DVD with "eject cdrom" command.  Cannot control backlight with FN-arrow keys (system will hang).  Also cannot play DVDs with either Movie Player or VLC.  Internal mic does not work.  Haven't tried wired LAN yet.  Attempted posted work-arounds for backlight, but did not help.  My system: AS4810TZ-4696.  Still trolling this forum to find workable solution, but so far I am sold on Ubuntu.  More stuff working now than with Snow Leopard Hackintosh.

---

### Post by Foxcow on 2010-04-30
> **eBalut said:**
> New to Ubuntu.  Installed 10.04 today along with Restricted Extras, Adobe Reader, and Cairo-Dock.  Using Launcher work-around to mount/unmount CD/DVD with "eject cdrom" command.  Cannot control backlight with FN-arrow keys (system will hang).  Also cannot play DVDs with either Movie Player or VLC.  Internal mic does not work.  Haven't tried wired LAN yet.  Attempted posted work-arounds for backlight, but did not help.  My system: AS4810TZ-4696.  Still trolling this forum to find workable solution, but so far I am sold on Ubuntu.  More stuff working now than with Snow Leopard Hackintosh.



Strange.  I tried to adjust the backlight on mine as well and it froze.

---

### Post by hugo491 on 2010-04-30
I also have the same issue. Trying to adjust the brightness causes the system to freeze. Also, Ubuntu understands when I use the touchpad on/off switch, (I see the notification) but the touchpad stops working and then the system needs to be rebooted or put to sleep. Unfortunately, the splash i8042.nomux workaround no longer works. Wireless and ethernet cards work perfectly. I just wrote my own keyboard shortcut and hotkeyed it to workaround the eject button.

---

### Post by eBalut on 2010-04-30
Did some more reading in the forum.  If you select "None" in System | Preferences | Appearance | Visual Effects, you can adjust screen brightness with the FN-arrow keys without system hang.  Off course, Cairo-Dock leaves a big black square on the desktop, so I will keep searching for a solution.

---

### Post by PockyMaster on 2010-05-01
Hi guys!

Well, Back on 9.10, the problem seems to be compiz related, in terms of the backlight adjustment. 

The crude method I use is setting the brightness before loading up compiz. Then I hibernate, start up again, and load up compiz afterwards. 

On other notes: my touchpad off button does work with all of the ui pop-up stuff, per se, but it locks it up after the first press. I had to unlock it with:

<sudo modprobe -r psmouse && sudo modprobe psmouse>

Did you guys have any problems before with high transfers of data on the wireless? Mine seemed to cut off often when doing so, but not with 10.04. My networking pci card is, i believe, some atheros variant. 

Bios I'm using issss, I believe, 1.35

---

### Post by Foxcow on 2010-05-01
I never had any problem on 9.10 and thus far on 10.04 with the transfers.  I never had any trouble changing the display brightness on 9.10 with compiz installed either.

---

### Post by PockyMaster on 2010-05-01
Ohh, Nice. I wonder if it's something I did. 

So I guess these Don't apply to you: [https://help.ubuntu.com/community/AspireTimeline/Fixes]("https://help.ubuntu.com/community/AspireTimeline/Fixes")

What Bios version do you have running?

---

### Post by Foxcow on 2010-05-01
I'm running bios version 1.30 9/29/2009.  Thanks for the link, I'm checking it out now.

---

### Post by hdesoto on 2010-05-27
I've been looking for others with this same problem of system freezing when changing the screen brightness on Acer 4810...! At least i found someone. 
I'll try disabling the visual effects, if that works it's ok for me for the moment. Having the screen at full drained my battery in an hour or two.
Thanks!
Hernan.

---

