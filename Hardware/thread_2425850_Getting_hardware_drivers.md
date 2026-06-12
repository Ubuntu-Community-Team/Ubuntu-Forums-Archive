---
title: "Getting hardware drivers"
date: 2019-08-31
forum: Hardware
---

### Post by likewise2 on 2019-08-31
I am new to linux so please be kind. I am getting a new laptop its in DOS.

I will be provided with drivers like the graphics, sound etc. But they will be for windows, right?

I am planning on installing the latest version of Ubuntu in it. So, my query here is how would I get those drivers?

---

### Post by deadflowr on 2019-08-31
*Thread moved to **Hardware***

If you want to install Ubuntu you don't need any Windows drivers.
Do you know what laptop it is yet, or do you know what specs it has?
Information can help others provide assistance as to how to move forward.

---

### Post by TheFu on 2019-08-31
First, do NOT install the latest version.  Install the current LTS version. That would be 18.04.  Newer isn't always better and currently, 19.04 will only have support until January, so you'll be forced to reinstall in Nov/Dec a new OS anyways.

Please explain: 
>  I am getting a new laptop its in DOS.
Is that some place in the world?

If you pick a good laptop, then the Ubuntu install will discover all the hardware and install the correct drivers automatically.  If you don't pick a linux-friendly laptop, you'll get to learn more about Linux that anyone new should need to know and some of the hardware may not have drivers, so it won't work.  For example, my laptop fingerprint reader doesn't have any Linux drivers and none are planned, so it will never work.  OTOH, everything else has worked perfectly since install and I know how poor using a fingerprint is for security. No big deal.

Linux is different thank Windows.  Getting drivers directly from the vendor is the last place you should look. In general, it should be avoided.

I hope you did your homework BEFORE the purchase so you don't need to learn about compiling kernel drivers.  Just stay away from the bleeding edge hardware, so that can usually be avoided.  Any new hardware under about 12 months old is bleeding edge. Some vendors are known to violate standards, which causes issues for Linux too.  Best to avoid them.

---

### Post by likewise2 on 2019-09-01
I am thinking about buying [FONT=verdana]HP Notebook - 15-da0077tx.

And Can I ask how to know that a laptop is linux friendly or not?[/FONT]

---

### Post by him610 on 2019-09-01
I reviewed the specs at this HP webpaage, [https://store.hp.com/in-en/default/hp-notebook-15-da0077tx-4tt02pa.html]("https://store.hp.com/in-en/default/hp-notebook-15-da0077tx-4tt02pa.html")
It appears like the HP Notebook - 15-da0077tx has fairly standard CPU, GPU, RAM, HDD. There were no detailed specs for the audio, webcam, touchpad, or wireless chips; however, HP installs normally acquired peripherals from its supply chain so you should not (IMHO) experience issues. It appears as if it is a decent system.
Good luck; hope you enjoy your new laptop.

---

### Post by TheFu on 2019-09-01
HP is on my list of always avoid vendors, for a number of reasons. I've come to this over decades of dealing with HP and at installfests with about 1000 people over the years.

Perhaps HP has gotten better and I don't know?
Look for installation instructions for linux distros with that specific model to see any odd problems.
"15-da0077tx ubuntu install"
Looks like people complain about the wifi and bluetooth.

---

### Post by wizlon67 on 2019-09-05
I have just installed Ubuntu on a[SIZE=2] HP Notebook - 15-bw080nd with no problems, everything working fine and no extra drivers needed. The basic build is very similar to the [/SIZE][FONT=verdana]15-da0077tx as far as driver needs, so hopefully you shouldn't need to chase other drivers.[/FONT]

---

