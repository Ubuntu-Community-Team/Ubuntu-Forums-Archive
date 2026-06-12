---
title: "What to do with kernel panic?"
date: 2008-05-09
forum: Hardware
---

### Post by pbb on 2008-05-09
Hi all,

I am getting a kernel panic (flashing caps lock and scroll lock lights) after some wireless network usage.

It's not immediate; I can have a few 100 kB of network traffic without problems, but after that the system freezes.

I've tried internet browsing with Firefox, downloading packages with the installer, and remote desktop usage, and the results are the same in all situations.

I've checked the wireless network card (a CNet CWP-854, using a Ralink RT2560/RT61 driver according to lspci), and is properly inserted and secured on the mainboard.

What should I do? I am still not very familiar with Linux. Would it be easiest to just buy another network card? 

Thanks,
Peter

---

### Post by pbb on 2008-05-11
Anybody who can help please? :(

---

### Post by goliatmesh on 2008-05-14
Hi!

Look here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142/comments/6)

or the whole thread:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142)

---

### Post by pbb on 2008-05-14
Boy, that does look very complicated :( How am I going to download packages, when the machine crashes on downloading ????

I have another PC with Windows, but can I download something there and then get it to install on the Ubuntu PC?

Plus, the next comment seems to indicate you also have to install a firmware from RaLink. I've tried reading through the readme included in the download, but don't really understand much of it... :(

I am willing to buy another (cheap) wireless card if that works out of the box. However, the CNet CWP-854 has been listed as working out of the box since 2007-04 while this is definitely not the case. Can anybody suggest a card that is guaranteed to work, or help me with the instructions to fix support for the card I have?

---

### Post by Sef on 2008-05-14
Go into GRUB, (press esc), when booting up, and use the recovery mode.  See if the problem is solved and you can fix your computer.

---

### Post by pbb on 2008-06-10
> **Sef said:**
> Go into GRUB, (press esc), when booting up, and use the recovery mode.  See if the problem is solved and you can fix your computer.

Sef, this doesn't make any sense. I booted with recovery mode, which made no difference. And "you can fix your computer"??? No I can't, that is exactly the reason why I post for help!

Anybody else who can help?

---

### Post by drascus on 2008-06-10
I have a had a few kernal panics in my day. first try using your computer without the wireless card and see if you still get a kernal panic. usually I find that kernal panics have to do with bad memory. try running a live cd and running the memtest. if it comes up with any failed block get new ram. if it won't even run the cd definitely get new ram.

OH I should add if there is a problem with the wirless card itself it woudn't matter how well it was installed it could be a circuitry problem. if you have access try a different wireless card.

---

### Post by pbb on 2008-06-10
With the wireless card inserted in the computer, even with a live wireless network connection, I have no problem. The problems only come when downloading or uploading larger amounts of data.

Here is the official bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142/)

The problem is, I don't understand how to perform the workarounds that are provided in the article. (And anyway, the workarounds don't really seem to work now...)

Would be really great if someone could guide me step-by-step to a solution.

---

### Post by avtolle on 2008-06-10
There is no "solution" at present, just the workarounds at present. I suspect this may well be "fixed" when 8.10 is released in October, but take a look at the workarounds again and see if you are comfortable with any of them. I'd try the new kernel myself, were I you; the instructions given in the bug report seemed fairly clear.

---

### Post by pbb on 2008-06-11
I am sorry, but I really can't understand the workarounds and solutions that are given.

The first part where I am already hitting a wall: how do I download and install stuff when I don't have a working internet connection????

I might be able to download some stuff on my Windows PC (long live Windows!) --if I know where to get it, I wouldn't know where to get the 8.10 kernel-- but then I still don't understand how to install it.

---

