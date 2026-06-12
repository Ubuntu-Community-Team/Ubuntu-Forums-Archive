---
title: "Mouse not working on Cpq ProLiant 1600R"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by Willdawg on 2005-12-29
Hello all,

I'm using the Breezy Live CD to see if I can sucessfully run Ubuntu on an old Compaq server our company has inherited (ProLiant 1600R - PII/450 w/ 512MB RAM, Cpq SmartArray 3200 RAID controller.) Breezy Live does boot up (just hit return for default, no special startup options seemed to apply) and then GNOME starts OK, but when I get a mouse cursor in GNOME, the mouse does not respond, and I don't think the keyboard does either (not quite sure about that though... what I tried did not work) The server currently has NetWare 5.1 installed, and if I boot into that, the mouse and keyboard work fine. The keyboard also does work in the Live initial startup (select language, keyboard type, etc.)

I admit that I'm a bit rusty in my Linux skills, and I've never really used Ubuntu before (just played a bit with the Live CD on my home PC, which worked fine.) So, any pointers as to how I might help myself here are gratefully accepted :)

Thanks,
Will Dennis

---

### Post by Willdawg on 2005-12-30
Hi all,

OK, I found that I have the same problem with another Debian-based system (the Xen-3.0 live CD that uses Debian Etch) -- X/Xfce comes up, mouse pointer shows, but mouse does not work. In addition, if I kill off X, I get the following message:
[FONT="Courier New"]psmouse.c: bad data from KBC - timeout[/FONT]

This message reprints any time I hit a key on the keyboard. It does not happen, however, until I have started/stopped X.

I looked at the output from "dmesg", it does print the line:
[FONT="Courier New"]mice: PS/2 mouse device common for all mice[/FONT]

So, I assume from that line that the kernel does detect that a PS/2 mouse is attached (right?)

In /dev/input, I have two char devices -- "mice" and "mouse0"... Also, in /dev, there is a char device "psaux". I am used to using "psaux" from RedHat, but when I configured "/dev/psaux" as the mouse device in xorg.conf, it still does not work (it was set up for "/dev/input/mice" in the stock conf.)

Any way to see if the mouse device is working from the console before I try to start X?

I haven't had this much trouble with getting a mouse to work since RedHat 5.2... But again, I've never tried to get Linux running on a ProLiant 1600R... :???:

---

### Post by Willdawg on 2005-12-30
Next update :)

Back to Ubuntu Live 5.10 -- I have X/GNOME up, mouse pointer is showing but not functional. If I <Ctrl><Alt><F5> to get to a virtual console, and I grep the output of dmesg for the string "mouse", I get the same output as in the Xen demo CD, namely the kernel sees the PS/2 mouse attached, but then there's a whole bunch of messages about that "psmouse.c" error.

I know this is somewhat old hardware, but it doesn't make sense to me that a PS/2 mouse would not be supported... :(

---

### Post by abovett on 2005-12-30
Forgive me for suggesting the obvious, but - have you tried another mouse?

Andy B

---

### Post by Willdawg on 2005-12-30
You are forgiven :) 

Yes, when I went back to Breezy the second time, I switched the original mouse I was using with another known good one. (The first one works fine too in NetWare and Windows.)

---

### Post by Willdawg on 2006-01-02
Trying hard to solve my own problem (and not let this thread die ;) )

I have hooked the mouse (and keyboard) in question to another PC (an old Dell Optiplex GXa we have laying around here) and on the Xen-3.0 Live demo CD, as well as Kubuntu 5.10, the mouse is fully fuctional as normal.

Soooo, it must be the Compaq hardware... it doesn't work (yet!) in (K)Ubuntu, but does with Windows or NetWare. There must be a reason for this :???: 

I'd really like to use this old server, hope that I can get things working with it.

Thanks for reading,
Will

P.S. - Happy New Year!

---

### Post by Willdawg on 2006-01-02
Another clue!

