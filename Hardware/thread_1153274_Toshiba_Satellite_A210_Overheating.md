---
title: "Toshiba Satellite A210 Overheating"
date: 2009-05-08
forum: Hardware
---

### Post by Pyker on 2009-05-08
So, I've got a problem. It's not related to Ubuntu in any way, but to my laptop.

I've got a Toshiba Satellite A210 laptop that overheats much.
Like, it has always heated up since it was new, but nothing compared to this.
For example, the boot temperature (Windows Vista) was around 50ºC. The current temperature now (~2 hours after) is 60ºC and has reached 70ºC.

Yesterday night, I left my computer on for the next day (today), and, today, when I arrived home (~16 hours on Jaunty), I don't know what the temperature was, but even the keyboard was hot! I guess it was around 90ºC...

This has been happening for a few weeks now.
I already have searched for solutions for this on the web, and I found one: update the BIOS, which I already did, and didn't solve the problem.

So, how can I solve this problem?

Thank you,
Pedro Cunha

EDIT: Also, I don't know if this is in the correct section, but if not, please move it to the appropriate section. Thank you.

---

### Post by Kareeser on 2009-05-08
Have you tried taking a vacuum cleaner to the vents and clearing dust out?

Also, make sure your fans are in working order. If you cannot hear them running, then they may have malfunctioned, and you should remedy that as soon as possible.

---

### Post by Pyker on 2009-05-09
> Have you tried taking a vacuum cleaner to the vents and clearing dust out?
I'll try it now, thanks.

> Also, make sure your fans are in working order.
Yes, they are. I can hear them running, and, also, I don't think the problem is related to anything I have already spoken (sorry), because, today I arrived home, and I noticed that, according to what Ubuntu detects, my processors are 50~60ºC, that's OK. My hard drive is also 40~50ºC, which is also OK.
But what's not OK is an undetected temperature, I mean, when I touched the keyboard, in certain zones, like, at the bottom of the keyboard, it was so hot that it almost burned me. I mean, like, it was about 90ºC... Also, that zone is the middle of the motherboard...

Any suggestions?

Thank you,
Pedro Cunha

---

### Post by Dex73 on 2009-05-09
I have a similar problem with my laptop and Hardy. It gets the hottest when the screen saver is on. I've switched it around a lot, even hot on blank screen. Any ideas?

---

### Post by Pyker on 2009-05-09
It might have to do with the screensaver if it's because of the graphics card.
Is there any way to access my graphics card temperature sensor (if it exists)?
My graphics card is an ATI Mobility Radeon HD2400, my motherboard is an AMD K8 (Athlon64/Opteron).
(The information that Sysinfo outputted is attached).

Thank you,
Pedro Cunha

---

### Post by Dex73 on 2009-05-09
I'm not sure about the sensor. Anyway, I don't think my problem is my graphics card. My computer only gets hot where my hard drive is at. I've haven't taken any temp., but it almost burns you. When I took the computer apart to clean I saw that some of the wires have paper labels that are turning brown. Has me a little worried. It also cools down faster when I play a music file. Have no idea why using it creates less heat.

---

### Post by Pyker on 2009-05-09
> It also cools down faster when I play a music file. Have no idea why using it creates less heat.
Wow, that's weird. It was supposed to do the opposite, it was supposed to create heat.

> ... but it almost burns you.
Same with me.

> When I took the computer apart to clean I saw that some of the wires have paper labels that are turning brown. Has me a little worried.
Believe me, you should be. If your computer has reached the point of burning paper... :S
Have you already taken it to the repair service?

---

### Post by Dex73 on 2009-05-09
Not yet. There has to be something that can be done about it. And on yours, it sounds like it's getting really hot too. Maybe just as hot internally. Mine would get this hot occasionally when I had vista running on it, but not all the time like it does now. I think there maybe some program that runs in the background causing this but I haven't been able to find anything about it on the web.

---

### Post by Ceyx on 2009-05-09
You guys would do well to do a search in the forums for 

"Toshiba Fan"

there are a bazillion entries - some fixes work and some don't ( at least for me )....many overheating issues and overcooling issues 

Check it out !

Ciao !

---

### Post by Pyker on 2009-05-10
Thanks, I'll do that now.

I'll tell you later if it worked or not.

