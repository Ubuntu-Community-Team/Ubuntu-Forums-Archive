---
title: "SeagateFree Agent unable to be mounted"
date: 2009-10-05
forum: Hardware
---

### Post by yeosteve on 2009-10-05
I've had a 1TB Free Agent drive attached to my Ununtu 9.04 machine for a ehile now with no problems. I'm suddenly getting

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

The drive is still readable by my Win XP netbook, so it's OK.

I read somewhere that there's a problem with I/O with these drives because the power down, but I can't find the reference any more. Any ideas about how to fix this will be hugely appreciated, because its my main backup.

There was another messae which might help??

$MFTMirr does not match $MFT(record 0) Faile to mount dev/sdc1': Input/Output error NTFS is either inconsistent or there is a hardware fault.

That means nothing to me :)

---

### Post by cameron3200 on 2009-10-05
Try connecting the external HDD to the Windows computer, then with it connected shut down the Windows computer completely. Once the Windows computer is shut down completely and properly try disconnecting the external HDD and see if Ubuntu can mount it.

I've had a similar issue with a Seagate Freeagent and that is how I resolved it. Let me know how you make out :)

---

### Post by yeosteve on 2009-10-05
Hi,
Thanks for that, but it didn't work.  Shame, because it makes a good story to tell about fixing Linux probs with a Windows machine, but no this time.

The error was the same as the second one in my first post

---

### Post by cameron3200 on 2009-10-07
You may want to check out this thread as it deals with the same problem: [http://ubuntuforums.org/archive/index.php/t-1142397.html](http://ubuntuforums.org/archive/index.php/t-1142397.html)

No indication of resolution but the person who reported the problem didn't try the suggestions made.

---

### Post by MasterOfTheHat on 2009-10-07
When are you getting the error messages you listed? Is it when you plug the drive in or when you try to access it? That error message makes it sound like you have a corrupt MFT on the drive, but I would be surprised about that if it mounted up on an XP box.

You might try forcing the mount on the Ubuntu box and then gracefully unmounting it. Or it may be worth plugging it up on the XP box and running a chkdsk against it.

---

### Post by bobpur on 2009-10-07
I have a FreeAgent drive with similar problems.It's a 160 gb drive I use with my laptop (Acer Travelmate 4230-6179). 

When used in linux (Ubuntu 8.04.3, 9.04, Mint 6, 7, Mepis 7, 8 ) it gives an "Unable to mount" message. Checking details, it has a long list of things that don't make since to me. One thing that I can get out of it says that "unable to mount due to unclean shutdown in Windows" and the rest is how to fix the problem. None of which worked. This is not all the time. Most times it mounts with no problem. No problems at all, so far, in v9.10 (Karmic). I've only had it installed on my laptop for about two days. Similar results on my linux desktops.

In windows XP, upon booting, it wants to do a "Check Disk." If I hook it up after booting, no problem. Same thing in Vista 64-bit and 32-bit desktop.

I don't know the setup for a 1Tb drive as far as power supply goes, but my "little" FreeAgent drive comes with a split cable for additional power from another USB port. When I hook it up on some computers, it makes a "Clinking" noise until I hook up the other "power only" part of the cable. I wonder if low voltage could bring on these problems. I don't know, but I'll try to pay attention next time I use it and it has problems.

 My take on it is that it is just the nature of the beast and I live with it. There may be a fix in linux or with Seagate, I don't know.

I, also, use a Maxtor One Touch 120 gb with none of these problems in, either, linux or Windows.

---

