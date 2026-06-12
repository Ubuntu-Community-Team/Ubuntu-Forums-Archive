---
title: "I need some help deciphering these kernel messages"
date: 2009-06-10
forum: Hardware
---

### Post by jdacronym on 2009-06-10
I've been having some problems with my Vostro 1500 laptop.  Just now on resume it crashed again, and I was only able to copy down a few things before it tried to start Xorg and I could no longer see the kernel messages I was copying down.

[ <something>] ata3.0 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ <something>] ata3.0 status { DRDY }

and then something with "{errno=-5}" in it, repeated three times.  Then I get a black screen and a rapidly blinking mouse cursor.  I tried restarting xorg via Ctrl+Alt+Backspace, but all I got was a flash of some frames and my desktop background before it froze again (I'm told that I got a glimpse of whatever was in my draw buffer, and that my session was probably gone already)

I've taken a look around ubuntuforums and the web for similar threads, but I haven't found anything useful.  Smartctl tells me that my hard drive is healthy.  So what's going on?

---

### Post by cariboo on 2009-06-10
You probably have a few corrupted sectors on your hard drive. Boot from the live cd and run fsck on the hard drive to repair the problems.

---

### Post by jdacronym on 2009-06-10
Will any liveCD do?  I'm not sure I have my 7.10 install disc around, but I'm sure I have a knoppix 5.0.1 DVD.

---

### Post by jdacronym on 2009-06-16
Well, I tried restarting after 'sudo touch /forcefsck'.  The fsck logs show no irregularities, so I don't have any information about that.  This problem hasn't happened again, except...

This morning something similar happened again on restore.  This time however the messages were a little different, and eventually my computer finished the restore just fine.  Here's the context for the new messages:

[    1.987599] sd 2:0:0:0: [sda] Starting disk
[    1.987913] PM: Finishing wakeup.
[    1.987915] Restarting tasks ... done.
[B][    8.182024] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[    8.182189] ata3.00: cmd ca/00:20:f7:82:9a/00:00:00:00:00/ef tag 0 dma 16384 
out
[    8.182192]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeo
ut)
[    8.182347] ata3.00: status: { DRDY }
[    9.081904] ata3: port is slow to respond, please be patient (Status 0xd0)
[   10.027307] ata3: device not ready (errno=-16), forcing hardreset
[   10.027321] ata3: soft resetting link
[   10.178972] ata3.00: NODEV after polling detection
[   10.178984] ata3.00: revalidation failed (errno=-2)
[   10.179138] ata3: failed to recover some devices, retrying in 5 secs[/B]
[   11.313273] ata3: soft resetting link
[   11.351537] ata3.00: configured for UDMA/133
[   11.351579] ata3: EH complete

The parts that are similar to my previous error messages are in bold.

So is my hard drive just slow to wake up, or could I still have bad blocks in my filesystem that fsck didn't find?  Or is it something else?

Thanks in advance for any information you can provide,
~jdacronym

---

