---
title: "What is using 100% of my CPU? Please help, please."
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by chadjohnson on 2008-02-02
My laptop (Acer Aspire 5050) is very, very slow upon resume. htop output tells me that 100% of my CPU is constantly being used (screenshot below), but the most CPU usage that is shown is 9.1%.
[IMG]http://chadjohnson.ath.cx/htop.png[/IMG]

How can I tell what is hogging all of my CPU? PLEASE help...I depend on this computer for work and school.

---

### Post by article on 2008-02-03
It is slow upon resume? Do you mean when it comes out of suspend or hibernation? Does it run okay before it goes into suspend?

Do you find that 100% of your processesor is used as soon as you boot or after it has been running for a while? If it is after it has been running for a while, my first inclination would be to suspect that the processor is overheating. 

What kind of processor do you have?

---

### Post by cdtech on 2008-02-03
Looking at your top, it shows me that your swap is equal to your ram (which should really be twice the amount for hibernate). You still have processes running in your swap partition. It looks as though your lap went into hibernate (using swap).
Just guessing of course.

---

### Post by chadjohnson on 2008-02-03
Thank you for the reply.

CPU usage us at 100% upon resuming from suspension--not sure about resuming from hibernation. It runs perfectly fine before suspending.

Upon first boot, I can open 20 Firefox windows and close them, and the CPU usage will jump back down 100% once they're closed.

---

### Post by chadjohnson on 2008-02-03
Thank you also for your reply.

I resized the swap partition to 2GB, and htop shows that it is in fact being used, but the problem is still present.

---

### Post by chadjohnson on 2008-02-03
Look here--http://www.nycresistor.com/2007/10/23/htop-makes-top-look-bad/--it looks like system processes are causing the spike: "Red is system usage, blue is idle usage, and green is user usage."

Let me add that the harddrive is in constant use while this problem is occurring (the LED is constantly on, and I can hear it spinning). This still happens after running 'hdparm -B 254 /dev/sda' (as well as -B 255).

---

### Post by Yellow Pasque on 2008-02-03
Does System -> Administration -> System Monitor show 100% CPU usage as well?

---

### Post by chadjohnson on 2008-02-03
Strangely, no.

Also, I left it on overnight, and CPU usage jumped down to 21.7%. I can switch to TTY's, but Gnome is completely frozen (except the mouse).

---

### Post by chadjohnson on 2008-02-03
Bump...please help--it's urgent.

---

### Post by chadjohnson on 2008-02-04
Bump.

I've done a lot of Google searching, but nothing helpful has turned up thus far.

---

### Post by dabl on 2008-02-04
If you run ```
top
``` it will show the running processes in descending order of resource usage.  Which process is hogging your resources when you resume?  It looks like "XGL" is taking 9% -- but that doesn't explain a near-lockup.

---

### Post by chadjohnson on 2008-02-04
Both top and htop show that 100% of my CPU is being used, but neither show what process(es) is (are) actually using the processor that much. All it generally shows is a listing similar to what's in the screenshot.

---

### Post by ObjectAgnosia on 2008-02-05
I'm also on the same boat as you.  I'm running a Gateway laptop, 1.6 pentium-m with 2g of ram.  The fan is running at full blast and it's hot around the cpu area.  Programs are running pretty slow as well.  I just installed 7.10 today on a 40g hdd.  Swap is at 1.95 gigs.  Not sure whats going on.  Hope we can figure it out.

---

### Post by stream303 on 2008-02-05
Does anything unusual just keep spitting out errors in your system logs?

I wonder if trying some kernel parameters such as noapic during boot might point to something else that isn't showing up...  just some thoughts I know it can be frustrating...

---

### Post by chadjohnson on 2008-02-05
> **ObjectAgnosia said:**
> I'm also on the same boat as you.  I'm running a Gateway laptop, 1.6 pentium-m with 2g of ram.  The fan is running at full blast and it's hot around the cpu area.  Programs are running pretty slow as well.  I just installed 7.10 today on a 40g hdd.  Swap is at 1.95 gigs.  Not sure whats going on.  Hope we can figure it out.

Finally...someone else who has this or a similar problem. I've taken some notes of things to try or look at when this happens again:
[LIST]
[*]Check for anything unusual in system logs (syslog, dmesg)
[*]```
echo 1 /proc/sys/vm/block_dump
dmesg -c

```
[*]kill vbetool (and if this works, perhaps chmod -x on vbetool to prevent it from running anymore)
[*]See if this problem occurs with xserver-xgl not installed (perhaps Xgl is causing at least part of the problem)
[*]Try running with data=writeback and noatime not in /boot/grub/menu.lst and /etc/fstab
[/LIST]

My kernel parameters are as follows (and what are yours?):
```

ro quiet splash vga=792 rootflags=data=writeback

```

My fstab for the root partition is:
```

/dev/sda1 /  reiserfs notail,data=writeback,noatime          0       1

```

---

### Post by cdtech on 2008-02-07
I found some information about this bug with "trackerd". Seems to still be an issue in Gutsy.

I've just had the same issue plugging in a USB stick which triggered Trackerd and started using 100% of my CPU.  I also had no response from my desktop as well.

Bug #131983 in tracker (Ubuntu):  [[COLOR="DarkRed"]131983[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/131983")

---

### Post by chadjohnson on 2008-02-07
Ah yes, the indexer. Of course. OK, I turned off all indexing...let's see how this works.

I should add, though, that I uninstalled xserver-xgl, turned off the screensaver, and turned off auto-suspend on battery, and I have had no problems for a couple days now. So if at this point the problem is solved, we'll have to narrow things down to tell for sure what the problem is.

---

### Post by chadjohnson on 2008-02-11
Does anything here look unusual?

