---
title: "gnome power manager - nonfunctional in edgy?"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by atonaldenim on 2006-12-18
I upgraded my Sony laptop from Dapper to Edgy immediately after Edgy's release. Since then, Gnome Power Manager hasn't worked properly: when the power state changes (AC -> battery), nothing happens. The screen doesn't dim, it doesn't sleep when the lid is closed, none of the specified settings actually take effect. Likewise, when I change the settings for AC power, like turning down screen brightness, they fail to take effect.

I am able to change the LCD brightness fine using Fn + F5/F6, apparently a built-in feature, and also using the Sony-specific command **spicctrl** (which no longer requires sudo privileges in kernel 2.6).

Also, suspend does work if I manually trigger it via the Gnome Power Manager applet menu, or via Gnome's shutdown menu (although I had to [replace the X.org i810 driver ]("https://bugs.freedesktop.org/show_bug.cgi?id=5795") to stop the screen from melting on resume. G-P-M didn't work before I replaced it, either.)

And, all this used to work fine in Dapper. G-P-M does recognize that the power states are changing, it gives a notification window (in the wrong corner of the screen, grrr), it just doesn't do anything about it.

Unrelated note: why do the G-P-M tabs have exposed HTML tags? (literally) "<b>Running on AC Power</b>"

**Relevant info: **
Sony R505-DS
Intel i830 video
gnome-screensaver turned off

---

### Post by ThomasA76 on 2006-12-24
Did you find a solution? If so, please tell me what you did...I have same problems as yours :(

---

### Post by Soulbrighter on 2007-01-16
It seems just like what I'm experiencing on my laptop! I found out that if I kill the hald daemon and the gnome-power-manager process and then restart them both they work like they should. Maybe someone could tell us what difference is there between the first start and the others :)

---

### Post by Ikkath on 2007-01-16
I am getting the exact same problem on my Vaio FE31Z.

G-P-M does not do anything...

Watching the thread for any ideas.

---

### Post by golem3 on 2007-01-17
Bumping this thread since I have the same issue on my Acer Travelmate c314xmi. Please help.

---

### Post by Soulbrighter on 2007-01-18
I solved the problem: acpid is started after hald (which is started by dbus), so hald cannot know the battery status. That's why if hald is restarted, gnome power manager (which relies on hal for battery polling) works again. To solve the issue, I simply renamed the symlink that makes acpid start in /etc/rcx.d/ to a lesser number. There was only one rc (I think it was 2 but I'm not sure) that was wrong: the symlink was called S50acpid, while in the other rcs it was called S10acpid, so I simply renamed the S50acpid symlink to S10acpid. I hope I wrote this clearly enough :)

---

### Post by omnipotent22 on 2007-01-19
Could this be explained to a novice in clearer terms?

---

### Post by Soulbrighter on 2007-01-20
I can try, but I am by no means an expert so there could be some errors in what I'll write.
The problem I found is that the HAL (Hardware Abstraction Layer) daemon is started at boot time before the ACPI (Advanced Configuration and Power Interface) daemon, so it cannot get the battery information from the ACPI daemon. To see if this is what happens to your machine too you just have to try to restart the HAL daemon and the gnome-power-manager applet and see if it comes back to work. To do so, type in a shell:
sudo pkill hald
pkill gnome-power-man
sudo hald
gnome-power-manager

After that the power icon in gnome should be back to normal and work fine until next reboot.
If this is the case, you can modify the boot scripts to make the ACPI daemon start before the HAL daemon. To do so, simply go to /etc/ and look in every rcX.d/ (rc0.d, rc1.d, ... rcS.d) folder. There are many files named with a starting letter, then a 2 digits number, then the rest. Look if in one of these folders the file containing 'acpid' in its name has a greater number than the file containing 'hald' in its name. When this happens, rename the file containing 'acpid' changing the number to the same number of the others rcX.d folders. For example, if in /etc/rc2.d/ there is a 'S50acpid' and a 'S20acpid' file, rename the 'S50acpid' file to 'S10acpid' by typing: sudo mv S50acpid S10acpid. 

I hope this helps!

---

### Post by rebelDNS on 2007-05-20
> **Soulbrighter said:**
> I solved the problem: acpid is started after hald (which is started by dbus), so hald cannot know the battery status. That's why if hald is restarted, gnome power manager (which relies on hal for battery polling) works again. To solve the issue, I simply renamed the symlink that makes acpid start in /etc/rcx.d/ to a lesser number. There was only one rc (I think it was 2 but I'm not sure) that was wrong: the symlink was called S50acpid, while in the other rcs it was called S10acpid, so I simply renamed the S50acpid symlink to S10acpid. I hope I wrote this clearly enough :)

OMG you're a genius.  thanks, I've been running through this problem over and over again and I could only find that it only works if hald is restarted every time.  Thanks!

---

