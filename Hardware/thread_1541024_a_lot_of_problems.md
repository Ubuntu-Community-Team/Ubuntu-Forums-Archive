---
title: "a lot of problems"
date: 2010-07-28
forum: Hardware
---

### Post by azedddine on 2010-07-28
hello,

i'm running ubuntu 10.04 on a laptop, i have : 

> "00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller" 

as a sound card, i can't listen to music or watch movies correctely, sound works good for a short time and then it gives a "khkhkkhkhkh" or a bad sound.

second problem is: when i try to turn off my laptop it won't power off, it gives: "system halted" 

third problem is i can't get the combinaison (Fn + Fx)

forth problem is with the text editor gedit, when i use a command like "sudo gedit..." i get this: 
> (gedit:5017): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:5017): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

i'm asking for help

thank you

---

### Post by quixote on 2010-07-31
(In general, it's a good idea to put different topics in different threads, so you may want to start a few new questions, and edit this one down.)

1) I don't know anything about that sound card.
2) When it won't complete a system shutdown, it's generally some problem with power management.  However, if it's reached the "system halted" point, it's safe to just turn it off with the power button.  Inconvenient, but not damaging.
3) Not sure what you mean by this one.
4) gedit is a graphical program, so it's supposed to be started with gksudo rather than plain sudo.```
gksudo gedit
```Do you still get the errors then?

---

### Post by azedddine on 2010-07-31
i steel get the message error for all problems

---

### Post by lidex on 2010-08-01
For your audio issue do this. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

For your other issues check your logs:
```
dmesg | less
```
Q to exit

```
cat /var/log/syslog
cat /var/log/messages
```

---