[EDIT]
Checking the log files of Ubuntu, I found out that my computer has some serious problems with ACPI, like:
```
May 10 01:18:48 pedro-laptop kernel: [   30.391258] APIC error on CPU0: 00(40)
May 10 01:18:48 pedro-laptop kernel: [   30.391263] APIC error on CPU1: 00(40)
May 10 01:19:23 pedro-laptop kernel: [   65.317005] APIC error on CPU0: 40(40)
May 10 01:19:23 pedro-laptop kernel: [   65.317011] APIC error on CPU1: 40(40)
```
and
```
May  8 10:34:59 pedro-laptop kernel: [41258.989280] APIC error on CPU1: 40(40)
May  8 10:34:59 pedro-laptop kernel: [41258.989285] APIC error on CPU0: 40(40)
May  8 11:22:31 pedro-laptop kernel: [44110.716644] APIC error on CPU0: 40(40)
May  8 11:22:31 pedro-laptop kernel: [44110.716652] APIC error on CPU1: 40(40)
May  8 11:31:18 pedro-laptop kernel: [44637.540003] APIC error on CPU1: 40(40)
May  8 11:31:18 pedro-laptop kernel: [44637.540010] APIC error on CPU0: 40(40)
May  8 11:48:46 pedro-laptop kernel: [45685.532003] APIC error on CPU1: 40(40)
May  8 11:48:46 pedro-laptop kernel: [45685.532010] APIC error on CPU0: 40(40)
May  8 12:10:07 pedro-laptop kernel: [46966.800006] APIC error on CPU1: 40(40)
May  8 12:10:07 pedro-laptop kernel: [46966.800012] APIC error on CPU0: 40(40)
May  8 12:10:07 pedro-laptop kernel: [46967.092003] APIC error on CPU1: 40(40)
May  8 12:10:07 pedro-laptop kernel: [46967.092010] APIC error on CPU0: 40(40)
May  8 12:10:09 pedro-laptop kernel: [46969.296006] APIC error on CPU1: 40(40)
May  8 12:10:09 pedro-laptop kernel: [46969.296013] APIC error on CPU0: 40(40)
May  8 12:10:10 pedro-laptop kernel: [46969.612006] APIC error on CPU1: 40(40)
May  8 12:10:10 pedro-laptop kernel: [46969.612013] APIC error on CPU0: 40(40)
May  8 12:10:11 pedro-laptop kernel: [46970.632006] APIC error on CPU1: 40(40)
May  8 12:10:11 pedro-laptop kernel: [46970.632013] APIC error on CPU0: 40(40)
May  8 12:10:11 pedro-laptop kernel: [46970.644003] APIC error on CPU1: 40(40)
May  8 12:10:11 pedro-laptop kernel: [46970.644010] APIC error on CPU0: 40(40)
May  8 12:10:29 pedro-laptop kernel: [46988.528003] APIC error on CPU1: 40(40)
May  8 12:10:29 pedro-laptop kernel: [46988.528010] APIC error on CPU0: 40(40)
May  8 12:10:29 pedro-laptop kernel: [46988.560003] APIC error on CPU1: 40(40)
May  8 12:10:29 pedro-laptop kernel: [46988.560007] APIC error on CPU0: 40(40)
May  8 12:10:29 pedro-laptop kernel: [46989.212005] APIC error on CPU1: 40(40)
May  8 12:10:29 pedro-laptop kernel: [46989.212011] APIC error on CPU0: 40(40)
May  8 12:10:30 pedro-laptop kernel: [46989.836004] APIC error on CPU1: 40(40)
May  8 12:10:30 pedro-laptop kernel: [46989.836010] APIC error on CPU0: 40(40)
May  8 12:10:30 pedro-laptop kernel: [46990.128004] APIC error on CPU1: 40(40)
May  8 12:10:30 pedro-laptop kernel: [46990.128010] APIC error on CPU0: 40(40)
May  8 12:10:30 pedro-laptop kernel: [46990.244004] APIC error on CPU1: 40(40)
May  8 12:10:30 pedro-laptop kernel: [46990.244010] APIC error on CPU0: 40(40)
May  8 12:10:31 pedro-laptop kernel: [46990.804005] APIC error on CPU1: 40(40)
May  8 12:10:31 pedro-laptop kernel: [46990.804012] APIC error on CPU0: 40(40)
May  8 12:10:31 pedro-laptop kernel: [46991.060005] APIC error on CPU1: 40(40)
May  8 12:10:31 pedro-laptop kernel: [46991.060011] APIC error on CPU0: 40(40)
May  8 12:10:34 pedro-laptop kernel: [46994.016006] APIC error on CPU1: 40(40)
May  8 12:10:34 pedro-laptop kernel: [46994.016013] APIC error on CPU0: 40(40)
May  8 12:10:34 pedro-laptop kernel: [46994.044003] APIC error on CPU1: 40(40)
May  8 12:10:34 pedro-laptop kernel: [46994.044009] APIC error on CPU0: 40(40)
May  8 12:19:24 pedro-laptop kernel: [47523.528004] APIC error on CPU1: 40(40)
May  8 12:19:24 pedro-laptop kernel: [47523.528010] APIC error on CPU0: 40(40)
May  8 14:00:44 pedro-laptop kernel: [53603.859846] APIC error on CPU0: 40(40)
May  8 14:00:44 pedro-laptop kernel: [53603.859853] APIC error on CPU1: 40(40)
May  8 14:21:19 pedro-laptop kernel: [54838.944006] APIC error on CPU1: 40(40)
May  8 14:21:19 pedro-laptop kernel: [54838.944013] APIC error on CPU0: 40(40)
May  8 14:21:19 pedro-laptop kernel: [54838.952002] APIC error on CPU1: 40(40)
May  8 14:21:19 pedro-laptop kernel: [54838.952007] APIC error on CPU0: 40(40)
May  8 14:21:19 pedro-laptop kernel: [54839.316006] APIC error on CPU1: 40(40)
May  8 14:21:19 pedro-laptop kernel: [54839.316011] APIC error on CPU0: 40(40)
May  8 14:21:20 pedro-laptop kernel: [54839.596006] APIC error on CPU1: 40(40)
May  8 14:21:20 pedro-laptop kernel: [54839.596011] APIC error on CPU0: 40(40)
May  8 14:21:20 pedro-laptop kernel: [54839.676005] APIC error on CPU1: 40(40)
May  8 14:21:20 pedro-laptop kernel: [54839.676011] APIC error on CPU0: 40(40)
May  8 14:21:20 pedro-laptop kernel: [54839.736003] APIC error on CPU1: 40(40)
May  8 14:21:20 pedro-laptop kernel: [54839.736008] APIC error on CPU0: 40(40)
May  8 14:21:20 pedro-laptop kernel: [54839.744003] APIC error on CPU1: 40(40)
May  8 14:21:20 pedro-laptop kernel: [54839.744007] APIC error on CPU0: 40(40)
May  8 14:21:21 pedro-laptop kernel: [54840.608006] APIC error on CPU1: 40(40)
May  8 14:21:21 pedro-laptop kernel: [54840.608013] APIC error on CPU0: 40(40)
May  8 14:21:21 pedro-laptop kernel: [54840.692003] APIC error on CPU1: 40(40)
May  8 14:21:21 pedro-laptop kernel: [54840.692007] APIC error on CPU0: 40(40)
May  8 14:21:21 pedro-laptop kernel: [54840.972006] APIC error on CPU1: 40(40)
May  8 14:21:21 pedro-laptop kernel: [54840.972012] APIC error on CPU0: 40(40)
May  8 14:21:21 pedro-laptop kernel: [54841.048003] APIC error on CPU1: 40(40)
May  8 14:21:21 pedro-laptop kernel: [54841.048009] APIC error on CPU0: 40(40)
May  8 14:21:21 pedro-laptop kernel: [54841.352006] APIC error on CPU1: 40(40)
May  8 14:21:21 pedro-laptop kernel: [54841.352013] APIC error on CPU0: 40(40)
May  8 14:21:22 pedro-laptop kernel: [54841.780006] APIC error on CPU1: 40(40)
May  8 14:21:22 pedro-laptop kernel: [54841.780012] APIC error on CPU0: 40(40)
May  8 14:21:23 pedro-laptop kernel: [54842.828006] APIC error on CPU1: 40(40)
May  8 14:21:23 pedro-laptop kernel: [54842.828012] APIC error on CPU0: 40(40)
May  8 14:21:23 pedro-laptop kernel: [54843.492004] APIC error on CPU1: 40(40)
May  8 14:21:23 pedro-laptop kernel: [54843.492010] APIC error on CPU0: 40(40)
May  8 14:21:24 pedro-laptop kernel: [54843.592006] APIC error on CPU1: 40(40)
May  8 14:21:24 pedro-laptop kernel: [54843.592011] APIC error on CPU0: 40(40)
May  8 14:21:24 pedro-laptop kernel: [54843.864006] APIC error on CPU1: 40(40)
May  8 14:21:24 pedro-laptop kernel: [54843.864012] APIC error on CPU0: 40(40)
May  8 14:21:24 pedro-laptop kernel: [54844.288006] APIC error on CPU1: 40(40)
May  8 14:21:24 pedro-laptop kernel: [54844.288011] APIC error on CPU0: 40(40)
May  8 14:21:24 pedro-laptop kernel: [54844.360006] APIC error on CPU1: 40(40)
May  8 14:21:24 pedro-laptop kernel: [54844.360013] APIC error on CPU0: 40(40)
May  8 14:21:24 pedro-laptop kernel: [54844.484005] APIC error on CPU1: 40(40)
May  8 14:21:24 pedro-laptop kernel: [54844.484010] APIC error on CPU0: 40(40)
May  8 14:21:43 pedro-laptop kernel: [54863.368005] APIC error on CPU1: 40(40)
May  8 14:21:43 pedro-laptop kernel: [54863.368012] APIC error on CPU0: 40(40)
May  8 14:21:44 pedro-laptop kernel: [54863.560005] APIC error on CPU1: 40(40)
May  8 14:21:44 pedro-laptop kernel: [54863.560010] APIC error on CPU0: 40(40)
May  8 14:21:44 pedro-laptop kernel: [54864.136005] APIC error on CPU1: 40(40)
May  8 14:21:44 pedro-laptop kernel: [54864.136011] APIC error on CPU0: 40(40)
May  8 14:21:44 pedro-laptop kernel: [54864.432005] APIC error on CPU1: 40(40)
May  8 14:21:44 pedro-laptop kernel: [54864.432012] APIC error on CPU0: 40(40)
May  8 14:21:45 pedro-laptop kernel: [54864.580005] APIC error on CPU1: 40(40)
May  8 14:21:45 pedro-laptop kernel: [54864.580010] APIC error on CPU0: 40(40)
May  8 14:21:45 pedro-laptop kernel: [54865.372006] APIC error on CPU1: 40(40)
May  8 14:21:45 pedro-laptop kernel: [54865.372012] APIC error on CPU0: 40(40)
May  8 14:21:46 pedro-laptop kernel: [54865.596003] APIC error on CPU1: 40(40)
May  8 14:21:46 pedro-laptop kernel: [54865.596009] APIC error on CPU0: 40(40)
May  8 14:21:46 pedro-laptop kernel: [54865.636002] APIC error on CPU1: 40(40)
May  8 14:21:46 pedro-laptop kernel: [54865.636007] APIC error on CPU0: 40(40)
May  8 14:21:46 pedro-laptop kernel: [54865.644000] APIC error on CPU1: 40(40)
May  8 14:21:46 pedro-laptop kernel: [54865.644004] APIC error on CPU0: 40(40)
May  8 14:21:46 pedro-laptop kernel: [54865.656000] APIC error on CPU1: 40(40)
May  8 14:21:46 pedro-laptop kernel: [54865.656004] APIC error on CPU0: 40(40)
May  8 14:21:46 pedro-laptop kernel: [54865.920006] APIC error on CPU1: 40(40)
May  8 14:21:46 pedro-laptop kernel: [54865.920012] APIC error on CPU0: 40(40)
May  8 14:21:47 pedro-laptop kernel: [54867.224006] APIC error on CPU1: 40(40)
May  8 14:21:47 pedro-laptop kernel: [54867.224013] APIC error on CPU0: 40(40)
May  8 14:21:47 pedro-laptop kernel: [54867.472006] APIC error on CPU1: 40(40)
May  8 14:21:47 pedro-laptop kernel: [54867.472013] APIC error on CPU0: 40(40)
May  8 14:21:48 pedro-laptop kernel: [54867.788005] APIC error on CPU1: 40(40)
May  8 14:21:48 pedro-laptop kernel: [54867.788011] APIC error on CPU0: 40(40)
May  8 14:21:48 pedro-laptop kernel: [54867.964005] APIC error on CPU1: 40(40)
May  8 14:21:48 pedro-laptop kernel: [54867.964011] APIC error on CPU0: 40(40)
May  8 14:21:49 pedro-laptop kernel: [54868.664006] APIC error on CPU1: 40(40)
May  8 14:21:49 pedro-laptop kernel: [54868.664013] APIC error on CPU0: 40(40)
May  8 14:21:49 pedro-laptop kernel: [54868.668003] APIC error on CPU1: 40(40)
May  8 14:21:49 pedro-laptop kernel: [54868.668008] APIC error on CPU0: 40(40)
May  8 14:21:50 pedro-laptop kernel: [54869.544006] APIC error on CPU1: 40(40)
May  8 14:21:50 pedro-laptop kernel: [54869.544012] APIC error on CPU0: 40(40)
May  8 14:21:50 pedro-laptop kernel: [54869.572004] APIC error on CPU1: 40(40)
May  8 14:21:50 pedro-laptop kernel: [54869.572009] APIC error on CPU0: 40(40)
May  8 14:21:50 pedro-laptop kernel: [54870.048005] APIC error on CPU1: 40(40)
May  8 14:21:50 pedro-laptop kernel: [54870.048012] APIC error on CPU0: 40(40)
May  8 15:02:46 pedro-laptop kernel: [57326.257320] APIC error on CPU1: 40(40)
May  8 15:02:46 pedro-laptop kernel: [57326.257325] APIC error on CPU0: 40(40)
```

