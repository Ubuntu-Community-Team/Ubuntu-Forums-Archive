---
title: "Palm IIIC not Synchronizing"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by william_nbg on 2005-11-26
I just got my wife to make the big switch from xp to Ubuntu.

Everything working perfectly and she was really impressed, until she tried to synchronize her Palm IIIc.

I've set up Ubuntu now on 4 or 5 computers with sucess, but have never owned or dealt with a pda.

The computer seems to recognize the device, it just won't synchronize.

Any help, or tips would be highly appreciated.:D

---

### Post by Leif on 2005-11-26
try jpilot, it works fine with my IIIe

---

### Post by matthew on 2005-11-26
Take a look at this and see if it will help you.

[http://ubuntuforums.org/showthread.php?t=77387](http://ubuntuforums.org/showthread.php?t=77387)

---

### Post by william_nbg on 2005-11-26
Thanks a lot for your quick replies.

The Palm IIIc conents via a port, but I connected with a USB adapter, It didn't work the first try with jpilot but I think I'll try going back to a port connection.

---

### Post by william_nbg on 2005-11-28
Alright!!!! We got it synchronized. 

My wife will stay with Ubuntu!! 

We found a great 'How to' on synchronizing pda's:

[http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html")


We had to make the link - 'dev/pilot' back to 'ttys0', change to permission on 'ttyS0' and then it worked like a charm.

---

### Post by matthew on 2005-11-28
Great news! I'm happy it finally worked. Thanks for the link as well. I will make a note of it for future use with ohters who are trying to get theirs to work.

---

