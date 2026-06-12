---
title: "cs : pcmcia_socket0: unable to apply power"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by freddymv on 2005-04-17
Hi everybody,

Im writting here coz I have days looking for some answer on my problem.

I did install hoary on my laptop (Averatec 3200),  everything went ok, but at boot time it is giving me this erros message:

cs : pcmcia_socket0: unable to apply power

At firts time, it did show up a lot of times, after that he continued loading ubuntu as usual .

I think it is important to say that it comes up after it says Configuring Network Interfaces.... 

The same thing happens when ubuntu is shutting down.

Trying to work around this, I found out a funny thing, if i disable both network  cards ( eth0 and wlan0, both built in ) the error message appears just a couple of times... it is less anoying...

More than that... I found out that the same thing happened when i assign to both network cards an static ip......

Conclusion ?, DHCP makes the error message to show up a lot more!

I really dont know what do my network cards have to do with pcmcia... since they are both internal and my pcmcia socket... is empty....

Thanks a lot ! 

Freddy!!

---

### Post by laka on 2005-04-17
Maybe this can help you... [http://pcmcia.arm.linux.org.uk/](http://pcmcia.arm.linux.org.uk/)

---

### Post by freddymv on 2005-04-17
Thanks for your answer.

I think I have read that page a lot of times, i cannot find a solution there.

Is there anyway i can disable network look up at startup ? since the problem seems to happen there...

---

### Post by laka on 2005-04-17
```
man interfaces
``` ;-)

---

### Post by fluideye on 2005-05-17
I am getting the same thing.  However, i'm not using the pcmcia slot so is there away to disable if i don't plan on using it.  The loop gets very annoying when trying to boot.  i've put in a bug but haven't gotten a response yet and the "mystery" as explained here  [http://pcmcia.arm.linux.org.uk/](http://pcmcia.arm.linux.org.uk/) doesn't help too much.

---

### Post by cdean on 2005-05-28
from the PCMCIA site mentioned: A fix which does automatically avoids the use of such areas was merged into 2.6.11

This is for the latter error, which I am getting, as well.  

Perhaps we wait until Ubuntu moves to 2.6.11?  This error does nothing but halt the boot process until killed (okay, so it's a big thing) but with a Ctrl-C, it works fine.

---

### Post by fluideye on 2005-05-28
[QUOTE=cdean]Perhaps we wait until Ubuntu moves to 2.6.11?  This error does nothing but halt the boot process until killed (okay, so it's a big thing) but with a Ctrl-C, it works fine.[/QUOTE]
I suppose waiting for 2.6.11 isn't a bad thing weighing against all the great things about Ubuntu!  Thanks for the Ctrl-C tip, I just rebooted and it took all of a minute (instead of the 2 or 3 before).  However, I noticed it killed my wifi and so I had to go in and manually activate.  So exactly what does that keyboard command do?

---

### Post by cdean on 2005-06-04
I have since compiled my own kernel from 2.6.11 and the situation has not improved.  There's a few topics on this on LinuxQuestions in the Gentoo, Fedora, and Debian forums on this, so it's not an Ubuntu-only problem.

---

### Post by fluideye on 2005-06-04
Thanks for the heads up.  I still have't gotten a resoponse on Ubuntu Bugzilla either.

---

### Post by cdean on 2005-06-19
Strangely, I don't get *any* errors when using Knoppix 3.9 (kernel 2.6.11).  ```
dmesg
``` shows nothing of note.

2.6.12 came out yesterday - I'll compile it tonight and see the difference.

---

### Post by cdean on 2005-06-19
I'm on 2.6.12 now - no difference, still getting the same errors.  I'm gonna investigate how Knoppix 3.9 does things tomorrow night if I have some time.  I don't think it has anything to do with the rt2x00 wireless card drivers, seeing as though they weren't installed when I booted (have to be rebuilt for each kernel version, obv) and I still got those messages.

---

### Post by freddymv on 2005-07-24
Has anyone find any solution to this ?

I haven't. It became less anoying when i did disable dhcp at boot time.

Its a pain coz now i have to enable my lan from gnome when i wanna use it, but it keeps this problem away.

---

### Post by freddymv on 2005-07-24
Take a look here:

[http://www.opensubscriber.com/message/whitebox-users@beau.org/1690778.html](http://www.opensubscriber.com/message/whitebox-users@beau.org/1690778.html)

Can't try it out coz i don have my laptop with me right now.

---

