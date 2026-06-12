---
title: "External Hard Drive Problem"
date: 2008-11-20
forum: Hardware
---

### Post by kduvey on 2008-11-20
ive been using ubuntu for awhile now, but am in no way a power user. my external hard drive (i dont know what format it is in) has always worked. i upgraded to 8.10 when it first came out, and my external worked fine. now all of a sudden it dosnet work, when i plug it in it get the error message :

Unable to mount MEDIA
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

i have many important files for school as well as my invaluable music collection on there...

can anyone please please help? im scared!

---

### Post by cariboo on 2008-11-20
What is the output of dmesg when you plug the drive in? to see the output open a Applications-->Accessories-->Terminal and type:

```
tail -n 10 /var/log/dmesg
```

This will output the last 10 lines of dmesg. Paste the output into your next post so that we can help you diagnose the problem.

Jim

---

### Post by kduvey on 2008-11-20
thank you so much for your time and effort, the data on this hard drive means so much to me


kduvey@kevin-laptop:~$ tail -n 10 /var/log/dmesg
[   26.511404] cs: IO port probe 0x820-0x8ff: clean.
[   26.512159] cs: IO port probe 0xc00-0xcf7: clean.
[   26.513060] cs: IO port probe 0xa00-0xaff: clean.
[   26.949671] lp: driver loaded but no devices found
[   27.163123] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   27.709200] EXT3 FS on sda1, internal journal
[   28.584691] type=1505 audit(1227205880.800:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4320
[   28.787756] type=1505 audit(1227205881.004:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4325
[   28.787977] type=1505 audit(1227205881.004:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4325
[   28.893665] ip_tables: (C) 2000-2006 Netfilter Core Team


that is what shows up


here are a few interesting tid bits, not sure if they will help you

-when i run lsusb just after i restart the HDD, it shows up on the list. but i still cant see the files. shortly after it disappears.
- the only thing i did between the time it worked and now is install qtpfsgui and various packages its needs to work. qtpfsgui is a program to make HDR images using tone mapping (photography). i used synaptic package manager to install the 4-5 packages and am willing to uninstall them, but i dont remember the name of them all. is there a way to view the history and delete the last few packages i installed? or revert back to a set time like you can do in windows?

thanks agian

---

