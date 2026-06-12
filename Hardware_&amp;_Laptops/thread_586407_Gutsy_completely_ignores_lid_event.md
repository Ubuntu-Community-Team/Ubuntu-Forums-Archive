---
title: "Gutsy completely ignores lid event"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by 1comment on 2007-10-22
Greetings,

since an fresh install of gutsy my computer ignores the lid close event. Actions in gnome-power-manager are set correctly. It seems to be some non-gnome issue, as xev does not report on any event on press or release of lid button and "cat /proc/acpi/button/lid/state" outputs always "closed", no matter if the lid is open or if i hold down the lid button. Im sure it is not an hw issue, since windows recognize the closing of the lid and perform the action specified. Everything worked ok in feisty. Thanks for any advice.

Jiri

---

### Post by Bubs on 2007-10-28
Same problem on Xubuntu gutsy install.  noticed it this morning when light was coming from under the laptop lid.  noticed the screen doesn't shut off when lid is closed...

no solutions?

---

### Post by ErikZap on 2007-11-09
I am running an updated Gutsy Kubuntu on a Thinkpad R40.

I have some strange findings, too. After having had some trouble with power management features, I set the switch in GRUB's menu.lst to acpi=on apm=off . Setting apm=off seemed to remedy some of the troubles I've had, such as NetworkManager would cease to work at all, suspend buttons wouln't work. Now, the suspend button works reliably, and suspend over the logout KDE-menu works fine. 

BUT: the lid switch event is unreliable. I was experiencing that after a fresh boot up, the lid switch event would stop to work after a couple of resumes, but I was unable to detect a specific pattern in this behavior. Sometimes it works, sometimes it doesn't.

Comparing the actions I see this:
1) suspend button on keybd / suspend via KDE logout: normal suspend & resume
2) lid button: when it fails: screen blanks, but not completely, i.e. if you look at a certain angle you will still notice a picture that is still updated. also, xscreensaver was turned on and is still running after releasing the button. 
Notice that xscreensaver is NEVER running after resume from action 1).

Does anyone see observe similar behavior? And does anyone now more about how these two events differ in the scripts residing in /etc/acpi?

---

### Post by ErikZap on 2007-11-09
I have just looked at /var/log/acpid.

I have noticed this error, regardless of whether or not suspend with lit button worked or not:
ERROR: Couldn't attach to DCOP server!
This is while guidance-power-manager is running.

Notice this thread discussing the issue:
[https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/116416](https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/116416)
So it seems it's not a configuration error.

Intersting to note that there are two different scripts in /etc/acpi, lid.sh and sleepbtn.sh
- perhaps a workaround would be to 
mv lid.sh lid.sh.bu
ln -s lid.sh sleepbtn.sh ?

Any comments?

---

### Post by jose.mico on 2007-11-12
With a fresh Gutsy install, the lid switch does not work at all in my HP 530. But after an hibernate and resume sequence, it works properly (?!)

---

### Post by sillyxone on 2007-11-17
from the bug report: 
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/163265](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/163265)

edit this file: /etc/acpi/events/lidbtn

change the line:
event=button[ /]lid

to:
 event=button[/]lid"

restart, works right away on my Dell D620

---

### Post by crouton on 2007-11-29
This fix did not work on my R40 with Xubuntu 7.10, using 'radeon' driver.  Manually depressing the lid button blanks the screen but does not appear to suspend/hibernate, as  screen pops back up immediately when I let go of the button.

---

