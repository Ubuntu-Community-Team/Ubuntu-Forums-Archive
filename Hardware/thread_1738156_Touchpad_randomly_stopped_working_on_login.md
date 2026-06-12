---
title: "Touchpad randomly stopped working on login"
date: 2011-04-24
forum: Hardware
---

### Post by sc4s2cg on 2011-04-24
Ubuntu 10.10 - 64 bit version 
HP Pavilion dv7 series
AMD 64bit

I was watching some BritainsGotTalent on YT and quite enjoying myself, when all of a sudden my touchpad stopped working. I rebooted, mouse worked fine in the login screen, then it stopped working (it froze) after I logged in. The same happens on the netbook edition and Ubuntu safe mode. Right now I can access programs through the use of a launcher, so not totally helpless, but I would like my mouse back.

Does anyone anyone have any suggestions?

---

### Post by sc4s2cg on 2011-04-24
Was able to kind of solve this.

[http://ubuntuforums.org/showthread.php?t=1479286&highlight=touchpad+stopped+working](http://ubuntuforums.org/showthread.php?t=1479286&highlight=touchpad+stopped+working)

[quote=Hopper122]Found a fix that worked for me. I am using a HP Pavilion dv9000 touch pad stopped working but a USB mouse would work fine. Also my touch pad would work in KDE but not in Gnome... So either install KDE and use it or...

Create a file called
/etc/modprobe.d/touchpad.conf

You can do this by typing
sudo gedit /etc/modprobe.d/touchpad.conf
in your terminal (Applications --> Accessories --> Terminal). It will ask for your password

when the file opens put in it
options psmouse proto=imps
Save the file and restart.

Hope this works for you [/quote]

So now I am able to use the touchpad, however I cannot use the "middle scroll" button. And the pointer seems to be moving slower than usual, despite me setting the speed to "fast" under System --> Preferences --> Mouse

Ideas?

---

### Post by sc4s2cg on 2011-04-24
Aha!

[quote=Troubleshooting]This usually happens when you disable your touchpad and then suspend your computer. To fix this just run this command:

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

If nothing else works, see the other touchpad debugging pages.

[/quote]

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

After a reboot my touchpad, including scrolling, works fine. Still a little slow, but I suspect that's just a setting thing. So lesson learned: don't reboot while touchpad is disabled. ;)

---

### Post by KegHead on 2011-04-24
Hi!

Additional software:

software center..."touchpad".

KegHead

---

### Post by sc4s2cg on 2011-04-24
Hey, thanks! That software solved all my touchpad problems, including speed.

Thank you so much!

(For future searchers, it's called "Pointing Devices" and it lets you disabled mousepad, speed up pointer, etc. all through a GUI.)

---

### Post by KegHead on 2011-04-24
Hi!

Congrats!

Please mark you thread as "solved".

KegHead

---

### Post by Drewvt on 2011-05-04
Thanks for this! I couldn't figure out why the touchpad on my Asus 1201N stopped working after a reboot.

---

