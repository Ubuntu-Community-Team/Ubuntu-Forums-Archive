---
title: "[SOLVED] Problem with wireless"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by formula on 2007-11-08
Hi All,

I have just installed Ubuntu on my laptop (I had enough of Vista...) 
My main problem is to connect to my wireless network (BTHomehub)

First off all when I click on the network icon on the top right (near the speaker) it says wireless networks but I can see any (and in my building I know that here are at least 5)

so I read some stuff on the net, and someone offer to use lshw command to see if the wireless installed

what I get it this:
network 1 DISABLED
and some other info including the driver model.

My question is how can I enable it?

Thanks,
Assaf

---

### Post by cubeist on 2007-11-08
not all wireless cards are natively supported.  Can you post the output of running lspci in the terminal, that will tell us which card you have.

---

### Post by Mondoman on 2007-11-08
Assaf, what version of Ubuntu are you using? Gutsy?
Also, make sure any ethernet *cable* is unplugged from your laptop before starting it.  Otherwise, the laptop will try to connect via the wired ethernet and ignore the wireless.

---

### Post by formula on 2007-11-08
thanks all,

I found the answer:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

I am so happy that it works!

---

### Post by Mondoman on 2007-11-08
Glad to hear it!  Now that you have solved your problem, please change the thread title to indicate it is  [SOLVED].

---

