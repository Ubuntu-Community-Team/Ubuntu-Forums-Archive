---
title: "Cannot boot from Ubuntu install CD"
date: 2008-12-21
forum: Hardware
---

### Post by bogdanbiv on 2008-12-21
Hello,

Here is what I did:
I got a new laptop ([HP 6730s ]("http://h10010.www1.hp.com/wwpc/uk/en/sm/WF06a/321957-321957-64295-89315-89315-3687778.html")) with FreeDOS preinstalled. I booted the Ubuntu 8.10 CD normally and I installed Ubuntu in a new partition. That worked fine, with some problems connecting to secure wireless networks. 

So I installed Windows XP to see how wireless would work with that OS, thinking that would help me fix Ubuntu. I did not change the Ubuntu partitions, so if I restore GRUB it should be fine. Trouble is I was counting on using the Ubuntu install CD to fix GRUB after the Windows install.

And now when I boot from the Ubuntu CD, after I choose the language and "Try Ubuntu without any change to your computer", it gets stuck. The boot menu simply hangs on screen doing nothing, or like it is waiting some input, but my keyboard is locked. If I keep pressing keys, after a while it makes a beep on every key - like the keyboard buffer is full. It stops reading the CD and simply hangs around.

I've tried pressing "F6 Other options", and I've added NOACPI option at the end of the line or removing the quiet option:
```
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash noacpi --
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash -- noacpi
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz splash --

```
But there was no change to it's state. Please advise what should I try next, I'm out of ideas!

---

### Post by bogdanbiv on 2008-12-21
If I may answer my own question:
I've just tried Kubuntu live CD and it goes over that step that the Ubuntu CD gets stuck into. Although that is the same CD I had installed Ubuntu first time, I think it might have been damaged since then.

UPDATE: Kubuntu booted fine and now I see the desktop from the live CD.

Rethoric question: does it matter that the Ubuntu live CD is really a CD and Kubuntu is actually written on DVD? That remains to be seen.

---

