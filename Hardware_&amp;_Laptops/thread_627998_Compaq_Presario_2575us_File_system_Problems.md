---
title: "Compaq Presario 2575us File system Problems"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by Sammybeany on 2007-11-30
Hello.

I have Ubuntu 7.10 installed on my Compaq Presario 2575us laptop.  The laptop is acting primarily as a server for me and is not my main computer.

After it sits idle for a while . . . sometimes a few hours, sometimes a few days, sometimes a few weeks . . . the entire filesystem will suddenly become read-only.  Upon rebooting, it tells me to run fsck.  If I run "fsck -y" and reboot when it finishes, things will be back to normal.

Any ideas what could be causing this and how to fix it?  Thanks in advance.

---

### Post by Sammybeany on 2007-12-01
A friend of mine suggested disabling ACPI, which I just finished doing.  Now it's just kind of a waiting game to see if that actually did anything.

If anyone has ideas or insight in the meantime, I'd still really appreciate it.

---

### Post by jcsteele on 2007-12-01
Probably not much useful, but what does smartctl say about the drive?

[http://gentoo-wiki.com/HOWTO_Monitor_your_hard_disk(s)_with_smartmontools](http://gentoo-wiki.com/HOWTO_Monitor_your_hard_disk(s)_with_smartmontools)

You can skip the first couple steps about installing...below will do it for you.

$ sudo apt-get install smartmontools

//jcs

---

### Post by Sammybeany on 2007-12-01
Hah, it crapped out again.  Sooner than I expected!

So, yeah, back at square one.  Any ideas?

---

### Post by jcsteele on 2007-12-01
Other than the notion of a hardware problem, I don't really have any suggestions...

Sorry.

//jcs

---

### Post by covox on 2007-12-01
Just to clarify, the drive mounts normally (RW) then switches to RO mode after a length of time?

What kind of drive (IDE, SATA, USB), and which filesystem does it use?

Have you tried typing 'dmesg' at the console and checking for anything suspicious (i.e. messages involving the hard-drive) just after the disk goes RO?

Read only can be triggered when Something Terrible happens, as a sort of precaution to prevent further drive corruption. With that in mind, fscking a sick drive can be like kicking a landmine. Backup your important data ASAP!

---

### Post by Sammybeany on 2007-12-01
Correct, it starts out RW then ends up RO.  This is my main and only hard drive.  The one I boot from.  It's the laptop's internal IDE drive.  Filesystem is ext3.

All of the important data is regularly backed up, so that is not a concern.

This has been happening (ir)regulary for the past several months, ever since I installed Ubuntu.  It's not a new issue; it's been plaguing the system all along.

I tried looking around in the logs a bit before, but I don't know what I'd really be looking for.  It seems to happen out of nowhere.  I suspect SOMETHING is triggering it, but who knows . . . 

(On a side note . . . Covox?  Your name/avatar seem familiar.  Were you involved with the Sonic community a long time ago or something back before it became a festering bin of idiocy?  I feel like I know you from somewhere.)

---

### Post by covox on 2007-12-01
Yep, I hung around the Clickteam scene quite a bit about four years ago. Your name also rings a bell.

Probably the easiest way to go about doing this is to run the command 'dmesg > dmesg.out', then paste the file dmesg.out as an attachment. If the hard-drive has done its switch from RW to RO, there's probably something in the log saying why.

---

### Post by Sammybeany on 2007-12-01
The uploading thing is being stupid and is saying the file is too large or something, so try this:

[http://horseface.org/dmesg.out](http://horseface.org/dmesg.out)

I'm noticing there is a bunch of ACPI stuff in there.  Would that indicate that ACPI is, in fact, not disabled?  It's SUPPOSED to be, but maybe I did something wrong. :|

---

