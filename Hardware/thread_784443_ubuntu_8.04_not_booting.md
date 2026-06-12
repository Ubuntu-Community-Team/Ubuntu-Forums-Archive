---
title: "ubuntu 8.04 not booting"
date: 2008-05-06
forum: Hardware
---

### Post by jsaturno on 2008-05-06
Hi, I've recently installed the ubuntu 8.04 on my pc (dual boot with XP)
This is booting whenever it wants. I have a nvidia graphic card but it doesn't seems to be the problem...

When it stucks booting shows a message: "Segmentation fault"

I can publish any log file if you want to help me...

---

### Post by fain on 2008-05-06
What does it say before the "Segmentation fault"?

---

### Post by jsaturno on 2008-05-06
I really don't know...
Where can i find this? any log file?

---

### Post by fain on 2008-05-06
try /var/log/syslog or /var/log/messages

Are you able to get in the system at all? What does the live cd do?

---

### Post by jsaturno on 2008-05-07
Hi,
There is nothing in this log files... (No error messages)
Sometimes i can get into the system and all is fine but is difficult to do that (i have to reboot so many times)

I'm not using the live cd because i've used the alternate cd for installation...

---

### Post by fain on 2008-05-07
I would try the live cd and see what happens.  Make note of all errors. See if any drivers are loading at the time etc. A segmentation fault usually means the software has tried to access a place in memory that it cant. [(http://en.wikipedia.org/wiki/Segmentation_fault)]("http://en.wikipedia.org/wiki/Segmentation_fault") 
Try running a memtest from the grub menu for a few hours.

---

### Post by jsaturno on 2008-05-07
I'll try the livecd

I have done the memtest but nothing... I think it could be the graphic card memory, is that possible?

---

### Post by fain on 2008-05-07
Ya maybe.

---

### Post by daemon3 on 2008-05-07
I had generally the same problem doing this (an error about reading squash), and it ended up it was the live CD.  If I were you, I would get a CD-RW and keep trying with a different disc image.  Try for a slow speed when you're burning.  Hope that helps.

---

### Post by Zorael on 2008-05-07
<hijack>

I always burn the live cds at almost the lowest speed possible with verification enabled, and then I always pick 'Check CD for defects' before proceeding to install. I'd rather spend the extra time waiting for it to burn and hash the files than ending up frustrated by a corrupt install and having to do it all over again.

</hijack>

---

### Post by jsaturno on 2008-05-07
Hi,

I have not tried the live cd yet but want to show you some other error messages:

"* Cannot check root file system because it is not mounted read-only"
.
.
.
"init: rc2 main process (4863) killed by SEGV signal"

I've read that it could be a partition problem but really don't know...

---

### Post by jsaturno on 2008-05-13
Hi, i've tried the live cd and the same error happens...
What can I do???????
Help me please...

---

### Post by fain on 2008-05-14
Whats your /etc/fstab look like? 

What file system are you using?

What error did the live cd give you? The segfault or the read only error?

---

### Post by jsaturno on 2008-05-14
Hi fain

I cannot check etc/fstab/ because my system is not booting anymore... :(

I'm using ext3, there is another better?

The live cd gave me the segfault error.


Another thing that i can tell you is that sometimes, when booting, i can see this:
System kernel event manager     [fail]

---

### Post by jsaturno on 2008-05-24
Help me please!!! I don't want to use windows anymore!!!:(

---

