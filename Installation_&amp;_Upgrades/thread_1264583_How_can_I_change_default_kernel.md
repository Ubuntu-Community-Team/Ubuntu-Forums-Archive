---
title: "How can I change default kernel"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by norm.h on 2009-09-12
Have upgraded to Ubuntu 9.04 using Update Manager but can't boot to the
selected kernel 2.6.28-15 generic.
If I select the 2.6.27-14 generic kernel the machine will boot OK.
How can I make this the default kernel?
I tried the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=1050278](http://ubuntuforums.org/showthread.php?t=1050278), but then neither kernel would boot, so I undid the edits.
norm

---

### Post by PmDematagoda on 2009-09-12
What error or problem do you get when trying to boot the Ubuntu 9.04 kernel?

---

### Post by norm.h on 2009-09-12
None. I just get a blank, black screen
norm

---

### Post by PmDematagoda on 2009-09-12
> **norm.h said:**
> None. I just get a blank, black screen
norm

What is your VGA card?

---

### Post by ahbart on 2009-09-12
You can try startupmanager. Install it from synaptic.
In there you can select what kernel you want to use by default.

---

### Post by norm.h on 2009-09-12
Sorry, no way of knowing, but as the machine works OK, as it does now, (I'm using it to  write this), then surely it can't be the card?
Everything is OK with this kernel 2.6.27-1, I simply want to make it the default to avoid having to select it each time I boot up
The machine is about 10 year old Compaq Armada E500 laptop, with 25m memory
norm

---

### Post by drs305 on 2009-09-12
Hopefully you can get the newer kernel problems resolved but if you are currently able to boot from the same partition with an older kernel you can use StartUp-Manager as previously mentioned. Here is a guide on how to install and run SUM:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

SUM will let you set the default kernel, menu timeout and lots of other Grub settings without manually editing menu.lst

---

### Post by PmDematagoda on 2009-09-12
> **norm.h said:**
> Sorry, no way of knowing, but as the machine works OK, as it does now, (I'm using it to  write this), then surely it can't be the card?
Everything is OK with this kernel 2.6.27-1, I simply want to make it the default to avoid having to select it each time I boot up
The machine is about 10 year old Compaq Armada E500 laptop, with 25m memory
norm

Since the card is ATi, it can be the card since the catalyst driver(the kernel module of it) is probably not matching the Ubuntu Jaunty kernel.

Can you post the contents of /etc/X11/xorg.conf?

---

### Post by norm.h on 2009-09-12
> **ahbart said:**
> You can try startupmanager. Install it from synaptic.
In there you can select what kernel you want to use by default.

Many,many thanks.
The simple answers are generally the best!!!
norm

---

