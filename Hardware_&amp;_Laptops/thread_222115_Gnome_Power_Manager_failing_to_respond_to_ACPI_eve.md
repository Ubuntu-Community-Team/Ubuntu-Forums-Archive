---
title: "Gnome Power Manager failing to respond to ACPI events - ThinkPad T41"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by fluffnik on 2006-07-24
Gnome Power Manager, or at least its icon, is failing to update both level of charge and un/plugged status despite the contents of /proc/acpi looking sensible and reacting to events.

I get a beep and the screen dims when I unplug, a bleep and brightness when I replug, I get Suspend and Hibernate options on the Shut Down menu, and they work.  The Battery Charge Monitor 2.14.2 applet reacts correctly to events and reports dis/charge state accurately.

The Gnome Power Manager icon correctly displays the state of play when it is started, and will update when killed and restarted but left to its own devices will not change or react.

It used to work with this installation and it still works running from the live CD.  Could something I have installed be trapping the info?

I'm puzzled.

6.06, up to date:
teeth@flagstone:~$ uname -a
Linux flagstone 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686 GNU/Linux

---

### Post by chadwick359 on 2006-08-26
I know this is necromancy, but better than making a new topic. I'm having the same problem on my Dell 9300. Has anybody ran into a fix for this?

---

### Post by Abdi110 on 2007-06-20
Having the same issue, found this thread, and then I found this...

[http://ubuntuforums.org/showthread.php?p=1611091](http://ubuntuforums.org/showthread.php?p=1611091)

Now to figure out how to restart dbus at start up.

---

