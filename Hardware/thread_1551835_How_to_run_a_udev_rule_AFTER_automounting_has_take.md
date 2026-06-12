---
title: "How to run a udev rule AFTER automounting has taken place"
date: 2010-08-12
forum: Hardware
---

### Post by Porkchop Johnson on 2010-08-12
Hi all,

I am trying to get a udev rule to fire after USB automounting has taken place, not before.  Although I named it /etc/udev/rules.d/999-my-camera.rules, it always runs before the device is automounted.   The rule itself is triggered by the correct event and runs the correct script, so that part isn't a problem.

The problem is I want the rule to launch a script that basically does cp -R /media/camera/* /somewherelse.   But I can't do that if the rule fires before the device has been mounted.  I don't know how to make the rule fire after automounting.

Help?

---

### Post by Porkchop Johnson on 2010-08-13
OK... I still don't know the answer to my question, but I worked around my problem by making the udev rule itself perform the mounting.  

I found the clue here, [https://answers.launchpad.net/ubuntu/+source/nautilus/+question/64803](https://answers.launchpad.net/ubuntu/+source/nautilus/+question/64803) , and apparently I needed to tweak my rule to wait for the block device (SUBSYSTEM=="block") instead of firing in response to the usb event.

What happens to automount when it sees the volume is already mounted?  Not sure I really care at this point, but I really would like to know how to finely tweak how gnome does automounting in response to different volumes, and how this interacts with udev.  SO that part of the question is still open.

---

### Post by Porkchop Johnson on 2010-08-14
Continuing along the lines of trying to answer my own question/solve my own problem in the hopes it helps someone else... 

My biggest problem after figuring out the above was that I need a rule that fires in response to the block device, but when I do udevadmin info, the ATTRS of the block devices have no uniquely identifying information.   The hardware has logs of it, but not the filesystem.

However, I noticed that the script fired by the udev rule has all sorts of useful environment variables that didn't show up in udevadmin info (for whatever reason, maybe I just suck at using udevadmin info).

So what I ended up doing was having a generic rule that fires a generic script in response to ANY block subsustem event.   In that generic script, now I have access to all sorts of useful vars, in particular ID_FS_UUID, which I can easily use to do what I want  (in this case mount/umount the volume and then do stuff with the files).   

Having mounted the USB mass storage in the script, gnome then doesn't do any automounting, which suits me fine although I wish I understood better how that works.

Hope this helps someone else.  I wasted a lot of time with it.

---

