---
title: "Change of hardware"
date: 2008-08-20
forum: Hardware
---

### Post by dsbharadwaj on 2008-08-20
I had Ubuntu Distribution in AMD 3200+ and Asus M2N-MX (mother board) and it was working fine.

I replaced that hardware with AMD 4600+ and Asus M2A-VM without changing the hard disk. I was expecting that the OS can't boot because mother board (chip set) is different. To my surprise, the Ubuntu was booting in text mode. What i'm comfortable with is, Gnome desktop environment. 
(I should have seen the initlevel which i dint.)

When i was using a live DVD, audio, networking were fine. So, i would like to continue with Ubuntu. I can reinstall  but that makes me to loose my data.

So how should i repair my existing Ubuntu so that Gnome desktop is restored?

Thanks in advance

---

### Post by prshah on 2008-08-20
> **dsbharadwaj said:**
> 
the Ubuntu was booting in text mode.
So how should i repair my existing Ubuntu so that Gnome desktop is restored?


From the text mode, login, and then give the command ```
startx
``` If it gets you to a GUI well and good; otherwise, if it gives you an error "no screens found", then you need to dump your old xorg config info.

In Hardy, the xorg.conf file is more or less marginalized, but you may have made some specific entries to get it working before.

So, try getting rid of the xorg.conf```
sudo mv /etc/X11/xorg.conf ~
``` and then using the "startx" command. If it still doesn't work, you can build a skeleton xorg.conf with the command ```
sudo dpkg-reconfigure xserver-xorg
``` and try startx again.

---

