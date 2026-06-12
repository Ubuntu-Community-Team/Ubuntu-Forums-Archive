---
title: "Can't adjust brightness"
date: 2010-02-11
forum: Hardware
---

### Post by clash101 on 2010-02-11
I have been combing the forums for about 2 hours now trying to fix this.
My brightness cannot be adjusted. I can move the sliders on the brightness applet and in the power manager, and the brightness does not change. I press the fn button and my left/right arrows (brightness adjustment for my computer) and the notification window comes up and the indicator changes, but the brightness does not. I am sure my battery would last much longer if I could get the brightness to adjust.

I have: 
Gateway EC14D
11.6" LED LCD screen
3 GB RAM
Intel Pentium SU4100 1.30GHz
64-bit architecture

I am running:
Ubuntu 9.10 Karmic 64-bit
Gnome 2.28.1
Kernel Linux 2.6.31-19-generic

I have used Ubuntu since 7.04 and think it is fantastic, but this the first problem I have encountered that I could not solve simply by reading the Forums. Thanks in advance for any help!

(Also, be broad in your descriptions about problem solving please; my terminal knowledge is spotty...)

---

### Post by clash101 on 2010-02-11
I should also note I tried to edit /etc/default/grub by adding "nomodeset acpi_backlight=vendor", and while this added steps to the brightness adjustment for the keyboard shortcut, did nothing else.

---

### Post by clash101 on 2010-02-19
bump

---

### Post by chumbert on 2010-04-17
Did you find a solution? I bought the same computer, and I've got this problem too... I applied some modification, but anything has been worked. Very frustating.

If someone can help us, it will be appreciated. Thanks you.

---

### Post by chumbert on 2010-04-17
**@clash101** : I found a solution to solve the problem.

```
sudo gedit /etc/default/grub
```Replace :
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```by:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
```After :
```
sudo update-grub
```Just restart and brightness adjustment will work! The only point is the increase/decrease value is inversed (Fn+decrease = increase, and Fn+increase  = decrease), but it works! :P

---

### Post by clash101 on 2010-04-17
@[chumbert]("http://ubuntuforums.org/member.php?u=1055550"):

Still no solution. The solution you posted was the first thing I tried 2 months ago and it didn't work for me.
Are you running 9.10 64bit? I think that may be where my problem lies. I am just going to wait for 10.04 and see what happens with the new edition...

---

### Post by chumbert on 2010-04-17
Yes, I'm running Karmic 64bits, and the fix works fine on my Gateway. I've tried with Lucid Lynx beta2 but the problem still the same (without fix).

I hope you'll find a solution, and sorry if the fix that I suggested didn't work for you.

---

