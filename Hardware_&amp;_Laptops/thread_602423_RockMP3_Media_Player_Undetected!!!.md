---
title: "RockMP3 Media Player Undetected!!!"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by rochak on 2007-11-04
Hi guys,

I purchased a RockMP3 media player and it is not working with ubuntu :(( .. when I connect it to my computer, ubuntu detects it and shows me the mp3 folder files but then immediately disconnects after like 5 seconds. 

I searched a lot on the internet and came across a geek who had the same problem and modifed his unusual_devs.h file, he has given the code to put in but I have no clue where and how to put it. His comment are on this page [http://groups.google.com/group/linux.kernel/browse_thread/thread/8fcc3de1d9397a0e](http://groups.google.com/group/linux.kernel/browse_thread/thread/8fcc3de1d9397a0e)

I tried the below :

1. I went to the location /usr/src/linux-headers-2.6.22-14/drivers/usb/storage#  and created the file unusual_devs.h as I did not have one by default. (am I in the right directory ??)

2. I then copied the code from his page to the file. I am attaching my file unusual_devs.h for your reference

I tried plugging my rockMP3 again but it was the  same problem again :((  It detected the mp3 player but then automatically unplugged it after a few seconds. 

I will greatly appreciate if someone can edit my unusual_devs.h so that it will work with my MP3 player and give me the instructions to make it work. Thanks a lot!

----- unusual_devs.h file ---------

 @@ -897,6 +897,22 @@
                US_SC_DEVICE, US_PR_DEVICE, NULL,
                US_FL_FIX_CAPACITY ),

+/* Reported by Massimiliano Ghilardi <massimiliano.ghila...@gmail.com>
+ * This USB MP3/AVI player device fails and disconnects if more than 128 sectors (64kB)
+ * are read/written in a single command, and may be present at least in the following products:
+ *
+ * "Magnex Digital Video Panel DVP 1800"
+ * "MP4 AIGO 4GB SLOT SD"
+ * "Teclast TL-C260 MP3"
+ * "i.Meizu PMP MP3/MP4"
+ * "Speed MV8 MP4 Audio Player"
+ */
+UNUSUAL_DEV(  0x071b, 0x3203, 0x0100, 0x0100,
+               "RockChip",
+               "ROCK MP3",
+               US_SC_DEVICE, US_PR_DEVICE, NULL,
+               US_FL_MAX_SECTORS_64),
+
 /* Reported by Olivier Blondeau <zeit...@gmail.com> */
 UNUSUAL_DEV(  0x0727, 0x0306, 0x0100, 0x0100,
                "ATMEL",

---

### Post by pinkunicorn on 2007-12-21
I have the exact same problem, and would be interested in a solution.

---

### Post by Folly on 2008-01-17
Found a workaround for get it working!

I've followed this post [http://forums.fedoraforum.org/showthread.php?t=155595](http://forums.fedoraforum.org/showthread.php?t=155595) and after created the set128_MP3 script under my home dir (don't forget to chmod it to make it executable!!) I've created the file 80-MP3player.rules under the /etc/udev/rules.d directory putting inside it the following line:

ACTION=="add",SYSFS{model}=="USB MP3",RUN+="/root/udev/set128_MP3"

(change /root/udev with your correct path to the script)

Once inserted again my player it worked like a charm!

Enjoy!

:wink:

---

