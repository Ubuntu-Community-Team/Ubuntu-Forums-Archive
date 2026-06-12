---
title: "Problem-free graphic card?"
date: 2014-12-22
forum: Hardware
---

### Post by sleppythought on 2014-12-22
Hello everyone,

since some time now I am having a terrible problems with my Nvidia geforce 680 gtx. System freezes every dozen or so minutes while I play games, when I don't play sometimes it freezes sometimes it doesn't. I use Kubuntu 14.10 now but it all started few releases ago, I even tried Debian hoping that it will help, unfortunately it didn't. When I switch to Nvidia geforce 480 gtx everything runs perfectly! I lost hope of ever solving this issue and I decided to just buy a new graphic card.

So my question is:
Can you recommend a graphic card good enough for gaming(preferably Nvidia) that you find problem-free? I would hate to buy another card that would not cooperate with Kubuntu.

Thank you!

---

### Post by mörgæs on 2014-12-23
Before spending money you could try the development release 15.04.

---

### Post by pqwoerituytrueiwoq on 2014-12-23
If you card is factory overclocked and you are NOT using nvidia's driver i have had that issue
i have a 650 TI Boost and i have not had a single stability issues (except when testing OCs)
I softmoded my card to get a nice OC out of it

---

### Post by sleppythought on 2014-12-23
Thank you for your answers! 
Mörgæs I will definitely try it out.
Pqwoerituytrueiwoq I am using nvidia driver.

---

### Post by sleppythought on 2014-12-24
So, I have installed Kubuntu 15.04 on a separate partition and then installed Nvidia driver 340.65. After first reboot system froze... Here is the output from my syslog:

```
[  121.331400] NVRM: GPU at PCI:0000:01:00: GPU-b47b78f9-b9d9-272f-5f10-043e977b5633
[  121.331414] NVRM: Xid (PCI:0000:01:00): 62, 12b2(1fa0) 00000000 00000000
[  123.340745] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
[  125.337354] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
[  125.337379] [sched_delayed] sched: RT throttling activated
[  127.333988] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
[  129.330593] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
[  131.471674] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
```

I don't think trying older driver would help as I did it in the past with no result. Also even though I used exactly the same drivers for both graphic cards I had no problems with geforce 480 gtx.
I will try nvidia 346 driver later today and will let you know whether it helped.

---

### Post by sleppythought on 2014-12-25
I switched to 346 nvidia driver yesterday (on Kubuntu 14.10) since then my system froze 4 times...
After that I did sudo apt-get purge nvidia* and just choose recommended 340.65 from Driver Manager for now.
I'll be able to test my graphic card in a different desktop, with Debian distribution installed. 
I want to see if the problem will continue on a different machine.

---

### Post by Jacob_Goff on 2014-12-31
I like Raedon, it is good for gaming graphics, and works wonders with Linux if you get a high end one, but, I have a low end one and I seem to have a fondness for this graphics card, and I wouldn't have it any other way. Fortunately, it's good enough to work with tons of RAM and balance it out, or at-least so my friend tells me, and I never have any problems with it. I still have updates for it every month, and I've have my computer for 2 years. I have a Compaq Presario CQ57. Do NOT get the student edition like I did, you'll regret it, because you can't up/downgrade anything to make things better or more balanced, but it comes balanced as it is. My computer only cost about 300-400 dollars, and I saved for months to earn it after paying my bills for 4 months of savings, and I had 2 extra years of warranty. When I ran out of my warranty, I said "to hell with windows, I'm going to Linux." My computer works 4x better since I had windows, and the functionality level is beautious. As for freezing, have you tried updating your drivers with PlayOnLinux? I REALLY reccommend the Raedon AMD graphics card to you because it's both cheap and efficient for what you could pay and works just as good as any other graphics card.

---

### Post by efflandt on 2015-01-01
It is possible that the card may have a problem. Some time ago I had a cheap Galaxy GT 430 that began failing just after its 1 year warranty expired. In Win7 it would occasionally hang, then say something about "video driver stopped responding, recovered", regardless of trying different nvidia drivers. The symptom in Linux (11.10 at the time) was that response to keyboard and mouse clicks would suddenly stop (so it appeared to be locking up), but usually mouse cursor could still move. The only thing I could do at that point was a hard shutdown using the power button. Eventually it started throwing log errors during boot that the video card was not responding.

I replaced it with EVGA GTX 550 Ti (3 yr warranty) and no more problems in 11.10 or 12.04. I recently installed a GTX 750 Ti and did a fresh install of 14.04, which had some teething problems because the ancient nvidia-current 304 version did not support my new card with Maxwell chip. But I got that turned around by purging that and installing nvidia-331, and now ppa version 346.22 which supports adjusting video overclock in Nvidia X Server Settings (with --cool-bits=8, or 12 to also control fan, in nvidia-xconfig options).

---

