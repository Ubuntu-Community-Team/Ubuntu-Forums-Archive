---
title: "Gateway NV53"
date: 2010-06-26
forum: Hardware
---

### Post by lazyrobot47 on 2010-06-26
Here's a whole slew of questions, the first being this:
I installed Ubuntu 10.04 Lucid Lynx, but I'm a musician, and want to use Ubuntu Studio. Is there some way to upgrade to 10.04 Studio without reinstalling? I want to keep the way things are set up on here, but I want the functionality of studio. 

Some other stuff:
I can't figure these things and I've tried.
-Can turn touch pad off, but back not on.
-Can't get audio off internal mic
-Can't access internal webcam.
-Speakers don't shut off when I plug my headphones in.
-I don't think its registering audio input from microphone jack
-Weird recurring white screen skip, its kinda like a little flash. Doesn't affect much just bugs the hell out of me.

I'm semi-new to ubuntu. I installed it on a super old machine with no internet (a toy, some relative got a new machine and gave it to me) but that was around 6.04, I've been trying to implement Ubuntu for ages and now that I have this laptop, it finally happened. I love it, but I do need help with those things. I'm pretty good with computers, and am looking forward to really getting to know this operating system. Which brings me to my next, and final thing. What programming languages should I learn to start writing and editing source code to make this better? I want to learn how to make and release patches and everything, to help the betterment of this awesome community.
Thanks a pinch, all.

PS- Running 64 bit.

---

### Post by mikewhatever on 2010-06-26
> **lazyrobot47 said:**
> Here's a whole slew of questions, the first being this:
I installed Ubuntu 10.04 Lucid Lynx, but I'm a musician, and want to use Ubuntu Studio. Is there some way to upgrade to 10.04 Studio without reinstalling? I want to keep the way things are set up on here, but I want the functionality of studio. 

To 'upgrade' to Ubuntu Studio, install the ubuntustudio-desktop package from the repositories. That package will pull in all the other packages required for Ubuntu Studio.

> Some other stuff:
I can't figure these things and I've tried.
-Can turn touch pad off, but back not on.
-Can't get audio off internal mic
-Can't access internal webcam.
-Speakers don't shut off when I plug my headphones in.
-I don't think its registering audio input from microphone jack
-Weird recurring white screen skip, its kinda like a little flash. Doesn't affect much just bugs the hell out of me.

It would have been helpful to post the hardware specs - CPU, RAM, graphics model, sound card model.
Hint: 'aplay -l' and 'lspci -v' will show a lot of useful info.

> What programming languages should I learn to start writing and editing source code to make this better?
BASH, C, Python. Take your pick.

---

### Post by lazyrobot47 on 2010-06-26
[http://www.bestbuy.com/site/Gateway+-+Laptop+with+AMD+Athlon%26%23153;+II+X2+Dual-Core+Processor+-+Midnight+Blue/9695339.p?id=1218150605281&skuId=9695339&st=nv53&cp=1&lp=1]("http://www.bestbuy.com/site/Gateway+-+Laptop+with+AMD+Athlon%26%23153;+II+X2+Dual-Core+Processor+-+Midnight+Blue/9695339.p?id=1218150605281&skuId=9695339&st=nv53&cp=1&lp=1")

That is exactly what I have.

---

### Post by lazyrobot47 on 2010-06-27
Update/Bump.
Got Ubuntu Studio Running great, No longer having the white rectangle problem, but a new one has arisen. I had Flash running using [this method]("http://blog.mattrudge.net/2010/05/03/installing-flash-player-on-ubuntu-10-04-64-bit/") but now when I tried that method in Chromium it saves the file you have to download to your home directory into my downloads and in Mozilla it doesn't even register that I told it to save the file, or if it did notice there is certainly no evidence of it when i run the terminal commands. Any ideas as to what could be the problem?

---

### Post by lazyrobot47 on 2010-06-27
Got flash working using the updated fix on there. Works great now,

---

### Post by mikewhatever on 2010-06-27
> **lazyrobot47 said:**
> [http://www.bestbuy.com/site/Gateway+-+Laptop+with+AMD+Athlon%26%23153;+II+X2+Dual-Core+Processor+-+Midnight+Blue/9695339.p?id=1218150605281&skuId=9695339&st=nv53&cp=1&lp=1]("http://www.bestbuy.com/site/Gateway+-+Laptop+with+AMD+Athlon%26%23153;+II+X2+Dual-Core+Processor+-+Midnight+Blue/9695339.p?id=1218150605281&skuId=9695339&st=nv53&cp=1&lp=1")

That is exactly what I have.

I get this:
```
Sorry, the page you requested was not found.
```

---

### Post by lazyrobot47 on 2010-06-28
If you go to [www.bestbuy.com](www.bestbuy.com) and search "Gateway NV53" Its the very first result.

---

### Post by mikewhatever on 2010-06-28
Found it. The problem is, there is no touchpad nor graphics card info, the two pieces of hardware you seem to have problems with. Hopefully someone with the same model sees your thread soon enough.

---

### Post by drklunk on 2010-07-30
I have the same laptop and running Ubuntu 10.04 (or .4, cant remember) 64bit. Before 10.04 I was on 9.10 32bit and had all these same problems. There is a review somewhere on the Best Buy website for this laptop in which a guy actually explains how to fix a few of these problems. 

Found it: 
> I have bought this 4 times now. Two for work, one for a friend, and one for myself. Almost all of them have Ubuntu Linux on them and it works great.

Notes for Ubuntu 9.10: This laptop works great with Ubuntu but needs a few minor adjustments:

1) Use the 32-bit version, and once installed, add the 'pae' kernel, headers, and modules from Synaptic (just search for "pae"). This allows full access to all 4GB of RAM.

2) Install the ATI driver, which Ubuntu will tell you to do via "Hardware Drivers" - this will get desktop effects working.

3) Also install "linux-backports-modules-wireless-karmic-generic-pae" to improve wireless signal strength and prevent dropouts

4) add "acer-wmi" to /etc/modules to allow wireless toggle switch to work properly.

5) Touchpad disable button fails to re-enable touchpad, to fix this add kernel boot parameter "i8042.nomux" in /etc/default/grub right after the default boot parameters.
look for this: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
change to this: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux" 

Hopefully that helps with some of your problems my friend

---

