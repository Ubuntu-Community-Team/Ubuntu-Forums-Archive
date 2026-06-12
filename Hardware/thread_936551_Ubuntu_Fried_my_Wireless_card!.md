---
title: "Ubuntu Fried my Wireless card!"
date: 2008-10-02
forum: Hardware
---

### Post by cballin on 2008-10-02
So i get asked to help test out a new version of ubuntu..

and with no warnings saying this could damage your hardware..

i now have a fried wireless card in my new HP Pavillion Special edition laptop thanks to upgrading to 8.10 intrepid ibex

How do i fix this..

or id like a contact to whom at Ubuntu is going to be replacing my wirelss card

this is crap.

help?

---

### Post by lisati on 2008-10-02
The problem is known about and has been documented: [http://ubuntuforums.org/showthread.php?t=927943](http://ubuntuforums.org/showthread.php?t=927943)

I didn't realise that 8.10 had been officially released yet......

---

### Post by cballin on 2008-10-02
thats nice except that was posted almost a after it was installed..

and doesn't solve my problem that this operating system has ruined my hardware.

---

### Post by cariboo on 2008-10-03
I find it hard to believe that installing software fried your wireless card especially if you didn't download any firmware updates The warning was about Intel e1000e wired network adapters. Have you tried it with any other operating systems?

What is the output of:

```
sudo lshw -C network
```

If you could paste the output of the above command in your next post, maybe we can help you solve your problem.


Jim

---

### Post by p_quarles on 2008-10-03
Provide some substantial evidence that 1) Your hardware is damaged, and 2) The operating system is at fault. Otherwise I'm going to close this thread.

As for "Ubuntu" replacing the card, that will not happen even if it were somehow the case that the OS is at fault. There is no warranty, and the software is provided as is.

---