### Post by tokyobadger on 2015-01-01
Your Xid 62 error code suggests [Hardware Error, Driver Error, or Thermal Issue](http://docs.nvidia.com/deploy/xid-errors/index.html) - it's not one that nvidia has categorized as "common" 

Reading around:
Hardware - check your connections (esp PSU to GPU), reseat GPU, RAM (possibly try different slots), try a different set of cables, try a new PSU
Driver - I'm using the nvidia-346 driver (xorg-edgers ppa) on 14.10 with 2 680GTX in SLI (AA mode) - I've used all of the 300 series with this set up (bar of course the 14.10 - I upgrade rather than reinstall)
Thermal - try a clean up of internal components with compressed air - esp the GPU fans

Google yields all manner of suggestions as nvidia error messages similar to yours are not new - without knowing anything about your set-up other than OS and GPU, I'll put one them here - when you next boot up modify the boot options at the grub prompt (press e) as follows (change /dev/sda1 for your ubuntu partition)

```
... root=/dev/sda1 ro quiet nolapic_timer ...
```

---

### Post by sleppythought on 2015-01-06
Thank you for all the answers,

Jacob_Goff it did cross my mind to try out Radeon but I was using Nvidia my whole life and I think it would be to big a step for me to switch to it now...


Efflandt as I informed in a previous posts this card was tested on a different machine and worked flawlessly.


Tokyobadger I too checked the information on this error code as well as tried to find an answer to my problem on various forums and websites.
I did check my connections to PSU and GPU more then once and I used a different nvidia card for some time with no problems whatsoever( that&#8217;s why I think that it's not the connections, because different card wouldn't work either) On the other hand my card was tested, for over a month, on a different machine with Windows installed and it worked perfectly(I assumed, that it's not connectors on the card itself either, because we would experience some issues on this second machine then).
I tried reseating my GPU, tried different slots for RAM - nothing.
If by trying out different set of cables you mean the ones connecting PSU with other components, then it's not possible because they are not detachable in my PSU.


I will try to lay my hands on a different PSU and try it out.


You telling me that you're using 680GTX cards, and with no problems, just adds to the chaos and helplessness that I'm felling. I was hoping that my problem has something to do with a card model and not my specific set-up.


I try to clean my hardware regularly also I'm experiencing this issue from the start. I doubt it's a dust in my fans. Said that, I will clean in anyway.


I just made suggested by you changes in Grub, unfortunately Kubuntu already froze...


There's one more thing but being inexperienced user I have no idea if this set-up is right or wrong let alone whether it may cause freezes. I have boot set up for EFI and not legacy. I don't have any Windows partitions and I am wondering if it makes any difference?




My machine specification:
Linux 3.16.0-28-generic
KDE 4.14.1
CPU Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz
RAM 2x Kingston 4096 MB DDR3 1333 MHz
Motherboard Asus P8Z77-V Deluxe
Graphics Evga Geforce GTX 680 2048MB
Hard Drive Western Digital Black 1TB (WD1002FAEX-00Y9A0) 7200rpm, 64mb cache internal 3.5" HDD
Case HAF 912 Plus (Fans: front 200mm led x1, top 200mm x1, rear 120mm x1

---

### Post by efflandt on 2015-01-06
One thing I don't think you have mentioned yet is what power supply (PSU) you are using. I don't know what the power draw of those cards are, but maybe you have enough for GTX 480, but not quite enough for GTX 680. You cannot necessarily go by total watts of the PSU because better ones may have more amps on the 12volt rail than cheaper ones.

---

### Post by sleppythought on 2015-01-07
You're right! I forgot about it.

PSU XFX PRO Series 650W Core Edition Full Wired

---

### Post by tokyobadger on 2015-01-07
Sorry to hear you're not having luck yet - I'll throw a few more ideas out

1) [According to ASUS you don't have "approved" RAM](http://dlcdnet.asus.com/pub/ASUS/mb/LGA1155/P8Z77-V_DELUXE/P8Z77-V_DELUXE_DRAM_QVL_201406.pdf) - not sure how significant that is but I came across several owners mentioning the mobo is RAM-fussy
2) [your mobo has all sorts of bells and whistles](http://www.asus.com/Motherboards/P8Z77V_DELUXE/) that look like they might interfere - "smart voltage control", CPU wattage cut in half! UEFI BIOS, etc 
3) You have integrated GPU - is that disabled in BIOS? 
4) Have you updated to latest BIOS?
5) Have you tried the GPU in a different slot?
6) Did this GPU and hardware set-up work together under windows?

Given what you listed for HW I'd think the PSU would be enough, but the PSU could also be the culprit. If you've set up properly and you're having these issues then either the PSU is bad, cables are bad, RAM is bad, mobo is bad, GPU is bad

---

### Post by sleppythought on 2015-01-16
I think the problemis solved, my system didn't freeze once over a last few days!


[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Itried all the things mentioned by Tokyobadger, aside from testinghardware under Windows (I don't own a copy of this OS). So I trieddifferent PSU, my BIOS was already updated and integrated GPUdisabled. And of course the last think I did (because it cannot bethat simple) I tried GPU in a different slot. And it works![/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Thankyou all for suggestions.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Tokyobadgeryou're the best! Thank you so much! I just hugged my computer![/FONT][/COLOR]

---

### Post by tokyobadger on 2015-01-16
Happy to hear things are working out for you. 
(Edit: thanks for marking solved)

---

