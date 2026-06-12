---
title: "Suspend on Tecra M4 actually works!  (Mostly, anyway)"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by mapage on 2006-07-25
After a couple of weeks of letting this issue stew, I tried again to suspend and hibernate my laptop.  It actually worked this time!  I guess one of the more recent kernel changes made it possible.

Have any of you other Tecra M4 users found that Suspend works now?

Mind you, it isn't perfect yet...  It still takes it about 5 minutes to actually power down when I suspend, but it comes back to life in like 5-7 seconds!

If any of you also have this working, let me know!  To be perfect, I need to get rid of the 5 minute delay.

---

### Post by 23meg on 2006-07-26
What's the exact kernel version you got it working with?

---

### Post by mapage on 2006-07-26
Here is the output of uname -a

Linux rainstorm 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686 GNU/Linux

---

### Post by wasteed on 2006-07-29
Thanks to mapage for the original post, as I'd never had the patience to wait 5mins to see if the suspend to ram would work - but it eventually did. My laptop is a Tecra M5 (Centrino Duo, with Nvidia Quadro NVS 110M graphics) which is running the 2.6.15-26-686 #1 SMP PREEMPT kernel.


The  syslog  file seems to suggest the delay occurs after the 2nd CPU is taken down, 

Jul 30 02:23:21 laptop kernel: [17187482.748000] Freezing cpus ...
Jul 30 02:23:21 laptop kernel: [17187482.872000] CPU 1 is now offline
Jul 30 02:23:21 laptop kernel: [17187482.876000] SMP alternatives: switching to UP code
Jul 30 02:23:21 laptop kernel: [17187482.920000] CPU1 is down
Jul 30 02:29:26 laptop kernel: [17187482.920000] Stopping tasks: ============================================================================================
Jul 30 02:29:26 laptop kernel: [17187482.940000] ata2: suspend device
Jul 30 02:29:26 laptop kernel: [17187482.944000] ata1: suspend device
Jul 30 02:29:26 laptop kernel: [17187483.372000] ACPI: PCI interrupt for device 0000:06:0b.0 disabled

Does anyone have any ideas about the cause of this delay? 

After I resumed from the suspend I noticed that the builtin wireless internet connection hadn't restarted, and also the mousepad no longer allowed me to scroll web page windows/terminal windows using the right hand edge of the touchpad. I don't recall either of these problems after testing the hibernate to disk option. Also, somethng which may be related is that the fan hasn't gone off for a couple of hours now even though the temperature is only 33C.

---

### Post by mapage on 2006-07-31
I've noticed similar results.  Seems to be near the 'Stopping tasks:" that the delay occurs.  Here is a snippet of my syslog.

Jul 31 12:10:15 localhost kernel: [17181105.320000] ACPI: PCI interrupt for device 0000:02:00.0 disabled

Jul 31 12:10:15 localhost kernel: [17181105.384000] ACPI: PCI interrupt for device 0000:03:05.0 disabled

Jul 31 12:10:15 localhost kernel: [17181105.400000] ieee80211_1_1_13_crypt: unregistered algorithm 'NULL'

Jul 31 12:18:30 localhost kernel: [17181107.196000] Stopping tasks: ======================================================================================================|

Jul 31 12:18:30 localhost kernel: [17181107.212000] ata1: suspend device

Apparently, it's timing out waiting for something to quit or unload.  I'm going to spend some time trying to figure out what is causing the delay.  I wonder if there is a way to get more verbose system messages...  At least where the Stopping tasks: entry is concerned.

---

### Post by wasteed on 2006-07-31
I've performed a number of tests with hibernate and suspend on my Tecra M5 now. It seems to be a pretty hit and miss affair whether they work properly or not. For example, the 1st time I tried hibernate, it worked just fine, and  when it came back it even restored the built in wireless connection flawlessly. On another occasion, the laptop appeared to go down fine but didn't recover properly - before the display came back on the capslock key started flashing and it seemed to get no further, so I had to power it off and back on.

