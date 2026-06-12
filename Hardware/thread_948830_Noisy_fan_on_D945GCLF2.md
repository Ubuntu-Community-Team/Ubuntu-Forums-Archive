---
title: "Noisy fan on D945GCLF2"
date: 2008-10-15
forum: Hardware
---

### Post by hinge on 2008-10-15
Hi 

Just bought a D945GCLF2 with the new ATOM CPU. I gonna use it as a media portal with XBMC. I have most of it running by now an I gotta say that this is a nice mobo - especially compared to the cost.

My only problem is that I think that the fan on top on the graphics chip is very noisy. In the bios there is an option about controlling the speed. so I tried enabling this and setting up lm-sensors and fancontrol - but nothing happens. It's like the speed can not be controlled.

Has anybody tried and succeeded in noising down the fan on this board ?
Any ideas ?

I read that some guy simply replaced the fan with a scythe fan and that had solved it - would that be enough ?

I would like to be able to control the fan - I do that on an other (AMD) computer that I have - that really nice...

---

### Post by ifallacy on 2008-10-17
I replaced the fan on my D945GCLF2 with a scythe fan from newegg and the loudest thing in my server setup now are the hard drives - make sure you get a scythe fan with the right height though, mine is way too tall, so it's mounted on top of the actual heatsink, instead of right inbetween the top and bottom - i think i read somewhere that you want the 10mm tall ones (so i think that's 40x10mm)

quick question - what version of ubuntu are you running? my 8.04.1 64bit seems to act up quite a bit, esp. with regards to the network card - the output of ifconfig always shows tons of dropped packets

---

### Post by hinge on 2008-10-18
Hi,

Thanks for your reply. Ill try the scythe fan. I've never gotten around to the 64 bit stuff on any of my computers. I'm running the newest ubuntu 32 bit om my board and it is doing just fine - for me...anyway

---

### Post by C.S.Cameron on 2008-10-19
Yeah, that fan is loud, I stuck my wife's D945GCLF into a cigar box that has a hole right over the fan.
I understand that the fan is on top of the GPU and not the CPU.
Her's works fine with 32 bit, haven't tried with 64.
Any idea if the s-video is working with Ubuntu on the D945GCLF2?
I've been trying to find out for weeks.

---

### Post by esaym on 2008-11-01
Could someone please install lm-sensors and run sensor-detect and see if this board has any supported sensors?

Thanks,
Sam

---

### Post by hinge on 2008-11-02
Hi easym,

i have lm-sensors installed and I get all the read otus on temps and rpms...I do have problems controlling the speed of the gpu fan - it just does not regulate...
I can post at dump of the sensors command later - I'm not at that computer now.

Did anybody succeed in controlling the gpu fan ??

---

### Post by grcodal on 2008-11-02
I've removed the gpu fan about 7 days ago and no problems so far, the gpu temp remains below 60C at around 56C.

---

### Post by esaym on 2008-11-02
> **hinge said:**
> Hi easym,

i have lm-sensors installed and I get all the read otus on temps and rpms...I do have problems controlling the speed of the gpu fan - it just does not regulate...
I can post at dump of the sensors command later - I'm not at that computer now.

Did anybody succeed in controlling the gpu fan ??

ah that is great.  I was thinking about using this board to replace the guts in my web server mainly to reduce power requirements.  But as I read it seems people are reporting power usage of 30-50 watts depending on the set up.  Seems pretty high for a cpu that only draws 2 watts idle.  For reference my pentium 3 is rated at a 20 watt idle draw and the whole box is 45 watts idle.

---

### Post by dankuoni on 2008-11-04
I've also removed the gpu fan. With a big (and slow ~1000 rpm) case fan near the gpu and cpu the temperature is around 38°C in idle mode and 57°C under full load.

*dankuoni

---

### Post by hinge on 2008-11-05
I just replaced the gpu fan with a mini kaze from scythe - zero noise !!!
Sweet

Now I just need to replace the chassis fan. Anybody have  a recommendation for a 6 x 6 x 1 SILENT fan ?
Can't find one from scythe that match the dimension

---

### Post by stek79 on 2008-11-10
Hi guys,
   I'm delighted to see some ubuntu users owning this board!

I'm considering to buy it too, do you find that it's fast enough for a net-based use case? Say firefox, pidgin, transmission, skype...

I have some questions, if somebody is so kind to reply it would be great:

1) for those who have removed the fan, you are running with the case fan or without _any_ fan?

2) can you check if gnome-power-statistics gives the current power consumption of the board, just like it does on a laptop? If yes, what kind of power draw did you get (screenshots are wellcome :) ?

