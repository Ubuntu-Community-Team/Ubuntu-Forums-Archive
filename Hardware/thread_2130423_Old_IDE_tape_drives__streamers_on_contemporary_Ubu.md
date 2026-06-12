---
title: "Old IDE tape drives / streamers on contemporary Ubuntu?"
date: 2013-03-29
forum: Hardware
---

### Post by isync on 2013-03-29
I've got an old "*iomega tape 420*" Floppy cable connected (similar to IDE) tape drive, a [Ditto]("http://en.wikipedia.org/wiki/Ditto_%28drive%29") drive, for [QIC]("http://en.wikipedia.org/wiki/Quarter_Inch_Cartridge")80 tapes, connected to my floppy disk IDE connector. Now, where to go from here?

The drive powers up bgut Ubuntu doesn't show any references to it upon bootup or any tape-resembling entries in /dev.
(In case the drive is only mounted when a tape is inserted, I inserted one, the motors spun up, shuttling the tape and then rested - still no change and no activity in syslog, is that normal, what should it do?)

Additionally all tape-related stuff seems to have vanished from the repos, no *ftape* driver, no *ztape* driver, no *ide-tape* driver.

How can I get this thing working? Can I??

Also: I'm unsure if I hooked it up correctly, no markings there. Is there a way to debug if my Floppy cable is connected correctly, in the right direction etc., even when there's no way to operate the actual tape drive with proper drivers?

Back then I filled the tapes with the Windows (proprietary?) software for the IoMega devices, problably using some compression.
Would be geeky fun to look into my old collection of Sony 2120 tapes and waste some time...

---

### Post by |{urse on 2013-03-29
what does the command

mt status

give you?

---

### Post by isync on 2013-03-29
Aha! First pointer: the command *mt* (for 'magnetic tape')!

After reading the man, I did (a stupid) *mt status* which resulted in "mt: /dev/tape: rmtopen failed: File or Device not found"
But that was the second pointer: the default mount point for a tape device for contemporary Debian/Ubuntu seems to be */dev/tape*, right?
And, well, that mountpoint is missing! With or without tape doesn't seem to make a difference.

---

### Post by coldraven on 2013-03-29
I have a hazy memory of some IDE cables that had a twist in them. I think that the middle section of the cable was reversed from end to end.
I could go and search the loft in the shed, I probably still have some!

---

### Post by isync on 2013-03-29
No need to... But thank your for offering it. Let's not focus on the cabling stuff, I will use [this page here]("http://www.pcguide.com/ref/fdd/confCable-c.html") to make sure I've got it connected properly...

But how should Ubuntu react to it, how can I mount it, how can I make sure the system is able to talk to it??

---

### Post by |{urse on 2013-03-29
well, you can try this:

sudo mkdir /media/tape

mount /media/tape /dev/tape

Now open the /media/tape folder, is your data showing up?

If that actually mounted, follow the rest of these instructions

[http://www.cyberciti.biz/faq/mount-drive-from-command-line-ubuntu-linux/](http://www.cyberciti.biz/faq/mount-drive-from-command-line-ubuntu-linux/)

---

### Post by |{urse on 2013-03-29
You'll be able to find the /dev/ mountpoint with either the mount command or poking around dmesg | tail

---

### Post by isync on 2013-03-30
I know, I know... Mounting isn't the problem. The problem is that there's no entry in /dev for the device, at all! It seems the system is completely unaware of the tape-drive being connected. Nothing on bootup, nothing in syslog or dmesg. All activity the iomega shows is hardware stuff from powering it up thorugh the molex connector. But the system completely ignores it.

Would lspci show devices connected via floppy cable?

Any more hints? Anyone??

---

### Post by plucky on 2013-03-30
Try some of these commands

```
Tape Drive Commands
Rewind tape drive:
# mt -f /dev/st0 rewind

Find out what block you are at with mt command:
# mt -f /dev/st0 tell

Display list of files on tape drive:
# tar -tzf /dev/st0

Restore /www directory:
# cd /
# mt -f /dev/st0 rewind
# tar -xzf /dev/st0 www

Unload the tape:
# mt -f /dev/st0 offline

Display status information about the tape unit:
# mt -f /dev/st0 status

Erase the tape:
# mt -f /dev/st0 erase

You can go BACKWARD or FORWARD on tape with mt command itself:
(a) Go to end of data:
# mt -f /dev/st0 eod
(b) Goto previous record:
# mt -f /dev/st0 bsfm 1
(c) Forward record:
# mt -f /dev/st0 fsf 1

```

I cannot remember where I got them,but they used to work on and old backup tape system I used to play with.
Got bored on how slow it worked.

Good Luck

---

### Post by isync on 2013-04-05
Neither [FONT=Courier New]lspci -vv[/FONT] nor [FONT=Courier New]hwinfo --block --short[/FONT] show any trace of the device when connected.

---

### Post by cortman on 2013-04-05
I'd disconnect and check dmesg | tail, then reconnect and check the same, and see if the system even "sees" it.

---

