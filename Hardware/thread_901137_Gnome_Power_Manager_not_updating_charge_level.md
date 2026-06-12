---
title: "Gnome Power Manager not updating charge level"
date: 2008-08-26
forum: Hardware
---

### Post by Lil_Pete on 2008-08-26
Hello,

I've recently installed Ubuntu Hardy Heron on my Travelmate 3201XMi and have two problems, the first of which is the graphics card being made by ATI and causing lock-ups when using restricted drivers, the second, and the one being discussed here, is that the Gnome Power Manager is failing to update its status.

For example;
I turn the laptop on (unplugged) with a full battery, when it gets into linux it reads say 98% charge. After 20mins it still reads 98% charge.
Same when charging, the battery charge level just refuses to update.

My problem appears identical to the following;
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/194960](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/194960)

I've added the Battery Charge Level applet, which seems to update properly, so I believe it's gnome power manager that's having issues.

If I go from being unplugged to plugged in then whilst the panel applet responds instantly, gnome power manager does respond after a significant delay (30 seconds or so) and the charge level is updated then, but then freezes again. Sometimes the panel applet also fails to change battery charge levels or plugged-in status.

When querying the battery status information I get the following;
peter@Arthur:~$ cat /proc/acpi/battery/*/*
alarm:                   480 mAh
present:                 yes
design capacity:         4800 mAh
last full capacity:      3517 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: unknown
design capacity low:     unknown
capacity granularity 1:  unknown
capacity granularity 2:  unknown
model number:            01ZA
serial number:           32397
battery type:            LION
OEM info:                SANYO
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            2455 mA
remaining capacity:      1305 mAh
present voltage:         11680 mV

Which does update properly as the battery charges/discharges.

Any idea where it's gone wrong?

Thanks,

Peter

---

### Post by Lil_Pete on 2008-08-27
I've now tried reinstalling Ubuntu (just in case something went funky somehow) and even after a fresh install it doesn't work.

I've tried reinstalling HAL and gnome-power-manager as well as following the advice here;
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413)
which suggests changing the order things start in (I think..)

Still no luck.

To reiterate, gnome-power-manager correctly reports the power levels and states on start-up, but then fails to update past then.
It does detect whether or not the AC power is attached correctly, albeit sometimes with a sizeable delay.

Please help! It's driving me mad!

---

### Post by molochi on 2008-08-27
Wow someone else is using this notebook (TM 3201xci). I have noticed that the battery charge monitor doesn't reliably update. Usually it will report the correct charge at login, but only very rarely updates after this. I've noticed that 

Prompt:~$ cat /proc/acpi/battery/BAT0/state

gives an acurate charge reading and will often (but not always... sometimes you have to cat 2-3 times) cause the applet to update to the correct current charge state, but then it usually just stays at that level until I check it in terminal again. It's polling something that isn't getting updated I guess, but I haven't looked into it.

My mr9700 doesn't work with any of the proprietary ati driver install methods either. 

Everything else seems to work including file transfer over bluetooth (didn't expect it to), though I haven't managed to get my BT earpeice working.

---

### Post by Lil_Pete on 2008-08-28
Mine's actually the 3202XMi, i think the only difference is the cpu being 100mhz faster!

I've been having all kinds of issues with this laptop, mostly revolving around the power management. In Vista it won't detect the battery, in Linux (both Ubuntu (gnome and KDE) and Fedora so far) the charge level doesn't update properly.
In XP (the OS sold with the laptop) the keyboard stutters annoyingly when the battery is attached, not really a problem when plugged in as I can take out the battery, but when it's unplugged it's annoying.
I can't exactly pin it down but it does seem to be related to how often something updates the battery status (ie XP is relatively fine until I install any additional power management software, and Vista doesn't stutter at all because it doesn't know there is a battery).

I managed to get the mobility 9700 drivers installed, but if I try to use desktop effects or anything that actually uses them then the laptop locks and the screen goes funky colours.

Going to try Mandriva shortly, but I'm doubtful it'll be much different =(

</ramble>

---

### Post by molochi on 2008-08-29
I've got a lot of use out of this thing. I think it was the best computer buy I ever made. I upgraded the memory to 1.5GB a couple of years ago, and about the same time put a 120GB Seagate in it. I also found a P-M 755 (2GHz) for cheap in december, but I've been too lazy to go through swapping it out. Doesn't really need it anyways. Got two new batteries for free when Acer recalled them and you do want to have the newer battery (it's a free new batt plus supposedly it won't burst into flames, heh). I run the Omega drivers in XP for the mr9700 which are less trouble than hacking AMDs/ATi's to work. Oh and I put a screen protector on it to prevent "powerbook marks" on it.

I've really liked the stability and the balance of power, features and weight. It runs cool when I want it to, and has good battery life for a thin and light with a real videocard (3Hrs). Firewire, GB ethernet. TF2 runs well on it too. Not bad for a nearly 4 year old 2KG notebook.

Now if I could just get the videocard working under fglrx... well at least the keyboard works correctly under ubuntu. I always figured it was unfixable and my only real complaint. Mine skips occasional keystrokes under XP regardless of the power source. I always thought it was just a crappy keyboard design, but it's perfect in linux. Sample rate difference?

(that's a long bump)

---

### Post by Lil_Pete on 2009-03-18
Old post bumping I know, but it's my post and still relevant.
If the person who previously posted is still reading this, I have found that adding "highres=off nohz=off irqpoll" to the kernel options has fixed my problems with the Mobility 9700 causing X to freeze.
I have also, after much searching, managed to trace the keyboard stutter problem under windows back to the battery. Apparently in these models the battery is communicated to via the SMBus, which I think also handles the keyboard. Essentially everytime the battery's status is polled it interrupts the keyboard, hence the stutter.
I hate to break it to you but the reason the stutter isn't appearing in Ubuntu appears to be because the system isn't automatically polling the battery charge level.

By running "watch cat /proc/acpi/battery/*/*" I am able to get the gnome power manager to update, although there's a keyboard and mouse stutter every 2 seconds, the default polling period.
However as you are able to specify an update period for the "watch" command I think setting this to something like 5 minutes should give reasonable battery charge level accuracy with minimal keyboard interruptions.

Does anybody have any thoughts??

---