3) hw question. Which PSU are you using?

Many thanks in advance guys, go ubuntu!

---

### Post by hinge on 2008-11-10
I just wanted to add my "final-so-far" specs and usecase for this board.

I have mounted the board into a [morex cubid 3688]("http://www.morex.com.tw/products/productdetail.php?fd_id=37") chassis. The size of this cigarbox is unbelievable 21x25x6,5 cm. I not sure how many watts the built in mini PSU gives - but I have not had problems so far. The chassis has two USB plugs on the front side that works nicely with the board. There is no audio up front  - thats OK with me though. The Chassis fan is a little noisy but I have that under control using fancontrol - I might change it in the near future if I can find a scythe with dimensions 6x6x1 cm

Inside the chassis I have the D945GCLF2 board with 2 gigs of ram and a 2.5" SATA2 320 GB SEAGATE MOMENTUS 5400.5 8MB harddisk. I exchanged the fan on the GPU with a Scythe Mini-Kaze 40x40x10mm - it is SILENT. I have no CD rom drive - I could slip a slimline in there but I have no need for it. The tiny chassis has a downside; it's hard to get rid of all the heat temperatures rise to 63 degC

I am using this cigarbox as a multimedia portal (just came up with that word) in our living room. So I have Ubuntu Hardy and XBMC on it. I have 3 kids so all our cartoons and disney movies have been ripped to XVID and are stored on the box or streamed from our main computer via samba, some 150 - 200 movies  - my two oldest kids (6 and 8 years old) master XBMC. Also all our CD (some 40 GB of music) and pictures + home video are accessible via XBMC. + all the other stuff internet radio and youtube ...

For mail I use thunderbird and browsing firefox (of cause).