Looking at /var/log/debug, the harddrive is being accessed a considerable amount each second. Here is part of the log, for just TWO seconds (after running 'echo 1 > /proc/sys/vm/block_dump'):
```

Feb 10 17:35:12 atlas kernel: [10690.688000] gnome-power-man(6225): READ block 775552 on sda2
Feb 10 17:35:12 atlas kernel: [10690.688000] gnome-power-man(6225): READ block 775560 on sda2
Feb 10 17:35:12 atlas kernel: [10690.688000] gnome-power-man(6225): READ block 775568 on sda2
Feb 10 17:35:12 atlas kernel: [10690.688000] gnome-power-man(6225): READ block 775576 on sda2
Feb 10 17:35:12 atlas kernel: [10690.688000] gnome-power-man(6225): READ block 775584 on sda2
Feb 10 17:35:12 atlas kernel: [10690.688000] gnome-power-man(6225): READ block 775592 on sda2
Feb 10 17:35:12 atlas kernel: [10690.688000] gnome-power-man(6225): READ block 775600 on sda2
Feb 10 17:35:12 atlas kernel: [10690.688000] gnome-power-man(6225): READ block 775608 on sda2
Feb 10 17:35:12 atlas kernel: [10690.692000] gnome-power-man(6225): READ block 869312 on sda2
Feb 10 17:35:12 atlas kernel: [10690.692000] gnome-power-man(6225): READ block 869320 on sda2
Feb 10 17:35:12 atlas kernel: [10690.692000] gnome-power-man(6225): READ block 869328 on sda2
Feb 10 17:35:12 atlas kernel: [10690.692000] gnome-power-man(6225): READ block 869336 on sda2
Feb 10 17:35:12 atlas kernel: [10690.692000] gnome-power-man(6225): READ block 869344 on sda2
Feb 10 17:35:12 atlas kernel: [10690.692000] gnome-power-man(6225): READ block 869352 on sda2
Feb 10 17:35:12 atlas kernel: [10690.692000] gnome-power-man(6225): READ block 869360 on sda2
Feb 10 17:35:12 atlas kernel: [10690.692000] gnome-power-man(6225): READ block 869368 on sda2
Feb 10 17:35:12 atlas kernel: [10690.696000] gnome-power-man(6225): READ block 937024 on sda2
Feb 10 17:35:12 atlas kernel: [10690.696000] gnome-power-man(6225): READ block 937032 on sda2
Feb 10 17:35:12 atlas kernel: [10690.696000] gnome-power-man(6225): READ block 937040 on sda2
Feb 10 17:35:12 atlas kernel: [10690.700000] gnome-power-man(6225): READ block 937048 on sda2
Feb 10 17:35:12 atlas kernel: [10690.712000] gnome-power-man(6225): READ block 892032 on sda2
Feb 10 17:35:12 atlas kernel: [10690.712000] gnome-power-man(6225): READ block 892040 on sda2
Feb 10 17:35:12 atlas kernel: [10690.712000] gnome-power-man(6225): READ block 892048 on sda2
Feb 10 17:35:12 atlas kernel: [10690.712000] gnome-power-man(6225): READ block 892056 on sda2
Feb 10 17:35:12 atlas kernel: [10690.712000] gnome-power-man(6225): READ block 892064 on sda2
Feb 10 17:35:12 atlas kernel: [10690.712000] gnome-power-man(6225): READ block 892072 on sda2
Feb 10 17:35:12 atlas kernel: [10690.712000] gnome-power-man(6225): READ block 892080 on sda2
Feb 10 17:35:12 atlas kernel: [10690.712000] gnome-power-man(6225): READ block 892088 on sda2
Feb 10 17:35:12 atlas kernel: [10690.720000] gnome-power-man(6225): READ block 891520 on sda2
Feb 10 17:35:12 atlas kernel: [10690.720000] gnome-power-man(6225): READ block 891528 on sda2
Feb 10 17:35:12 atlas kernel: [10690.720000] gnome-power-man(6225): READ block 891536 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 891544 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 891552 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 891560 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 891568 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 891576 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 775488 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 775496 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 775504 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 775512 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 775528 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 775536 on sda2
Feb 10 17:35:12 atlas kernel: [10690.724000] gnome-power-man(6225): READ block 775544 on sda2
Feb 10 17:35:12 atlas kernel: [10690.736000] gnome-power-man(6225): READ block 891904 on sda2
Feb 10 17:35:12 atlas kernel: [10690.736000] gnome-power-man(6225): READ block 891912 on sda2
Feb 10 17:35:12 atlas kernel: [10690.736000] gnome-power-man(6225): READ block 891920 on sda2
Feb 10 17:35:12 atlas kernel: [10690.736000] gnome-power-man(6225): READ block 891928 on sda2
Feb 10 17:35:12 atlas kernel: [10690.736000] gnome-power-man(6225): READ block 891936 on sda2
Feb 10 17:35:12 atlas kernel: [10690.736000] gnome-power-man(6225): READ block 891944 on sda2
Feb 10 17:35:12 atlas kernel: [10690.736000] gnome-power-man(6225): READ block 891952 on sda2
Feb 10 17:35:12 atlas kernel: [10690.736000] gnome-power-man(6225): READ block 891960 on sda2
Feb 10 17:35:12 atlas kernel: [10690.748000] NetworkManager(4745): READ block 8389256 on sda1
Feb 10 17:35:12 atlas kernel: [10690.760000] NetworkManager(4745): READ block 8497008 on sda1
Feb 10 17:35:12 atlas kernel: [10690.764000] NetworkManager(4745): READ block 8497296 on sda1
Feb 10 17:35:12 atlas kernel: [10690.768000] NetworkManager(4745): READ block 816640 on sda2
Feb 10 17:35:12 atlas kernel: [10690.772000] NetworkManager(4745): READ block 816648 on sda2
Feb 10 17:35:12 atlas kernel: [10690.772000] NetworkManager(4745): READ block 816656 on sda2
Feb 10 17:35:12 atlas kernel: [10690.772000] NetworkManager(4745): READ block 816664 on sda2
Feb 10 17:35:12 atlas kernel: [10690.772000] NetworkManager(4745): READ block 816672 on sda2
Feb 10 17:35:12 atlas kernel: [10690.772000] NetworkManager(4745): READ block 816680 on sda2
Feb 10 17:35:12 atlas kernel: [10690.772000] NetworkManager(4745): READ block 816688 on sda2
Feb 10 17:35:12 atlas kernel: [10690.772000] NetworkManager(4745): READ block 816696 on sda2
Feb 10 17:35:12 atlas kernel: [10690.808000] gnome-panel(6166): READ block 614408 on sda2
Feb 10 17:35:12 atlas kernel: [10690.808000] gnome-panel(6166): READ block 614416 on sda2
Feb 10 17:35:12 atlas kernel: [10690.812000] gnome-panel(6166): READ block 614424 on sda2
Feb 10 17:35:12 atlas kernel: [10690.812000] gnome-panel(6166): READ block 614432 on sda2
Feb 10 17:35:12 atlas kernel: [10690.812000] gnome-panel(6166): READ block 614440 on sda2
Feb 10 17:35:12 atlas kernel: [10690.812000] gnome-panel(6166): READ block 614448 on sda2
Feb 10 17:35:12 atlas kernel: [10690.812000] gnome-panel(6166): READ block 614456 on sda2
Feb 10 17:35:12 atlas kernel: [10690.832000] gnome-panel(6166): READ block 634624 on sda2
Feb 10 17:35:12 atlas kernel: [10690.832000] gnome-panel(6166): READ block 634632 on sda2
Feb 10 17:35:12 atlas kernel: [10690.832000] gnome-panel(6166): READ block 634640 on sda2
Feb 10 17:35:12 atlas kernel: [10690.832000] gnome-panel(6166): READ block 634656 on sda2
Feb 10 17:35:12 atlas kernel: [10690.832000] gnome-panel(6166): READ block 634664 on sda2
Feb 10 17:35:12 atlas kernel: [10690.832000] gnome-panel(6166): READ block 634672 on sda2
Feb 10 17:35:12 atlas kernel: [10690.840000] update-notifier(6198): READ block 328640 on sda2
Feb 10 17:35:12 atlas kernel: [10690.844000] update-notifier(6198): READ block 328648 on sda2
Feb 10 17:35:12 atlas kernel: [10690.844000] update-notifier(6198): READ block 328656 on sda2
Feb 10 17:35:12 atlas kernel: [10690.844000] update-notifier(6198): READ block 328664 on sda2
Feb 10 17:35:12 atlas kernel: [10690.844000] update-notifier(6198): READ block 328672 on sda2
Feb 10 17:35:12 atlas kernel: [10690.844000] update-notifier(6198): READ block 328680 on sda2
Feb 10 17:35:12 atlas kernel: [10690.844000] update-notifier(6198): READ block 328688 on sda2
Feb 10 17:35:12 atlas kernel: [10690.844000] update-notifier(6198): READ block 328696 on sda2
Feb 10 17:35:12 atlas kernel: [10690.872000] Xgl(6137): READ block 938176 on sda2
Feb 10 17:35:12 atlas kernel: [10690.872000] Xgl(6137): READ block 938184 on sda2
Feb 10 17:35:12 atlas kernel: [10690.872000] Xgl(6137): READ block 938192 on sda2
Feb 10 17:35:12 atlas kernel: [10690.872000] Xgl(6137): READ block 938232 on sda2
Feb 10 17:35:12 atlas kernel: [10690.884000] Xgl(6137): READ block 8445992 on sda1
Feb 10 17:35:12 atlas kernel: [10690.884000] Xgl(6137): READ block 8446024 on sda1
Feb 10 17:35:12 atlas kernel: [10690.884000] Xgl(6137): READ block 8446072 on sda1
Feb 10 17:35:12 atlas kernel: [10690.884000] Xgl(6137): READ block 8446120 on sda1
Feb 10 17:35:12 atlas kernel: [10690.884000] Xgl(6137): READ block 8446168 on sda1
Feb 10 17:35:12 atlas kernel: [10690.884000] Xgl(6137): READ block 8446216 on sda1
Feb 10 17:35:12 atlas kernel: [10690.904000] Xgl(6137): READ block 888008 on sda2
Feb 10 17:35:12 atlas kernel: [10690.904000] Xgl(6137): READ block 888016 on sda2
Feb 10 17:35:12 atlas kernel: [10690.904000] Xgl(6137): READ block 888040 on sda2
Feb 10 17:35:12 atlas kernel: [10690.904000] Xgl(6137): READ block 888048 on sda2
Feb 10 17:35:12 atlas kernel: [10690.904000] Xgl(6137): READ block 888056 on sda2
Feb 10 17:35:12 atlas kernel: [10690.920000] Xgl(6137): READ block 896512 on sda2
Feb 10 17:35:12 atlas kernel: [10690.920000] Xgl(6137): READ block 896520 on sda2
Feb 10 17:35:12 atlas kernel: [10690.920000] Xgl(6137): READ block 896528 on sda2
Feb 10 17:35:12 atlas kernel: [10690.920000] Xgl(6137): READ block 896536 on sda2
Feb 10 17:35:12 atlas kernel: [10690.920000] Xgl(6137): READ block 896552 on sda2
Feb 10 17:35:12 atlas kernel: [10690.924000] Xgl(6137): READ block 968968 on sda2
Feb 10 17:35:12 atlas kernel: [10690.940000] Xgl(6137): READ block 895808 on sda2
Feb 10 17:35:12 atlas kernel: [10690.940000] Xgl(6137): READ block 895816 on sda2
Feb 10 17:35:12 atlas kernel: [10690.940000] Xgl(6137): READ block 895832 on sda2
Feb 10 17:35:12 atlas kernel: [10690.940000] Xgl(6137): READ block 895840 on sda2
Feb 10 17:35:12 atlas kernel: [10690.940000] Xgl(6137): READ block 895848 on sda2
Feb 10 17:35:12 atlas kernel: [10690.940000] Xgl(6137): READ block 895856 on sda2
Feb 10 17:35:12 atlas kernel: [10690.940000] Xgl(6137): READ block 895864 on sda2
Feb 10 17:35:12 atlas kernel: [10690.952000] Xgl(6137): READ block 931152 on sda2
Feb 10 17:35:12 atlas kernel: [10690.952000] Xgl(6137): READ block 931160 on sda2
Feb 10 17:35:12 atlas kernel: [10690.952000] Xgl(6137): READ block 931168 on sda2
Feb 10 17:35:12 atlas kernel: [10690.956000] Xgl(6137): READ block 993624 on sda2
Feb 10 17:35:12 atlas kernel: [10690.980000] gtk-window-deco(6188): READ block 908160 on sda2
Feb 10 17:35:12 atlas kernel: [10690.980000] gtk-window-deco(6188): READ block 908168 on sda2
Feb 10 17:35:12 atlas kernel: [10690.984000] gtk-window-deco(6188): READ block 908176 on sda2
Feb 10 17:35:12 atlas kernel: [10690.984000] gtk-window-deco(6188): READ block 908184 on sda2
Feb 10 17:35:12 atlas kernel: [10690.984000] gtk-window-deco(6188): READ block 908192 on sda2
Feb 10 17:35:12 atlas kernel: [10690.984000] gtk-window-deco(6188): READ block 908200 on sda2
Feb 10 17:35:12 atlas kernel: [10690.984000] gtk-window-deco(6188): READ block 908208 on sda2
Feb 10 17:35:12 atlas kernel: [10690.984000] gtk-window-deco(6188): READ block 908216 on sda2
Feb 10 17:35:12 atlas kernel: [10690.988000] gtk-window-deco(6188): READ block 887360 on sda2
Feb 10 17:35:12 atlas kernel: [10690.988000] gtk-window-deco(6188): READ block 887368 on sda2
Feb 10 17:35:12 atlas kernel: [10690.988000] gtk-window-deco(6188): READ block 887376 on sda2
Feb 10 17:35:12 atlas kernel: [10690.988000] gtk-window-deco(6188): READ block 887384 on sda2
Feb 10 17:35:12 atlas kernel: [10690.988000] gtk-window-deco(6188): READ block 887392 on sda2
Feb 10 17:35:12 atlas kernel: [10690.988000] gtk-window-deco(6188): READ block 887400 on sda2
Feb 10 17:35:12 atlas kernel: [10690.988000] gtk-window-deco(6188): READ block 887408 on sda2
Feb 10 17:35:12 atlas kernel: [10690.992000] gtk-window-deco(6188): READ block 887416 on sda2
Feb 10 17:35:12 atlas kernel: [10690.992000] gtk-window-deco(6188): READ block 893376 on sda2
Feb 10 17:35:12 atlas kernel: [10690.992000] gtk-window-deco(6188): READ block 893392 on sda2
Feb 10 17:35:12 atlas kernel: [10690.992000] gtk-window-deco(6188): READ block 893400 on sda2
Feb 10 17:35:12 atlas kernel: [10690.992000] gtk-window-deco(6188): READ block 893416 on sda2
Feb 10 17:35:12 atlas kernel: [10690.992000] gtk-window-deco(6188): READ block 893424 on sda2
Feb 10 17:35:12 atlas kernel: [10690.992000] gtk-window-deco(6188): READ block 893432 on sda2
Feb 10 17:35:12 atlas kernel: [10690.996000] gtk-window-deco(6188): READ block 893440 on sda2
Feb 10 17:35:12 atlas kernel: [10690.996000] gtk-window-deco(6188): READ block 893448 on sda2
Feb 10 17:35:12 atlas kernel: [10690.996000] gtk-window-deco(6188): READ block 886784 on sda2
Feb 10 17:35:12 atlas kernel: [10690.996000] gtk-window-deco(6188): READ block 886792 on sda2
Feb 10 17:35:12 atlas kernel: [10690.996000] gtk-window-deco(6188): READ block 886800 on sda2
Feb 10 17:35:12 atlas kernel: [10690.996000] gtk-window-deco(6188): READ block 886808 on sda2
Feb 10 17:35:12 atlas kernel: [10690.996000] gtk-window-deco(6188): READ block 886816 on sda2
Feb 10 17:35:12 atlas kernel: [10691.000000] gtk-window-deco(6188): READ block 886824 on sda2
Feb 10 17:35:12 atlas kernel: [10691.004000] gtk-window-deco(6188): READ block 896264 on sda2
Feb 10 17:35:12 atlas kernel: [10691.004000] gtk-window-deco(6188): READ block 896272 on sda2
Feb 10 17:35:12 atlas kernel: [10691.004000] gtk-window-deco(6188): READ block 896280 on sda2
Feb 10 17:35:12 atlas kernel: [10691.004000] gtk-window-deco(6188): READ block 896288 on sda2
Feb 10 17:35:12 atlas kernel: [10691.004000] gtk-window-deco(6188): READ block 896296 on sda2
Feb 10 17:35:12 atlas kernel: [10691.008000] gtk-window-deco(6188): READ block 896304 on sda2
Feb 10 17:35:12 atlas kernel: [10691.008000] gtk-window-deco(6188): READ block 896312 on sda2
Feb 10 17:35:12 atlas kernel: [10691.008000] gtk-window-deco(6188): READ block 46927232 on sda1
Feb 10 17:35:12 atlas kernel: [10691.020000] gnome-power-man(6225): READ block 773184 on sda2
Feb 10 17:35:12 atlas kernel: [10691.020000] gnome-power-man(6225): READ block 773192 on sda2
Feb 10 17:35:12 atlas kernel: [10691.020000] gnome-power-man(6225): READ block 773200 on sda2
Feb 10 17:35:12 atlas kernel: [10691.020000] gnome-power-man(6225): READ block 773208 on sda2
Feb 10 17:35:12 atlas kernel: [10691.020000] gnome-power-man(6225): READ block 773216 on sda2
Feb 10 17:35:12 atlas kernel: [10691.020000] gnome-power-man(6225): READ block 773224 on sda2
Feb 10 17:35:12 atlas kernel: [10691.020000] gnome-power-man(6225): READ block 773232 on sda2
Feb 10 17:35:12 atlas kernel: [10691.020000] gnome-power-man(6225): READ block 773240 on sda2
Feb 10 17:35:12 atlas kernel: [10691.024000] gnome-power-man(6225): READ block 497016 on sda1
Feb 10 17:35:12 atlas kernel: [10691.040000] gnome-power-man(6225): READ block 496656 on sda1
Feb 10 17:35:12 atlas kernel: [10691.040000] gnome-power-man(6225): READ block 496672 on sda1
Feb 10 17:35:12 atlas kernel: [10691.040000] gnome-power-man(6225): READ block 496728 on sda1
Feb 10 17:35:12 atlas kernel: [10691.040000] gnome-power-man(6225): READ block 496752 on sda1
Feb 10 17:35:12 atlas kernel: [10691.048000] gnome-power-man(6225): READ block 890560 on sda2
Feb 10 17:35:12 atlas kernel: [10691.048000] gnome-power-man(6225): READ block 890568 on sda2
Feb 10 17:35:12 atlas kernel: [10691.048000] gnome-power-man(6225): READ block 890576 on sda2
Feb 10 17:35:12 atlas kernel: [10691.048000] gnome-power-man(6225): READ block 890584 on sda2
Feb 10 17:35:12 atlas kernel: [10691.048000] gnome-power-man(6225): READ block 890592 on sda2
Feb 10 17:35:12 atlas kernel: [10691.048000] gnome-power-man(6225): READ block 890600 on sda2
Feb 10 17:35:12 atlas kernel: [10691.048000] gnome-power-man(6225): READ block 890608 on sda2
Feb 10 17:35:12 atlas kernel: [10691.048000] gnome-power-man(6225): READ block 890616 on sda2
Feb 10 17:35:12 atlas kernel: [10691.064000] gnome-panel(6166): READ block 897696 on sda2
Feb 10 17:35:12 atlas kernel: [10691.064000] gnome-panel(6166): READ block 897720 on sda2
Feb 10 17:35:12 atlas kernel: [10691.076000] gnome-panel(6166): READ block 967688 on sda2
Feb 10 17:35:12 atlas kernel: [10691.088000] gnome-panel(6166): READ block 614352 on sda2
Feb 10 17:35:12 atlas kernel: [10691.096000] gnome-panel(6166): READ block 613184 on sda2
Feb 10 17:35:12 atlas kernel: [10691.096000] gnome-panel(6166): READ block 613192 on sda2
Feb 10 17:35:12 atlas kernel: [10691.096000] gnome-panel(6166): READ block 613216 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 613120 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 613136 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 613152 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 613160 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 613168 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 613176 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 614208 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 614216 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 614224 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 614232 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 614240 on sda2
Feb 10 17:35:12 atlas kernel: [10691.104000] gnome-panel(6166): READ block 614264 on sda2
Feb 10 17:35:12 atlas kernel: [10691.116000] gnome-panel(6166): READ block 885696 on sda2
Feb 10 17:35:12 atlas kernel: [10691.116000] gnome-panel(6166): READ block 885720 on sda2
Feb 10 17:35:12 atlas kernel: [10691.116000] gnome-panel(6166): READ block 885744 on sda2
Feb 10 17:35:12 atlas kernel: [10691.124000] gnome-panel(6166): READ block 906368 on sda2
Feb 10 17:35:12 atlas kernel: [10691.124000] gnome-panel(6166): READ block 906376 on sda2
Feb 10 17:35:12 atlas kernel: [10691.124000] gnome-panel(6166): READ block 906384 on sda2
Feb 10 17:35:12 atlas kernel: [10691.124000] gnome-panel(6166): READ block 906392 on sda2
Feb 10 17:35:12 atlas kernel: [10691.124000] gnome-panel(6166): READ block 906400 on sda2
Feb 10 17:35:12 atlas kernel: [10691.124000] gnome-panel(6166): READ block 906408 on sda2
Feb 10 17:35:12 atlas kernel: [10691.124000] gnome-panel(6166): READ block 906416 on sda2
Feb 10 17:35:12 atlas kernel: [10691.124000] gnome-panel(6166): READ block 906424 on sda2
Feb 10 17:35:12 atlas kernel: [10691.128000] gnome-panel(6166): READ block 613504 on sda2
Feb 10 17:35:12 atlas kernel: [10691.128000] gnome-panel(6166): READ block 613512 on sda2
Feb 10 17:35:12 atlas kernel: [10691.128000] gnome-panel(6166): READ block 613520 on sda2
Feb 10 17:35:12 atlas kernel: [10691.128000] gnome-panel(6166): READ block 613528 on sda2
Feb 10 17:35:12 atlas kernel: [10691.128000] gnome-panel(6166): READ block 613536 on sda2
Feb 10 17:35:12 atlas kernel: [10691.128000] gnome-panel(6166): READ block 613544 on sda2
Feb 10 17:35:12 atlas kernel: [10691.132000] gnome-panel(6166): READ block 613552 on sda2
Feb 10 17:35:12 atlas kernel: [10691.132000] gnome-panel(6166): READ block 613560 on sda2
Feb 10 17:35:12 atlas kernel: [10691.132000] gnome-panel(6166): READ block 895936 on sda2
Feb 10 17:35:12 atlas kernel: [10691.132000] gnome-panel(6166): READ block 895952 on sda2
Feb 10 17:35:12 atlas kernel: [10691.132000] gnome-panel(6166): READ block 895960 on sda2
Feb 10 17:35:12 atlas kernel: [10691.132000] gnome-panel(6166): READ block 895984 on sda2
Feb 10 17:35:12 atlas kernel: [10691.132000] gnome-panel(6166): READ block 895992 on sda2
Feb 10 17:35:12 atlas kernel: [10691.140000] gnome-panel(6166): READ block 618944 on sda2
Feb 10 17:35:12 atlas kernel: [10691.140000] gnome-panel(6166): READ block 618952 on sda2
Feb 10 17:35:12 atlas kernel: [10691.140000] gnome-panel(6166): READ block 618960 on sda2
Feb 10 17:35:12 atlas kernel: [10691.140000] gnome-panel(6166): READ block 618968 on sda2
Feb 10 17:35:12 atlas kernel: [10691.140000] gnome-panel(6166): READ block 618984 on sda2
Feb 10 17:35:12 atlas kernel: [10691.140000] gnome-panel(6166): READ block 618992 on sda2
Feb 10 17:35:12 atlas kernel: [10691.140000] gnome-panel(6166): READ block 619000 on sda2
Feb 10 17:35:12 atlas kernel: [10691.148000] gnome-panel(6166): READ block 908096 on sda2
Feb 10 17:35:12 atlas kernel: [10691.148000] gnome-panel(6166): READ block 908104 on sda2
Feb 10 17:35:12 atlas kernel: [10691.148000] gnome-panel(6166): READ block 908112 on sda2
Feb 10 17:35:12 atlas kernel: [10691.148000] gnome-panel(6166): READ block 908120 on sda2
Feb 10 17:35:12 atlas kernel: [10691.148000] gnome-panel(6166): READ block 908128 on sda2
Feb 10 17:35:12 atlas kernel: [10691.148000] gnome-panel(6166): READ block 908136 on sda2
Feb 10 17:35:12 atlas kernel: [10691.148000] gnome-panel(6166): READ block 908144 on sda2
Feb 10 17:35:12 atlas kernel: [10691.148000] gnome-panel(6166): READ block 908152 on sda2
Feb 10 17:35:12 atlas kernel: [10691.172000] update-notifier(6198): READ block 931800 on sda2
Feb 10 17:35:12 atlas kernel: [10691.172000] update-notifier(6198): READ block 931808 on sda2
Feb 10 17:35:12 atlas kernel: [10691.172000] update-notifier(6198): READ block 931816 on sda2
Feb 10 17:35:12 atlas kernel: [10691.172000] update-notifier(6198): READ block 931832 on sda2
Feb 10 17:35:12 atlas kernel: [10691.184000] update-notifier(6198): READ block 887008 on sda2
Feb 10 17:35:12 atlas kernel: [10691.196000] update-notifier(6198): READ block 869056 on sda2
Feb 10 17:35:12 atlas kernel: [10691.196000] update-notifier(6198): READ block 869112 on sda2
Feb 10 17:35:12 atlas kernel: [10691.204000] update-notifier(6198): READ block 919744 on sda2
Feb 10 17:35:12 atlas kernel: [10691.204000] update-notifier(6198): READ block 919752 on sda2
Feb 10 17:35:12 atlas kernel: [10691.208000] update-notifier(6198): READ block 919768 on sda2
Feb 10 17:35:12 atlas kernel: [10691.208000] update-notifier(6198): READ block 919776 on sda2
Feb 10 17:35:12 atlas kernel: [10691.208000] update-notifier(6198): READ block 919800 on sda2
Feb 10 17:35:12 atlas kernel: [10691.220000] python(6205): READ block 777408 on sda2
Feb 10 17:35:12 atlas kernel: [10691.220000] python(6205): READ block 777416 on sda2
Feb 10 17:35:12 atlas kernel: [10691.220000] python(6205): READ block 777424 on sda2
Feb 10 17:35:12 atlas kernel: [10691.220000] python(6205): READ block 777432 on sda2
Feb 10 17:35:12 atlas kernel: [10691.220000] python(6205): READ block 777440 on sda2
Feb 10 17:35:12 atlas kernel: [10691.220000] python(6205): READ block 777448 on sda2
Feb 10 17:35:12 atlas kernel: [10691.220000] python(6205): READ block 777456 on sda2
Feb 10 17:35:12 atlas kernel: [10691.220000] python(6205): READ block 777464 on sda2
Feb 10 17:35:12 atlas kernel: [10691.220000] update-notifier(6198): READ block 929512 on sda2
Feb 10 17:35:12 atlas kernel: [10691.248000] gtk-window-deco(6188): READ block 46981672 on sda1
Feb 10 17:35:12 atlas kernel: [10691.300000] Xgl(6137): READ block 993664 on sda2
Feb 10 17:35:12 atlas kernel: [10691.300000] Xgl(6137): READ block 993704 on sda2
Feb 10 17:35:12 atlas kernel: [10691.300000] Xgl(6137): READ block 993744 on sda2
Feb 10 17:35:12 atlas kernel: [10691.304000] Xgl(6137): READ block 1007080 on sda2
Feb 10 17:35:12 atlas kernel: [10691.320000] gnome-screensav(6236): READ block 696640 on sda2
Feb 10 17:35:12 atlas kernel: [10691.320000] gnome-screensav(6236): READ block 696648 on sda2
Feb 10 17:35:12 atlas kernel: [10691.320000] gnome-screensav(6236): READ block 696656 on sda2
Feb 10 17:35:12 atlas kernel: [10691.320000] gnome-screensav(6236): READ block 696664 on sda2
Feb 10 17:35:12 atlas kernel: [10691.320000] gnome-screensav(6236): READ block 696672 on sda2
Feb 10 17:35:12 atlas kernel: [10691.320000] gnome-screensav(6236): READ block 696680 on sda2
Feb 10 17:35:12 atlas kernel: [10691.320000] gnome-screensav(6236): READ block 696688 on sda2
Feb 10 17:35:12 atlas kernel: [10691.320000] gnome-screensav(6236): READ block 696696 on sda2
Feb 10 17:35:12 atlas kernel: [10691.320000] compiz.real(6189): READ block 46924280 on sda1
Feb 10 17:35:12 atlas kernel: [10691.324000] gnome-power-man(6225): READ block 890496 on sda2
Feb 10 17:35:12 atlas kernel: [10691.324000] gnome-power-man(6225): READ block 890504 on sda2
Feb 10 17:35:12 atlas kernel: [10691.324000] gnome-power-man(6225): READ block 890512 on sda2
Feb 10 17:35:12 atlas kernel: [10691.324000] gnome-power-man(6225): READ block 890520 on sda2
Feb 10 17:35:12 atlas kernel: [10691.324000] gnome-power-man(6225): READ block 890528 on sda2
Feb 10 17:35:12 atlas kernel: [10691.324000] gnome-power-man(6225): READ block 890536 on sda2
Feb 10 17:35:12 atlas kernel: [10691.324000] gnome-power-man(6225): READ block 890544 on sda2
Feb 10 17:35:12 atlas kernel: [10691.324000] gnome-power-man(6225): READ block 890552 on sda2
Feb 10 17:35:12 atlas kernel: [10691.328000] gnome-power-man(6225): READ block 774528 on sda2
Feb 10 17:35:12 atlas kernel: [10691.328000] gnome-power-man(6225): READ block 774536 on sda2
Feb 10 17:35:12 atlas kernel: [10691.328000] gnome-power-man(6225): READ block 774544 on sda2
Feb 10 17:35:12 atlas kernel: [10691.328000] gnome-power-man(6225): READ block 774552 on sda2
Feb 10 17:35:12 atlas kernel: [10691.328000] gnome-power-man(6225): READ block 774560 on sda2
Feb 10 17:35:12 atlas kernel: [10691.328000] gnome-power-man(6225): READ block 774568 on sda2
Feb 10 17:35:12 atlas kernel: [10691.328000] gnome-power-man(6225): READ block 774576 on sda2
Feb 10 17:35:12 atlas kernel: [10691.328000] gnome-power-man(6225): READ block 774584 on sda2
Feb 10 17:35:12 atlas kernel: [10691.336000] gnome-terminal(13629): READ block 667296 on sda1
Feb 10 17:35:12 atlas kernel: [10691.356000] gnome-terminal(13629): READ block 663648 on sda1
Feb 10 17:35:12 atlas kernel: [10691.356000] gnome-terminal(13629): READ block 663688 on sda1
Feb 10 17:35:12 atlas kernel: [10691.356000] gnome-terminal(13629): READ block 663824 on sda1
Feb 10 17:35:12 atlas kernel: [10691.360000] gnome-terminal(13629): READ block 664576 on sda1
Feb 10 17:35:12 atlas kernel: [10691.360000] gnome-terminal(13629): READ block 664672 on sda1
Feb 10 17:35:12 atlas kernel: [10691.360000] gnome-terminal(13629): READ block 664696 on sda1
Feb 10 17:35:12 atlas kernel: [10691.360000] gnome-terminal(13629): READ block 664720 on sda1
Feb 10 17:35:12 atlas kernel: [10691.372000] gnome-terminal(13629): READ block 947304 on sda2
Feb 10 17:35:12 atlas kernel: [10691.384000] gnome-terminal(13629): READ block 940416 on sda2
Feb 10 17:35:12 atlas kernel: [10691.384000] gnome-terminal(13629): READ block 940424 on sda2
Feb 10 17:35:12 atlas kernel: [10691.384000] gnome-terminal(13629): READ block 940432 on sda2
Feb 10 17:35:12 atlas kernel: [10691.384000] gnome-terminal(13629): READ block 940440 on sda2
Feb 10 17:35:12 atlas kernel: [10691.384000] gnome-terminal(13629): READ block 940448 on sda2
Feb 10 17:35:12 atlas kernel: [10691.384000] gnome-terminal(13629): READ block 940456 on sda2
Feb 10 17:35:12 atlas kernel: [10691.384000] gnome-terminal(13629): READ block 940464 on sda2
Feb 10 17:35:12 atlas kernel: [10691.384000] gnome-terminal(13629): READ block 940472 on sda2
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 20464728 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 20464712 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810328 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810336 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810344 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810624 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810632 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810640 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810648 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810656 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810664 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810672 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810680 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810688 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810696 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810704 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810712 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810720 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810728 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810736 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810584 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810592 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810600 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810608 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810616 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810896 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810904 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810912 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810920 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810928 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810936 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810944 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810952 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810960 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810968 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810976 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810984 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810464 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810472 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810480 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810760 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810768 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810776 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810784 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810792 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810800 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810808 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810816 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810824 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810832 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810840 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810848 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810856 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810864 on sda1
Feb 10 17:35:12 atlas kernel: [10691.404000] pdflush(13679): WRITE block 64810872 on sda1
Feb 10 17:35:12 atlas kernel: [10691.412000] syslogd(4653): dirtied inode 5709 (syslog) on sda1
Feb 10 17:35:12 atlas kernel: [10691.412000] syslogd(4653): dirtied inode 6555 (kern.log) on sda1
Feb 10 17:35:12 atlas kernel: [10691.412000] syslogd(4653): dirtied inode 33710 (debug) on sda1
Feb 10 17:35:12 atlas kernel: [10691.440000] gnome-panel(6166): READ block 896608 on sda2
Feb 10 17:35:12 atlas kernel: [10691.452000] gnome-panel(6166): READ block 895040 on sda2
Feb 10 17:35:12 atlas kernel: [10691.452000] gnome-panel(6166): READ block 895056 on sda2
Feb 10 17:35:12 atlas kernel: [10691.452000] gnome-panel(6166): READ block 895064 on sda2
Feb 10 17:35:12 atlas kernel: [10691.452000] gnome-panel(6166): READ block 895072 on sda2
Feb 10 17:35:12 atlas kernel: [10691.452000] gnome-panel(6166): READ block 895080 on sda2
Feb 10 17:35:12 atlas kernel: [10691.452000] gnome-panel(6166): READ block 895088 on sda2
Feb 10 17:35:12 atlas kernel: [10691.452000] gnome-panel(6166): READ block 895096 on sda2
Feb 10 17:35:12 atlas kernel: [10691.460000] gnome-panel(6166): READ block 614080 on sda2
Feb 10 17:35:12 atlas kernel: [10691.460000] gnome-panel(6166): READ block 614104 on sda2
Feb 10 17:35:12 atlas kernel: [10691.460000] gnome-panel(6166): READ block 614112 on sda2
Feb 10 17:35:12 atlas kernel: [10691.464000] gnome-panel(6166): READ block 614128 on sda2
Feb 10 17:35:12 atlas kernel: [10691.464000] gnome-panel(6166): READ block 614136 on sda2
Feb 10 17:35:12 atlas kernel: [10691.472000] gnome-panel(6166): READ block 541120 on sda2
Feb 10 17:35:12 atlas kernel: [10691.472000] gnome-panel(6166): READ block 541128 on sda2
Feb 10 17:35:12 atlas kernel: [10691.472000] gnome-panel(6166): READ block 541136 on sda2
Feb 10 17:35:12 atlas kernel: [10691.472000] gnome-panel(6166): READ block 541144 on sda2
Feb 10 17:35:12 atlas kernel: [10691.472000] gnome-panel(6166): READ block 541152 on sda2
Feb 10 17:35:12 atlas kernel: [10691.472000] gnome-panel(6166): READ block 541160 on sda2
Feb 10 17:35:12 atlas kernel: [10691.472000] gnome-panel(6166): READ block 541168 on sda2
Feb 10 17:35:12 atlas kernel: [10691.472000] gnome-panel(6166): READ block 541176 on sda2
Feb 10 17:35:12 atlas kernel: [10691.484000] gnome-panel(6166): READ block 896632 on sda2
Feb 10 17:35:12 atlas kernel: [10691.484000] gnome-panel(6166): READ block 894400 on sda2
Feb 10 17:35:12 atlas kernel: [10691.484000] gnome-panel(6166): READ block 894408 on sda2
Feb 10 17:35:12 atlas kernel: [10691.484000] gnome-panel(6166): READ block 894416 on sda2
Feb 10 17:35:12 atlas kernel: [10691.484000] gnome-panel(6166): READ block 894424 on sda2
Feb 10 17:35:12 atlas kernel: [10691.484000] gnome-panel(6166): READ block 894432 on sda2
Feb 10 17:35:12 atlas kernel: [10691.484000] gnome-panel(6166): READ block 894440 on sda2
Feb 10 17:35:12 atlas kernel: [10691.484000] gnome-panel(6166): READ block 894448 on sda2
Feb 10 17:35:12 atlas kernel: [10691.484000] gnome-panel(6166): READ block 894456 on sda2
Feb 10 17:35:12 atlas kernel: [10691.496000] gnome-panel(6166): READ block 631320 on sda2
Feb 10 17:35:12 atlas kernel: [10691.504000] gnome-panel(6166): READ block 866624 on sda2
Feb 10 17:35:12 atlas kernel: [10691.508000] gnome-panel(6166): READ block 866632 on sda2
Feb 10 17:35:12 atlas kernel: [10691.508000] gnome-panel(6166): READ block 866648 on sda2
Feb 10 17:35:12 atlas kernel: [10691.508000] gnome-panel(6166): READ block 866656 on sda2
Feb 10 17:35:12 atlas kernel: [10691.508000] gnome-panel(6166): READ block 866664 on sda2
Feb 10 17:35:12 atlas kernel: [10691.508000] gnome-panel(6166): READ block 866672 on sda2
Feb 10 17:35:12 atlas kernel: [10691.508000] gnome-panel(6166): READ block 866680 on sda2
Feb 10 17:35:12 atlas kernel: [10691.516000] python(6205): READ block 330880 on sda2
Feb 10 17:35:12 atlas kernel: [10691.516000] python(6205): READ block 330888 on sda2
Feb 10 17:35:12 atlas kernel: [10691.516000] python(6205): READ block 330896 on sda2
Feb 10 17:35:12 atlas kernel: [10691.516000] python(6205): READ block 330904 on sda2
Feb 10 17:35:12 atlas kernel: [10691.516000] python(6205): READ block 330912 on sda2
Feb 10 17:35:12 atlas kernel: [10691.516000] python(6205): READ block 330920 on sda2
Feb 10 17:35:12 atlas kernel: [10691.516000] python(6205): READ block 330928 on sda2
Feb 10 17:35:12 atlas kernel: [10691.516000] python(6205): READ block 330936 on sda2
Feb 10 17:35:12 atlas kernel: [10691.524000] python(6205): READ block 776128 on sda2
Feb 10 17:35:12 atlas kernel: [10691.524000] python(6205): READ block 776136 on sda2
Feb 10 17:35:12 atlas kernel: [10691.524000] python(6205): READ block 776144 on sda2
Feb 10 17:35:12 atlas kernel: [10691.524000] python(6205): READ block 776152 on sda2
Feb 10 17:35:12 atlas kernel: [10691.524000] python(6205): READ block 776160 on sda2
Feb 10 17:35:12 atlas kernel: [10691.524000] python(6205): READ block 776168 on sda2
Feb 10 17:35:12 atlas kernel: [10691.524000] python(6205): READ block 776176 on sda2
Feb 10 17:35:12 atlas kernel: [10691.524000] python(6205): READ block 776184 on sda2
Feb 10 17:35:12 atlas kernel: [10691.532000] python(6205): READ block 777600 on sda2
Feb 10 17:35:12 atlas kernel: [10691.532000] python(6205): READ block 777608 on sda2
Feb 10 17:35:12 atlas kernel: [10691.532000] python(6205): READ block 777616 on sda2
Feb 10 17:35:12 atlas kernel: [10691.532000] python(6205): READ block 777624 on sda2
Feb 10 17:35:12 atlas kernel: [10691.532000] python(6205): READ block 777632 on sda2
Feb 10 17:35:12 atlas kernel: [10691.532000] python(6205): READ block 777640 on sda2
Feb 10 17:35:12 atlas kernel: [10691.532000] python(6205): READ block 777648 on sda2
Feb 10 17:35:12 atlas kernel: [10691.532000] python(6205): READ block 777656 on sda2
Feb 10 17:35:12 atlas kernel: [10691.540000] python(6205): READ block 331008 on sda2
Feb 10 17:35:12 atlas kernel: [10691.540000] python(6205): READ block 331016 on sda2
Feb 10 17:35:12 atlas kernel: [10691.540000] python(6205): READ block 331024 on sda2
Feb 10 17:35:12 atlas kernel: [10691.540000] python(6205): READ block 331032 on sda2
Feb 10 17:35:12 atlas kernel: [10691.540000] python(6205): READ block 331040 on sda2
Feb 10 17:35:12 atlas kernel: [10691.540000] python(6205): READ block 331048 on sda2
Feb 10 17:35:12 atlas kernel: [10691.540000] python(6205): READ block 331056 on sda2
Feb 10 17:35:12 atlas kernel: [10691.540000] python(6205): READ block 331064 on sda2
Feb 10 17:35:12 atlas kernel: [10691.548000] python(6205): READ block 775680 on sda2
Feb 10 17:35:12 atlas kernel: [10691.548000] python(6205): READ block 775688 on sda2
Feb 10 17:35:12 atlas kernel: [10691.548000] python(6205): READ block 775696 on sda2
Feb 10 17:35:12 atlas kernel: [10691.548000] python(6205): READ block 775704 on sda2
Feb 10 17:35:12 atlas kernel: [10691.548000] python(6205): READ block 775712 on sda2
Feb 10 17:35:12 atlas kernel: [10691.548000] python(6205): READ block 775720 on sda2
Feb 10 17:35:12 atlas kernel: [10691.548000] python(6205): READ block 775728 on sda2
Feb 10 17:35:12 atlas kernel: [10691.548000] python(6205): READ block 775736 on sda2
Feb 10 17:35:12 atlas kernel: [10691.560000] python(6205): READ block 19922976 on sda1
Feb 10 17:35:12 atlas kernel: [10691.572000] python(6205): READ block 29622344 on sda1
Feb 10 17:35:12 atlas kernel: [10691.584000] python(6205): READ block 29654736 on sda1
Feb 10 17:35:12 atlas kernel: [10691.596000] python(6205): READ block 29652800 on sda1
Feb 10 17:35:12 atlas kernel: [10691.608000] python(6205): READ block 47193984 on sda1
Feb 10 17:35:12 atlas kernel: [10691.616000] python(6205): READ block 47196256 on sda1
Feb 10 17:35:12 atlas kernel: [10691.636000] gnome-terminal(13629): READ block 940224 on sda2
Feb 10 17:35:12 atlas kernel: [10691.636000] gnome-terminal(13629): READ block 940232 on sda2
Feb 10 17:35:12 atlas kernel: [10691.636000] gnome-terminal(13629): READ block 940248 on sda2
Feb 10 17:35:12 atlas kernel: [10691.640000] gnome-terminal(13629): READ block 940280 on sda2
Feb 10 17:35:12 atlas kernel: [10691.640000] Xgl(6137): READ block 8445512 on sda1
Feb 10 17:35:12 atlas kernel: [10691.640000] Xgl(6137): READ block 8445544 on sda1
Feb 10 17:35:12 atlas kernel: [10691.640000] Xgl(6137): READ block 8445560 on sda1
Feb 10 17:35:12 atlas kernel: [10691.640000] Xgl(6137): READ block 8445600 on sda1
Feb 10 17:35:12 atlas kernel: [10691.640000] Xgl(6137): READ block 8445624 on sda1
Feb 10 17:35:12 atlas kernel: [10691.640000] Xgl(6137): READ block 8445648 on sda1
Feb 10 17:35:12 atlas kernel: [10691.640000] Xgl(6137): READ block 8445688 on sda1
Feb 10 17:35:12 atlas kernel: [10691.640000] bash(13693): READ block 279488 on sda1
Feb 10 17:35:12 atlas kernel: [10691.640000] bash(13693): READ block 279608 on sda1
Feb 10 17:35:12 atlas kernel: [10691.640000] bash(13693): READ block 279656 on sda1
Feb 10 17:35:12 atlas kernel: [10691.640000] bash(13693): READ block 279680 on sda1
Feb 10 17:35:12 atlas kernel: [10691.640000] bash(13693): READ block 279728 on sda1
Feb 10 17:35:12 atlas kernel: [10691.656000] compiz.real(6189): READ block 46984024 on sda1
Feb 10 17:35:12 atlas kernel: [10691.656000] compiz.real(6189): READ block 46984072 on sda1
Feb 10 17:35:12 atlas kernel: [10691.656000] compiz.real(6189): READ block 46984096 on sda1
Feb 10 17:35:12 atlas kernel: [10691.656000] compiz.real(6189): READ block 46984200 on sda1
Feb 10 17:35:12 atlas kernel: [10691.656000] compiz.real(6189): READ block 46984232 on sda1
Feb 10 17:35:12 atlas kernel: [10691.676000] gnome-power-man(6225): READ block 26360344 on sda1
Feb 10 17:35:13 atlas kernel: [10691.700000] gnome-power-man(6225): READ block 46988520 on sda1
Feb 10 17:35:13 atlas kernel: [10691.700000] gnome-power-man(6225): READ block 46988600 on sda1
Feb 10 17:35:13 atlas kernel: [10691.700000] gnome-power-man(6225): READ block 46988728 on sda1
Feb 10 17:35:13 atlas kernel: [10691.716000] gnome-panel(6166): READ block 871040 on sda2
Feb 10 17:35:13 atlas kernel: [10691.716000] gnome-panel(6166): READ block 871048 on sda2
Feb 10 17:35:13 atlas kernel: [10691.716000] gnome-panel(6166): READ block 871056 on sda2
Feb 10 17:35:13 atlas kernel: [10691.716000] gnome-panel(6166): READ block 871064 on sda2
Feb 10 17:35:13 atlas kernel: [10691.716000] gnome-panel(6166): READ block 871072 on sda2
Feb 10 17:35:13 atlas kernel: [10691.716000] gnome-panel(6166): READ block 871088 on sda2
Feb 10 17:35:13 atlas kernel: [10691.720000] gnome-panel(6166): READ block 631424 on sda2
Feb 10 17:35:13 atlas kernel: [10691.720000] gnome-panel(6166): READ block 631432 on sda2
Feb 10 17:35:13 atlas kernel: [10691.720000] gnome-panel(6166): READ block 631440 on sda2
Feb 10 17:35:13 atlas kernel: [10691.720000] gnome-panel(6166): READ block 631448 on sda2
Feb 10 17:35:13 atlas kernel: [10691.720000] gnome-panel(6166): READ block 631456 on sda2
Feb 10 17:35:13 atlas kernel: [10691.720000] gnome-panel(6166): READ block 631464 on sda2
Feb 10 17:35:13 atlas kernel: [10691.720000] gnome-panel(6166): READ block 631472 on sda2
Feb 10 17:35:13 atlas kernel: [10691.720000] gnome-panel(6166): READ block 631480 on sda2
Feb 10 17:35:13 atlas kernel: [10691.732000] gnome-panel(6166): READ block 631360 on sda2
Feb 10 17:35:13 atlas kernel: [10691.732000] gnome-panel(6166): READ block 631368 on sda2
Feb 10 17:35:13 atlas kernel: [10691.732000] gnome-panel(6166): READ block 631376 on sda2
Feb 10 17:35:13 atlas kernel: [10691.732000] gnome-panel(6166): READ block 631384 on sda2
Feb 10 17:35:13 atlas kernel: [10691.732000] gnome-panel(6166): READ block 631392 on sda2
Feb 10 17:35:13 atlas kernel: [10691.732000] gnome-panel(6166): READ block 631400 on sda2
Feb 10 17:35:13 atlas kernel: [10691.732000] gnome-panel(6166): READ block 631408 on sda2
Feb 10 17:35:13 atlas kernel: [10691.732000] gnome-panel(6166): READ block 631416 on sda2
Feb 10 17:35:13 atlas kernel: [10691.740000] gnome-panel(6166): READ block 630400 on sda2
Feb 10 17:35:13 atlas kernel: [10691.744000] gnome-panel(6166): READ block 630408 on sda2
Feb 10 17:35:13 atlas kernel: [10691.744000] gnome-panel(6166): READ block 630416 on sda2
Feb 10 17:35:13 atlas kernel: [10691.744000] gnome-panel(6166): READ block 630424 on sda2
Feb 10 17:35:13 atlas kernel: [10691.744000] gnome-panel(6166): READ block 630432 on sda2
Feb 10 17:35:13 atlas kernel: [10691.744000] gnome-panel(6166): READ block 630440 on sda2
Feb 10 17:35:13 atlas kernel: [10691.744000] gnome-panel(6166): READ block 630448 on sda2
Feb 10 17:35:13 atlas kernel: [10691.744000] gnome-panel(6166): READ block 630456 on sda2
Feb 10 17:35:13 atlas kernel: [10691.760000] python(6205): READ block 331520 on sda2
Feb 10 17:35:13 atlas kernel: [10691.760000] python(6205): READ block 331528 on sda2
Feb 10 17:35:13 atlas kernel: [10691.760000] python(6205): READ block 331536 on sda2
Feb 10 17:35:13 atlas kernel: [10691.760000] python(6205): READ block 331544 on sda2
Feb 10 17:35:13 atlas kernel: [10691.760000] python(6205): READ block 331552 on sda2
Feb 10 17:35:13 atlas kernel: [10691.760000] python(6205): READ block 331560 on sda2
Feb 10 17:35:13 atlas kernel: [10691.760000] python(6205): READ block 331568 on sda2
Feb 10 17:35:13 atlas kernel: [10691.760000] python(6205): READ block 331576 on sda2
Feb 10 17:35:13 atlas kernel: [10691.780000] python(6205): READ block 777280 on sda2
Feb 10 17:35:13 atlas kernel: [10691.780000] python(6205): READ block 777288 on sda2
Feb 10 17:35:13 atlas kernel: [10691.780000] python(6205): READ block 777296 on sda2
Feb 10 17:35:13 atlas kernel: [10691.780000] python(6205): READ block 777304 on sda2
Feb 10 17:35:13 atlas kernel: [10691.780000] python(6205): READ block 777312 on sda2
Feb 10 17:35:13 atlas kernel: [10691.780000] python(6205): READ block 777320 on sda2
Feb 10 17:35:13 atlas kernel: [10691.780000] python(6205): READ block 777328 on sda2
Feb 10 17:35:13 atlas kernel: [10691.780000] python(6205): READ block 777336 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 775744 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 775752 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 775760 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 775768 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 775776 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 775784 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 775800 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 777344 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 777352 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 777360 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 777368 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 777376 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 777384 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 777392 on sda2
Feb 10 17:35:13 atlas kernel: [10691.792000] python(6205): READ block 777400 on sda2
Feb 10 17:35:13 atlas kernel: [10691.804000] python(6205): READ block 29622352 on sda1
Feb 10 17:35:13 atlas kernel: [10691.816000] python(6205): READ block 29646504 on sda1
Feb 10 17:35:13 atlas kernel: [10691.828000] gnome-power-man(6225): READ block 403376 on sda1
Feb 10 17:35:13 atlas kernel: [10691.840000] gnome-power-man(6225): READ block 403024 on sda1
Feb 10 17:35:13 atlas kernel: [10691.840000] gnome-power-man(6225): READ block 403088 on sda1
Feb 10 17:35:13 atlas kernel: [10691.840000] gnome-power-man(6225): READ block 403112 on sda1
Feb 10 17:35:13 atlas kernel: [10691.844000] gnome-power-man(6225): READ block 403192 on sda1
Feb 10 17:35:13 atlas kernel: [10691.844000] gnome-power-man(6225): READ block 403224 on sda1
Feb 10 17:35:13 atlas kernel: [10691.852000] Xgl(6137): READ block 8447352 on sda1
Feb 10 17:35:13 atlas kernel: [10691.852000] Xgl(6137): READ block 8447464 on sda1
Feb 10 17:35:13 atlas kernel: [10691.852000] Xgl(6137): READ block 8447480 on sda1
Feb 10 17:35:13 atlas kernel: [10691.852000] Xgl(6137): READ block 8447504 on sda1
Feb 10 17:35:13 atlas kernel: [10691.852000] Xgl(6137): READ block 8447520 on sda1
Feb 10 17:35:13 atlas kernel: [10691.852000] Xgl(6137): READ block 8447568 on sda1
Feb 10 17:35:13 atlas kernel: [10691.872000] gnome-panel(6166): READ block 631232 on sda2
Feb 10 17:35:13 atlas kernel: [10691.872000] gnome-panel(6166): READ block 631240 on sda2
Feb 10 17:35:13 atlas kernel: [10691.872000] gnome-panel(6166): READ block 631248 on sda2
Feb 10 17:35:13 atlas kernel: [10691.872000] gnome-panel(6166): READ block 631256 on sda2
Feb 10 17:35:13 atlas kernel: [10691.872000] gnome-panel(6166): READ block 631264 on sda2
Feb 10 17:35:13 atlas kernel: [10691.884000] gnome-panel(6166): READ block 631328 on sda2
Feb 10 17:35:13 atlas kernel: [10691.884000] gnome-panel(6166): READ block 629824 on sda2
Feb 10 17:35:13 atlas kernel: [10691.884000] gnome-panel(6166): READ block 629832 on sda2
Feb 10 17:35:13 atlas kernel: [10691.884000] gnome-panel(6166): READ block 629840 on sda2
Feb 10 17:35:13 atlas kernel: [10691.884000] gnome-panel(6166): READ block 629848 on sda2
Feb 10 17:35:13 atlas kernel: [10691.884000] gnome-panel(6166): READ block 629856 on sda2
Feb 10 17:35:13 atlas kernel: [10691.884000] gnome-panel(6166): READ block 629864 on sda2
Feb 10 17:35:13 atlas kernel: [10691.884000] gnome-panel(6166): READ block 629872 on sda2
Feb 10 17:35:13 atlas kernel: [10691.884000] gnome-panel(6166): READ block 629880 on sda2
Feb 10 17:35:13 atlas kernel: [10691.888000] gnome-panel(6166): READ block 629760 on sda2
Feb 10 17:35:13 atlas kernel: [10691.888000] gnome-panel(6166): READ block 629768 on sda2
Feb 10 17:35:13 atlas kernel: [10691.888000] gnome-panel(6166): READ block 629776 on sda2
Feb 10 17:35:13 atlas kernel: [10691.888000] gnome-panel(6166): READ block 629784 on sda2
Feb 10 17:35:13 atlas kernel: [10691.888000] gnome-panel(6166): READ block 629792 on sda2
Feb 10 17:35:13 atlas kernel: [10691.888000] gnome-panel(6166): READ block 629800 on sda2
Feb 10 17:35:13 atlas kernel: [10691.888000] gnome-panel(6166): READ block 629816 on sda2
Feb 10 17:35:13 atlas kernel: [10691.892000] sync(13720): WRITE block 33048 on sda1
Feb 10 17:35:13 atlas kernel: [10691.892000] sync(13720): WRITE block 33056 on sda1
Feb 10 17:35:13 atlas kernel: [10691.892000] sync(13720): WRITE block 33064 on sda1
Feb 10 17:35:13 atlas kernel: [10691.892000] sync(13720): WRITE block 33072 on sda1
Feb 10 17:35:13 atlas kernel: [10691.892000] sync(13720): WRITE block 33080 on sda1
Feb 10 17:35:13 atlas kernel: [10691.892000] sync(13720): WRITE block 33088 on sda1
Feb 10 17:35:13 atlas kernel: [10691.892000] sync(13720): WRITE block 33096 on sda1
Feb 10 17:35:13 atlas kernel: [10691.892000] sync(13720): WRITE block 33104 on sda1
Feb 10 17:35:13 atlas kernel: [10691.892000] sync(13720): WRITE block 33112 on sda1
Feb 10 17:35:13 atlas kernel: [10691.892000] sync(13720): WRITE block 33120 on sda1
Feb 10 17:35:13 atlas kernel: [10691.924000] python(6205): READ block 47195528 on sda1
Feb 10 17:35:13 atlas kernel: [10691.940000] python(6205): READ block 47195040 on sda1
Feb 10 17:35:13 atlas kernel: [10691.944000] python(6205): READ block 47195856 on sda1
Feb 10 17:35:13 atlas kernel: [10691.956000] python(6205): READ block 331136 on sda2
Feb 10 17:35:13 atlas kernel: [10691.956000] python(6205): READ block 331144 on sda2
Feb 10 17:35:13 atlas kernel: [10691.956000] python(6205): READ block 331152 on sda2
Feb 10 17:35:13 atlas kernel: [10691.956000] python(6205): READ block 331160 on sda2
Feb 10 17:35:13 atlas kernel: [10691.956000] python(6205): READ block 331168 on sda2
Feb 10 17:35:13 atlas kernel: [10691.956000] python(6205): READ block 331176 on sda2
Feb 10 17:35:13 atlas kernel: [10691.956000] python(6205): READ block 331184 on sda2
Feb 10 17:35:13 atlas kernel: [10691.956000] python(6205): READ block 331192 on sda2
Feb 10 17:35:13 atlas kernel: [10691.960000] java(9056): READ block 878272 on sda2
Feb 10 17:35:13 atlas kernel: [10691.960000] java(9056): READ block 878280 on sda2
Feb 10 17:35:13 atlas kernel: [10691.960000] java(9056): READ block 878288 on sda2
Feb 10 17:35:13 atlas kernel: [10691.960000] java(9056): READ block 878296 on sda2
Feb 10 17:35:13 atlas kernel: [10691.960000] java(9056): READ block 878304 on sda2
Feb 10 17:35:13 atlas kernel: [10691.960000] java(9056): READ block 878312 on sda2
Feb 10 17:35:13 atlas kernel: [10691.960000] java(9056): READ block 878320 on sda2
Feb 10 17:35:13 atlas kernel: [10691.960000] java(9056): READ block 878328 on sda2
Feb 10 17:35:13 atlas kernel: [10691.972000] python(6205): READ block 777216 on sda2
Feb 10 17:35:13 atlas kernel: [10691.972000] python(6205): READ block 777224 on sda2
Feb 10 17:35:13 atlas kernel: [10691.972000] python(6205): READ block 777232 on sda2
Feb 10 17:35:13 atlas kernel: [10691.972000] python(6205): READ block 777240 on sda2
Feb 10 17:35:13 atlas kernel: [10691.972000] python(6205): READ block 777248 on sda2
Feb 10 17:35:13 atlas kernel: [10691.972000] python(6205): READ block 777256 on sda2
Feb 10 17:35:13 atlas kernel: [10691.972000] python(6205): READ block 777264 on sda2
Feb 10 17:35:13 atlas kernel: [10691.972000] python(6205): READ block 777272 on sda2
Feb 10 17:35:13 atlas kernel: [10691.976000] python(6205): READ block 331456 on sda2
Feb 10 17:35:13 atlas kernel: [10691.976000] python(6205): READ block 331464 on sda2
Feb 10 17:35:13 atlas kernel: [10691.976000] python(6205): READ block 331472 on sda2
Feb 10 17:35:13 atlas kernel: [10691.976000] python(6205): READ block 331480 on sda2
Feb 10 17:35:13 atlas kernel: [10691.976000] python(6205): READ block 331488 on sda2
Feb 10 17:35:13 atlas kernel: [10691.976000] python(6205): READ block 331496 on sda2
Feb 10 17:35:13 atlas kernel: [10691.976000] python(6205): READ block 331504 on sda2
Feb 10 17:35:13 atlas kernel: [10691.976000] python(6205): READ block 331512 on sda2
Feb 10 17:35:13 atlas kernel: [10691.996000] Xgl(6137): READ block 957632 on sda2
Feb 10 17:35:13 atlas kernel: [10691.996000] Xgl(6137): READ block 957648 on sda2
Feb 10 17:35:13 atlas kernel: [10691.996000] Xgl(6137): READ block 957656 on sda2
Feb 10 17:35:13 atlas kernel: [10691.996000] Xgl(6137): READ block 957664 on sda2
Feb 10 17:35:13 atlas kernel: [10691.996000] Xgl(6137): READ block 957672 on sda2
Feb 10 17:35:13 atlas kernel: [10691.996000] Xgl(6137): READ block 957680 on sda2
Feb 10 17:35:13 atlas kernel: [10691.996000] Xgl(6137): READ block 957688 on sda2
Feb 10 17:35:13 atlas kernel: [10692.016000] Xgl(6137): READ block 887488 on sda2
Feb 10 17:35:13 atlas kernel: [10692.016000] Xgl(6137): READ block 887496 on sda2
Feb 10 17:35:13 atlas kernel: [10692.016000] Xgl(6137): READ block 887504 on sda2
Feb 10 17:35:13 atlas kernel: [10692.016000] Xgl(6137): READ block 887512 on sda2
Feb 10 17:35:13 atlas kernel: [10692.016000] Xgl(6137): READ block 887520 on sda2
Feb 10 17:35:13 atlas kernel: [10692.016000] Xgl(6137): READ block 887528 on sda2
Feb 10 17:35:13 atlas kernel: [10692.016000] Xgl(6137): READ block 887536 on sda2
Feb 10 17:35:13 atlas kernel: [10692.016000] Xgl(6137): READ block 887544 on sda2
Feb 10 17:35:13 atlas kernel: [10692.032000] gnome-panel(6166): READ block 631352 on sda2
Feb 10 17:35:13 atlas kernel: [10692.032000] gnome-panel(6166): READ block 629696 on sda2
Feb 10 17:35:13 atlas kernel: [10692.032000] gnome-panel(6166): READ block 629704 on sda2
Feb 10 17:35:13 atlas kernel: [10692.032000] gnome-panel(6166): READ block 629712 on sda2
Feb 10 17:35:13 atlas kernel: [10692.032000] gnome-panel(6166): READ block 629720 on sda2
Feb 10 17:35:13 atlas kernel: [10692.032000] gnome-panel(6166): READ block 629728 on sda2
Feb 10 17:35:13 atlas kernel: [10692.032000] gnome-panel(6166): READ block 629736 on sda2
Feb 10 17:35:13 atlas kernel: [10692.036000] gnome-panel(6166): READ block 629744 on sda2
Feb 10 17:35:13 atlas kernel: [10692.036000] gnome-panel(6166): READ block 629752 on sda2
Feb 10 17:35:13 atlas kernel: [10692.036000] gnome-panel(6166): READ block 619904 on sda2
Feb 10 17:35:13 atlas kernel: [10692.036000] gnome-panel(6166): READ block 619912 on sda2
Feb 10 17:35:13 atlas kernel: [10692.036000] gnome-panel(6166): READ block 619920 on sda2
Feb 10 17:35:13 atlas kernel: [10692.036000] gnome-panel(6166): READ block 619928 on sda2
Feb 10 17:35:13 atlas kernel: [10692.036000] gnome-panel(6166): READ block 619936 on sda2
Feb 10 17:35:13 atlas kernel: [10692.036000] gnome-panel(6166): READ block 619944 on sda2
Feb 10 17:35:13 atlas kernel: [10692.036000] gnome-panel(6166): READ block 619952 on sda2
Feb 10 17:35:13 atlas kernel: [10692.036000] gnome-panel(6166): READ block 619960 on sda2
Feb 10 17:35:13 atlas kernel: [10692.040000] gnome-panel(6166): READ block 618880 on sda2
Feb 10 17:35:13 atlas kernel: [10692.040000] gnome-panel(6166): READ block 618888 on sda2
Feb 10 17:35:13 atlas kernel: [10692.040000] gnome-panel(6166): READ block 618896 on sda2
Feb 10 17:35:13 atlas kernel: [10692.040000] gnome-panel(6166): READ block 618904 on sda2
Feb 10 17:35:13 atlas kernel: [10692.040000] gnome-panel(6166): READ block 618912 on sda2
Feb 10 17:35:13 atlas kernel: [10692.040000] gnome-panel(6166): READ block 618920 on sda2
Feb 10 17:35:13 atlas kernel: [10692.048000] gnome-panel(6166): READ block 885576 on sda2
Feb 10 17:35:13 atlas kernel: [10692.048000] gnome-panel(6166): READ block 885584 on sda2
Feb 10 17:35:13 atlas kernel: [10692.048000] gnome-panel(6166): READ block 885592 on sda2
Feb 10 17:35:13 atlas kernel: [10692.048000] gnome-panel(6166): READ block 885608 on sda2
Feb 10 17:35:13 atlas kernel: [10692.048000] gnome-panel(6166): READ block 885616 on sda2
Feb 10 17:35:13 atlas kernel: [10692.056000] gnome-panel(6166): READ block 631344 on sda2
Feb 10 17:35:13 atlas kernel: [10692.072000] gnome-power-man(6225): READ block 94720 on sda2
Feb 10 17:35:13 atlas kernel: [10692.072000] gnome-power-man(6225): READ block 94728 on sda2
Feb 10 17:35:13 atlas kernel: [10692.072000] gnome-power-man(6225): READ block 94736 on sda2
Feb 10 17:35:13 atlas kernel: [10692.072000] gnome-power-man(6225): READ block 94744 on sda2
Feb 10 17:35:13 atlas kernel: [10692.076000] gnome-power-man(6225): READ block 94752 on sda2
Feb 10 17:35:13 atlas kernel: [10692.076000] gnome-power-man(6225): READ block 94760 on sda2
Feb 10 17:35:13 atlas kernel: [10692.076000] gnome-power-man(6225): READ block 94768 on sda2
Feb 10 17:35:13 atlas kernel: [10692.076000] gnome-power-man(6225): READ block 94776 on sda2
Feb 10 17:35:13 atlas kernel: [10692.088000] kswapd0(162): WRITE block 1078304 on sda2
Feb 10 17:35:13 atlas kernel: [10692.088000] kswapd0(162): WRITE block 1078312 on sda2
Feb 10 17:35:13 atlas kernel: [10692.088000] gnome-power-man(6225): READ block 46988264 on sda1
Feb 10 17:35:13 atlas kernel: [10692.088000] gnome-power-man(6225): READ block 46988328 on sda1
Feb 10 17:35:13 atlas kernel: [10692.092000] gnome-power-man(6225): READ block 46988400 on sda1
Feb 10 17:35:13 atlas kernel: [10692.104000] gnome-power-man(6225): READ block 46988776 on sda1
Feb 10 17:35:13 atlas kernel: [10692.108000] gnome-power-man(6225): READ block 869120 on sda2
Feb 10 17:35:13 atlas kernel: [10692.112000] gnome-power-man(6225): READ block 869128 on sda2
Feb 10 17:35:13 atlas kernel: [10692.112000] gnome-power-man(6225): READ block 869136 on sda2
Feb 10 17:35:13 atlas kernel: [10692.112000] gnome-power-man(6225): READ block 869144 on sda2
Feb 10 17:35:13 atlas kernel: [10692.112000] gnome-power-man(6225): READ block 869152 on sda2
Feb 10 17:35:13 atlas kernel: [10692.112000] gnome-power-man(6225): READ block 869160 on sda2
Feb 10 17:35:13 atlas kernel: [10692.112000] gnome-power-man(6225): READ block 869168 on sda2
Feb 10 17:35:13 atlas kernel: [10692.112000] gnome-power-man(6225): READ block 869176 on sda2
Feb 10 17:35:13 atlas kernel: [10692.124000] Xgl(6137): READ block 893824 on sda2
Feb 10 17:35:13 atlas kernel: [10692.124000] Xgl(6137): READ block 893832 on sda2
Feb 10 17:35:13 atlas kernel: [10692.124000] Xgl(6137): READ block 893848 on sda2
Feb 10 17:35:13 atlas kernel: [10692.124000] Xgl(6137): READ block 893856 on sda2
Feb 10 17:35:13 atlas kernel: [10692.124000] Xgl(6137): READ block 893864 on sda2
Feb 10 17:35:13 atlas kernel: [10692.124000] Xgl(6137): READ block 893872 on sda2
Feb 10 17:35:13 atlas kernel: [10692.136000] Xgl(6137): READ block 893312 on sda2
Feb 10 17:35:13 atlas kernel: [10692.136000] Xgl(6137): READ block 893344 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 331072 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 331080 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 331088 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 331096 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 331104 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 331112 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 331120 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 331128 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 776512 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 776520 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 776528 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 776536 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 776544 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 776552 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 776560 on sda2
Feb 10 17:35:13 atlas kernel: [10692.156000] python(6205): READ block 776568 on sda2
Feb 10 17:35:13 atlas kernel: [10692.172000] python(6205): READ block 780864 on sda2
Feb 10 17:35:13 atlas kernel: [10692.172000] python(6205): READ block 780872 on sda2
Feb 10 17:35:13 atlas kernel: [10692.172000] python(6205): READ block 780880 on sda2
Feb 10 17:35:13 atlas kernel: [10692.172000] python(6205): READ block 780888 on sda2
Feb 10 17:35:13 atlas kernel: [10692.172000] python(6205): READ block 780896 on sda2
Feb 10 17:35:13 atlas kernel: [10692.172000] python(6205): READ block 780904 on sda2
Feb 10 17:35:13 atlas kernel: [10692.172000] python(6205): READ block 780912 on sda2
Feb 10 17:35:13 atlas kernel: [10692.172000] python(6205): READ block 780920 on sda2
Feb 10 17:35:13 atlas kernel: [10692.176000] python(6205): READ block 776384 on sda2
Feb 10 17:35:13 atlas kernel: [10692.176000] python(6205): READ block 776392 on sda2
Feb 10 17:35:13 atlas kernel: [10692.176000] python(6205): READ block 776400 on sda2
Feb 10 17:35:13 atlas kernel: [10692.176000] python(6205): READ block 776408 on sda2
Feb 10 17:35:13 atlas kernel: [10692.176000] python(6205): READ block 776416 on sda2
Feb 10 17:35:13 atlas kernel: [10692.176000] python(6205): READ block 776424 on sda2
Feb 10 17:35:13 atlas kernel: [10692.176000] python(6205): READ block 776432 on sda2
Feb 10 17:35:13 atlas kernel: [10692.176000] python(6205): READ block 776440 on sda2
Feb 10 17:35:13 atlas kernel: [10692.180000] python(6205): READ block 331328 on sda2
Feb 10 17:35:13 atlas kernel: [10692.180000] python(6205): READ block 331336 on sda2
Feb 10 17:35:13 atlas kernel: [10692.180000] python(6205): READ block 331344 on sda2
Feb 10 17:35:13 atlas kernel: [10692.180000] python(6205): READ block 331352 on sda2
Feb 10 17:35:13 atlas kernel: [10692.180000] python(6205): READ block 331360 on sda2
Feb 10 17:35:13 atlas kernel: [10692.180000] python(6205): READ block 331368 on sda2
Feb 10 17:35:13 atlas kernel: [10692.180000] python(6205): READ block 331376 on sda2
Feb 10 17:35:13 atlas kernel: [10692.180000] python(6205): READ block 331384 on sda2
Feb 10 17:35:13 atlas kernel: [10692.180000] python(6205): READ block 47196512 on sda1
Feb 10 17:35:13 atlas kernel: [10692.196000] python(6205): READ block 777472 on sda2
Feb 10 17:35:13 atlas kernel: [10692.196000] python(6205): READ block 777480 on sda2
Feb 10 17:35:13 atlas kernel: [10692.196000] python(6205): READ block 777488 on sda2
Feb 10 17:35:13 atlas kernel: [10692.196000] python(6205): READ block 777496 on sda2
Feb 10 17:35:13 atlas kernel: [10692.196000] python(6205): READ block 777504 on sda2
Feb 10 17:35:13 atlas kernel: [10692.196000] python(6205): READ block 777512 on sda2
Feb 10 17:35:13 atlas kernel: [10692.196000] python(6205): READ block 777520 on sda2
Feb 10 17:35:13 atlas kernel: [10692.196000] python(6205): READ block 777528 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 331584 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 331592 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 331600 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 331608 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 331616 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 331624 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 331632 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 331640 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 771264 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 771272 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 771280 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 771288 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 771296 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 771304 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 771312 on sda2
Feb 10 17:35:13 atlas kernel: [10692.208000] python(6205): READ block 771320 on sda2
Feb 10 17:35:13 atlas kernel: [10692.220000] python(6205): READ block 47196752 on sda1
Feb 10 17:35:13 atlas kernel: [10692.232000] python(6205): READ block 331840 on sda2
Feb 10 17:35:13 atlas kernel: [10692.232000] python(6205): READ block 331848 on sda2
Feb 10 17:35:13 atlas kernel: [10692.232000] python(6205): READ block 331856 on sda2
Feb 10 17:35:13 atlas kernel: [10692.232000] python(6205): READ block 331864 on sda2
Feb 10 17:35:13 atlas kernel: [10692.232000] python(6205): READ block 331872 on sda2
Feb 10 17:35:13 atlas kernel: [10692.232000] python(6205): READ block 331880 on sda2
Feb 10 17:35:13 atlas kernel: [10692.232000] python(6205): READ block 331888 on sda2
Feb 10 17:35:13 atlas kernel: [10692.232000] python(6205): READ block 331896 on sda2
Feb 10 17:35:13 atlas kernel: [10692.248000] python(6205): READ block 891328 on sda2
Feb 10 17:35:13 atlas kernel: [10692.248000] python(6205): READ block 891336 on sda2
Feb 10 17:35:13 atlas kernel: [10692.248000] python(6205): READ block 891344 on sda2
Feb 10 17:35:13 atlas kernel: [10692.248000] python(6205): READ block 891352 on sda2
Feb 10 17:35:13 atlas kernel: [10692.248000] python(6205): READ block 891360 on sda2
Feb 10 17:35:13 atlas kernel: [10692.248000] python(6205): READ block 891368 on sda2
Feb 10 17:35:13 atlas kernel: [10692.248000] python(6205): READ block 891376 on sda2
Feb 10 17:35:13 atlas kernel: [10692.248000] python(6205): READ block 891384 on sda2
Feb 10 17:35:13 atlas kernel: [10692.256000] python(6205): READ block 47195384 on sda1
Feb 10 17:35:13 atlas kernel: [10692.272000] gnome-panel(6166): READ block 631336 on sda2
Feb 10 17:35:13 atlas kernel: [10692.284000] gnome-panel(6166): READ block 885504 on sda2
Feb 10 17:35:13 atlas kernel: [10692.284000] gnome-panel(6166): READ block 885512 on sda2
Feb 10 17:35:13 atlas kernel: [10692.284000] gnome-panel(6166): READ block 885520 on sda2
Feb 10 17:35:13 atlas kernel: [10692.284000] gnome-panel(6166): READ block 885528 on sda2
Feb 10 17:35:13 atlas kernel: [10692.284000] gnome-panel(6166): READ block 885552 on sda2
Feb 10 17:35:13 atlas kernel: [10692.296000] gnome-panel(6166): READ block 625088 on sda2
Feb 10 17:35:13 atlas kernel: [10692.296000] gnome-panel(6166): READ block 625096 on sda2
Feb 10 17:35:13 atlas kernel: [10692.296000] gnome-panel(6166): READ block 625104 on sda2
Feb 10 17:35:13 atlas kernel: [10692.296000] gnome-panel(6166): READ block 625112 on sda2
Feb 10 17:35:13 atlas kernel: [10692.300000] gnome-panel(6166): READ block 625120 on sda2
Feb 10 17:35:13 atlas kernel: [10692.300000] gnome-panel(6166): READ block 625128 on sda2
Feb 10 17:35:13 atlas kernel: [10692.300000] gnome-panel(6166): READ block 625136 on sda2
Feb 10 17:35:13 atlas kernel: [10692.300000] gnome-panel(6166): READ block 625144 on sda2
Feb 10 17:35:13 atlas kernel: [10692.312000] gnome-panel(6166): READ block 624256 on sda2
Feb 10 17:35:13 atlas kernel: [10692.312000] gnome-panel(6166): READ block 624264 on sda2
Feb 10 17:35:13 atlas kernel: [10692.312000] gnome-panel(6166): READ block 624272 on sda2
Feb 10 17:35:13 atlas kernel: [10692.312000] gnome-panel(6166): READ block 624280 on sda2
Feb 10 17:35:13 atlas kernel: [10692.312000] gnome-panel(6166): READ block 624288 on sda2
Feb 10 17:35:13 atlas kernel: [10692.312000] gnome-panel(6166): READ block 624296 on sda2
Feb 10 17:35:13 atlas kernel: [10692.312000] gnome-panel(6166): READ block 624304 on sda2
Feb 10 17:35:13 atlas kernel: [10692.312000] gnome-panel(6166): READ block 624312 on sda2
Feb 10 17:35:13 atlas kernel: [10692.320000] gnome-panel(6166): READ block 624576 on sda2
Feb 10 17:35:13 atlas kernel: [10692.320000] gnome-panel(6166): READ block 624584 on sda2
Feb 10 17:35:13 atlas kernel: [10692.320000] gnome-panel(6166): READ block 624592 on sda2
Feb 10 17:35:13 atlas kernel: [10692.320000] gnome-panel(6166): READ block 624600 on sda2
Feb 10 17:35:13 atlas kernel: [10692.320000] gnome-panel(6166): READ block 624608 on sda2
Feb 10 17:35:13 atlas kernel: [10692.324000] gnome-panel(6166): READ block 624616 on sda2
Feb 10 17:35:13 atlas kernel: [10692.324000] gnome-panel(6166): READ block 624624 on sda2
Feb 10 17:35:13 atlas kernel: [10692.324000] gnome-panel(6166): READ block 624632 on sda2
Feb 10 17:35:13 atlas kernel: [10692.324000] gnome-panel(6166): READ block 618752 on sda2
Feb 10 17:35:13 atlas kernel: [10692.324000] gnome-panel(6166): READ block 618760 on sda2
Feb 10 17:35:13 atlas kernel: [10692.324000] gnome-panel(6166): READ block 618768 on sda2
Feb 10 17:35:13 atlas kernel: [10692.324000] gnome-panel(6166): READ block 618776 on sda2
Feb 10 17:35:13 atlas kernel: [10692.324000] gnome-panel(6166): READ block 618784 on sda2
Feb 10 17:35:13 atlas kernel: [10692.324000] gnome-panel(6166): READ block 618792 on sda2
Feb 10 17:35:13 atlas kernel: [10692.324000] gnome-panel(6166): READ block 618800 on sda2
Feb 10 17:35:13 atlas kernel: [10692.324000] gnome-panel(6166): READ block 618808 on sda2
Feb 10 17:35:13 atlas kernel: [10692.336000] gnome-panel(6166): READ block 619848 on sda2
Feb 10 17:35:13 atlas kernel: [10692.336000] gnome-panel(6166): READ block 619856 on sda2
Feb 10 17:35:13 atlas kernel: [10692.336000] gnome-panel(6166): READ block 619880 on sda2
Feb 10 17:35:13 atlas kernel: [10692.336000] gnome-panel(6166): READ block 619888 on sda2
Feb 10 17:35:13 atlas kernel: [10692.336000] gnome-panel(6166): READ block 619896 on sda2
Feb 10 17:35:13 atlas kernel: [10692.348000] gnome-panel(6166): READ block 893192 on sda2
Feb 10 17:35:13 atlas kernel: [10692.348000] gnome-panel(6166): READ block 893200 on sda2
Feb 10 17:35:13 atlas kernel: [10692.348000] gnome-panel(6166): READ block 893208 on sda2
Feb 10 17:35:13 atlas kernel: [10692.348000] gnome-panel(6166): READ block 893216 on sda2
Feb 10 17:35:13 atlas kernel: [10692.348000] gnome-panel(6166): READ block 893232 on sda2
Feb 10 17:35:13 atlas kernel: [10692.348000] gnome-panel(6166): READ block 893240 on sda2
Feb 10 17:35:13 atlas kernel: [10692.356000] gnome-panel(6166): READ block 549760 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] gnome-panel(6166): READ block 549768 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] gnome-panel(6166): READ block 549776 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] gnome-panel(6166): READ block 549784 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] gnome-panel(6166): READ block 549792 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] gnome-panel(6166): READ block 549800 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] gnome-panel(6166): READ block 549808 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] gnome-panel(6166): READ block 549816 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] Xgl(6137): READ block 884672 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] Xgl(6137): READ block 884680 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] Xgl(6137): READ block 884688 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] Xgl(6137): READ block 884704 on sda2
Feb 10 17:35:13 atlas kernel: [10692.360000] Xgl(6137): READ block 884712 on sda2
Feb 10 17:35:13 atlas kernel: [10692.364000] Xgl(6137): READ block 884544 on sda2
Feb 10 17:35:13 atlas kernel: [10692.364000] Xgl(6137): READ block 884552 on sda2
Feb 10 17:35:13 atlas kernel: [10692.364000] Xgl(6137): READ block 884568 on sda2
Feb 10 17:35:13 atlas kernel: [10692.364000] Xgl(6137): READ block 884576 on sda2
Feb 10 17:35:13 atlas kernel: [10692.364000] Xgl(6137): READ block 884592 on sda2
Feb 10 17:35:13 atlas kernel: [10692.364000] Xgl(6137): READ block 884600 on sda2
Feb 10 17:35:13 atlas kernel: [10692.372000] Xgl(6137): READ block 929664 on sda2
Feb 10 17:35:13 atlas kernel: [10692.372000] Xgl(6137): READ block 929680 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] compiz.real(6189): READ block 358688 on sda1
Feb 10 17:35:13 atlas kernel: [10692.376000] Xorg(5777): READ block 26360552 on sda1
Feb 10 17:35:13 atlas kernel: [10692.376000] firefox-bin(9074): READ block 867968 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] firefox-bin(9074): READ block 867976 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] firefox-bin(9074): READ block 867984 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] firefox-bin(9074): READ block 867992 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] firefox-bin(9074): READ block 868000 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] firefox-bin(9074): READ block 868008 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] firefox-bin(9074): READ block 868016 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] firefox-bin(9074): READ block 868024 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] Xgl(6137): READ block 929688 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] Xgl(6137): READ block 929696 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] Xgl(6137): READ block 929704 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] Xgl(6137): READ block 929712 on sda2
Feb 10 17:35:13 atlas kernel: [10692.376000] Xgl(6137): READ block 929720 on sda2
Feb 10 17:35:13 atlas kernel: [10692.380000] nautilus(6168): READ block 832640 on sda2
Feb 10 17:35:13 atlas kernel: [10692.380000] nautilus(6168): READ block 832648 on sda2
Feb 10 17:35:13 atlas kernel: [10692.384000] nautilus(6168): READ block 832656 on sda2
Feb 10 17:35:13 atlas kernel: [10692.384000] nautilus(6168): READ block 832664 on sda2
Feb 10 17:35:13 atlas kernel: [10692.384000] nautilus(6168): READ block 832672 on sda2
Feb 10 17:35:13 atlas kernel: [10692.384000] nautilus(6168): READ block 832680 on sda2
Feb 10 17:35:13 atlas kernel: [10692.384000] nautilus(6168): READ block 832688 on sda2
Feb 10 17:35:13 atlas kernel: [10692.384000] nautilus(6168): READ block 832696 on sda2
Feb 10 17:35:13 atlas kernel: [10692.388000] Xgl(6137): READ block 930368 on sda2
Feb 10 17:35:13 atlas kernel: [10692.388000] Xgl(6137): READ block 930376 on sda2
Feb 10 17:35:13 atlas kernel: [10692.388000] Xgl(6137): READ block 930424 on sda2
Feb 10 17:35:13 atlas kernel: [10692.408000] Xgl(6137): READ block 861376 on sda2
Feb 10 17:35:13 atlas kernel: [10692.408000] Xgl(6137): READ block 861384 on sda2
Feb 10 17:35:13 atlas kernel: [10692.408000] Xgl(6137): READ block 861392 on sda2
Feb 10 17:35:13 atlas kernel: [10692.408000] Xgl(6137): READ block 861400 on sda2
Feb 10 17:35:13 atlas kernel: [10692.408000] Xgl(6137): READ block 861408 on sda2
Feb 10 17:35:13 atlas kernel: [10692.408000] Xgl(6137): READ block 861416 on sda2
Feb 10 17:35:13 atlas kernel: [10692.408000] Xgl(6137): READ block 861424 on sda2
Feb 10 17:35:13 atlas kernel: [10692.408000] Xgl(6137): READ block 861432 on sda2
Feb 10 17:35:13 atlas kernel: [10692.420000] Xgl(6137): READ block 861632 on sda2
Feb 10 17:35:13 atlas kernel: [10692.420000] Xgl(6137): READ block 861640 on sda2
Feb 10 17:35:13 atlas kernel: [10692.420000] Xgl(6137): READ block 861648 on sda2
Feb 10 17:35:13 atlas kernel: [10692.420000] Xgl(6137): READ block 861656 on sda2
Feb 10 17:35:13 atlas kernel: [10692.420000] Xgl(6137): READ block 861664 on sda2
Feb 10 17:35:13 atlas kernel: [10692.420000] Xgl(6137): READ block 861672 on sda2
Feb 10 17:35:13 atlas kernel: [10692.420000] Xgl(6137): READ block 861680 on sda2
Feb 10 17:35:13 atlas kernel: [10692.420000] Xgl(6137): READ block 861688 on sda2
Feb 10 17:35:13 atlas kernel: [10692.424000] Xgl(6137): READ block 861568 on sda2
Feb 10 17:35:13 atlas kernel: [10692.424000] Xgl(6137): READ block 861576 on sda2
Feb 10 17:35:13 atlas kernel: [10692.424000] Xgl(6137): READ block 861584 on sda2
Feb 10 17:35:13 atlas kernel: [10692.424000] Xgl(6137): READ block 861592 on sda2
Feb 10 17:35:13 atlas kernel: [10692.424000] Xgl(6137): READ block 861600 on sda2
Feb 10 17:35:13 atlas kernel: [10692.424000] Xgl(6137): READ block 861608 on sda2
Feb 10 17:35:13 atlas kernel: [10692.428000] Xgl(6137): READ block 861616 on sda2
Feb 10 17:35:13 atlas kernel: [10692.428000] Xgl(6137): READ block 861624 on sda2
Feb 10 17:35:13 atlas kernel: [10692.428000] Xgl(6137): READ block 861504 on sda2
Feb 10 17:35:13 atlas kernel: [10692.428000] Xgl(6137): READ block 861512 on sda2
Feb 10 17:35:13 atlas kernel: [10692.428000] Xgl(6137): READ block 861520 on sda2
Feb 10 17:35:13 atlas kernel: [10692.428000] Xgl(6137): READ block 861528 on sda2
Feb 10 17:35:13 atlas kernel: [10692.428000] Xgl(6137): READ block 861536 on sda2
Feb 10 17:35:13 atlas kernel: [10692.428000] Xgl(6137): READ block 861544 on sda2
Feb 10 17:35:13 atlas kernel: [10692.428000] Xgl(6137): READ block 861552 on sda2
Feb 10 17:35:13 atlas kernel: [10692.428000] Xgl(6137): READ block 861560 on sda2
Feb 10 17:35:13 atlas kernel: [10692.432000] Xgl(6137): READ block 861440 on sda2
Feb 10 17:35:13 atlas kernel: [10692.432000] Xgl(6137): READ block 861448 on sda2
Feb 10 17:35:13 atlas kernel: [10692.432000] Xgl(6137): READ block 861456 on sda2
Feb 10 17:35:13 atlas kernel: [10692.432000] Xgl(6137): READ block 861464 on sda2
Feb 10 17:35:13 atlas kernel: [10692.432000] Xgl(6137): READ block 861472 on sda2
Feb 10 17:35:13 atlas kernel: [10692.432000] Xgl(6137): READ block 861480 on sda2
Feb 10 17:35:13 atlas kernel: [10692.432000] Xgl(6137): READ block 861488 on sda2
Feb 10 17:35:13 atlas kernel: [10692.432000] Xgl(6137): READ block 861496 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] notification-da(6344): READ block 859840 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] notification-da(6344): READ block 859848 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] notification-da(6344): READ block 859856 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] notification-da(6344): READ block 859864 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] notification-da(6344): READ block 859872 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] notification-da(6344): READ block 859880 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] notification-da(6344): READ block 859888 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] notification-da(6344): READ block 859896 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] Xgl(6137): READ block 940160 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] Xgl(6137): READ block 940168 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] Xgl(6137): READ block 940184 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] Xgl(6137): READ block 940192 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] Xgl(6137): READ block 940200 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] Xgl(6137): READ block 940208 on sda2
Feb 10 17:35:13 atlas kernel: [10692.436000] Xgl(6137): READ block 940216 on sda2
Feb 10 17:35:13 atlas kernel: [10692.456000] notification-da(6344): READ block 89664 on sda2
Feb 10 17:35:13 atlas kernel: [10692.456000] notification-da(6344): READ block 89672 on sda2
Feb 10 17:35:13 atlas kernel: [10692.456000] notification-da(6344): READ block 89680 on sda2
Feb 10 17:35:13 atlas kernel: [10692.456000] notification-da(6344): READ block 89688 on sda2
Feb 10 17:35:13 atlas kernel: [10692.456000] notification-da(6344): READ block 89696 on sda2
Feb 10 17:35:13 atlas kernel: [10692.456000] notification-da(6344): READ block 89704 on sda2
Feb 10 17:35:13 atlas kernel: [10692.456000] notification-da(6344): READ block 89712 on sda2
Feb 10 17:35:13 atlas kernel: [10692.456000] notification-da(6344): READ block 89720 on sda2
Feb 10 17:35:13 atlas kernel: [10692.480000] python(6205): READ block 777152 on sda2
Feb 10 17:35:13 atlas kernel: [10692.480000] python(6205): READ block 777160 on sda2
Feb 10 17:35:13 atlas kernel: [10692.480000] python(6205): READ block 777168 on sda2
Feb 10 17:35:13 atlas kernel: [10692.480000] python(6205): READ block 777176 on sda2
Feb 10 17:35:13 atlas kernel: [10692.480000] python(6205): READ block 777184 on sda2
Feb 10 17:35:13 atlas kernel: [10692.480000] python(6205): READ block 777192 on sda2
Feb 10 17:35:13 atlas kernel: [10692.480000] python(6205): READ block 777200 on sda2
Feb 10 17:35:13 atlas kernel: [10692.480000] python(6205): READ block 777208 on sda2
Feb 10 17:35:13 atlas kernel: [10692.488000] python(6205): READ block 331264 on sda2
Feb 10 17:35:13 atlas kernel: [10692.488000] python(6205): READ block 331272 on sda2
Feb 10 17:35:13 atlas kernel: [10692.488000] python(6205): READ block 331280 on sda2
Feb 10 17:35:13 atlas kernel: [10692.488000] python(6205): READ block 331288 on sda2
Feb 10 17:35:13 atlas kernel: [10692.488000] python(6205): READ block 331296 on sda2
Feb 10 17:35:13 atlas kernel: [10692.488000] python(6205): READ block 331304 on sda2
Feb 10 17:35:13 atlas kernel: [10692.488000] python(6205): READ block 331312 on sda2
Feb 10 17:35:13 atlas kernel: [10692.488000] python(6205): READ block 331320 on sda2
Feb 10 17:35:13 atlas kernel: [10692.496000] python(6205): READ block 330944 on sda2
Feb 10 17:35:13 atlas kernel: [10692.496000] python(6205): READ block 330952 on sda2
Feb 10 17:35:13 atlas kernel: [10692.496000] python(6205): READ block 330960 on sda2
Feb 10 17:35:13 atlas kernel: [10692.496000] python(6205): READ block 330968 on sda2
Feb 10 17:35:13 atlas kernel: [10692.496000] python(6205): READ block 330976 on sda2
Feb 10 17:35:13 atlas kernel: [10692.496000] python(6205): READ block 330984 on sda2
Feb 10 17:35:13 atlas kernel: [10692.496000] python(6205): READ block 330992 on sda2
Feb 10 17:35:13 atlas kernel: [10692.496000] python(6205): READ block 331000 on sda2
Feb 10 17:35:13 atlas kernel: [10692.500000] python(6205): READ block 770880 on sda2
Feb 10 17:35:13 atlas kernel: [10692.500000] python(6205): READ block 770888 on sda2
Feb 10 17:35:13 atlas kernel: [10692.500000] python(6205): READ block 770896 on sda2
Feb 10 17:35:13 atlas kernel: [10692.500000] python(6205): READ block 770904 on sda2
Feb 10 17:35:13 atlas kernel: [10692.500000] python(6205): READ block 770912 on sda2
Feb 10 17:35:13 atlas kernel: [10692.500000] python(6205): READ block 770920 on sda2
Feb 10 17:35:13 atlas kernel: [10692.500000] python(6205): READ block 770928 on sda2
Feb 10 17:35:13 atlas kernel: [10692.500000] python(6205): READ block 770936 on sda2
Feb 10 17:35:13 atlas kernel: [10692.516000] python(6205): READ block 331200 on sda2
Feb 10 17:35:13 atlas kernel: [10692.516000] python(6205): READ block 331208 on sda2
Feb 10 17:35:13 atlas kernel: [10692.516000] python(6205): READ block 331216 on sda2
Feb 10 17:35:13 atlas kernel: [10692.516000] python(6205): READ block 331224 on sda2
Feb 10 17:35:13 atlas kernel: [10692.516000] python(6205): READ block 331232 on sda2
Feb 10 17:35:13 atlas kernel: [10692.516000] python(6205): READ block 331240 on sda2
Feb 10 17:35:13 atlas kernel: [10692.516000] python(6205): READ block 331248 on sda2
Feb 10 17:35:13 atlas kernel: [10692.516000] python(6205): READ block 331256 on sda2
Feb 10 17:35:13 atlas kernel: [10692.520000] python(6205): READ block 331392 on sda2
Feb 10 17:35:13 atlas kernel: [10692.520000] python(6205): READ block 331400 on sda2
Feb 10 17:35:13 atlas kernel: [10692.520000] python(6205): READ block 331408 on sda2
Feb 10 17:35:13 atlas kernel: [10692.520000] python(6205): READ block 331416 on sda2
Feb 10 17:35:13 atlas kernel: [10692.520000] python(6205): READ block 331424 on sda2
Feb 10 17:35:13 atlas kernel: [10692.520000] python(6205): READ block 331432 on sda2
Feb 10 17:35:13 atlas kernel: [10692.520000] python(6205): READ block 331440 on sda2
Feb 10 17:35:13 atlas kernel: [10692.520000] python(6205): READ block 331448 on sda2
Feb 10 17:35:13 atlas kernel: [10692.532000] gnome-panel(6166): READ block 609472 on sda2
Feb 10 17:35:13 atlas kernel: [10692.540000] gnome-panel(6166): READ block 614024 on sda2
Feb 10 17:35:13 atlas kernel: [10692.540000] gnome-panel(6166): READ block 614032 on sda2
Feb 10 17:35:13 atlas kernel: [10692.540000] gnome-panel(6166): READ block 614064 on sda2
Feb 10 17:35:13 atlas kernel: [10692.548000] gnome-panel(6166): READ block 618368 on sda2
Feb 10 17:35:13 atlas kernel: [10692.548000] gnome-panel(6166): READ block 618376 on sda2
Feb 10 17:35:13 atlas kernel: [10692.548000] gnome-panel(6166): READ block 618392 on sda2
Feb 10 17:35:13 atlas kernel: [10692.548000] gnome-panel(6166): READ block 618400 on sda2
Feb 10 17:35:13 atlas kernel: [10692.548000] gnome-panel(6166): READ block 618408 on sda2
Feb 10 17:35:13 atlas kernel: [10692.548000] gnome-panel(6166): READ block 618416 on sda2
Feb 10 17:35:13 atlas kernel: [10692.548000] gnome-panel(6166): READ block 618424 on sda2
Feb 10 17:35:13 atlas kernel: [10692.552000] gnome-panel(6166): READ block 636808 on sda2
Feb 10 17:35:13 atlas kernel: [10692.552000] gnome-panel(6166): READ block 636816 on sda2
Feb 10 17:35:13 atlas kernel: [10692.552000] gnome-panel(6166): READ block 636824 on sda2
Feb 10 17:35:13 atlas kernel: [10692.552000] gnome-panel(6166): READ block 636832 on sda2
Feb 10 17:35:13 atlas kernel: [10692.552000] gnome-panel(6166): READ block 636840 on sda2
Feb 10 17:35:13 atlas kernel: [10692.552000] gnome-panel(6166): READ block 636848 on sda2
Feb 10 17:35:13 atlas kernel: [10692.552000] gnome-panel(6166): READ block 636856 on sda2
Feb 10 17:35:13 atlas kernel: [10692.552000] sync(13720): WRITE block 33128 on sda1
Feb 10 17:35:13 atlas kernel: [10692.572000] compiz.real(6189): READ block 358216 on sda1
Feb 10 17:35:13 atlas kernel: [10692.572000] compiz.real(6189): READ block 358456 on sda1
Feb 10 17:35:13 atlas kernel: [10692.580000] compiz.real(6189): READ block 360528 on sda1
Feb 10 17:35:13 atlas kernel: [10692.580000] compiz.real(6189): READ block 358888 on sda1
Feb 10 17:35:13 atlas kernel: [10692.588000] compiz.real(6189): READ block 894528 on sda2
Feb 10 17:35:13 atlas kernel: [10692.588000] compiz.real(6189): READ block 894536 on sda2
Feb 10 17:35:13 atlas kernel: [10692.588000] compiz.real(6189): READ block 894544 on sda2
Feb 10 17:35:13 atlas kernel: [10692.588000] compiz.real(6189): READ block 894560 on sda2
Feb 10 17:35:13 atlas kernel: [10692.588000] compiz.real(6189): READ block 894568 on sda2
Feb 10 17:35:13 atlas kernel: [10692.588000] compiz.real(6189): READ block 894576 on sda2
Feb 10 17:35:13 atlas kernel: [10692.588000] compiz.real(6189): READ block 894584 on sda2
Feb 10 17:35:13 atlas kernel: [10692.600000] Xorg(5777): READ block 46964416 on sda1
Feb 10 17:35:13 atlas kernel: [10692.600000] Xorg(5777): READ block 46964520 on sda1
Feb 10 17:35:13 atlas kernel: [10692.600000] Xorg(5777): READ block 46964608 on sda1
Feb 10 17:35:13 atlas kernel: [10692.600000] Xorg(5777): READ block 46964648 on sda1
Feb 10 17:35:13 atlas kernel: [10692.612000] Xorg(5777): READ block 920576 on sda2
Feb 10 17:35:13 atlas kernel: [10692.612000] Xorg(5777): READ block 920592 on sda2
Feb 10 17:35:13 atlas kernel: [10692.616000] Xorg(5777): READ block 920616 on sda2
Feb 10 17:35:13 atlas kernel: [10692.616000] Xorg(5777): READ block 920624 on sda2
Feb 10 17:35:13 atlas kernel: [10692.616000] Xorg(5777): READ block 920632 on sda2
Feb 10 17:35:13 atlas kernel: [10692.632000] Xorg(5777): READ block 896976 on sda2
Feb 10 17:35:13 atlas kernel: [10692.632000] Xorg(5777): READ block 896984 on sda2
Feb 10 17:35:13 atlas kernel: [10692.632000] Xorg(5777): READ block 896992 on sda2
Feb 10 17:35:13 atlas kernel: [10692.632000] Xorg(5777): READ block 897016 on sda2
Feb 10 17:35:13 atlas kernel: [10692.648000] nautilus(6168): READ block 875456 on sda2
Feb 10 17:35:13 atlas kernel: [10692.648000] nautilus(6168): READ block 875464 on sda2
Feb 10 17:35:13 atlas kernel: [10692.648000] nautilus(6168): READ block 875472 on sda2
Feb 10 17:35:13 atlas kernel: [10692.648000] nautilus(6168): READ block 875480 on sda2
Feb 10 17:35:13 atlas kernel: [10692.648000] nautilus(6168): READ block 875488 on sda2
Feb 10 17:35:13 atlas kernel: [10692.648000] nautilus(6168): READ block 875496 on sda2
Feb 10 17:35:13 atlas kernel: [10692.652000] nautilus(6168): READ block 875504 on sda2
Feb 10 17:35:13 atlas kernel: [10692.652000] nautilus(6168): READ block 875512 on sda2
Feb 10 17:35:13 atlas kernel: [10692.660000] nautilus(6168): READ block 96320 on sda2
Feb 10 17:35:13 atlas kernel: [10692.660000] nautilus(6168): READ block 96328 on sda2
Feb 10 17:35:13 atlas kernel: [10692.660000] nautilus(6168): READ block 96336 on sda2
Feb 10 17:35:13 atlas kernel: [10692.660000] nautilus(6168): READ block 96344 on sda2
Feb 10 17:35:13 atlas kernel: [10692.660000] nautilus(6168): READ block 96352 on sda2
Feb 10 17:35:13 atlas kernel: [10692.660000] nautilus(6168): READ block 96360 on sda2
Feb 10 17:35:13 atlas kernel: [10692.660000] nautilus(6168): READ block 96368 on sda2
Feb 10 17:35:13 atlas kernel: [10692.664000] nautilus(6168): READ block 96376 on sda2
Feb 10 17:35:13 atlas kernel: [10692.664000] nautilus(6168): READ block 836800 on sda2
Feb 10 17:35:13 atlas kernel: [10692.664000] nautilus(6168): READ block 836808 on sda2
Feb 10 17:35:13 atlas kernel: [10692.668000] nautilus(6168): READ block 836816 on sda2
Feb 10 17:35:13 atlas kernel: [10692.668000] nautilus(6168): READ block 836824 on sda2
Feb 10 17:35:13 atlas kernel: [10692.668000] nautilus(6168): READ block 836832 on sda2
Feb 10 17:35:13 atlas kernel: [10692.668000] nautilus(6168): READ block 836840 on sda2
Feb 10 17:35:13 atlas kernel: [10692.668000] nautilus(6168): READ block 836848 on sda2
Feb 10 17:35:13 atlas kernel: [10692.668000] nautilus(6168): READ block 836856 on sda2

```

