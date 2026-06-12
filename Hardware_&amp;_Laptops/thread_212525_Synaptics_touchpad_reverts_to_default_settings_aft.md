---
title: "Synaptics touchpad reverts to default settings after reboot."
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by hygraed on 2006-07-10
I have a Toshiba Satellite L25-S1194 laptop with a Synaptics touchpad.
I downloaded the qsynaptic configuration program, and I have the drivers and shared memory enabled and everything.
However, after I start or restart my PC the touchpad reverts to its default settings. The odd thing is, when I go back into qsynaptic, the settings are exactly as I set them. The touchpad is just behaving badly.
Anyone else have this problem?

---

### Post by hygraed on 2006-07-11
bump

Please help, if you need more info just ask

---

### Post by Martybartfast on 2006-07-12
Hi, I've got a similar problem. I'm on a Dell Inspiron 6000 and am having problems with the scroll function intermittently not working. When I boot the laptop the scroll buttons don't always work, however if I just reboot then it will often come up with the scroll buttons working O.K. I guess that the scroll buttons work about half the time. I have found that if I hibernate or suspend when the buttons are working then  they will work when it comes back.

I'm pretty sure I've got xorg.conf right and the drivers loaded as otherwise it wouldn't be working half the time.

Can anyone suggest where I can look for the cause of this intermittent failure?

TIA for any help, and appologies to hygraed for hijacking the thread but I though that we might both be able to benefit from any advice.

---

### Post by eitan_a on 2006-12-30
I'm experiencing the same thing.  Would love help on it...thanks!

---

### Post by shane2peru on 2007-01-02
Help, same deal, except it worked better before, I started tinkering with it, and now I have to run qsynaptics to get it to work right.  I use a mouse when at the desk.  When I pull the plug and go mobiel while running I have to hit alt - F2 and startup qsynaptics to get my touchpad to respond.  Then it is super slow, and no tapping, (which it did before I installed qsynaptics), and the mouse is super sloooooooow.  Here is my xorg.conf for my touchpad:```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
### My added options
	Option		"LeftEdge"		"1700"
	Option		"RightEdge"		"5300"
	Option		"TopEdge"		"1700"
	Option		"BottomEdge"		"4200"
	Option		"FingerLow"		"25"
	Option		"FingerHigh"		"30"
	Option		"MaxTapTime"		"0"
	Option		"MaxTapMove"		"0"
	Option		"HorizScrollDelta"	"0"
	Option		"VertScrollDelta"	"0"
	Option		"MinSpeed"		"0.09"
	Option		"MaxSpeed"		"0.18"
	Option		"AccelFactor"		"0.0015"
	Option		"SHMConfig"		"on"


EndSection

```  Any ideas?  Thanks.

Shane

---

### Post by shane2peru on 2007-01-02
Ok, I removed qsynaptics and that seemed to fix things for me.  If you want a semi-decent working touchpad configuration, you can take mine from above.  I still don't have scrolling ability while using my touchpad, but it is a lot faster in its speed. 

Shane

---

### Post by oudent on 2007-01-28
What works for me to get it working, though it is not a fix, is running:

sudo dpkg-reconfigure xserver-xorg
Selecting the ExplorerPS/2 mouse option (though this is already in my xorg.conf), and afterwards everything works.

Why it works, I'm not entirely sure. Unfortunately I don't really want to have to do that everytime I restart my computer.

Maybe this can give someone a hint as to what the problem is.

---

### Post by morehavoc on 2007-01-29
I am having a similar problem, my new mouse settings do not work after reboot, but everything works fine if restart X with a ctrl-alt-backspace?  i was wondering if the old settings are being stored somewhere, and X is looking in this place for the settings, instead of the xorg.conf file.  I have never had this happen before, any ideas?

---

### Post by oudent on 2007-01-29
Could this be a problem due to the order of loading things during initialization? I have a feeling that if we could force the touchpad driver to be loaded before X starts, or xorg.conf is read that might just solve the problem.

I understand that 6.10 has a new startup setup designed to speed things up as well as make things a little more dynamic.

---

### Post by mrgoodkat on 2007-09-24
This is exactly the problem i'm facing now. After reboot/relogging in, my settings (I set qsynaptics to disable tapping altogether, it drives me crazy) don't seem to take effect until I run qsynaptic again...

Was a solution known at all?

---

### Post by kerry_s on 2007-09-24
you need to put> qsynaptics -r
into your startup for it to restore.

doesn't anyone read the man pages? (man qsynaptics)

---

### Post by mrgoodkat on 2007-09-24
> **kerry_s said:**
> you need to put> qsynaptics -r
into your startup for it to restore.

doesn't anyone read the man pages? (man qsynaptics)

Ahhh, I never knew there was a manual, i'm still VERY new to Linux.

That command to be put into startup looks perfect, but i'm not exactly sure where the startup script is/which one it is? Is it the x.conf file?

Kind regards

---

### Post by mrgoodkat on 2007-09-24
> **mrgoodkat said:**
> Ahhh, I never knew there was a manual, i'm still VERY new to Linux.

That command to be put into startup looks perfect, but i'm not exactly sure where the startup script is/which one it is? Is it the x.conf file?

Kind regards

Found it!! From this link: [http://ubuntuforums.org/showthread.php?t=181041](http://ubuntuforums.org/showthread.php?t=181041)

If you go to System > Preferences > Sessions, then add "qsynaptics -r" as a command. All is good!

---

### Post by shane2peru on 2007-09-24
> **kerry_s said:**
> you need to put> qsynaptics -r
into your startup for it to restore.

doesn't anyone read the man pages? (man qsynaptics)

apparently about 7 of us don't, that is what makes you a cut above us.  :lolflag:  Thanks for the answer. 

Shane

---

