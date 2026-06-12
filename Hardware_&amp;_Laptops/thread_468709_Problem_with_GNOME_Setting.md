---
title: "Problem with GNOME Setting"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by gunbladeiv on 2007-06-09
I Need Help.  I've successfully configure and install Beryl with ATI on my laptop.  I do the reboot with no problem twice.  After that i add some software with synaptic and when i reboot i got error message tell me that failure at gnome setting.  How do i solve this problem.  may i know how to solve this.  if u need any info please let me know =...

---

### Post by neptho on 2007-06-09
It would help to know the error you were getting.

---

### Post by gunbladeiv on 2007-06-09
> **neptho said:**
> It would help to know the error you were getting.

may i know how can i view the log to find what error that i counter with on startup? i think my problem is with the gnome setting daemon.
i going to reboot and look at the errors.  i'll post it here in a few minutes

---

### Post by neptho on 2007-06-09
It really depends on the program that's sending the error.  Can you start it back and write down the error so you can report to us?  Without knowing what's failing, there's an impossible number of places to look.

You may try 'dmesg' to see if there's an error showing there, and then look in /var/log/messages and /var/log/syslog.

---

### Post by gunbladeiv on 2007-06-09
this is the error that appear on the message dialog.

[B]Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.[/B]

---

### Post by neptho on 2007-06-09
> **gunbladeiv said:**
> this is the error that appear on the message dialog.

[B]Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.[/B]

Try running '/usr/lib/control-center/gnome-settings-daemon' in a terminal and see what it says.

---

### Post by gunbladeiv on 2007-06-09
it doesnt run.  it says that only one session could run on the same time. i did the ps aux |grep gnome-setting and i found out that it is running.  How can i fix my problem?

---

### Post by gunbladeiv on 2007-06-09
i did install splash screen, some emerald themes from gnome-look.org ... is it damaging my gnome?  Do I have to wait for 5-10 minutes before my gnome start? Someone please help...

---

### Post by oxalá on 2007-06-09
having the same problem, though all i did was install Ubuntu Studio.  Help!

---

### Post by neptho on 2007-06-09
If it's running, it would appear that your gnome configuration is broken.

This should get you back to a 'basic' gnome feel.. but you can always move it back.

```
mkdir ~/temp_gnome
mv  ~/.gnome* ~/.temp_gnome
mv ~/.nautilus ~/.temp_gnome
```
Turn off 'save session', and restart X.  You will have the original 'basic' gnome install, but it should take care of this problem - whatever you installed may have broken your gnome settings.

---

