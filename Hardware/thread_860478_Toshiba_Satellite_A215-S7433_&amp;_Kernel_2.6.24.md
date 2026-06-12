---
title: "Toshiba Satellite A215-S7433 &amp; Kernel 2.6.24"
date: 2008-07-15
forum: Hardware
---

### Post by Jeremiah Griffin on 2008-07-15
I've got Hardy installed on my laptop (model in the title), and most everything is working nicely--sound worked right away, the proprietary drivers for the video card do everything, USB works, etc etc. However, there's two problems:

a) Wireless (RTL8187B) doesn't work, and the patched drivers cause my system to lock up when I run "./wlan0up," but I'll make a different thread for that.
b) Every now and then, when I'm using the keyboard or just running a command in a terminal, X will start going really slow and stops polling for keyboard input and doesn't update the screen until I move my mouse. Sometimes, when I launch a program, the whole of X freezes up until I send an ACPI (pretty sure it's ACPI...) event, such as pressing the power button, which causes the Ubuntu shutdown, restart, etc. dialog to pop up. I'm going to assume that this is an 2.6.24 kernel problem or an X problem, because it didn't happen in Gutsy, and still happens with the open source and EnvyNG drivers for my video card.

Any help would be appreciated. I can't work like this.

---

### Post by Jeremiah Griffin on 2008-07-16
Still no luck. I'm going to try a fresh installation, and if that fails, a custom-compiled kernel. If those don't work, I'll have to start hopping between distributions again, trying to find one that works...<sigh>

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

