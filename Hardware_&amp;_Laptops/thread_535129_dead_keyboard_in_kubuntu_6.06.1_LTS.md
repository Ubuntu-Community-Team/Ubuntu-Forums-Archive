---
title: "dead keyboard in kubuntu 6.06.1 LTS"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by cgl72 on 2007-08-26
A strange thing has happened. Since yesterday morning I have lost the used of my keyboard when running kubuntu. My Usb mouse continues to work.

Kubuntu 6.06.1 lts, kernel 2.6.15-28-386
Running without issues for over 1 year
Shuttle 61G2
standard Logitech 104 key PS/2 keyboard on generic keyboard driver

The symptoms are the following: keyboard works at the kubuntu login splashscreen. It also works if the session Type "Failsafe" is chosen at the login menu. But after KDE is loaded, it stops working all together. None of the keys are active.
This seems to indicate that the problem is with Kubuntu or X and not with the kernel version (is that correct?).

I ran some updates on friday night (a long list, cannot recall what they were), then Sat morning I walked in on my 2 1/2 year old who had been randomly pressing keyboard strokes that had opened ksnapshot windows (wich I then closed using my usb mouse). 
Shortly after, I noticed that the keyboard refused to record my keystrokes. I have those two events separately or combined have caused this trouble.

What can I do?

I have tried: multiple reboots with the different kernels that are proposed at startup by Grub, no avail. I have looked at the keyboard settings in Kubuntu, changing the Keyboard model choice. Nothing happens. One strange thing: I changed the option in the keyboard setup in kubuntu to have numlock set to "on" at startup, and that change is now effective, the numlock is on at startup! But of course, no way to turn it off once kubuntu is up since the keyboard is not responding!

Tried the kubuntu Dapper 6.06.1 live CD, Keyboard works fine!

Any help will be welcome!

Thanks
Christian

---

### Post by cgl72 on 2007-08-26
I am very happy in spite of my embarassement..

After trying many complicated things, I found this

[https://bugs.launchpad.net/ubuntu/+bug/41427](https://bugs.launchpad.net/ubuntu/+bug/41427)

and sure enough, my slow keys were activated! By unchecking the Slow keys box under

System Settings/ Regional & Accessibility / Accessibility /Keyboard filters

everything is now back in order!

---

