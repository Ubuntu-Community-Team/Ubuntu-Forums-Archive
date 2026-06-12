---
title: "USB Mouse freezes randomly in i386, but works in amd64?"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by zaubara on 2006-07-11
Hey there!

I am sorry to annoy you again, but I am experiencing a very strange problem with my mouse ... and I hope you're able to help me a little :)


I recently tried to install Dapper on my machine (nForce4-4x, amd64, geforce 6800 etc.) in a FakeRaid - which works really well, I am able to dualboot into Windows and Linux.
Most things worked fine at first on my amd64 install, but then I discovered that I would rather have the i386 version - so I tried to install this one.

The problem I now experience is as follows: my USB mouse freezes randomly after a few seconds to minutes, being only awaken again by un- und replugging my mouse. A few seconds later, it will freeze again.

When I used the amd64 Live-CD and the install the mouse worked fine!
Now, using the i386 version, may it be the Live-CD or the install, my mouse keeps freezing ... and I don't know how to fix that.

Any ideas?

Thanks!
Martin

---

### Post by zaubara on 2006-07-16
Anyone, please? :(

---

### Post by Anduu on 2006-07-16
Did you completely format your old 64bit install or just install i386 version over it?If the latter is true I bet there is some 64bit stuff left hanging around and messing things up.

---

### Post by zaubara on 2006-07-17
Nope, I did a complete format and reinstalled it from scratch...

My mouse freezes even on the i386 Live-CD, so it must have something to do with... well... anything kernel or driver related, I think? :-k

---

### Post by Katryx on 2006-07-17
I'm having a similar problem.  About half the time I start my computer, by the time it reaches the login screen the mouse (and keyboard) don't work.  So I restart, and sometimes it works, with no further trouble throughout the time the computer is on.

Mouse is a USB optical, Microsoft "Vision."  Keyboard is ps/2, Microsoft "Natural."  Maybe it's a driver issue, or just the fact they're Microsoft?

---

### Post by zaubara on 2006-07-27
After some more searching, I found out that disabling mmconf did the trick for me :D

I guess you had to disable acpi in grub?
Using pci=nommconf instead of acpi=off in grub did the trick for me - I also have Plug&Play OS enabled now in BIOS, USB Legacy support is still activated.

Good Luck!

---

### Post by RobMBaker on 2006-09-05
I have a similar problem too - except mine has only just started, so I know it's something I've done. I have a USB optical mouse, and it worked fine until I reconfigured X after installing ATI drivers. Now I don't know if I'm using the right settings for the mouse, cos it randomly freezes after a while. Either that, or it definitely freezes when I click the Log Off-Shut Down (etc) icon.
The relevant (I hope) section of my xorg.conf is:
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

And I've tried using both the protocols that it offers - ExplorerPS/2 and the ImPS/2 (or whatever) and I'm pretty sure it makes no difference.
Does anyone know what I've changed that should be different?

---

### Post by dysplaced on 2006-09-06
I have the exact same problem as RobMBaker.
Some additional information for my case: I have confirmed that it's not a problem with the mouse itself, since i've tried another (opical USB) mouse from a different vendor with the same results. 
This all happens on an IBM ThinkPad and when the usb mouse stops working I can still use the IBM Mouse-Stick-Thingy. As with RobMBaker, I didn't experience these problems from the beginning, only since I began to change different things in the system, among them installing the ATI-Driver.

Does anyone know what could be causing this, it's really quite annoying...

---

### Post by dysplaced on 2006-09-09
*shameless bump*
Nobody has a clue why this is happening? I haven't found anything I have done that seems to cause it...

---

### Post by beniwtv on 2006-09-09
I had once a similar problem as the OP with my optical mouse. 

I got around it plugging it into anoyther usb port (which was on a PCI usb card). After this, all worked fine.

Hope this helps.

---

### Post by glypph on 2006-11-06
Just spent a weekend tracking down a very similar problem.  (Hope the OP got his solved by now.)  Random system freezes--first the USB mouse, then keyboard, then the whole system stopped.  This is a newly built system, upgraded from Dapper to Edgy.  The upgrade didn't fix the problem. Tried everything suggested in this thread.  Freezes just got worse over time.

Long story made short: what appeared to be a mouse/software problem was apparently a simple problem with a $5 cable.  The clue: at some point, my main SATA hdd was not detected on boot.  Then it was back.  Diagnostic program from the disk manufacturer said the drive was okay.  Replaced the data cable and swapped in a different lead from the power supply to the drive.  It's working fine so far! [fingers crossed].

My lesson: it's always worth checking the hardware--even if "it worked fine under the previous setup."  Maybe the problem is something in the new setup. Or it *could* mean the memory stick/hard drive/power supply/cable/motherboard/whatever coincidentally happened to begin to fail when you switched to the new setup.  In my case, I may have just bumped a data cable loose somewhere along the way, or I had a bad connection from the power supply.

Random freezes might indicate a hardware problem, even if the freezes don't seem all that random.  And start troubleshooting with the least expensive piece of hardware involved--that's the one most likely to go wrong.

---

### Post by agentx on 2007-06-02
I have the same problem and I found a temporary solution by disabling USB Legacy Support from BIOS.

---