Forgot the most important part - the box is connected to our 32 inch flatscreen (I know it's tiny...). To control the thing I've bought a logitech DiNovo mini keyboard - I have all keys + pad working on that thing (despite what you might find elsewhere on the net - I'v posted some stuff on xbmc forums). The DiNovo is what brings it all together...

The overall impression is, now that everything is working, that it performs great for xbmc, mail, music, surfing. I tried running Google earth, but that I could not do - it did not perform at all, don't know why

I'm in Denmark and I have paid around 400 euros for the whole thing...

---

### Post by throke on 2008-12-01
Not really an Ubuntu guy(my first time trying to dual boot Ubuntu/xp) anyway, I've been dickin around with this board since I got it a week ago. Try *speedfan* to monitor temps and fan speeds, I've found it works the best out of most of them and its free. other then that I cant seem to get this thing to dual boot(only goes to windows w/ no grub menu at startup???? sorry, I'm newer than a nubie. Anyway google 40x40x10 fans w/three pin connector. I bought a 3500 rpm 14 db fan from newegg and it seems to be a hell of a lot quieter then the stock one. I've also done a lot of reading that the heatsink was problematic for psu box being in the way so I ordered a low-pro one from mini-box, mine came with a low profile HS so they must have corrected this. I do like the mini-box HS better(more fins)

---

### Post by Ray_GTI-R on 2008-12-05
OK, my D945GCLF2 board came with the (latest low-profile Northbridge heatsink fitted with a 40mm x 40mm x 10mm fan made by T&T, ref 4010H12S NF1 0.16A 12VDC.
Worked fine for almost two weeks @ 30 - 60 minutes a day ... then went noisy.
A slight tap quietened it (I have it fitted to a heavily modified HSPC Tech Station like the Top Mount design only much better, so playing about is easy).
Then it took two taps ... eventually it just stayed noisy.
I took the fan off (removed the Intel-intentionally-wobbly Northbridge heatsink [see documentation on Intels website] as that's safer than trying to fix a fan in situ onto a bare silicon chip).
I tested the original fan independently and  ... it's horrible. The plastic fan chassis is incredibly thin at 3 points. It does not benefit from structurally inbuilt webbing at all, so any deformation e.g., by heat etc is directly transferred to the weakest areas.
I replaced this cheap, nasty Intel / T&T item with a top-of-the-range Papst drop-in replacement see Ebay item id 360105094024, using ShinEtsu Microsi paste.
STOP!!!
Any such "modification" invalidates the Intel 3-year warranty. I read elsewhere that Intel requires such trivial fixes to undergoe a RMA process FOR THE BARD NOT SIMPLY THE FAN that can take weeks ... if eventually approved by Intel. Given the 3 year warranty, I anticipate Intel is swamped and will continue to be until they replace the truly awful T&T fan with something better.
WARNING!!!
Replacing the Northbridge heatsink with a passive alternative is dangerous. The Northbridge fan also cools the (again, awful both in shape, efficiency and position) CPU heatsink. It also sends air over the exposed Southbridge chip to cool it (YUK!). My Southbridge chip was always pretty warm so I have fitted BGA ramsinks to the Southbridge and they do the job very nicely, cooled by the new fan.
I have been running this setup for over 3 weeks almost non-stop for testing other stuff like a PCI graphics card that runs under VISTA Ultimate etc etc and ... it works. Quiet, cool & a cheap fix.
I'm posting this here because I honestly believe this simple solution will help other owners of the noisy D945GCLF2 board to get the best out of a superb CPU and without full knowledge they may waste lots of time, effort & money.
FWIW BIOS temps @ ambient 21C:-
Startup
CPU ...............  37
Internal ..........  28
Remote ........... 32
After 10 minutes
CPU ...............  38
Internal ..........  28
Remote ........... 33
FWIW
As most people know,  BIOS temperatures are true, reliable (no O/S effect) and represent good working data for CPU usage at moderately high CPU usage.

---

### Post by maerki on 2008-12-12
Concerns: INTEL D945GCLF2 / Ubuntu 8.10

> Background: The board supports to fans: The CHIPSET-Fan and the CHASSIS-Fan. According to the specification of the board only the CHASSIS-Fan may run at variable speed. But the fan is connected to the header which only runs at full speed. So all we have to do is to plug the fan in to the other header - the rest is straight forward.

This is how to run the fan quietly at variable speed:

**IMPORTANT: Disconnect the Chipset-Fan cable and connect it to the Chassis-Fan Header which is located next to the edge of the board.**

In die BIOS: Leave the default settings: [FONT="Courier New"]System Fan Control <Enable>[/FONT].

Install lm-sensors
```
apt-get install lm-sensors
```

Run [FONT="Courier New"]sensors-detect[/FONT]

Edit [FONT="Courier New"]/etc/modules[/FONT] to make sure that the required modules will be loaded:

```
# cat /etc/modules
fuse
lp

# Generated by sensors-detect on Thu Dec 11 23:44:51 2008
# I2C adapter drivers
i2c-i801
# Chip drivers
smsc47m192
smsc47m1

ac
thermal
processor
cpureq-userspace
```

Run ```
pwmconfig
```

This will produce [FONT="Courier New"]/etc/fancontrol[/FONT]. However, I edited
the file by myself.
```
# cat /etc/fancontrol
INTERVAL=10
FCTEMPS=hwmon1/device/pwm1=hwmon0/device/temp3_input
FCFANS= hwmon1/device/pwm1=hwmon1/device/fan1_input
MINTEMP=hwmon1/device/pwm1=30
MAXTEMP=hwmon1/device/pwm1=60
MINSTART=hwmon1/device/pwm1=40
MINSTOP=hwmon1/device/pwm1=40
MINPWM=hwmon1/device/pwm1=40
```

Try the configuration using
[FONT="Courier New"]/etc/init.d/fancontrol start[/FONT]

On my baord, I get the following temperatures and speed:
```
# sensors
smsc47m192-i2c-0-2d
Adapter: SMBus I801 adapter at 2000
+2.5V:       +2.55 V  (min =  +0.00 V, max =  +3.32 V)   
VCore:       +1.15 V  (min =  +0.00 V, max =  +2.99 V)   
+3.3V:       +3.37 V  (min =  +0.00 V, max =  +4.38 V)   
+5V:         +5.08 V  (min =  +0.00 V, max =  +6.64 V)   
+12V:       +12.25 V  (min =  +0.00 V, max = +15.94 V)   
VCC:         +3.37 V  (min =  +0.00 V, max =  +4.38 V)   
+1.5V:       +1.58 V  (min =  +0.00 V, max =  +1.99 V)   
+1.8V:       +1.77 V  (min =  +0.00 V, max =  +2.39 V)   
Chip Temp:   +30.0°C  (low  = -127.0°C, high = +127.0°C)  
CPU Temp:    +38.0°C  (low  = +33.0°C, high = +40.0°C)  
Sys Temp:    +35.0°C  (low  = -127.0°C, high = +127.0°C)  
cpu0_vid:   +2.050 V

smsc47m1-isa-0680
Adapter: ISA adapter
fan1:       3413 RPM  (min = 1280 RPM, div = 4)
fan2:          0 RPM  (min = 1280 RPM, div = 4)  ALARM
```
[/CODE]

The fan is running now nicely and quietly on about 3k RPM!

-----------------------------------------------------
On Ubuntu 9.10 the above does not work.
See: [https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/458811](https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/458811)

In **/boot/grub/menu.lst** add **acpi_enforce_resources=lax** instead of **quiet splash**, run **update-grub**, reboot the system and sensors works fine now.

---

### Post by maerki on 2008-12-12
.

---

### Post by JRV on 2008-12-14
I have an Intel D945GCLF board with the single core Atom processor.  It came with a taller heat sink with more fins and the same fan as on my D945GCLF2. For some reason this heatsink/fan combo runs almost sielent.  I swapped the heat sinks and that solved the problem.  I think the problem is that the fan sets up a vibration in the heatsink.

---

### Post by Betelgeuse on 2008-12-27
I have the same board and the fan was working full speed. There are two fan connectors on the mainboard, I connected that fan to the other connector and now it's controlling itself with the temperature. I think intel connected this fan to wrong connector.

---

### Post by hinge on 2008-12-27
Did any of you guys owning the D945GCLF2 have any problems using suspend and hibernate. None of the work for me - even though it should, according to the manual. 

Where can I find a guide for troubleshooting...
Any advice ?

I'm running hardy for now, but I'm planning to upgrade to intrepid.

Hinge

---

### Post by maerki on 2008-12-27
On intrepid, both hibernate and suspend seem to work ok.

---

### Post by hinge on 2008-12-27
Hi maerki,
you didn't do anything to make it work ?
Wonder if an upgrade to intrepid would make it work....

---

### Post by maerki on 2008-12-27
> **hinge said:**
> Hi maerki,
you didn't do anything to make it work ?
Wonder if an upgrade to intrepid would make it work....
I just installed intrepid out of the net.

---

### Post by Ray_GTI-R on 2008-12-29
Two things, in reply to earlier posts;-

1) that original noisy Intel fan. ... it's was still noisy even when removed from the heatsink & running free of any fixing.
HOWEVER ... after I left it lying around on my desk for a week or two I got bored over the Christmas break so "just for fun" I connected it back up to the chassis header at 100% RPMs and - not noisy anymore. I also tried running it mounting it vertically (removed from the heatsink) and it's even sweeter. *Weird or what!* It's as if the heatsink mounting somehow warps the fan. Easily done ... the original is a flimsy fan Par Excellence ;-)

2) it is Not A Good Idea to swap the CPU fan header onto the chassis fan header. The reason is that 
[INDENT]a) the 945 Northbridge is a hot-running chip so needs the best that the fan can give.
b) the Southbridge is the hottest running that I've ever seen (aside from those on broken mobos). I have many boards pass through my workshop and this one is naughty - I've added four MOSFET/BGA heatsinks which benefit from the N/B fan.
OK, the board WILL run if you swap the CPU/chaassis headers BUT it'll shorten the life of the components. No Doubt.[/INDENT]
HTH, Ray

