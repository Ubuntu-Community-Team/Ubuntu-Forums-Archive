---
title: "Hardware message"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by bricksen on 2007-08-23
Anyone who can tell me what this is?
Everything seems to be working.

Aug 23 11:18:08 bricksen kernel: [ 2556.326218] end_request: I/O error, dev hdc, sector 0
Aug 23 11:18:08 bricksen kernel: [ 2556.326322] hdc: tray open
Aug 23 11:18:08 bricksen kernel: [ 2556.326503] end_request: I/O error, dev hdc, sector 4
Aug 23 11:18:08 bricksen kernel: [ 2556.326736] hdc: tray open

---

### Post by dante on 2007-09-12
I see this same thing, on rare occasions, and have never been able to find the cause.
The message itself is completely wrong, at least in my case.  The hdc (or hda on
some of my machines) refers to the cdrom drive.  

The thing is, my machines are locked in racks in two different buildings.  I also
have some Redhat servers.  When I see this message in my logwatch summaries,
it has always been present in all of my Ubuntu 6.06 servers, both my Sun machines
(x86_64) and my Dell machines (x86) at nearly but not precisely the same time-frames,
and never occurs in my other servers in the same racks.  At no time has any use of the
cd drive been attempted, nor any of the trays actually open.

I would think a kernel bug, though they are using different kernels (some are amd-64
machines, some x86).

I'm now looking for any common thread I can find to explain this, as I've just gotten
these messages again today -- not something you want to see on important production
servers, though in the past, I've experienced no problems from the servers after
seeing these messages.

---

### Post by dante on 2007-09-18
Well that was easy enough...I had added `lshw` output to a scripts I run in cron to
capture machine info to a file (such as superblock info, partition info, etc).

The kernel messages were coincident with this updated script running.  It seems
it's merely `lshw` probing hardware, and running in to the empty cd drive
(though the actual error message is a bit odd).  

I was able to recreate the "end_request: I/O error...."
entries to kern.log with this command.

---

### Post by tgalati4 on 2007-09-18
Try putting some data CD's into those drive bays.  This will give the kernel something to chew on.  See if the errors go away.  It's a cheesy fix.

I think it's related to the automount daemon probing the drives for mountable media.

Once it's mounted, it calms down.

---

