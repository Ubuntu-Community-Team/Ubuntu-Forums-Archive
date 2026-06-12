---
title: "Help detecting Dell laptop webcam"
date: 2020-04-06
forum: Hardware
---

### Post by owbizi on 2020-04-06
Hi, everyone. I'm helping out a friend who recently switched to Ubuntu  in detecting his laptop (a Dell Inspiron 5458) webcam. If you could help  us out, that'd be great!

I ran the following commands in order to further inspect his machine,  but to no avail, and every returned output is included in the uploaded  attachment:

```

apt list --installed
dmesg
hwinfo
lsb_release -a
lsmod
lspci
lspci -v
lsusb
lsusb -v
uname -a

```

So far, I noticed here is no detected device such as **/dev/video*** and seemingly no driver loaded as well (lsmod/lspci/lsusb). Any help would be appreciated!

---

### Post by slickymaster on 2020-04-06
Thread closed. Duplicate [here]("https://ubuntuforums.org/showthread.php?t=2440143")

Please don't start duplicate threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by slickymaster on 2020-04-06
Reopening this one since a fellow staff member already closed the original thread.

---

### Post by Autodave on 2020-04-06
I have a couple Dells here that required nothing to make the cam work.  What version of 'buntu did you install?

---

### Post by owbizi on 2020-04-06
Latest LTS (18.04). I also own a laptop from Dell that just works out of the box - it seems like an alternative driver is required instead of common uvcvideo.

P.s. thanks @slickymaster!

---

