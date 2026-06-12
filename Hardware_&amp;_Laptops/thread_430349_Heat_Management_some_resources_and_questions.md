---
title: "Heat Management: some resources and questions"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by infinitelink on 2007-05-02
Hi, so I originally posted this on [http://ubuntuforums.org/showthread.php?p=2576965#post2576965](http://ubuntuforums.org/showthread.php?p=2576965#post2576965), but that's quite an old thread. 

> **capt_cope said:**
> I've actually downloaded i8kfanutils, then gkrellm and i8krell. As of right now all i get in Gkrellm is a scrolling text where I have i8k placed. it reads: i8Krellm error: missing proc file, see (it restarts, but it's clear it was supposed to go on.) I have'nt played with linux long enough to know how to start trying to fix it. I've re-installed all files related to it but no dice.

I'm in the same situation with an Inspiron XPS PIV running Feisty.

> **wylie348 said:**
> You have to force the module to load and also add it to /etc/modules.conf so that i8k loads on boot.  If you search the forums you WILL find it here - I keep refering to the posts when I do a re-install.
:P

How do you add it to modules.conf?

First, is the pathway to modules.conf just

sudo gedit /etc/modules.conf

or could it be elswhere?

Then, what pathway do we put into modules.conf with what other info?

Also, how do we "force it" (i8k...whatever) to start at boot with the rest of the kernel?

Please explain nicely, non-linux user (usually) here, only learning. Thanks.


Here's a discussion over on suseforums that might help anyone who might help us: [http://www.suseforums.net/lofiversion/index.php/t27436.html]("http://www.suseforums.net/lofiversion/index.php/t27436.html").

I learned from [http://ubuntuforums.org/showthread.php?t=216652&page=2&highlight=i8k]("http://ubuntuforums.org/showthread.php?t=216652&page=2&highlight=i8k") that "i8k.ko" ought to be in kernel/drivers/char, (my path is lib/modules/2.6.20-15-generic/kernel/drivers/char), but it's not: how does one put it there??? Also, where do I find i8k.ko and what do I do once I can see the thing? Unlike at [http://ubuntuforums.org/showthread.php?t=216652&page=2&highlight=i8k]("http://ubuntuforums.org/showthread.php?t=216652&page=2&highlight=i8k") my problem isn't an old bios: I keep it up to date.

I copied the following from the i8kfangui (windows utility) website concerning linux options:

> Fan control for other operating systems

   1. A FreeBSD/NetBSD/OpenBSD version of the original DOS i8kfan command line tool ported to *BSD by Damir Lampa (unfortunately the link is dead)

   2. Since Linux kernel 2.4.15 there's also a kernel module written by Massimo Dal Zotto to get access to the important SMM functions under Linux. The tools to access that driver are here:

      [http://www.debian.org/~dz/i8k/](http://www.debian.org/~dz/i8k/)

   3. Here's a daemon called dellfand specifically for the linux 2.6 kernel series:

      [http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)

Anyone have the expertise or background to tell me how to use these things for getting things working correctly? the dellfand.dinglisch.net thing looks interesting however it's woefully underdeveloped (just read the page and blech!), and not worth the trouble.

I did download the debian i8k tar but it might be out of date (I really don't know) and I don't know what to do with those files anyways...???


**Update**


So I learned a little trick:

infinitelink@GBGAAG:~$ locate i8k.ko

Which gave me:

/lib/modules/2.6.17-10-generic/kernel/drivers/char/i8k.ko


So it's in the 2.6.17-10 area.

First: why does ubuntu have multiple kernels after new ones get installed? Is it safe to remove them? If so why isn't it done automatically!!! err...

Second: so if it's there, does it need to be in my 2.6.20-(and so on) kernel? If so, how do I install i8k to be in the right place?

Third: How do I uninstall this from the wrong place first...

Fourth: If kernels get upgraded, doesn't the system move packges to the new kernel area? 

Fifth: once this is all straightened-out, how do I set it to load at boot in proc/ ????

Thanks.

---

### Post by infinitelink on 2007-05-02
I'd still like answers to those questions, but...here's the solution to the i8k problem people have been having, taken from [http://ubuntuforums.org/showthread.php?t=399913](http://ubuntuforums.org/showthread.php?t=399913)

> **lifeempowered.com said:**
> 


**_FAN CONTROL_**

**1. First install the needed module and app:**

```
sudo apt-get install i8kutils gkrellm gkrellm-i8k
```

**2. Now start the i8k module:**

```
sudo modprobe i8k force=1
```

**3. Next configure your system so the module starts automatically:**

```
sudo gedit /etc/modules
```
*Add the following at the end of the file and save your changes:*
```
i8k force=1
```

**4. Now go to System > Preferences > Sessions > Startup Programs**
*Click New and put a name, such as FanUtil, then in the command section put:* **gkrellm**

**5. Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds, etc. using the GUI.**

***That's about everything!  Keep in mind that this guide was intended for use on a Dell with the same or similar specs as mine.  You may have trouble if your system is different.  Also, before you freak out about Beryl not working, make sure you have clicked on Sessions and selected the XGL session BEFORE you login.  If after that it doesn't work, complain away!  Hope you don't have any trouble though and I'll help as much as I can.***

---