---

### Post by chadjohnson on 2008-02-11
babump

---

### Post by mivo on 2008-02-12
Does ...

**sudo top**

... provide more insightful results than a plain top?

---

### Post by chadjohnson on 2008-02-12
Thanks, but nope, 'sudo top' and 'top' produce the same output :(

---

### Post by cdtech on 2008-02-14
> Does anything here look unusual?

Looking at /var/log/debug, the harddrive is being accessed a considerable amount each second. Here is part of the log, for just TWO seconds (after running 'echo 1 > /proc/sys/vm/block_dump'):

Type :
```
pstree -p
```
This will show you the block ID

---

### Post by bn127 on 2008-02-14
I had the same problem and unchecking Tracker in System>Preferences>Sessions got it solved (after rebooting).

bn127

---

### Post by chadjohnson on 2008-02-16
Thanks, but this did not work.

I think I am going just say goodbye to Ubuntu. This is costing me too much time.

---

### Post by chadjohnson on 2008-02-16
Thanks for the help, but I think that shows PIDs rather than block IDs.

This problem is simply ridiculous.

---

### Post by mivo on 2008-02-16
Have you looked at one of the other distros? Just to isolate the problem a little more, i.e. if it's a distro-dependent issue or a general Linux trouble related to your specific hardware setup.

---

### Post by chadjohnson on 2008-02-16
Do you mean Kubuntu or Xubuntu, or something non-Ubuntu like Fedora or SuSE?

---

### Post by mivo on 2008-02-16
Fedora or SuSE, yes. Something that isn't based on Ubuntu or Debian. If it happens with those distros as well, it would indicate an actual Linux issue -- something that is fundamentally in need of improvement. When I had some booting/video card issues, I tried different distros just to see if it's my hardware, the distro or Linux. Fedora, at the time, was the only distro I tried that worked fine on my new hardware, though it gave me a meaningful, non-critical warning, which gave me the necessary information to fix the problem in Ubuntu.

Before you give up on Linux completely, I'd definitely give Fedora a whirl. I don't currently use it, but I quite liked it and thought it was well done and offered good hardware support. An alternative is to look at the dev version of the next Ubuntu release, but I don't know how comfortable you'd be with an alpha version.

---

### Post by bn127 on 2008-02-16
Don't give up. Leave the Tracker unchecked (Sessions) , go to System>Preferences>Indexing Preferences and uncheck also the two check boxes in the first tab. Then in the Performance Tab  (second Tab) index speed to Slower.

bn127

---

### Post by chadjohnson on 2008-02-18
Thanks...I did all that, and I even removed the tracker app completely, but this problem persists...

---

### Post by chadjohnson on 2008-02-19
Still happening...still can't figure this out. Please help...


Please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help please help

Why is the CPU at 100%?

[IMG]http://chadjohnson.ath.cx/htop.png[/IMG]

---

### Post by bn127 on 2008-02-19
I'm sorry that it didn't work. In fact these procedures solved the problem in my machine.

bn127

---

### Post by cdtech on 2008-02-19
what do you get:
```
lsof
```
Are you running Google desktop?
The gdl_fs_crawler could cause this by hanging on a particular file.

Just a thought.

---

### Post by chadjohnson on 2008-02-19
Hey, I didn't mean to sound rude. I really and greatly appreciate your efforts. I appreciate everyone's efforts thus far. I'm just frustrated ;)

---

### Post by chadjohnson on 2008-02-19
Hmmm...I noticed today that after suspending at school with my PCMCIA wireless card plugged in (and having a connection with the school's network) and then coming home and resuming without the PCMCIA card plugged in, I had no problems. However, immediately after plugging in the PCMCIA card, the CPU jumped to 100% utilization.

I'll have to test this some more by resuming and not plugging in the wireless card. Is this a known problem?

---

### Post by cdtech on 2008-02-20
Hmm...
There is a bug similar to what you describe "disabling my wireless card fixes the issue", Bug [[COLOR="DarkRed"]#67126[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/67126")

Is this what your experiencing?

---

### Post by ShodanjoDM on 2008-02-20
Maybe you can install and try gps to find out

```
sudo aptitude install gps
```

It's the process monitor that I use, more useful than the standard system monitor. See the attachment.

---

### Post by chadjohnson on 2008-02-25
Thanks...I don't want to add acpi=off to my boot options though as I won't be able to suspend/resume.

---

### Post by chadjohnson on 2008-02-25
gps produced the same output as htop--nothing was using 100% of the CPU.

I noticed that--after updating my ATI drivers so that I could successfully restart my X session without the computer locking up--if I hit ctrl+alt+backspace and restarted my X session, the problem went away. So it must be X or something running alongside X or the GNOME session. Any ideas?

---

### Post by alien_mind on 2008-02-27
I have the same problem too. Check the %wa (iowait) of your CPU. It may be at 100% on single core or 50% with dual core.

If that's your case, it may be a bug related with kswapd after resuming, on 2.6.21 systems:

[http://groups.google.com/group/linux.kernel/browse_thread/thread/910c08e97eb0357e](http://groups.google.com/group/linux.kernel/browse_thread/thread/910c08e97eb0357e)

It seems not to be fixed

---

