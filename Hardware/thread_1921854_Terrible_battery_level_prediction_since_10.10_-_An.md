---
title: "Terrible battery level prediction since 10.10 - Any fixes?"
date: 2012-02-07
forum: Hardware
---

### Post by chrismyers on 2012-02-07
Hi Guys,

Ubuntu battery prediction is terrible with my laptop. Upon power-up, Ubuntu frequently reports one minute of battery power remaining, yet the hardware LED is happily glowing green.

I know that my laptop is OK with Linux - Ubuntu 10.10 & earlier work fine. I have been using Ubuntu for years (since Breezy).

 My laptop is a Lenovo 3000 0769-B4G

I have tried various suggestions in the past without success & I am now at the stage where I have forgotten what I have tried!

I am trying very hard, but I'm starting to get a little disheartened with the new changes. :cry:

Does anyone know of a fix that works?

Many thanks.

---

### Post by xyzzyman on 2012-02-07
How old is your current battery? That model came out over 4.5 years ago, so if it's an original battery it's probably shot and will be reporting weird #'s. Usually you get 2.5-3 years off a battery. Sometimes more, sometimes less.

---

### Post by chrismyers on 2012-02-08
The battery is fine (I have 2). Discount any hardware problem.

I have dual boot on my laptop & the *other* OS has reasonable prediction.

The problem started since Unity. I can roll back to 10.10 & it all works fine.

---

### Post by xyzzyman on 2012-02-08
What's the other OS? Is it another Linux-based? 

Did you ever try 11.04? If not then most likely it's a regression in the kernel from the 2.6 to 3.0 change. Unity is just a desktop environment and it's battery indicator is just reporting what the ACPI in the kernel tells it to. You can see the information yourself by:

cat /proc/acpi/battery/BAT1/state

When you're on battery it'll show the remaining capacity and the current discharge rate. That's how it calculates the time remaining.

---

### Post by chrismyers on 2012-02-08
> **xyzzyman said:**
> What's the other OS? Is it another Linux-based? 

Windows, but other than "battery prediction works on another OS" I'm not sure that its pertinent.

> **xyzzyman said:**
> 
Did you ever try 11.04? If not then most likely it's a regression in the  kernel from the 2.6 to 3.0 change. Unity is just a desktop environment  and it's battery indicator is just reporting what the ACPI in the kernel  tells it to. You can see the information yourself by:


Yes, I tried 11.04, but it was badly broken for my laptop due to graphics card issues & freezing. I had to revert to 10.10 & wait for 11.10. *You may be right about the kernel.* I'm not necessarily blaming Unity, it's just that my problems started in the Unity timeframe.

> **xyzzyman said:**
> You can see the information yourself by:

cat /proc/acpi/battery/BAT1/state

When you're on battery it'll show the remaining capacity and the current  discharge rate. That's how it calculates the time remaining.

Ahh... This is one of the things I remember doing now.. Here are some results:


 **cat /proc/acpi/battery/BAT1/info **

present:                 yes
design capacity:         5100 mAh
last full capacity:      5100 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 420 mAh
design capacity low:     156 mAh
cycle count:          0
capacity granularity 1:  264 mAh
capacity granularity 2:  3780 mAh
model number:            PA3465U 
serial number:           3658Q
battery type:            Li-Ion
OEM info:                COMPAL 

** cat /proc/acpi/battery/BAT1/state **

present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            0 mA
remaining capacity:      4437 mAh
present voltage:         11100 mV

 **cat /proc/acpi/battery/BAT1/alarm **

alarm:                   unsupported

It's clearly reporting badly at a discharge rate of 0mA! Typically Ubuntu reports 10 minutes of battery life upon power-on, but increases to 45 minutes or so after some time.

Cheers :-)

---

### Post by chrismyers on 2012-02-11
An additional note:

I booted to 10.10 live CD & running the previous commands gives the same results.

Strange that 10.10 was absolutely fine at predicting the battery.

---

### Post by xyzzyman on 2012-02-11
Have you performed a BIOS upgrade since you originally ran 10.10 or changed a BIOS setting? Something has changed your ACPI and assuming there isn't a hardware failure, it's not compatible with the kernel. I'm willing to bet that even a livecd of Fedora would give you the same results.

---

### Post by chrismyers on 2012-02-12
It isn't hardware. Really, its not.

Battery prediction still works fine on 10.10 & also Windows.

I need to move forward with a fix for 11.10, or hope that 12.04 has a fix.

---

### Post by JC Cheloven on 2012-02-12
Perhaps your problem is ralated to this known [kernel issue]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131"), which is there since Ub 11.04. 

There is a fix, which (hopefully) will be applied in 12.04 Precise. In the meanwhile, and according to comment 242 in the above link, the fix for 11.10 Oneiric is to install linux kernel 3.0.20 from [this ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").

Hope it helps.

EDIT: I'm using that kernel right now. Not measued properly yet, but I'd the feeling of battery life being much better.
UPDATE: Tested properly, seems to work fine. Please see #6 [here]("ubuntuforums.org/showthread.php?p=11686854")

---

### Post by chrismyers on 2012-03-04
Tried the new kernel, but it did no good.

Just upgraded to 12.04 beta yesterday. First impressions appear that prediction is OK with 12.04.

Using the cat commands as described in earlier posts produces the same results, so it must be how 11.04 & 11.10 was interpreting the results.

Cheers guys.

---

### Post by totalnovice on 2012-03-05
I also am having a terrible battery time.  It shows 1hr 30 min, but screen goes dark and kicks me out in 5 minutes!!  Very annoying.  I have a 3 yr old HP Pavilion dv4.  I am IN NO WAY A COMPUTER GEEK!!  The guy that has helped me and got me on ubuntu has not heard of this and told me to get on here to see what suggestions I find.  Please give me some ideas. I went to batteries plus today to get a new battery, but the clerk said the battery I have shows I should have 2-3 hours life each time it's charged, and it showed fully charged at that time.  I turned on the computer and showed him it kicks me out.  he told me I didn't need a battery, I need to find the cause of the laptop not accepting the battery support.  Please give me any suggestions. Thanks.

---

