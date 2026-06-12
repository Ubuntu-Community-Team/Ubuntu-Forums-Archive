---
title: "How do I upgrade to new video card"
date: 2013-09-28
forum: Hardware
---

### Post by ptlundy on 2013-09-28
I just bought a EVGA (Nvidia) PCI graphic card.  I am running 12.04.  How do I go about replacing the video card I currently have installed? I tried just physically removing the old card and putting in the new one.  The computer booted and got me through the login screen and then just stopped.  I also tried to just start over from the ISO dvd but got the same thing.  I think I am caught between drivers(???)  Any help is appreciated.
Paul

---

### Post by papibe on 2013-09-28
Hi ptlundy.

Try this: when you got to a point when it freezes, press Ctrl+Alt+F1 to get to text mode and login there (if that fails boot into recovery mode, and select a root prompt).

Then run this command:
```
sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then reboot by running:
```
sudo reboot
```
If that don't work. I would try to boot using the **nomodeset** option. Check the section 'How to temporarily set kernel boot options on an installed OS' in this [thread]("http://ubuntuforums.org/showthread.php?t=1613132") for details.

If that works, follow the steps on the next section (How to permanently set kernel boot options on an installed OS) in order to set the option for every subsequent boot.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by ptlundy on 2013-09-30
Hi Papibe,
Thanks for the info.  I resolved this by just purging the nvidia drivers and rebooted.
Thanks

---

