---
title: "Ubuntu constantly freeze"
date: 2012-11-21
forum: Hardware
---

### Post by completepete on 2012-11-21
Hi all !

I'm very new to this forum. In fact I just registered. But I hope you can help me, and any kind of help will be appreciated 

The whole system randomly freeze. It gets totally stuck, and i can't do anything. Not even ctrl + alt + f1..  and it happes about 4-5 times a day. Other than that everything is working smooth and fine.

This has happened ever since i added "nohz = off" to /etc/default/grub, which I added to get rid of random smaller freezes, where every activity would stop, until I moved the mouse. I tried adding "nolapic_timer" too, with similar results.

Now, the reason I'm posting this in hardware, is because I suspect it could be a hardware related issue. To be exact: a cpu related issue. But i dont know.

specs:
Ubuntu 12.04 32bit

cpu: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
gpu: Nvidia Geforce 8600m gt
ram: 4gb
Thats about what i know.


Thanks in advance - this is really killing me.

---

### Post by ahallubuntu on 2012-11-21
Test the various components to rule them out one at a time.  First test the RAM with Memtest (comes on your Ubuntu CD, should also be in the Grub boot menu if you hold down the shift key at the beginning of boot.  Let Memtest run for a while and see if there are any issues.

The CPU itself is very unlikely to be the problem, but it could be overheating.  If the CPU fan/heat sink is clogged with dust and dirt, it won't be able to cool efficiently.  Also, the fan must be spinning.  If by chance the heat sink is not secured properly to the CPU/motherboard, it may also overheat.

Check the hard drive for S.M.A.R.T. issues.  If the hard drive is failing, that could definitely cause freezes.

Otherwise: could be a bad power supply, problem with your video card, etc.  At worst it's the motherboard, probably not worth fixing.  Try the Ultimate Boot CD to run some other troubleshooting tests.  Ultimate Boot CD contains the excellent Parted Magic Linux distro as well.  (You can test S.M.A.R.T. with Parted Magic easily - start by checking the Attributes and see if any are set.)

If you have no freezes in Parted Magic, and the other tests don't fail, maybe it is not a hardware problem.

---

### Post by completepete on 2012-11-21
Thanks for the input, I'll look at first thing in the morning.

But actually, it might just be more of an incompatibility thing.  As i understand, the small freezes I had before I added "nohz =off" or "nolapic_timer" to the grub config, was because of my acpi not being completely compatible with the new kernel. Whats weird is that, I dont remember having this issue 3-4 years ago.

Anyways. Thanks for the advice. I will try it tomorrow.

---

### Post by completepete on 2012-11-23
I only ran the memory test, and it went through without problems. I didn’t make any of the other tests, since I am pretty sure they are not relevant, (this problem only occurs in Linux).

It seems as though this is a software issue. Something to do with the clocksource..

Thanks for your help. I'll see if I can get more help in the software section.

Btw, even though this is not exactly solved, do I mark this as solved now?

---

### Post by Doug S on 2012-11-23
Is there any information in the logs files that might help? The log files are in /var/log and maybe /var/log/kern.log in particular.
You should not have to use nohz=off, that doesn't make sense to me.

---

### Post by completepete on 2012-11-25
I don&#8217;t know what exactly you are looking for, so I uploaded the whole file to Dropbox.
[http://dl.dropbox.com/u/21107303/kern.log](http://dl.dropbox.com/u/21107303/kern.log)

I'm not completely sure what nohz=off does. All I know is that it prevents Ubuntu from hanging when it idles. I get exactly the same from adding nolapic_timer. But both makes the whole system completely lock up now and then.

---

### Post by Doug S on 2012-11-25
> Now, the reason I'm posting this in hardware, is because I suspect it could be a hardware related issue. To be exact: a cpu related issue. But i dont know.
Yes, I think you are right, I think you have some hardware problem.
 
See also: [http://askubuntu.com/questions/148726/what-is-an-acpi-gpe-storm](http://askubuntu.com/questions/148726/what-is-an-acpi-gpe-storm)
And: [http://askubuntu.com/questions/181058/intel-4965-wifi-using-iwl4965-driver-is-very-unstable](http://askubuntu.com/questions/181058/intel-4965-wifi-using-iwl4965-driver-is-very-unstable)
 
And perhaps try another wireless card.
 
Beyond that, you would need to provide some time references for freezes in order to try to correlate with your huge kern.log file.

---

### Post by completepete on 2012-11-26
I Don't believe its the wireless card. This happens when it's off as well.

Is it fair to say that it might be an incompatibility thing with the kernel and my acpi?
And is there any way to find out?

---

### Post by completepete on 2012-11-27
So I think I confused you all and myself a littlebit. I'll try to explain the problem, step by step.

[LIST]
[*]Hangs at boot screen until I press a key.
[*]Unless I press a key or move the mouse, music lags horribly.
[*]The same happens when I watch video, from any source.
[/LIST]


And that's about it.


the reason i posted about nohz=off, is because adding that to grub solved the problem, although it gave me a new one, so I removed it.


So I looked inside syslog, and found something that might be interesting.

```

Nov 27 19:18:34 plinne-N-A kernel: [    0.336918] intel_idle: does not run on family 6 model 23

Nov  27 19:18:34 plinne-N-A kernel: [    0.233353]  pci0000:00: ACPI _OSC  request failed (AE_NOT_FOUND), returned control mask: 0x1d

Nov 27 19:18:34 plinne-N-A kernel: [    0.160882] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored

```and in kern.log:

```

Nov 27 20:29:33 plinne-N-A kernel: [  650.003306] ACPI: EC: GPE storm detected, transactions will use polling mode

```

I have no idea what these things mean, but it doesn’t look good.

---

### Post by completepete on 2012-11-27
I ran a little test. 
I disabled the wireless card and closed all programs.

Then I opened Rythmbox, and put on some music.

Music started playing at 9:04, and started lagging at 9:05.

I then opened every single log, to see if I could find something reported at 9:05, and found this:

[http://dl.dropbox.com/u/21107303/jockey.log.1](http://dl.dropbox.com/u/21107303/jockey.log.1)

This was all I could find in the logs.

So could it be an issue with the graphics driver?


EDIT: 
I thought i found something and posted a bit too fast.  I started the test at 21:04, it started lagging at 21:05. the log show something that happened at 9:05..

---

### Post by completepete on 2012-12-03
I just installed Ubuntu 12.10 64 bit version, to see if that would help.

Well, it actually enlightened me a bit. A fresh clean install, and I had no problems what so ever. But when I replaced the Nouveau driver with the current Nvidia driver, the problem came back.

Sound and video lags (like a broken record), very often. And while it does so, every system activity stops as well.

The logs show nothing at all!

so it wasnt apic, acpi, wifi or whatever.. it turned out to be the gfx card.

An easy fix would of course be to use the Nouveau driver, but then 3d applications run awfully.

what can I do?

---

### Post by completepete on 2012-12-03
messed around with xorg.conf, and so far no luck.

I added clocksource=jiffies to /etc/defaul/grub.

that worked great. everything runs smooth. Only problem, is that when i run htop, it says that there is  a constant 100% load on one of the cpu cores, while doing nothing.

strange..

should i be alarmed?

---

### Post by completepete on 2012-12-11
I guess my posts haven’t been formed clearly enough for you guys. As a result, most of the posts in this thread was from me, being confused - talking to myself.

I'm thank full for the all the help you gave me, but I at last figured it out myself.

It looks like, what caused the problem was the CPU idle after all.

Nohz=off helped it, but resulted in a complete lockup of the system. nolapic_timer did the same. clocksouce=jiffies fixed the problem, but gave me a 100% load on one cpu core - so it wasn’t a good fix.

Now, I figured out a way to fix the problem completely.

I added "processor.max_cstate=1" to /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash processor.max_cstate=1"
```This fixed it like magic! As I understand, it makes sure the CPU doesn’t reach the lowest idle state.. anyway. I'll mark this solved now.

Thanks.

---

### Post by grey1beard on 2013-01-28
Though this thread has been marked solved, I would like to add the following.
I did a fresh install of 12.04LTS and after a couple of upgrades, I, too, have found that my Toshiba laptop Celeron 2.6Ghz, 32bit running the 3.2.0-36 kernel would only keep running if I moved the mouse at frequent intervals. Some freezes could be restarted by the enter key or even a quick poke of the power button, and I could only boot up using the recovery mode version.
Finding the following on the Thread **"10.10 hangs unless typing or moving cursor", #22 **-

> I had to use the workaround suggested by sfranzyshen to fix booting of Ubuntu 11.04 on a Toshiba nb300 netbook.
The kernel is Linux 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:25:15 UTC 2011 i686 i686 i386 GNU/Linux.
So, in /etc/default/grub I set
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer clocksource=jiffies"
and then run
Code:
sudo update-grub
and restart.

I tried this, an it has worked perfectly since. It now boots OK, and I have just installed a webcam plus software, and all is still working perfectly.
John

---