I don't know if this will be any good, but the kern.log (the kernel log) is attached to this post.

---

### Post by cronos6 on 2009-05-20
Hi, 

  Glad to see I'm not alone. My Toshiba Satellite A210 overheat too. When the screen is close a couple of minute, you can't even put your hand back to the screen : insane. Fans are clean and here is the output :

```
root@catoshi:~# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +72.0°C  (crit = +102.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +64.0°C                                    
Core0 Temp:  +67.0°C                                    
Core1 Temp:  +66.0°C                                    
Core1 Temp:  +65.0°C    
```  

And I have also the same APIC errors :

```
May 20 19:19:27 catoshi kernel: [   87.503793] Clocksource tsc unstable (delta = -81071981 ns)
May 20 19:19:38 catoshi kernel: [   98.204029] eth0: no IPv6 routers present
May 20 21:06:59 catoshi kernel: [ 6539.729329] APIC error on CPU1: 00(40)
May 20 21:06:59 catoshi kernel: [ 6539.729345] APIC error on CPU0: 00(40)
May 20 21:17:13 catoshi kernel: [ 7154.010013] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
May 20 21:28:57 catoshi kernel: [ 7857.728460] APIC error on CPU0: 40(40)
May 20 21:28:57 catoshi kernel: [ 7857.728479] APIC error on CPU1: 40(40)
May 20 21:30:07 catoshi kernel: [ 7927.431592] APIC error on CPU1: 40(40)
May 20 21:30:07 catoshi kernel: [ 7927.431610] APIC error on CPU0: 40(40)
May 20 21:32:52 catoshi kernel: [ 8092.422102] APIC error on CPU1: 40(40)
May 20 21:32:52 catoshi kernel: [ 8092.422123] APIC error on CPU0: 40(40)
May 20 21:44:00 catoshi kernel: [ 8760.125011] APIC error on CPU0: 40(40)
May 20 21:44:00 catoshi kernel: [ 8760.125030] APIC error on CPU1: 40(40)
May 20 22:08:03 catoshi kernel: [10203.533011] APIC error on CPU0: 40(40)
May 20 22:08:03 catoshi kernel: [10203.533030] APIC error on CPU1: 40(40)
May 20 22:25:11 catoshi kernel: [11231.945018] APIC error on CPU1: 40(40)
May 20 22:25:11 catoshi kernel: [11231.945034] APIC error on CPU0: 40(40)
May 20 22:29:24 catoshi kernel: [11484.235558] APIC error on CPU0: 40(40)
May 20 22:29:24 catoshi kernel: [11484.235576] APIC error on CPU1: 40(40)
May 20 22:35:09 catoshi kernel: [11829.464011] APIC error on CPU1: 40(40)
May 20 22:35:09 catoshi kernel: [11829.464028] APIC error on CPU0: 40(40)
May 20 22:40:56 catoshi kernel: [12176.835870] APIC error on CPU1: 40(40)
May 20 22:40:56 catoshi kernel: [12176.835884] APIC error on CPU0: 40(40)
May 20 22:42:03 catoshi kernel: [12243.738166] APIC error on CPU0: 40(40)
May 20 22:42:03 catoshi kernel: [12243.738183] APIC error on CPU1: 40(40)
May 20 23:07:34 catoshi kernel: [13774.273017] APIC error on CPU1: 40(40)
May 20 23:07:34 catoshi kernel: [13774.273032] APIC error on CPU0: 40(40)
May 20 23:07:48 catoshi kernel: [13788.301572] APIC error on CPU0: 40(40)
May 20 23:07:48 catoshi kernel: [13788.301592] APIC error on CPU1: 40(40)
May 20 23:31:12 catoshi kernel: [15192.457513] APIC error on CPU1: 40(40)
May 20 23:31:12 catoshi kernel: [15192.457527] APIC error on CPU0: 40(40)
May 20 23:50:10 catoshi kernel: [16330.528011] APIC error on CPU1: 40(40)
May 20 23:50:10 catoshi kernel: [16330.528028] APIC error on CPU0: 40(40)
May 21 00:10:19 catoshi kernel: [17539.361011] APIC error on CPU0: 40(40)
May 21 00:10:19 catoshi kernel: [17539.361029] APIC error on CPU1: 40(40)
May 21 00:14:39 catoshi kernel: [17799.422662] APIC error on CPU0: 40(40)
May 21 00:14:39 catoshi kernel: [17799.422677] APIC error on CPU1: 40(40)
May 21 00:41:15 catoshi kernel: [19395.509024] APIC error on CPU1: 40(40)
May 21 00:41:15 catoshi kernel: [19395.509038] APIC error on CPU0: 40(40) 
```   

