---
title: "[SOLVED] Olympus Digital Voice Recorder VN-4100PC"
date: 2008-08-24
forum: Hardware
---

### Post by tmurry on 2008-08-24
I found a post which directed me to [http://code.google.com/p/odvr/](http://code.google.com/p/odvr/) to get the software required for my device.  So I downloaded the odvr_0.1.4.1_i386.deb file and installed it.  I understand that it is only supposed to work for XHQ and not HQ, LP, and SP.  The problem is that when I use Terminal to run "odvr -l", I get the following error: "Failed to open Olympus device: couldn't claim interface".  Any idea what I should do?

---

### Post by tmurry on 2008-08-27
I found out on the download website that this issue was reported already.  It works when you run it as "sudo odvr -l", etc.  Thanks.

---

### Post by IKhider on 2008-11-06
I am the owner of an Olympus Digital Voice Recorder VN-4100PC. The computer will not recognize the device.

I found a "solved" posting on the issue here
[http://ubuntuforums.org/showthread.php?t=899550](http://ubuntuforums.org/showthread.php?t=899550)

I followed instructions and installed this
[http://code.google.com/p/odvr/](http://code.google.com/p/odvr/)

Neither instructions recognized the device. The computer will not pick up the device. Alternately, I also installed the software via wine, and that did not help either.

So the posting is in error, too vague or I am doing something wrong.

---

### Post by mparker81 on 2009-10-15
back from the dead...   

i ran sudo odvr -l...   it shows my recording...  now what? how do i get it to my pc in a format i can listen to and share?

---

### Post by magicfab on 2010-03-16
You need to use other options to download the files. Thhese are the available options:

>   -h             : This help.
  -v             : Print version.
  -d <folder>    : Download all files in <folder>.
  -e             : Download everything.
  -l             : List all files.
  -x <folder>    : Delete all recordings in <folder>.
  -c             : Delete all recordings.
  -y             : "yes" to all yes/no questions.
  -r             : Reset the DVR. This may fix some sync issues.
  -D             : Enable debug tracing.

So, if -l shows your device & files, this should download the files from it:
sudo odvr -d ~/Music

Would you mind sharing the output of the -l option ? What files are then downloaded ? I'd like to propose this package for inclusion in Ubuntu at some point.

Thank you.

---

### Post by magicfab on 2010-04-12
I have since filed a "needs-packaging"  bug report:
[https://bugs.edge.launchpad.net/debian/+bug/561575](https://bugs.edge.launchpad.net/debian/+bug/561575)

---

### Post by cantillon on 2011-04-12
In this post you will find info on how to run the odvr commands without using sudo:

[http://ubuntuforums.org/showpost.php?p=10668452&postcount=12](http://ubuntuforums.org/showpost.php?p=10668452&postcount=12)

---

