---
title: "Help building a new kernel with suspend2"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by hunterzaiah on 2007-03-21
Hi, I am not really new to linux, but not a power-user by any means either. I have kubuntu edgy installed on my toshiba portege 4010 laptop, and have not been able to get suspend/resume functionality to work properly yet. I have spent quite a bit of time googling and searching forums to try to get this to work. If anyone knows of a clear howto or tutorial somewhere that could show me how to get suspend working without compiling a new kernel, please feel free to point me in that direction. But in my searching, I believe that I will need to build a new kernel with the suspend2 patch added. I have never undertaken a task as big as compiling a whole kernel before and have been somewhat confused by what I have read before. Can anyone tell me clearly, step by step, what I need to do to build a new kernel with suspend2 in it? Is it possible to patch the kernel I am currently using, or do I need to build a new one  from scratch? I am currently using 2.6.17-11-generic. Thanks in advance for any help related to getting suspend working or making a new kernel.
Isaiah

---

### Post by vespo on 2007-03-23
Hi

No need to recompile, everithing needed (acpi) is already in your kernel.

First, are you using klaptop or kpowersave? The former should be default in kubuntu dapper, right?
If so, just remove it and install kpowersave/powersaved and post your results. If you happen to already have kpowersave, remove it and try klaptop.

The two are quite different technology.

---

### Post by hunterzaiah on 2007-04-01
Ok, I have been monkeying around a little bit, and here are my results:
I believe the originally installed power manager was guidance (?), but I tried out both klaptop and kpowersave, with the following results.

klaptop
	Suspend- just starts screensaver

	hibernate - 1. tells me there is no swap device, then starts the screen saver (this is obviously a different issue)
	2. After I mkswap and swapon -a my swap partition, and try to hibernate again, it shuts down all the way. I press the power button, and it goes through a regular boot cycle.

kpowersave
	suspend to ram - suspends just fine, but when I wake it up, the screen appears just as I left it, but frozen. The rest of the system is totally unresponsive too. I don't know if it is just the x server that is stopped, or what, but I can't switch to any of the consoles either. I haven't been able to see if it is still pingable or available to ssh into yet either.

	suspend to disk - gives the following error message:

The resume partition is not set up. Probably you need to add a 'resume=...' option to your kernel command line and reboot. Suspend to disk and resume is not possible without a resume partition, please consult the documentation. You can skip this check by setting SUSPEND2DISK_SKIP_RESUME_CHECK to 'yes' in the sleep configuration file.

Any further advice? thanks for the help so far.

---

### Post by hardyn on 2007-04-01
IIRC suspend 2 is in feisty... and it is being released in 20 days... might be easier to sit tight and do the upgrade.

---

### Post by pelago on 2007-04-03
> **hardyn said:**
> IIRC suspend 2 is in feisty...
I don't think it is, unfortunately.

---

### Post by hardyn on 2007-04-03
you might be right, but i read a commendation somewhere for saybion and ubuntu building it in... oh well...

i did find this though:
[http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/](http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/)

somebody has prebuilt a bunch of kernels.
there is a post on this forum on how it use them.

---

### Post by hunterzaiah on 2007-04-07
> **hardyn said:**
> you might be right, but i read a commendation somewhere for saybion and ubuntu building it in... oh well...

i did find this though:
[http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/](http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/)

somebody has prebuilt a bunch of kernels.
there is a post on this forum on how it use them.

sorry, what forum has the instructions on how to use them?

---