Any ideas plz?

---

### Post by Pyker on 2009-05-31
Does anyone have another suggestion besides the ones that were already spoken of?

Thank you,
Pedro Cunha

---

### Post by Pyker on 2009-06-04
*Bump*

---

### Post by Duckter on 2009-06-04
```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +44.0°C                                    
Core1 Temp:  +46.0°C  
```Dunno if this helps with the overheating but I havent had any problems with heat from my A215 recently. I did add noapic to the end of my kernel line in /boot/grub/menu.lst as in...

```
title        Ubuntu 8.10, kernel 2.6.27-14-generic
uuid        ec7648e3-6c64-432b-bf8b-6af2877ee843
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=ec7648e3-6c64-432b-bf8b-6af2877ee843 ro **noapic **
initrd        /boot/initrd.img-2.6.27-14-generic
```Hope this helps or at least solves part of the problem.

---

### Post by peterwil on 2009-06-14
> **Pyker said:**
> Does anyone have another suggestion besides the ones that were already spoken of?

Thank you,
Pedro Cunha

Please see this thread..
[http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt)

Also please file a launchpad bug..This has been a problem with
Toshibas (Ubuntu) for a long time. About time there is a good clean fix for overheating issues with Toshiba.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/382806](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/382806)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/113081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/113081)

