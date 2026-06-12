---
title: "boot failure without message"
date: 2010-06-01
forum: Hardware
---

### Post by lsaffre on 2010-06-01
Hello,

I recently installed Ubuntu 10.04 LTS on a Compaq Presario CQ61 Notebook PC. Everything worked fine, until I did a hard restart to the machine because some processes were hanging. 

Now the system doesn't boot anymore. It displays the Ubuntu logo with five red dots (not blinking), a moment later the mouse cursor appears (but doesn't react to mouse movements), another moment later the hard disk stops and keeps quiet. I tried pressing Escape, Enter, Ctrl-Alt-F1 during the few seconds before the logo appears: nothing happens. I poked around in the BIOS setup but cannot see anything that looks strange. 

I booted from the installation CD into the live Ubuntu. That works, and I can see my hard disk and run the disk analyzer tool: everything looks okay, the disk is marked "bootable" and the self-test says that it is "healthy".

I might reinstall from scratch, but I would then loose some data, and also would fear that something similar hppens in the future again.

In case you wonder what I had been doing before the hard restart: I probably don't remember everything but I had asked to change the system language from Estonian to English while the Software Software center was downloading a database upgrade. Maybe the internet connection was closed from outside, anyway the machine did hang for good, impossible to open a terminal and type 'sudo halt'.

What can I do? please help!

Luc
[URL="http://releases.ubuntu.com/releases/10.04/"]
[/URL]

---

### Post by dabl on 2010-06-01
If you don't ever again use the power switch to restart, then you have no reason to fear a repeat of this problem.

First, the mnemonic to remember:

_R_aising _S_kinny _E_lephants _I_s _U_tterly _B_oring

BEFORE you reach for that power switch, give the Alt-SysRq combo a chance to do a graceful shutdown/reboot.  Press and hold down "Alt-SysRq" ("SysRq" is the key otherwise known in DOS-world as "PrtScn", normally near the right end of the top row of keys) and then, one at a time, S-L-O-W-L-Y in sequence, " r s e i u b ".

Probably you will be amazed to see your "locked up" system do a shutdown and normal reboot.


Reference:  [http://linuxgazette.net/issue81/vikas.html](http://linuxgazette.net/issue81/vikas.html)

---

### Post by lsaffre on 2010-06-02
Thank you, dabl. I didn't know about the Alt+SysRq key, and I'll try it as soon as my notebook starts up again! 

It doesn't work on the Ubuntu live system however (the one that starts from the 10.04 installation cd), is that normal?

Anyway my most urgent question remains unanswered: is there nothing I can do to make it boot again (without installing from scratch)? I can even mount that non-booting drive and see the whole file system, the data is not lost. Why then does it hang during boot?

I don' agree that it is normal to loose all your data after a power failure. I have a Debian server running for more than 5 years now, and there's a power breakage every few months here, and when I swtich it on again the server just does a file system check. There was never such a problem.

Okay, I'll ask my wife to wait another day for her notebook, because I still hope that somebody here finds time to help me investigate what happend! 

Luc

---

### Post by josarn on 2010-06-02
Whay joy when i learn something! By the way, if when you press the combination "Alt + SysRq" you get the taking a screenshot window, try "AltGr + SysRq" instead...

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by lsaffre on 2010-06-05
The explanation for these problems is that I had had the bad idea to disable the "Fan Always On" BIOS option, and didn't remember this when the computer afterwards started to freeze systematically. Thanks to [http://forum.ubuntuusers.de/topic/live-cd-funktioniert-installierte-version-fri/](http://forum.ubuntuusers.de/topic/live-cd-funktioniert-installierte-version-fri/) who helped me to get out of this problem. I wrote (and plan to maintain) a summary of my experiences with this computer:
[http://code.google.com/p/lino/wiki/LinuxOnCompaqPresarioCQ61](http://code.google.com/p/lino/wiki/LinuxOnCompaqPresarioCQ61).

---

