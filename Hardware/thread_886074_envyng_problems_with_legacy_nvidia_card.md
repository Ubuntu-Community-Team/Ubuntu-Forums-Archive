---
title: "envyng problems with legacy nvidia card"
date: 2008-08-10
forum: Hardware
---

### Post by zinarr on 2008-08-10
I've looked through numerous posts, but can't find one which matches the problem I'm encountering.

I installed Ubuntu Desktop 8.04.1  (x86) on a machine with a RIVA TNT2 nvidia card.  The card is detected, but X windows comes up with a max resolution of 720x400, and I'm unable to increase the screen resolution using the System --> Screen Resolution menu.

I then installed envyng, and ran it successfully.  However, now X doesn't start at all, and the xorg.conf file looks suspiciously brief (doesn't mention the monitor's model, which is an HP LP2065). Running dpkg-reconfigure xserver-xorg is also strange, since I get only questions about the keyboard and mouse, but no questions about the monitor or video card.

Any ideas how to get this working?  Thanks ...

Richard

---

### Post by tuxxy on 2008-08-10
You could try manually adding your monitors settings to the xorg, it may run them then, you would need to find out your monitors HZ and supported resolutions first.

There are pots already about adding your monitor details to xorg if you want to read up about jsut search

---

### Post by overdrank on 2008-08-10
> **zinarr said:**
> I've looked through numerous posts, but can't find one which matches the problem I'm encountering.

I installed Ubuntu Desktop 8.04.1  (x86) on a machine with a RIVA TNT2 nvidia card.  The card is detected, but X windows comes up with a max resolution of 720x400, and I'm unable to increase the screen resolution using the System --> Screen Resolution menu.

I then installed envyng, and ran it successfully.  However, now X doesn't start at all, and the xorg.conf file looks suspiciously brief (doesn't mention the monitor's model, which is an HP LP2065). Running dpkg-reconfigure xserver-xorg is also strange, since I get only questions about the keyboard and mouse, but no questions about the monitor or video card.

Any ideas how to get this working?  Thanks ...

Richard

Hi and welcome, the xorg has changed alot in Hardy. You may try and boot into recovery mode, which is usually the second choice from the grub and use the xfix option. Then if you still have issues with the resolution you may use the alt, F2 keys and use this command ```
gksu displayconfig-gtk
``` and adjust your resolution there.

---

### Post by pietjanjaap on 2008-08-11
With ubuntu 8.04, dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the "Try to fix X-server",
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

### Post by zinarr on 2008-08-11
I'm able to run xfix, and then "gksu displayconfig-gtk".  But even after selecting my monitor (HP LP2065) and driver (nv-nvidia Riva 128, RIVA TNT, ...), the results when I click "Test" are poor even at all of the resolutions I tried (1024x768,1280x1024, 1600x1200).

Not sure whether I should be using the nv driver, the restricted driver, or the envyng driver.  I think I've tried them all at this point without success. I'm not trying to use any fancy features - just trying to get a decent looking display.

I tried the monitor with an MS Windows box and it works fine, so I don't think there are any hardware issues with the monitor itself.

If anyone has any additional suggestions, please let me know.  Thanks ...

Richard

---