---

### Post by Pyker on 2009-07-02
Thank you all for your support.

Amazingly, my computer's only problem was dirt! I sent it to repair, and all they did it was "internal cleaning".

So, my problem is solved.
Unfortunatly, this problem (the real problem -- not the dirt problem) affects several people that just can't fix it by cleaning, since that ain't the problem.

Here's what I think: I guess Toshiba made Satellite A210/A215 with defects and now they won't take reponsability for their acts.

That said, I wish the best luck to all the people that suffer from this problem, and @peterwill, yes, it's about time that there is a solution, at least software-based, for this problem.

@moderators: Please don't close this thread, since it is solved for me, but not for the rest.

Also, @petterwill: I don't think the problem is OS-related. I guess it's either hardware or BIOS-related. But yes, the computer does get cooler while running Ubuntu, don't know exactly why (he must like Ubuntu :lolflag:).

---

### Post by congojack on 2010-06-18
Ahaa finally a thread that relates to my problem. I am in the same boat i have emailed toshiba countless times about this problem only to get back vague scripted responses about dirt etc, the insides of my laptop are squeeky clean, ever since the first day i got this laptop it has overheated to an immensely hot temperature.
 
It shouldnt be up to us to fix this problem but anyone with it should get a Belkin Cooling pad [http://www.belkin.com/IWCatProductPage.process?Product_Id=472610](http://www.belkin.com/IWCatProductPage.process?Product_Id=472610) i got one about a year and a half ago and it's still doing a great job and it's dead cheap.
 
I dont know what toshiba were thinking, when the first A210 came hot off the assembly lines, literally, they should have realised this problem, or maybe they did but like most companies try to play on the naivity of the common consumer and just sent them all out with an "ah sure it'll be grand" attitude. This is a very common thing with this make of laptop and you all are not alone, i have tried literally everything and i have alot of other problems unrelating to this forum but my best advice would be to get a cooling pad and with your laptop propped on the cooling pad, email toshiba saying you want the $20 or euros for the cost of their failure and an explanation. Good luck.

---

