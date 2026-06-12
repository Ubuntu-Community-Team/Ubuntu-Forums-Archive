---
title: "IBM T30: ATi powerplay, CPU speedstep, low power WiFi"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by aka5ha on 2006-01-09
Hello,

Ubuntu works perfectly on the T30, but battery life is horrible, about 1/3 of what XP lasts.  Why is this so, and what can be done about it?  It is what prevents me from running Linux permanently.  

1) CPU speedstep scales just fine (1.2 <--> 1.8 GHz).  
2) What about powerplay for the ATi mobility 7500 (270 MHz @ 1.5V <--> 66 MHz @ 1.2V).  XP manages this automatically, I would not even know where to begin in Ubuntu.  
3) What about lowest power setting for the built in wireless (Aironet 350)?  On XP you can choose max pwr saving mode.  
4) Hard disk spindown?  XP no problem, how about Linux?  (Any GUI alternative to HDPARM?).  

Any comments appreciated!

---

### Post by mpvano on 2006-01-09
What is your full model number and what exactly is the battery life you are getting? There seem to be several drastically different kinds of T30, with much different video and other hardware.

My 2ghz T30 (2366-97U) usually gets about two hours with normal use for me (wireless web surfing, text editing, etc). I don't think this is great, but it seems reasonable.

I think battery life depends on the T30 model you have, since they have a great deal of different hardware and there may be bugs in the support for some peripherals.

This one has everything but the kitchen sink installed, including the 1400x1050 lcd display hardware and bluetooth.

I do have one power related complaint, however - I wonder if it's what you're experiencing. This particular model, and some other T30 configurations, drain the battery very quickly WHILE SUSPENDED.

Mine seems to lose about 10% or more of the battery charge per hour during suspend. This is apparently a known bug in the video drivers for certain video hardware (mine has the radeon 7500) and is much discussed at thinkwiki ([http://www.thinkwiki.org/wiki/ThinkWiki)](http://www.thinkwiki.org/wiki/ThinkWiki)).

So far this problem is annoying, but I can live with it.

There seems to be a fix in the works that should appear in later kernel and xorg updates. Other than that, I'm pretty happy with the battery life.

Is this what you're seeing?

Mario

---

### Post by aka5ha on 2006-01-09
Hi Mario,  

My T30 has a 1024x768 TFT, an ATi 7500 GPU, a P4-m 1.8 GHz, and a cisco 350 mini PCI wireless card.  

I don't experience any battery drain when suspended to RAM or disk.  I am using XP, no service pack, and the latest IBM video drivers (8.133).  At least I haven't noticed.  But I will check later and report back my % loss/hour.  

I have a battery in the ultrabay, in addition to the main.  

The main battery lasts about 3 hours in XP, and 2 hours in Linux.  
With the ultrabay battery, about 4 hours in XP, and 2.5 hours in Linux.  

It is a huge disadvantage for me since I need about 3 hours minimum of battery!  

Since Linux CPU scaling works, it must have to do with wireless, GPU scaling, and hard disk spin down.  

Any further tips on reducing power consumption in Linux much appreciated!

---

### Post by mpvano on 2006-01-09
I don't have any ideas for you, I just wanted to compare notes. I think the SUSPEND drain is peculiar to only a few models....

It sounds like the big problem for you is that you're not getting the expected boost from the ultrabay battery - I wonder if it's actually being accounted for and enabled properly! I don't have one, so I can't be of any help there....

I rarely boot my machine up in XP, except to make sure the OS and IBM utilities are up to date, so I don't know what to expect - I just bought this thing about a month ago from IBM (an IBM factory refurb). I'm currently deeply immersed in some linux based development work, so I'm not likely to fire up XP much for a few months.

I'm sure the CPU scaling is working, but I think that there may be much more aggressive ways to save power (as you've suggested). I don't think linux currently pursues things like saving wireless power by default.

I've also noticed that this machine seems to have another CPU state that rarely kicks in, but that has drastically lower power consumption. When the machine is completely idle and operating on battery, the battery estimated run time sometimes jumps up abruptly and stays there until the next keystroke or other activity that kicks it out of that mode. I wonder if it shouldn't be spending more time in that state?

Here's something to pursue - I just checked and my wireless accepts the iwconfig power management commands. I think I'll see if that makes a difference over the next few days. This T30 model has the ibm high rate wireless/modem card installed, which is some sort of orinoco/prism/wavelan variant.

Because I am unhappy with Ubuntu's gnome network configuration management (it doesn't work at all for me on any of my notebooks), I use my own scheme involving manually switching customized location specific /etc/network/interfaces files. I just found that I can add the line "wireless-power on" to the eth0 network adapter "stanza".  This enables wireless power management. There are other commands that tailor the settings, but the defaults look pretty good.

