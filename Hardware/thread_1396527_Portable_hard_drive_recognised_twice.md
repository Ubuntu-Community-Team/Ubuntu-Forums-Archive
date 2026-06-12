---
title: "Portable hard drive recognised twice"
date: 2010-02-02
forum: Hardware
---

### Post by peterroots on 2010-02-02
At work I have access to a desktop and a laptop, both running Kubuntu9.10
We have just acquired a western digital My Book - a USB 1TB drive.
It was formatted as ntfs
When I pugged into my laptop the ntfs partition showed up, named something relevant to the drive and so did the virtual CD full of windows software
When I plugged it into the desktop the ntfs partition and the virtual CD showed up twice.
I then deleted the ntfs partition and created an ext3 one in its place named backup1
In my laptop the WD smartware virtual CD and backup1 show up in the recently plugged device list
On the desktop WD smartware shows up twice and so does backup1

Looking in media, after opening backup1, I have a folder backup1 (as expected) adn the side bar in dolphin shows backup1, wd smartware, floppy, backup1, wd smartware. Opening the second backup1 results in a folder backup1-1 which does not go away on unmounting and removing the drive so next time I get backup1 and backup1-2.

Any Idea why this happens on one machine and not the other?
Any idea how to spot the duplicate showing up?

A second My Book drive, yet to be reformatted does exactly the same.

---

### Post by IcarusR on 2010-02-02
I get this with my samba shares when I have both ethernet & wireless connected.

---

### Post by peterroots on 2010-02-02
The drive is connected to the desktop or laptop by usb only
The laptop is currently only connected to a network by wireless and the desktop only has a single ethernet connection

-----------------------
hakunamatatu - no bus

---

