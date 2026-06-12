---
title: "Touchscreen settings, VIA miniITX EN series ACPI problem."
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by SergeiFranco on 2007-08-22
Hello there,
I am builiding a carputer (carpc), My setup is simple:
VIA miniITX EN 15000 Main board/CPU combo.
Egalax 7" Touchscreen.
80Gb HDD.

My first issue is with touch screen: for some reason when i tap in one place and then tap in another (for example on desktop) it draws select square arround - similar to if you click and hold and move mouse. That issiue is very annoying - it requires to tap twice on places to achieve result I want. Is there any way to switch off that HOLD feature? It is greyed out in Touchkit calibration applet.
I use Egalax drivers for that touch screen.
Can I adjust sensitivity of the touchscreen?

miniITX issues:
ACPI does not work. How can I turn it on? it does not shut down, or suspend.
Sound: I cannot make 6 channels to work. There is no place in alsamixer/kmix where I can switch inputs to act as outputs?

Also slighlty off topic: I need good front end (mainly music player) for my car pc setup, what would you recommend? I have seen roadrunner front end on the youtube - it is bloody good, but it is Windoze only (sux). Another thing is - is there any KDE themes with larger buttons?

Thank You.

---

### Post by jai_mantravadi on 2007-10-07
I'm looking into building a carputer/carpc in the near future. 
I've done a bit of research on this, and the mp3car forums are a good place to start for a few of your questions. As far as front end, I'd check out the linuxICE distro at [http://linuxice.com/](http://linuxice.com/). ICE stands for in-car entertainment, and its basically a re-packaged ubuntu distro with some drivers for touch-screen and a front end called NGhost. Also, at the MP3car forums, there's a simple frontend using Mplayer as a backend (can't remember the name), and I think its a Linux program (it may be a windows program, but I thought it was mainly meant for linux). Sorry, but I can't help with the hardware issues.
Good luck!

---

### Post by SergeiFranco on 2008-02-09
I have fixed solution by compiling tkusb.ko module...
I have aslo made (still improving) a kommander script that works as front end for amarok (through DCOP).
as for the audio support... still struggling:
[http://ubuntuforums.org/showthread.php?p=4301719](http://ubuntuforums.org/showthread.php?p=4301719)

I have made separate thread about it.

---

