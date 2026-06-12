---
title: "&quot;Chewing&quot; hard drive problem"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by npu on 2005-12-06
I have a pretty puzzling story to tell. I really hope someone can help me out with this.

First my system specs: I have a system IDE/ATA hard drive sized 120 gb and three extra disks sized 200 gb each (two IDE/ATA and one SATA).

I was using MS Windows up until about a year and a half ago, and back then I noticed one of my disks was almost constantly working even when the computer was idling/not used. A pretty annoying sound, in Swedish I'd use the word for "chew" (I hope that makes sense in English to describe it :) ). About once every two minutes the disk would start this for about 30 seconds or more, almost as if it was reading something over and over again.

When I switched to SUSE Linux the problem was still there.
Then I found Ubuntu and was so impressed with the Live CD I installed it, and...
The problem was **gone**! All hds are as silent as one would expect them to be. I was happy.

About two weeks ago I decided to try out Kubuntu, so I installed it, and for some reason the problem is back. So my guess is this MUST be something with how the units are handled by the system. In GNOME (Ubuntu), no problem - in KDE/Windows, a chewing hard drive.

Anyone have any experience with this, or the technical knowledge to explain what could be wrong? I'm not sure which of the hds that does this, but IIRC I thought it was one of the 200 gb ATA:s back when I last had this problem.

Any help greatly appreciated, I love Kubuntu and want to stay with it. But this thing is really bugging me. The sound is annoying and makes me nervous. ;) It simply shouldn't do what it does.

Cheers.

(Oh, and, I've used the same mount commands in fstab under SUSE/Ubuntu/Kubuntu. I'm also sure it has nothing to do with that one of the drives are SATA and the others are not, the SATA disk was added after the problem first occured.)

---

### Post by poptones on 2005-12-06
On which drive did you install kubuntu? Is it on the same drive as ubuntu?

If it sounds like it's "reading something over and over again" it's very likely a failing hard drive. Drives can behave erratically like this for years before they finally give up the ghost. I'd suggest downloading an iso of gwscan, boot from it, and run a thorough diag on each of your hard drives.

---

### Post by npu on 2005-12-07
Thanks for the reply, poptones.

[QUOTE=poptones]On which drive did you install kubuntu? Is it on the same drive as ubuntu?[/QUOTE]Yes, the same drive for all OS:s.      (Identical fstab)

[QUOTE=poptones]If it sounds like it's "reading something over and over again" it's very likely a failing hard drive. Drives can behave erratically like this for years before they finally give up the ghost. I'd suggest downloading an iso of gwscan, boot from it, and run a thorough diag on each of your hard drives.[/QUOTE]Yeah, I'll try scanning them again, just in case. I did that back when I first had this problem, and found nothing. None of the drives are particularly old either.

But all this doesn't make sense... How come the drive was all OK under Ubuntu? The day I installed Ubuntu the sound stopped, and wasn't there for all those months when I used Ubuntu. And the exact day i uninstalled Ubuntu the sound was back. Seriously. :???:

Could it be some difference between GNOME:s and KDE:s hdd-power-down-something setting? If there are any. I know I haven't touched the BIOS, so that can't be it.

---

### Post by davidsrsb on 2005-12-07
Get the disk manufacturers diagnostic program (usually DOS) from the Net and run it.

---

### Post by poptones on 2005-12-07
Yes, run the manufacturer's scan. I suggested the gwscan (gateway) simpl becauuse I'm familiar with it and it seems to consolidate at least two major (maxtor and seagate) test utilities. 

The *possioble* reason for the drive seeming "fine" before and suddenly failing incvolves bad sectors; if there is no data stored at a bad part of the disc then the drive has no reason to access it and no need to retry when it cannot. If some data (like a bunch of pictures, music... or a new operating system) suddenly appears there, now it has to access it.... but it can't, so it reseeks.

Have you checked your error logs in the various operating systems?

---

### Post by poptones on 2005-12-07
Yes, run the manufacturer's scan. I suggested the gwscan (gateway) simpl becauuse I'm familiar with it and it seems to consolidate at least two major (maxtor and seagate) test utilities. 

The *possioble* reason for the drive seeming "fine" before and suddenly failing incvolves bad sectors; if there is no data stored at a bad part of the disc then the drive has no reason to access it and no need to retry when it cannot. If some data (like a bunch of pictures, music... or a new operating system) suddenly appears there, now it has to access it.... but it can't, so it reseeks.

Have you checked your error logs in the various operating systems?

---

### Post by npu on 2005-12-07
> **poptones]The *possioble* reason for the drive seeming "fine" before and suddenly failing incvolves bad sectors said:**
> 
Ok... However I'm totally sure all my four disks has been 100% full (or next to) at times as I shuffle a quite a lot of data (perhaps that doesn't rule out anything, but still).

[QUOTE]Have you checked your error logs in the various operating systems?
Thanks for your input so far (davidsrsb too), I'll go about scanning the drives and check the error logs. Can you direct me to where those are or how to switch them on? Perhaps even better if I could see (live) what each disk does, if possible. And should I _completely_ rule out that this simply cannot be a "system" issue? My technical knowledge doesn't go far enough to make a conclusion myself. And with all that time on Ubuntu without a single "chew" makes me wonder.

---

### Post by poptones on 2005-12-08
I would suggest installing smartmontools and checking the drives periodically to see if their error logs ae increasing (as well as to see if any drive has an unusually large number of recorded errors compared with the rest).

The type of noise you describe could be due to reseeking data or it could also be due to the drive having thermal issues. First task would be to figure out which drive is making the noise, then narrow down the "why."

You can view the error logs easily by browsing /var/messages or by clicking "log viewer" on your ubuntu "system tools" menu. Note that, if you DO have a drive that is failing and the log is so filled with messages that it occupies several megabytes, the desktop "log viewer" will take forever to open or may not at all.

---

### Post by ormus on 2005-12-08
i hope you havent got the infamous ibm deathstar rattle?
ive got a 60 gig hdd here, hardly used since new. out of warranty now. and completely useless.
(google for: ibm deathstar rattle).

ps, ibm have now sold their hdd business to hitachi.

---