Suspend is also a little bit flakey. Apart from the 5min delay before suspend actually kicks in, I noticed on one occasion that when it resumed the internal intel wireless had disappeared - turning the wireless kill switch off and on had no effect; eth1 was nowhere to be found.
On that same occasion, after resume, one of the CPUs was stuck in the performance setting, running permanently at 2.1GHz, rather than in userspace at 1GHz when under no load.

I've also tried a suspend after quitting X first (/etc/init.d/gdm stop), and it still took 5mins for the suspend light to start flashing. So it doesn't look like the nvidia graphics driver is the cause of the hang.

Other oddities, include occasional APIC errors : 

Jul 31 22:53:48 apb-laptop kernel: [17183540.248000] APIC error on CPU0: 00(40)
Jul 31 22:53:48 apb-laptop kernel: [17183540.248000] APIC error on CPU1: 00(40)


I've tried booting with the kernel noapic boot option, but when I do that the 2nd CPU appears to be stuck at 100% CPU load while trying to insert the Intel ipw3945 module, which is no good.

I've also noticed that after a period of heavy load, e.g. a 3D game, during which time the temperature increased, to say above 60C, so that the fan worked harder, then even after 1.5hrs back under normal load the fan ran non-stop even though the temperature appeared to have come down to a sensible level, 40C. It stayed on until I rebooted.

One other slight issue. Sometimes after a mousepad button click has been made nothing appears to happen and you'd think the permormance was taking a hit. However, as soon as the mouse pad is touched again, to move the cursor, then the previous mouse click operation is performed. Very odd...

---

### Post by bluetoad on 2006-08-01
> **wasteed said:**
> 
The  syslog  file seems to suggest the delay occurs after the 2nd CPU is taken down, 

Jul 30 02:23:21 laptop kernel: [17187482.748000] Freezing cpus ...
Jul 30 02:23:21 laptop kernel: [17187482.872000] CPU 1 is now offline
Jul 30 02:23:21 laptop kernel: [17187482.876000] SMP alternatives: switching to UP code
Jul 30 02:23:21 laptop kernel: [17187482.920000] CPU1 is down

Jul 30 02:29:26 laptop kernel: [17187482.920000] Stopping tasks: ============================================================================================
Jul 30 02:29:26 laptop kernel: [17187482.940000] ata2: suspend device
Jul 30 02:29:26 laptop kernel: [17187482.944000] ata1: suspend device
Jul 30 02:29:26 laptop kernel: [17187483.372000] ACPI: PCI interrupt for device 0000:06:0b.0 disabled

Does anyone have any ideas about the cause of this delay? 



On my Portege M500 I see the 6 minute delay between "SMP alternatives: switching to UP code" and "CPU1 is down".  I don't have any ideas yet.

Hibernate seems to work properly.  The only issue is that sometimes I need to enable/disable in Network Manager.

---

### Post by bluetoad on 2006-08-01
In another attempt (this time on AC power) the delay was 10 minutes in the same place as in wasteed's post.

Kernel version is the same.

---

### Post by wasteed on 2006-08-14
I should have said that all my experiments with suspend/hibernate have been performed on AC power. 

After using my laptop a little more heavily in the last two weeks, I'm finding that resuming from hibernate seems to fail more often than it succeeds - with the capslock key led flashing and a console full of ASCII garbage!

---

### Post by bluetoad on 2007-09-11
I just wanted to let you know that I have had suspend and resume working on my Portege M500 for a while now in Feisty.  It suspends in seconds rather than minutes.  The patch also includes the M5.  

Looking up the specs for the M4, it has SATA so it could be a candidate for the same patch.  It is not currently included.  If there is any interest, I'm willing to build the kernel packages for the M4 for you to try.  To patch for the M4 is trivial.   You just need to look at the output of

sudo dmidecode 

for the strings.

See [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90771](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90771) for details

---

