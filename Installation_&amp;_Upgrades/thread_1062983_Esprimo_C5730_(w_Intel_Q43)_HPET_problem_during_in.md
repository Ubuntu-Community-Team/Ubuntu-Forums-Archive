---
title: "Esprimo C5730 (w Intel Q43) HPET problem during installation"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by FoH on 2009-02-07
Hi,
---
I write this so that others can get information on the problem. I'm not entirely sure it can be considered solved. More on that further down.
---
**_The Computer_**
I recently bought a Fujitsu Siemens [Esprimo C5730]("http://www.fujitsu-siemens.com/products/deskbound/personal_computers/esprimo_c_series.html"). It's based on the Intel Q43 chipset and "sports" an Intel GMA 4500 integrated graphics adapter. Being Intel-based I figured it would make a nice Linux computer, and being that I got Windows Vista Business with it I should be able to legally virtualize it. I've been running Linux/Ubuntu for the past year on my Dell XPS M1330, and it has worked great. I've very rarely needed Windows since then, but I like to be on the safe side and virtualization is what I like to use when/if I need Windows for something. It's a small and quiet computer that doesn't consume a lot of power. It seems to be a great desktop computer! As long as Linux runs fine on it ;)

**_The Problem_**
When trying to install Ubuntu 8.10 64-bit version I ran into some problems. At first, I thought this was due to my monitor not being configured correctly. I had some problems with the graphics when using the GParted LiveCD to partition my hard drive (I prefer partitioning before running the installation). I got around that problem by running the Forcevideo command and entering the refresh rates into the xorg.conf file.

So when installing Ubuntu 8.10 64-bit version, the process got as far as to the Detecting Hardware phase, and that's where the screen went black. I thought that maybe some probing is done to get some settings for the monitor, and the new settings is wrong and therefore the screen goes black. Before that phase the screen had perfect resolution (1920x1200) and no problems could be seen. I tried safe graphics mode which got the same result. I then downloaded the text-based installation CD. When using the text-based installation it was obvious that something wasn't right since the screen flickered **very** much (beware seizure-prone ppl!), and the bottom part of the screen actually showed up in the upper area of the monitor, covering some of the text. However, most information was quite readable so I proceeded with the install.

Around the step where the packages are installed (not the base system), the process got killed with an error message saying that there wasn't enough space left. I switched to a console and thought that I'd check the logs for some hints. It turns out that kernel.log, messages and syslog each was about 320MB. With 2GB RAM (some which is used by the graphics card) it's no wonder there wasn't any space left. Upon investigating the logs it turns out they're filled with page upon page of call traces and warnings. Naturally, I didn't go through all 320MBs, but the first pages I quickly browsed through had warnings related to hpet.c. I didn't know what this was, so I spent some time on Google and Wikipedia. HPET stands for [High Precision Event Timer]("http://en.wikipedia.org/wiki/HPET"). It seems others have had the same problem (notably a Fedora 10 user with the same kernel). I also came across a nohpet kernel option, and that turned out to be the solution! :D

**_The Solution_**
The successful installation was made within the full LiveCD environment (which I accidentally started, I was supposed to boot Ubiquity only) and passing the nohpet option to the kernel (which is done by hitting F6 from the installation menu). After the installation I booted into Ubuntu and installed all the updates available. I also tried rebooting again without the nohpet option (with the updated kernel 2.6.27-11) thinking that the problem might have been fixed (I tried searching launchpad for bugs regarding this, but didn't find any that I thought was exactly like this one). I did have one warning and call trace when booting up, but that's the only one so far. No flooded logs any more. :D

So it seems the problem might be solved. I haven't used the system that much yet. I'll update this post with any new information that I get. In the next few days I'll try migrating my Ubuntu installation from the laptop to the desktop computer. :)

_However, I would like to know what some more experienced Linux people think about this:_
* Do I need HPET really?
* Should I perhaps keep the nohpet option for stability/safety purpose?
* Are there any known bugs regarding HPET that I should know about? And if so, am I better off with nohpet until Jaunty perhaps?

_I've attached the error messages to this post. From the top they are:_
No space left error message
ls of /var/logs
Snippet of /var/log/messages

---

### Post by FoH on 2009-02-07
I was just now checking the BIOS to make some changes and noted that there was an option to disable HPET. This would most certainly resolve the problem too.

I have a new problem regarding the C5730 and the monitor. I can't change to a virtual terminal (Ctrl+Alt+Fx), the screen goes blank and tells me that the mode is not optimal. After that it seems I can't get back to the graphic terminal (vt 6, or is it 7... I've tried both anyway). Is there a way to change the screen settings for vt:s? Should I pass an option to the kernel when booting? vga=some mode?

Edit: The monitor is a Samsung 2443BW. It's connected using DVI. It's possible it would behave differently if connected by VGA, but DVI is preferable.

---

### Post by FoH on 2009-02-07
I found the solution. I'm passing vga=858 to the kernel which gives me 1600x1200 and that's good enough, really. Switching to vt:s and back works now. I first entered 893 for 1920x1200 as stated here: [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

It didn't recognize that number as a valid mode. Neither 799 for 1600x1200x32 worked. Startup manager used 799 too. When starting with any invalid mode I got a question asking whether I wanted to continue or change mode, and from the list of modes that was shown I got 858 (ie 35A in hex code).

---

