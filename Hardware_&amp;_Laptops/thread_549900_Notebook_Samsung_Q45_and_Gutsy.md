---
title: "Notebook Samsung Q45 and Gutsy"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by damike2k on 2007-09-13
Hello everybody,

i just installed and set up Gutsy on my notebook, but the FN Keys does not work.

With 7.04, they worked but i got problems with my nvidia card with 7.04.

Any ideas?

Thanks for your help :)

Michael

---

### Post by damike2k on 2007-09-20
bump

---

### Post by slacher on 2007-10-14
Same problem here.While I could choose between 2 levels of brightness on my Q45 under Feisty, it doesn't seem to work anymore under Gutsy. However I can still use the Fn keys to turn the wifi on and off, to lock the touchpad and to change the sound volume. Very strange and annoyoing.

---

### Post by cubeist on 2007-10-14
This might be too simple of a solution, but have you tried going into keyboard shortcuts and manually setting the keys (system/prefs/keyboardshorcuts).  I had to do this on my hp to get the sleep fn key working...

---

### Post by slacher on 2007-10-15
Thanks Cubeist but I couldn't find anything about brightness in the Keybord shortcuts settings. Any other idea ?

---

### Post by floh1044 on 2007-11-02
Hello everybody,

I can confirm this problem. I am owner of a Samsung Q45 since 6 weeks and had first Feisty installed where the Fn keys worked fine, After a new install of Gutsy (suspend to memory works!) the Fn keys do work only partially, I can change the brightness of the screen and the sound but e.g. . I can not switch to a TextConsole with the usual Ctrl-Alt <F1>, ... <Fn> or printscreen. I conjecture that in my case the current keyboard model (Generic 105) does not map the keys the right way. However I did not find out which keyboard model would suit better to the Samsung Q45.

Grateful for any pointers

Florian

---

### Post by dbussacchini on 2007-11-04
Concerning the Q45 with a nvidia video card, the brightness buttons are disabled by the acpi video module. In the file, /etc/default/acpid, I have replaced 
MODULES=all
by
MODULES="ac battery bay button container dock fan processor sbs thermal"
(all the acpi modules excepted video, asus_acpi and toshiba_acpi).

A last remark, if you use the nvidia graphics driver, you must first switch to a virtual console (ctrl+alt+F1) before to change the brightness, then you return to X11 by typing ctrl+alt+F7.

---

### Post by SimoneMSR on 2008-01-10
i have a samsung q45 with an intel x3100 graphic card inside. i've installed ubuntu gutsy gibon 7.10 and i'm facing a problem: my desktop is smaller than my monitor and i can't enlarge it. what can i do to extend it to the same size of the monitor?
thanks.
simon.

---

### Post by jose Lang on 2008-01-15
if your desktop is shown at the wrong resolution, please have a look at the bug131646 in launchpad? Editing the xorg.conf and adding the following worked for me.
stoupos wrote.

Modify /etc/X11/xorg.conf so that a new monitor is added for
the tv-out, marked as disabled. Specify on the device section
the name of the dummy tv-out.

add:

Section "Monitor"
Identifier "TVOutput"
Option "Disable" "true"
EndSection

find Section "Device" and add:

Option "monitor-TV" "TVOutput"

---

### Post by shenshei on 2008-02-14
I try for the brightness without acpi_fake_ecdt=1 and with acpi=off and then I can change brightness.

I don't know what is ecdt but I think that if we can resolve it fn key will e ok.

shenshei

---

