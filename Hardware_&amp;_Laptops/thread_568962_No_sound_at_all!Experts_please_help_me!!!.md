---
title: "No sound at all!Experts please help me!!!"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by geofromalimos on 2007-10-06
I have just installed ubuntu Gutsy on my HP laptop but i cannot hear anything...Please help me.When I give the lspci command i get:

00:1b.0 Audio device: Intel Corporation 8201H (ICH8 Family) HD Audio Controller (rev 03)

Anyone has a same issue?Please help i you know!!!

---

### Post by Tavathlon on 2007-10-06
Take a look in this thread. I followed the guide in post #14, and it worked for me.  =)
[http://ubuntuforums.org/showthread.php?t=545318&page=2](http://ubuntuforums.org/showthread.php?t=545318&page=2)

Good luck!

---

### Post by geofromalimos on 2007-10-06
Well thanks but when i enter this command:

sudo apt-get install libncurses5-dev build-essential ncurses-dev gettext linux-headers-`uname -r`

i get

E: couldn't find package linux-headers-uname -r

Any ideas?

---

### Post by Tavathlon on 2007-10-06
Have you opened up third part repositories? I don't know if that's the issue, but that's what I can think of primarily anyway.

---

### Post by geofromalimos on 2007-10-06
Yeap!They are enabled on the Synaptics Package Manager...!

---

### Post by Tavathlon on 2007-10-06
In that case, I don't know about that. You could always try to proceed with the rest of the steps anyway, just make sure to install the rest of the packages in that command. Probably, you already have the latest version of linux-headers anyway.

---

### Post by geofromalimos on 2007-10-06
Everything ok!Thanksssssssssssssssssssss!!!!!!!!!!!!!!!

---

### Post by Tavathlon on 2007-10-07
No problem. I'm just glad that I could help someone, for one's sake.  =)

Just remember that you will have to do that procedure again after every kernel update, as is pointed out later in that thread.

---

