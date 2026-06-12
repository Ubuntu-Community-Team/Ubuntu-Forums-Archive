---
title: "Cannot run Ubuntu 8.10 on Amilo Notebook Pa 3553"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by multilanguman on 2009-01-26
I can install Ubuntu 8.04 on my laptop and it runs fine, but 8.10 cannot start the gnome desktop interface. Also I could not get the Atheros AR928x Wireless Network adapter to find a network connection (I found the correct driver on the forums for this).

I suspect Ubuntu incorrectly identifies the ati radeon video driver. I could wait until 9.04 comes out and hope there is a bug fix for this. It would also be cool if I could get the wlan to work.

Cheers

multilanguman

---

### Post by KokyOK on 2009-04-05
> I can install Ubuntu 8.04 on my laptop and it runs fine, but 8.10 cannot start the gnome desktop interface. Also I could not get the Atheros AR928x Wireless Network adapter to find a network connection (I found the correct driver on the forums for this).

I suspect Ubuntu incorrectly identifies the ati radeon video driver. I could wait until 9.04 comes out and hope there is a bug fix for this. It would also be cool if I could get the wlan to work.

For 8.10 you need to install a graphics driver. I used the "ati-driver-installer-9-3-x86.x86_64.run" (just Google and download it). After booting your system, you get in the console. Install the driver with:

```
sudo sh ati-driver-installer-9-3-x86.x86_64.run
```

Then download my the attached xorg.conf and copy it to /etc/X11/
(you may need to change the keyboard layout, mine is "German - Dead acute" ). Then just reboot and hope it worked. ;)

It works fine with my Amilo Pa 3553!

My Amilo Pa 3553 has a Ralink RT 2790 WLAN adapter and it makes problems too. I am still working on it. Already tried [Howto: Ralink RT2860 (m)PCI(e) (RT2760/RT2790/RT2860/RT2890) on Intrepid]("http://ubuntuforums.org/showthread.php?t=1045703") but it didn't work in my case.

---

### Post by multilanguman on 2009-04-07
Servus KokyOK, I'll give it a try.

At present I am dualbooting with Vista with my Amilo. Under Vista I can run the machine for about two hours max, under Ubuntu about half an hour less, is there a way to tweak power management with Ubuntu? What other experiences to you have running Ubuntu on your Amilo?

Multilanguman

---

### Post by ketaclisma on 2009-04-19
> **KokyOK said:**
> For 8.10 you need to install a graphics driver. I used the "ati-driver-installer-9-3-x86.x86_64.run" (just Google and download it). After booting your system, you get in the console. Install the driver with:

```
sudo sh ati-driver-installer-9-3-x86.x86_64.run
```

Then download my the attached xorg.conf and copy it to /etc/X11/
(you may need to change the keyboard layout, mine is "German - Dead acute" ). Then just reboot and hope it worked. ;)

It works fine with my Amilo Pa 3553!


Thanks a lot KokyOK!!!!!
finally i have Kubuntu 8.10 on my PA3553.....:D:D:D!!!!!!!!!!!!!!!!!!!!!!
grazie sei un grande!!!!!!!!! (i'm italian)
byebye...

---

