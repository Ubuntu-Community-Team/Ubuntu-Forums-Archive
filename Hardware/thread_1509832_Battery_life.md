---
title: "Battery life"
date: 2010-06-14
forum: Hardware
---

### Post by luismgl on 2010-06-14
Ive noticed that my battery life has shortened significantly. I have the pm-utils-powersave policy but I believe it isn't working, since the battery last more or less as long as if it would when on balanced using win7. 
Any suggestions what do I have to do?
Thank you

---

### Post by luismgl on 2010-06-15
just an up =)

---

### Post by yossell on 2010-06-15
Did you install powertop as I suggested in response to the other thread you posted of a similar title? What does its output say?

---

### Post by luismgl on 2010-06-15
here's the output
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (12.7%)         2.14 Ghz     2.2%
polling           1.0ms ( 0.1%)         2.00 Ghz     0.0%
C1 mwait          0.5ms ( 8.7%)         1333 Mhz     0.0%
C3 mwait          0.9ms (78.5%)         1199 Mhz     1.0%
                                         933 Mhz    96.8%

Wakeups-from-idle per second : 1010.1   interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  35.4% (676.8)   [kernel scheduler] Load balancing tick
  21.9% (418.6)   skype
  12.1% (231.6)   pulseaudio
  10.8% (205.8)   [TLB shootdowns] <kernel IPI>
   8.0% (153.2)   [ehci_hcd:usb1, ath9k] <interrupt>
   6.2% (118.0)   firefox-bin


How do I set it to powersave?

---

### Post by yossell on 2010-06-15
Ok! Good work!

As time goes by, powertop should make a few suggestions and ask you to press a key to accept its suggestion. I normally go along with what it says. 

It should suggest to enable the on-demand governer, and this makes a big difference too. But you should be able to do this yourself from startup - did you install the cpu scaling frequency monitor on your panel? You should - left click panel, and choose add to panel, and you should be able to add it. Right click it when it appears and choose powersave or ondemand - Ondemand usually works for me. There will be a little read out giving the clock speed: you want to make sure that the chip is mainly powered down, running about half the speed its capable of. 

Finally, and this is trickier, what you want to try and do is reduce the number of wakeups. 1010 wakeups from idle is EXTREMELY HIGH. That could be your problem. On a good day, I get mine under 10, and rarely over 200. What you need to do is look at the processes that are causing the most wakeups and trying to kill them or shut them down. At the moment, a big cause is this load balancing tick - this seems to be something funny with the current kernel, and there's not much to be done about this without loading an earlier kernal which is not worth it. But you see that your skype and your pulseaudio are causing a lot of wakeups. If you can kill off these processes when you're not using them, you should reduce wakeups to a better number and get better battery life.

It can take some tweaking, but I found, after some trial and error, that I could squeeze more battery life out of my laptop than on windows. 

Hope this helps

---

### Post by luismgl on 2010-06-15
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (37.4%)         2.14 Ghz    11.6%
C0                0.9ms ( 0.1%)         2.00 Ghz     0.2%
C1 mwait          0.5ms ( 7.4%)         1199 Mhz     0.8%
C2 mwait          0.8ms ( 1.5%)         1066 Mhz     0.5%
C3 mwait          1.0ms (53.6%)          933 Mhz    86.2%

Wakeups-from-idle per second : 702.7    interval: 3.0s
no ACPI power usage estimate available

Top causes for wakeups:
  29.7% (873.3)   [kernel scheduler] Load balancing tick
  15.8% (466.0)   skype
   9.1% (269.0)   [ehci_hcd:usb1, ath9k] <interrupt>
   9.0% (263.7)   [TLB shootdowns] <kernel IPI>
   8.6% (251.7)   USB device 2-1.5 : HP Webcam


After installing the cpu scaling monitor and setting it into powersave, I was able to lower some wakeups, wich is already good. I know that by having skype on I'm using many of my machine's resources, but I have to use skype right now so there is really isn't much I can do about it. I will buy a cooling pad, it will help manage the temperatures a little. Thank you very much for your help =)

---

### Post by luismgl on 2010-06-15
this kernel is a little funky indeed
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 0.1%)         2.14 Ghz     0.1%
C0                0.0ms ( 0.0%)         2.00 Ghz     0.0%
C1 mwait          0.6ms ( 0.1%)         1.87 Ghz     0.0%
C3 mwait         15.0ms (99.8%)         1333 Mhz     0.0%
                                         933 Mhz    99.9%

Wakeups-from-idle per second : 67.5     interval: 15.0s
no ACPI power usage estimate available

Top causes for wakeups:
  33.7% ( 47.1)   [kernel scheduler] Load balancing tick
  17.8% ( 24.9)   [ehci_hcd:usb1, ath9k] <interrupt>
  12.4% ( 17.3)   [kernel core] hrtimer_start (tick_sched_timer)
  11.3% ( 15.7)   USB device 1-1.5 : USB2.0-CRW (Generic)
   0.1% (  0.2)D  gconfd-2
   7.2% ( 10.0)   pulseaudio
   3.1% (  4.3)   phy0
   2.1% (  2.9)   [ahci] <interrupt>

