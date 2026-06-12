---
title: "Testing for damaged hardware?"
date: 2018-11-03
forum: Hardware
---

### Post by SourceSlayer on 2018-11-03
My parents laptop has had significant issues recently. It previously ran Windows but after continually failing to boot after an update, I installed Ubuntu and they have enjoyed it. I suspect these problems might might have something to do with a bad habit of leaving it on overnight, but not checking to ensure it's securely plugged in, thus leading the battery to die (this started long before I installed Ubuntu).

However, eventually every time it boots, it boots to an initframs shell, in which I type "reboot" and then I have to run fsck every time. I go to check the hard drive once I can manage to graphically boot and it says in Disk Manager, "Assessment: Disk is Okay, 5920 bad sectors (35°C/97°F)" which I'm fairly certain means the disk is not actually okay, since, though it's a terabyte, that seems like a lot of bad sectors, am I wrong?

If not, I can just replace the hard drive, but is there anyway to test the other hardware to see if it has any problems and if it does, what might the problems be?

It's a Toshiba Satellite, if that matters.

---

### Post by deadflowr on 2018-11-03
Over 5000 bad sectors is a lot and good reason to suspect as to the cause of failures.
Typically a count that high means the disk is toast.
Replace the disk.

Batteries are batteries so they're expected to die out eventually.
If you can find a replacement for that, all the better.

You can run Ubuntu's checkbox utility which run a basic scan of various pieces of hardware.
[https://help.ubuntu.com/community/Checkbox]("https://help.ubuntu.com/community/Checkbox")

That should give you a goof rundown of what state the system is in.

---

### Post by Autodave on 2018-11-03
Your hard drive has joined the forces of evil: replace it now. :-)

---