In Kubuntu on the Dell GXa, in the dmesg output, there's a line after the "mice:" line that reads:
[FONT="Courier New"]input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1[/FONT]

I'm pretty sure that line (or something like it) is not on the Cpq 1600R. So, I take it that this is a hardware detection issue?

Bueller? Bueller??

---

### Post by Willdawg on 2006-01-02
Last post for today...

Back to the 1600R... Using the same Kubuntu Live CD, I booted up and am in KDE. You guessed it -- mouse pointer shows, but doesn't work. So, over to a virtual console to look at the dmesg output and, guess what -- there is the "input:" line after the "mice:" line just as on the Dell GXa box. So, it looks to me like the HW autodetect does see a mouse. BUT, at the end of the dmesg output, there's many of those "[FONT="Courier New"]psmouse.c: bad data from KBC - timeout[/FONT]" messages. I know that wasn't happening on the GXa box.

So, I guess this is a case of unsupported hardware?? Can anyone who might know please confirm? I'll add my findings to the HAL list if I can confirm this is an unsupported HW issue.

Thanks.

---

### Post by hloureiro on 2006-02-03
You aren't alone in the dark ;) .  I'm facing the same issue with Ubuntu 5.10 and a old compaq proliant 1600.  I tried a lot of boot options like "noapic msmouse=12 acpi=off nousb" without success :cry:

---

### Post by hloureiro on 2006-02-03
Searching in the net (not by google, but using teoma), I found a interesting link about this subject:

[http://lists.olug.org/pipermail/olug/2005-January/015824.html](http://lists.olug.org/pipermail/olug/2005-January/015824.html)

Apparently they fixed it changing the bios settings for mouse (legacy, auto, or something else).  I didn't try yet because I couldn't figure out how to access bios since F1, F2, F10, F12 and Del keys didn't work for that.

---

### Post by stuffa on 2006-02-14
Guys.  I have exactly the same problem.
I am currently running my machine without a head, untill I get it resolved.
I have tried everyting I can think of.
I have checked all the config in smartstart - I have v5.2. - I downloaded the lattest version 5.5 from compaq, however I am unable to get the image to burn successfully to a CD.
I recently heard of someone who got their 1600 running by removing the compaq network card, apparently the interupt was shared with the mouse.
I havent tried it yet, but I dont expect that that is our problem.
I have the lattest bios etc.  everything is upto date except the smatstart CD.
I did manage to get a 5.5 config of floppy,  It didnt make any difference.
I have several ubuntu 5.10 servers here, the same mouse KB work on all of them,  just not the compaq 1600.

---

### Post by ramdez on 2006-02-17
Add another disgruntled user to this list.  I have the exact same problem with a Proliant 1600.  I was going to try using a serial mouse to see if it was the proprietary compaq mouse controller but thought i'd search.  i'm sure with 4(5..) of us we'll get it worked out.  Good to see it wasn't me who screwed something up :)  just a suggestion.  Try resolving this from another PC via ssh.  Might keep some headaches away and you can let the server cruise while you work on it.

---

### Post by mI3O on 2006-06-22
Hi Guys!
Has anyone solved the problem with Compaq (ps/2) mouse? I have the same problem. During installation of Ubuntu 6.06 I've had to exchange my Compaq mouse (using restart) with other mouse because cursor don't move in Ubuntu Live CD (6.06). After install I connected back my Compaq mouse (without restart) and it worked properly - but only untill restart. After that cursor doesn't move again. In Ubuntu 5.10 Live CD my Compaq mouse works, so I've rewritten xorg.config according to it but without any effect... Could anyone helps me?
Where else (next-to xorg.config) can I configure mouse? I want to compare another settings with other mouse connected.
In knoppix my Compaq mouse works, but there's no xorg.config, can I check something also in Knoppix to fix my problem in Ubuntu?
anything else: This Compaq mouse works in Ubuntu 5.10 which I had before 6.06 - but sometime also need restart to ensure cursor moving (in 6.06 restart isn't effective).
..thanx

---

