---
title: "USB Keyboard malfunction/not working in Dell Optiplex 755 running ubuntu 8.04 hardy"
date: 2008-06-26
forum: Hardware Team
---

### Post by sakthi_v_cse@yahoo.co.in on 2008-06-26
:(Hi,

Recently i migrated to Ubuntu 8.04 hardy.
I have a Dell Optiplex 755 Desktop PC, i am running VMware Workstation 6.5, Cross over office for MS Office 2003.
I am facing the following problems with my setup.

1. Keyboard is going mad, Ctrl key is not working (some times, rarely)

2. Any key press leads to close the current application. (Ex: open gedit, type "Hai", when i press H, the window gets closed) this is the same behaviour for any application. this happens repeatedly(3-4 times in a day)

3. Then i installed KDE4. KDE Visual effects doesnot work, makes the screen blank, and makes the keyboard unresponsive. sytem hangs and i need to reboot every time. - frequency 100%

Now i uninstalled KDE4, and working with Gnome, I have applied all updates given by ubuntu, till now(the time i post this). but still no resolution.

I also tried to select the right keyboard and layout but no improvement.

Temp. Resolution: Restart X / Logout if your screen is not locked. else press power  button for 10sec, this will powerdown the PC.

Any help is appreciated.

-Sakthivel.V
[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by (4M)Stephen on 2008-06-27
check what video drivers you'd need (depending on graphics card), I don't know if KDE4 will run on intergraded graphics very well, it depends on how much ram you have.

I would suggest trying a different keyboard and see if you get the same issue. unless you're sure it's ubuntu (ie checking in windows on the same machine.) you should also try plugging into other ports or use an adapter to plug into the ps/2 port.

---

### Post by sakthi_v_cse@yahoo.co.in on 2008-07-03
> **(4M)Stephen said:**
> check what video drivers you'd need (depending on graphics card), I don't know if KDE4 will run on intergraded graphics very well, it depends on how much ram you have.

I have 2 GB RAM

> **(4M)Stephen said:**
> I would suggest trying a different keyboard and see if you get the same issue. unless you're sure it's ubuntu (ie checking in windows on the same machine.) you should also try plugging into other ports or use an adapter to plug into the ps/2 port.

I tried hell lots of keyboards,
Generic 101 Key
Generic 105 Key (Intl)
Dell 105 Key
Dell 105 Key Multimedia

After applying last weeks updates the frequecy of crash was reduced.
i more careful now, if i found my keyboard is malfunctioning, then i will immediately change my Keyboard Layout to something else, then the problem is resolved.

this is the workaround i have as of now.

---

### Post by raywood on 2008-08-22
See [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982)

---