---

### Post by Betelgeuse on 2008-12-30
> **Ray_GTI-R said:**
> Two things, in reply to earlier posts;-
b) the Southbridge is the hottest running that I've ever seen (aside from those on broken mobos). I have many boards pass through my workshop and this one is naughty - I've added four MOSFET/BGA heatsinks which benefit from the N/B fan.
OK, the board WILL run if you swap the CPU/chaassis headers BUT it'll shorten the life of the components. No Doubt.[/INDENT]
HTH, Ray

there are 3 temperature readings from this mainboard. I've setup the pwm fancontrol scritps in ubuntu to start the fan when the cpu gets 55 celcius and run full speed when it reach 60 C. Now I did not see any more than 57C. The other temperature redigns are way low, so I assume the board is safe. Which one of the redings is the southbridge temperature?
I have a big HTPC case with 4 80mm fans running lowest speed without noise and I think there is a good airflow in the pc case. Should I worry?

---

### Post by Zillion on 2009-01-29
I have put a fanless Zalman ZM-NBF47 heatsink on it. See [here]("http://www.davewsmith.com/blog/") where I got the instructions from.

What kinda speed you guys get with that Realtek NIC?

I get RX and TX rate like 35 MiB  (using bmon).

---

### Post by PatrikG on 2009-04-23
I changed my northbridge cooler to an Akasa AK-120 chipset cooler with the fan removed instead of using the crappy standard one. And I put a Nexus case fan on the lid (it will fit, tightly). CPU temps with the fan at it's highest setting is around 40oC, and at the lowest possible it's around 50 degrees.

The heatsink is a breeze to put on, just remove the old one and use the same wire-clip to put on the new one. No bending needed.

The case is a bit loud, but it serving as a file/music server and is stuck away in an another room from where I'm usually is, so the noise is no problem. But it's definitively quiter than before!

---

