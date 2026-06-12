---
title: "Looking to build low power Ubuntu home server"
date: 2015-01-18
forum: Hardware
---

### Post by JohnyBeGood on 2015-01-18
[COLOR=#070F14][FONT=Verdana]Hi all,[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]I'm looking to build small but mainly low power as possible system which will serve as home server for file storage (pictures and videos) and some other stuff. I would like to install Ubuntu Desktop on it and maybe run a virtual machine also if possible but not a must.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Closest what I found online is this guide [/FONT][/COLOR][http://lifehacker.com/5938883/how-can-i-build-a-quiet-low-powered-home-file-server](http://lifehacker.com/5938883/how-can-i-build-a-quiet-low-powered-home-file-server)[COLOR=#070F14][FONT=Verdana] but its old and parts are already old.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]For motherboard I would like to stay with Asus since I had bad experience with other manufactures.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]As far as HDs I will start buying as deals come up. I would like case with at least 4 HD bays.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Can someone suggest parts for the system?[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]TIA[/FONT][/COLOR]

---

### Post by weatherman2 on 2015-01-18
Choose the CPU first, then the motherboard.  You may even wind up with a motherboard that comes with the CPU integrated; this is a growing trend that will probably be the norm in a few years.

I'd look at an Intel Celeron "Bay Trail-D" aka "Silvermont" (formerly marketed as "Atom"), a low power multi-core CPU that won't have much performance but will be extremely low power and not need much of a fan.  (For example, a Celeron J1900).  There are quad core versions too (marketed as "Pentium") if you want more performance but still a very low power CPU.

For a simple file server, you don't really need much performance.  But if you want a little more performance, consider a Celeron "Haswell" which is based on (budget version of) the 4th generation Intel CPU with dual core.  (For example, a Celeron G1830.)  That should blow a "Bay Trail-D" out of the water and not really consume much more power at idle (but more power under load for sure).  The whole system will still probably idle under 30 watts.

If you are starting new, I wouldn't plan on needing lots of hard drives myself.  When I think "home server" these days I think small, compact, and quiet.  I think RAID is also overrated for a simple home server, so I wouldn't even make a RAID array.  (RAID does not protect against file system corruption or accidental erasure.)  Instead, I'd get one large internal drive (4TB or even larger if you really have that much data) and then backup with external drives - sync every so often (the rsync tool in Linux is superb for this).  You can keep two backup drives, one always plugged into a USB dock the other offline perhaps in some other location in case of natural disaster.  The only way I'd get a RAID would be if I were making multiple changes to your data every day, and even then a daily backup/sync might suffice.

And I'd go for an SSD for the OS drive.

Stick with integrated graphics on the motherboard; avoid a separate video card unless you are planning to play performance games.

Get an efficient power supply.  Something that is around 400 watts is probably the best price point for a decent reliable power supply but is probably far more than required.

You can save more power by keeping the server in sleep/standby mode but wake it up - even remotely - with Wake-On Lan (WOL) when you need it.

---

### Post by JohnyBeGood on 2015-01-19
Thanks for taking time to reply!

I did lot of searching/reading and I came across this review [http://www.anandtech.com/show/8774/intel-haswell-low-power-cpu-review-core-i3-4130t-i5-4570s-and-i7-4790s-tested](http://www.anandtech.com/show/8774/intel-haswell-low-power-cpu-review-core-i3-4130t-i5-4570s-and-i7-4790s-tested)
which shows Intel i3-4130T would be a great choice.
But I still can't find MB. This site lists what should work [http://openbenchmarking.org/index/Motherboard](http://openbenchmarking.org/index/Motherboard) but when I find something like this ASUS H87I-PLUS [http://www.newegg.com/Product/Product.aspx?Item=N82E16813132032](http://www.newegg.com/Product/Product.aspx?Item=N82E16813132032) with 6 x SATA 6Gb/s ports its not listed there nor on Asus site [http://www.asus.com/websites/global/aboutasus/OS/Linux.pdf](http://www.asus.com/websites/global/aboutasus/OS/Linux.pdf)
More suggestions are welcomed!

---

### Post by weatherman2 on 2015-01-19
There's nothing wrong with that i3 - and it is a lower power version of the i3 - but for a home server running Ubuntu it may be more than you really need.

If you are trying to find out whether this motherboard has Linux support, that Asus list of Linux-qualified motherboards is ancient - hasn't been updated in years.  You won't find any Socket 1150 motherboards on there.  That doesn't mean say the H87i-PLUS won't work in Ubuntu - it means Asus hasn't bothered to test it.  You can read the NewEgg reviews and see if anyone has booted Ubuntu on it - often people do and post that in their reviews.

---

### Post by ian-weisser on 2015-01-19
"Low Power" and "run Ubuntu Desktop" seem like conflicting goals.
A system capable of running Unity (or most desktop environments) requires more CPU, RAM, and power than a mere headless fileserver.

My first experimental server was an older laptop. I installed Ubuntu server on it (console-only, no GUI), and set the power settings to prevent sleep (but turn off the screen) when the lid was closed. Then I closed the lid, put it on a top shelf (plugged in, with airflow), and simply interacted with it via SSH.

---

### Post by Dennis N on 2015-01-19
> **JohnyBeGood said:**
> Thanks for taking time to reply!

I did lot of searching/reading and I came across this review [http://www.anandtech.com/show/8774/intel-haswell-low-power-cpu-review-core-i3-4130t-i5-4570s-and-i7-4790s-tested](http://www.anandtech.com/show/8774/intel-haswell-low-power-cpu-review-core-i3-4130t-i5-4570s-and-i7-4790s-tested)
which shows Intel i3-4130T would be a great choice.
But I still can't find MB. This site lists what should work [http://openbenchmarking.org/index/Motherboard](http://openbenchmarking.org/index/Motherboard) but when I find something like this ASUS H87I-PLUS [http://www.newegg.com/Product/Product.aspx?Item=N82E16813132032](http://www.newegg.com/Product/Product.aspx?Item=N82E16813132032) with 6 x SATA 6Gb/s ports its not listed there nor on Asus site [http://www.asus.com/websites/global/aboutasus/OS/Linux.pdf](http://www.asus.com/websites/global/aboutasus/OS/Linux.pdf)
More suggestions are welcomed!

ASUS H87I-PLUS uses H87 chipset - newer are H97 and Z97 chipsets, also for Haswell processors. Read these articles:
[http://www.pugetsystems.com/labs/articles/What-is-new-in-Z97-and-H97-561/](http://www.pugetsystems.com/labs/articles/What-is-new-in-Z97-and-H97-561/)
[http://www.pugetsystems.com/labs/articles/Z97-vs-H97-What-is-the-Difference-562/](http://www.pugetsystems.com/labs/articles/Z97-vs-H97-What-is-the-Difference-562/)

I used ASUS H97M PLUS for my last build with Intel i3-4150. Everything works. The M is the motherboard size: M = micro atx; I = mini itx.

I used this motherboard:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813132119](http://www.newegg.com/Product/Product.aspx?Item=N82E16813132119)

(Newer version of ASUS H87I-PLUS is ASUS H97I-PLUS. If you want mini-ITX size look for that.)

---

### Post by weatherman2 on 2015-01-19
> **ian-weisser said:**
> "Low Power" and "run Ubuntu Desktop" seem like conflicting goals.

Not really.  I've been doing it for years.

> A system capable of running Unity (or most desktop environments) requires more CPU, RAM, and power than a mere headless fileserver.

But we are probably talking about a new build.  Even the slowest Haswell or Bay Trail-D CPU is more than capable of running Unity.  But one need not run Unity and still use Ubuntu desktop.  I use Ubuntu Fallback (or Flashback on 14.04) with the lowest resource setting.  It works fine as a home server.

Even 2GB of RAM is adequate for a basic home server running Ubuntu Desktop, but I would probably recommend a minimum of 4GB for a new build.

---

### Post by JohnyBeGood on 2015-01-19
> **Dennis N said:**
> ASUS H87I-PLUS uses H87 chipset - newer are H97 and Z97 chipsets, also for Haswell processors. Read these articles:
[http://www.pugetsystems.com/labs/articles/What-is-new-in-Z97-and-H97-561/](http://www.pugetsystems.com/labs/articles/What-is-new-in-Z97-and-H97-561/)
[http://www.pugetsystems.com/labs/articles/Z97-vs-H97-What-is-the-Difference-562/](http://www.pugetsystems.com/labs/articles/Z97-vs-H97-What-is-the-Difference-562/)

I used ASUS H97M PLUS for my last build with Intel i3-4150. Everything works. The M is the motherboard size: M = micro atx; I = mini itx.

I used this motherboard:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813132119](http://www.newegg.com/Product/Product.aspx?Item=N82E16813132119)

(Newer version of ASUS H87I-PLUS is ASUS H97I-PLUS. If you want mini-ITX size look for that.)
I've read both articles and for my purpose I don't think I will see any benefit. Thanks for M & I explanations!
If you used newer MB then H87I-PLUS should work for sure?! I'm referring to all drivers (NIC, Audio, Video etc.) because that's my main concern.

---

### Post by JohnyBeGood on 2015-01-19
> **ian-weisser said:**
> "Low Power" and "run Ubuntu Desktop" seem like conflicting goals.
A system capable of running Unity (or most desktop environments) requires more CPU, RAM, and power than a mere headless fileserver.

My first experimental server was an older laptop. I installed Ubuntu server on it (console-only, no GUI), and set the power settings to prevent sleep (but turn off the screen) when the lid was closed. Then I closed the lid, put it on a top shelf (plugged in, with airflow), and simply interacted with it via SSH.
I think CPU will be able to handle it, what would be minimum of RAM you would suggest?

---

### Post by kevdog on 2015-01-20
I appreciate your endeavor here, however just to simply things -- don't you have access to some old desktop system that could function as your server -- or are you limited by size and space of the device.  I've got about 3 very old 8+ year old desktops -- I think the most expensive was $50, that I have running as my server with a basic Ubuntu install.  They are not truly headless, however most of the interaction with them is through either rsync, ssh, or sshfs.

---

### Post by JohnyBeGood on 2015-01-20
> **kevdog said:**
> I appreciate your endeavor here, however just to simply things -- don't you have access to some old desktop system that could function as your server -- or are you limited by size and space of the device.  I've got about 3 very old 8+ year old desktops -- I think the most expensive was $50, that I have running as my server with a basic Ubuntu install.  They are not truly headless, however most of the interaction with them is through either rsync, ssh, or sshfs.
I do have 2 older Dell boxes and one of them was used for pfSense router and other for Ubuntu. Last year I replaced pfSense box with Shuttle DS437 [http://www.newegg.com/Product/Product.aspx?Item=N82E16856101152](http://www.newegg.com/Product/Product.aspx?Item=N82E16856101152) and boy it was a huge difference in noise, power consumption and heat (especially in the summer). Current Dell can not run a desktop version which I what I want to have and that's why I want to build something that will last me couple of years and I will see difference. I appreciate your suggestion!

---