---

### Post by yossell on 2010-06-15
It looks like it's spending a lot more time in a low Mhz state - which is good: should keep the cpu cooler and use less power. But it's annoying that there's no acpi usage estimate available, because that's a very handy figure on a laptop. It shows up when my computer is on battery, but not when plugged in - does it show when you're on battery power?

---

### Post by GeorgeOfTheBush on 2010-06-19
Here's my **powertop** output:

```

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (19.7%)         2.00 Ghz     4.7%
C0                1.4ms ( 0.1%)         1.60 Ghz     0.4%
C1 mwait          0.1ms ( 0.1%)         1200 Mhz    94.9%
C3 mwait          0.9ms (80.1%)


**Wakeups-from-idle per second** : [SIZE=4][COLOR=Red]**896.2**[/COLOR][/SIZE]    interval: 10.0s
**Power usage (ACPI estimate)**: [SIZE=4][COLOR=Red]**14.3W**[/COLOR][/SIZE] (2.0 hours) (long term: 18.0W,/1.6h)

Top causes for wakeups:
  35.1% (334.3)   PS/2 keyboard/mouse/touchpad interrupt
  21.4% (203.5)   [kernel scheduler] Load balancing tick
  16.3% (155.5)   firefox-bin
   9.0% ( 85.6)   [extra timer interrupt]
   4.2% ( 40.1)   [iwlagn] <interrupt>
   2.9% ( 27.6)   Xorg

Suggestion: Enable SATA ALPM link power management via:
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

```I keep getting these messages from [COLOR=Navy]**powertop**[/COLOR] [COLOR=Navy]**[COLOR=Red]in spite of following powertop's  suggestions.[/COLOR]**[/COLOR] 

```


A **USB device** is active 100.0% of the time:
USB device  1-2 : USB2.0-CRW (Generic)

An **audio device** is active 100.0% of the time:
hwC0D0 Intel G45 DEVCTG 

An **audio device** is active 61.3% of the time:
hwC0D2 Realtek ALC272

```[COLOR=Navy][COLOR=Black]However, I dont get any **suggestions** for these messages.

```


The program 'firefox-bin' is writing to file 'urlclassifier3.sqlite' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'firefox-bin' is writing to file 'cookies.sqlite' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'firefox-bin' is writing to file 'sessionstore-1.js' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'gconfd-2' is writing to file 'saved_state' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'ubuntuone-syncd' is writing to file 'syncdaemon.log' on /dev/sda6.
This prevents the disk from going to powersave mode.


```[/COLOR][B] 
Yossell[/B][/COLOR]

I realized that the no. of **Wakeups-from-idle per second** on my laptop is extremely high after reading your post where you have mentioned that you get this number to be [COLOR=Navy]**under 10**[/COLOR] - which is [COLOR=Navy]**too goooooood**[/COLOR] - something I cannot even imagine!

Also, [COLOR=Red]POWERTOP's suggestions are of no use to me[/COLOR] - even though I press  the keys corresponding to the suggestions, the battery power steadily  drains. So I dont see any benefit running Powertop as of now.

If you could give me any pointers on reducing the number of wakeups from idle per second, that would be great.

**The ONLY app I use** most of the time (and even as I type this post) is - **Firefox** with a number of tabs open.

Here's my **system configuration**:

```

Ubuntu 10.04
Kernel 2.6.32-22-generic
GNOME 2.30.0

Memory 3 GB
Pentium Dual Core 2 GHz

```

---

### Post by yossell on 2010-06-19
GeorgeOfTheBush,

I'm afraid I can't help you much here  - I'm not sure why you're not getting any suggestions. 

I should emphasise that I was only able to get so few (<10) wakeups when I was running 9.04 under an openbox session with wireless networking disabled. The load balancing tick is an issue with the current kernel and there's nothing we can do about it until it's fixed. It does seem to go down as you reduce other processes, though.

Nonetheless, that's still a very high number of wakeups you're getting. Currently, in 10.04 and under gnome and with firefox running, I'm getting 200, only 37 from firefox. Your keyboard/mouse is causing a LOT of wakeups - I don't know why there's such activity from them. 

I too get those `cannot go to powersave mode' since 10.04, but they haven't seemed to worsened my battery usage and so I've not investigated, but perhaps not something to worry about.

I've only three suggestions: (a) you can try entering those suggestions from a terminal and see if they make a difference. (b) you can run top to investigate processes that are taking up cpu time and killing them (c) you can run cpu frequency scaling monitor on gnome panel and set to powersave, to make sure chips stay in lowest power state mode.

But overall a powerusage estimate of 14w doesn't seem awful, so it may not be worth worrying about!

---