It may not work for your card, however, since it's definitely card dependent. I'm not sure how much power it saves anyway. I'm going to experiment with it for a while.....

One interesting thing I just thought of is that I'm sure both the wireless and wired adapters are always powered up with the standard ubuntu power management scripts, which seems a waste of power. I'm going to look in to that some more.....

This seems like a worthwhile discussion. I hope some other T30 (and similar machine) owners join in.....

Mario

PS:

Here's some late news

- I got a useful (but small) gain of perhaps 10 minutes or so in battery run time by the change mentioned above.

- I found that the biggest reason for the short battery run time in MY machine seems to be that the disk battery conservation scripts called "laptop-mode" are not being enabled.

There may be some risks associated with the use of laptop-mode because it lengthens the time data is held in memory before being written to disk, and there have been some other problems with it interacting badly with suspend and hibernation. I suspect that's why it's been disabled.

As an experiment, I've reenabled it in /etc/default/acpi-support. The results were quite startling - the most interesting development is that the area around the disk has dropped in temperature a great deal.

You can tell if laptop-mode is currently active by doing "cat /proc/sys/vm/laptop-mode". A value of zero means it's inactive - other values show its status.

Manually enabling it by "sudo laptop-mode start" followed by "sudo hdparm -S 4 /dev/hda" is also an alternative, but again I don't recommend this unless you are feeling like becoming part of an experiment!

I don't know that these findings are a solution, but they definitely seem to indicate that the problem is that Breezy is NOT managing the disk power at all on the T30, and that it's not doing the best it could with the network interfaces.

mv

PPS:

After less than two days of normal use with several suspend cycles, my T30 experienced its first failure to resume from suspend ever.

This definitely seems to be related to my experimental enabling of laptop-mode to determine how much of the power drain problem was being caused by the disk. The lockup at resume was in line with the comment in /etc/default/acpi-support which warns against enabling it.

Unfortunately, without some change to the disk buffering algorithm the presence of several daemons needlessly hammering on the disk makes it impossible to improve battery life by enabling disc drive power conservation - the drives are almost never idle long enough to shut down, and when they do, they are immediately restarted - which actually increases power drain over the long term.

I DON'T RECOMMEND enabling laptop-mode at this time on the T30. The extension of battery life is not worth the lost reliability - perhaps this will be fixed in the future.

mv

---

### Post by aka5ha on 2006-01-25
Hi Mario,

Thanks so much for all your suggestions.  As far as I can tell, you are correct on everything!  

It is really too bad about this.  I can see the need for reliability over battery life, but sometimes I give 3 hour lectures, so my battery(ies) must last that long.  

In various experimentation, I have found the maximum battery life is obtained with Windows 2000, which can get about 20 min more than XP for the same power settings (for display timeout, hard disk spin down, Wi-Fi card state, etc.).  I am not sure why this is, but Windows 2000 certainly does have only about half the memory footprint at boot, and has 16-bit color by default, vs 32-bit for XP.  

Will try dapper when it is a point release.  

Thanks again,

Aka5ha

---

### Post by qball on 2006-01-25
I have a ibm t42 with also horrible battery life.. (2 hours tops when running on full power-save mode.)

To get the video card to "power down" you could either use the official ati drivers (they will clock the card down, when being "idle") or if you use the opensource driver try adding the following:
Option  "DynamicClocks" "On" 
to the Device (of the video card) section in xorg.conf.

What I also did to reduce the power drain was:
* disable the infrared port, 
* disable pcmcia
* spindown the hardisk very fast (I got a 7k2 rpm disk, you can imagine that takes alot of power).
* Turn the brightness completely down. 
* Set the power govener to "powersave"
* unload the wifi module. (atheros driver doesn't do powermanagement for me, maybe you have more luck with your card)

I could get down to around 11-12 Wh doing this, giving me an official uptime of 4 hours. (48Wh battery)

I have the laptop for a year now and my battery max capacity is only 27 Wh, and I'm happy if I get an effective 1.5 hour.

---

### Post by mpvano on 2006-01-25
Wow! Those sound like a lot of good ideas. I'm certainly going to be busy for a couple of weeks trying them out! I've already added the DynamicClocks option and restarted X - it seems to be happy with the option (according to the log file).

Good point about the batteries as well. Mine's down to 36 Wh which is about 75% of full capacity.

thanks again,

Mario

---

### Post by qball on 2006-01-26
I've made this plot just a few month after I got my laptop, here you can see that even the "last-full-capacity" is not you real capacity.
Here it allready makes a 10% jumps charging/discharging.

[http://images.qballcow.nl/old/battery/discharging-100-2.png](http://images.qballcow.nl/old/battery/discharging-100-2.png)

---

### Post by aka5ha on 2006-01-31
This is a great thread.  Please post back on any additional findings regarding power consumption.  

I am reporting back on my T30 in suspend mode.  It does not appear to drain the battery a significant amount while suspended.  I have logged the % battery remaining every time I suspend the laptop by closing the lid, and when I resume power, it always reports % remaining within 5% of what it was when initially suspended.  So I am assuming there is no issue with losing charge when suspended or hibernated.  

Now, with all the tweaks posted here, one could make a little howto for power management!  If Linux could be frugal with the juice, nothing would be better.

---

### Post by mpvano on 2006-02-12
More to report on my T30.

I've recently had a problem at bootup ever since the last kernel update to /etc/X11/xorg.conf. About 50% of the time at bootup, the machine locks up right after it initializes the mouse devices (according to the Xorg logs). It's been a nuisance, but not a huge problem, since the following reboot typically works.

As a result, I removed DynamicClocks. That seemed to fix the problem.

Anyway, the good news is that I've tried enabling laptop mode again, and it now works reliably for me. It's adding as much as half an hour to my run time. I think maybe whatever broke DynamicClocks fixed the laptop mode lockups on resume...

In other T30 news, I've fixed the problem I had with the hostap drivers for the high-rate wireless interface / modem card constantly switching the device names around by removing the entry for the wireless interface's MAC from /etc/iftab. Scanning now works fine...

Also, if anyone else is having trouble getting the keypad mappings to work, it's because the numlock key is not working correctly This can be easily fixed with a custom .Xmodmap file in your home directory that says 

keycode 77 = Num_Lock

running "xmodmap .Xmodmap" can be done to test the entry, and it seems to be automatically picked up on subsequent X restarts.

Mario

---

### Post by biofooled on 2007-06-02
I just salvaged a T30 that had a bad disk.  It has built in bluetooth but I can't get it up and running.

I currently have
bluez-pin bluez-utils bluez-gnome bluez-hcidump gnome-bluetooth
installed and when the system boots the kernel sees the bluetooth device (at least partially).

kern.log and syslog entries follow.  Help!


/var/log/kern.log:May 28 16:21:14 kkron-laptop kernel: [  683.256000] platform bluetooth: freeze
/var/log/kern.log:May 28 16:21:14 kkron-laptop kernel: [  684.508000] platform bluetooth: LATE freeze
/var/log/kern.log:May 28 16:21:14 kkron-laptop kernel: [  685.508000] platform bluetooth: EARLY resume
/var/log/kern.log:May 28 16:21:14 kkron-laptop kernel: [  690.020000] platform bluetooth: resuming
/var/log/kern.log:May 29 07:45:31 kkron-laptop kernel: [ 1033.972000] platform bluetooth: suspend
/var/log/kern.log:May 29 07:45:31 kkron-laptop kernel: [ 1035.652000] platform bluetooth: LATE suspend
/var/log/kern.log:May 29 07:45:31 kkron-laptop kernel: [56141.652000] platform bluetooth: EARLY resume
/var/log/kern.log:May 29 07:45:31 kkron-laptop kernel: [56146.096000] platform bluetooth: resuming
/var/log/kern.log:Aug 29 03:56:18 kkron-laptop kernel: [58964.468000] platform bluetooth: freeze
/var/log/kern.log:Aug 29 03:56:18 kkron-laptop kernel: [58965.708000] platform bluetooth: LATE freeze
/var/log/kern.log:Aug 29 03:56:18 kkron-laptop kernel: [58966.708000] platform bluetooth: EARLY resume
/var/log/kern.log:Aug 29 03:56:18 kkron-laptop kernel: [58971.044000] platform bluetooth: resuming
/var/log/kern.log:May 29 09:44:32 kkron-laptop kernel: [63280.776000] platform bluetooth: freeze
/var/log/kern.log:May 29 09:44:32 kkron-laptop kernel: [63282.028000] platform bluetooth: LATE freeze
/var/log/kern.log:May 29 09:44:32 kkron-laptop kernel: [63283.028000] platform bluetooth: EARLY resume
/var/log/kern.log:May 29 09:44:32 kkron-laptop kernel: [63287.592000] platform bluetooth: resuming
/var/log/kern.log:May 31 14:05:18 kkron-laptop kernel: [ 1853.140000] platform bluetooth: suspend
/var/log/kern.log:May 31 14:05:18 kkron-laptop kernel: [ 1854.852000] platform bluetooth: LATE suspend
/var/log/kern.log:May 31 14:05:18 kkron-laptop kernel: [105244.852000] platform bluetooth: EARLY resume
/var/log/kern.log:May 31 14:05:18 kkron-laptop kernel: [105249.120000] platform bluetooth: resuming
/var/log/syslog:Jun  2 09:52:53 kkron-laptop hcid[4949]: Default passkey agent (:1.27, /org/bluez/applet) registered
/var/log/syslog:Jun  2 10:00:15 kkron-laptop NetworkManager: <debug info>^I[1180803615.691348] nm_hal_device_added (): New de
vice added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
/var/log/syslog:Jun  2 10:00:30 kkron-laptop hcid[5070]: Default passkey agent (:1.11, /org/bluez/applet) registered
/var/log/syslog:Jun  2 10:07:32 kkron-laptop hcid[5070]: Unregister path: /org/bluez
/var/log/syslog:Jun  2 10:17:00 kkron-laptop hcid[6260]: Unregister path: /org/bluez
/var/log/syslog.0:May 30 08:50:06 kkron-laptop NetworkManager: <debug info>^I[1180540206.233514] nm_hal_device_added (): New 
device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
/var/log/syslog.0:May 30 08:51:58 kkron-laptop NetworkManager: <debug info>^I[1180540318.615990] nm_hal_device_added (): New 
device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
/var/log/syslog.0:May 31 14:05:18 kkron-laptop kernel: [ 1853.140000] platform bluetooth: suspend
/var/log/syslog.0:May 31 14:05:18 kkron-laptop kernel: [ 1854.852000] platform bluetooth: LATE suspend
/var/log/syslog.0:May 31 14:05:18 kkron-laptop kernel: [105244.852000] platform bluetooth: EARLY resume
/var/log/syslog.0:May 31 14:05:18 kkron-laptop kernel: [105249.120000] platform bluetooth: resuming
/var/log/syslog.0:Jun  2 09:27:12 kkron-laptop NetworkManager: <debug info>^I[1180801632.631604] nm_hal_device_added (): New 
device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth').

---

