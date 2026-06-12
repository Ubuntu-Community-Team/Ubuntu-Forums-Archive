---
title: "Post your laptop temperature"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by nocturn on 2006-07-06
I'm monitoring my laptop temperature closely these days, as there's a heatwave here.

But I do not have much information about what is normal for laptops (outside the thermal guidelines for my CPU). 

So, this thread is about posting your laptop temperatures (CPU and others if you have them) idle and stressed together with the model and the CPU it uses (to be able to compare).  

I hope this is usefull to more people.

---

### Post by nocturn on 2006-07-06
My laptop: HP Pavilion ZV5474EA
CPU: AMD64 3400 (2.2Ghz)
NVIDIA GeForce4 440 Go

CPU sensor (via ACPI)
IDLE: 50 °C 
STRESSED: 60-70°C

* Room temperature is 27-30 °C

---

### Post by matthew on 2006-07-06
My laptop: AOpen 1557gls
CPU: Intel Pentium M (1.8Ghz)
ATI Mobility Radeon 9700 (128M)

CPU sensor (via ACPI)
IDLE: 50 °C 
STRESSED: 60-90°C

* Room temperature is 25-32 °C

---

### Post by dracolich on 2006-07-06
Inspiron E1405
CPU : CoreDuo T2300E
Graphic : Intel GMA 950

Idle : 30°C 
Load : 47-51°C 
Room temp : 26°C

---

### Post by maulattu on 2006-07-06
Acer TravelMate 654LC
CPU: Pentium4m 2.2.GHz (1.18 GHz)
RAM: 512MB DDR SDRAM
Graphic: ATI 7500 mobile 32MB [-( 

idle: 54°C
the fan runs when cpu temp reaches 64°C till it decreases to 54°C (about 1 min)
max temp reached: 71°C (during a heavy load)

---

### Post by bwayman on 2006-07-06
96.5  or you ment my CPU temp.

---

### Post by zgoda on 2006-07-06
HP nx6110
CPU: Celeron-M 360J (1.4 GHz)
RAM: 512M DDR SDRAM
Graphic: Intel GMA 915

Idle: 49 C
Load: 57-68 C

CPU fan is running all the time on my machine, but not on my wife's identical machine running Breezy. Cann't check the temperatures, though.

* room temp is approx 27 C

---

### Post by efreddi on 2006-07-06
Dell Latitude C600
Pentium III 850MHz
RAM: 256MB

idle: 50-60°C
load: arrives until 85°C and then start the fan and it drops to 70...
room temp around 26°C.



Elia

---

### Post by crazy___cow on 2006-07-06
Dell Inspiron 6000
CPU: Centrino 1.6 GHz
Video: Intel i915


Idle: 35-40 °C 
Stressed: 55-65 °C

---

### Post by Hellkeepa on 2006-07-06
HELLo!

Fujitsu Siemens Amilo Pro 2040
CPU: Centrino-M 1.6 GHz
Video: Intel 915

Idle: 49-50 C
Load: around 60-62 C
Room temp: 24-30 C

Note that these temps are taken on the -386 kernel, so I have very little in the way of power-management on the CPU (only freq. scaling). Also, the fan kicks in at temps above 50, which means it's running about 2-3 times a min (~5 sec bursts).

Happy codin'!

---

### Post by linuxworld on 2006-07-07
Idle: 41 °C
Stressed: 48-51 °C
Room temperature 25-30 °C

---

### Post by spier on 2006-07-07
Sony Vaio FS740W
Centrino 1.7GHz
Intel 915

Idle (0.8 MHz): ~38 Cº 
surfing (0.8 MHz): ~43 Cº
Stressed (1.7 GHz): 50-60 Cº (Fan Trigger: 60C)
Room temp: 15-20 Cº

---

### Post by Maggot on 2006-07-07
Dell XPS Gen2
CPU: Pentium M 2.13 GHz
Video: nVIDIA 6600 GO

Surfing net, listening to streaming music 47C
Room temp: 27C

---

### Post by mpalla on 2006-07-08
[Pavilion ze5702ea]("http://www.ubuntuforums.org/showthread.php?t=193506")
CPU: Intel(R) Celeron(R) CPU 2.80GHz
Room temp: 27 C
Idle after startup: 37 C
Surfing/streaming after 1h uptime: 49 C

temp going up with time up to 55-60 C (low CPU load)

---

### Post by 11hjpphty76lkjj on 2006-07-08
Dell Latitude C610

Idle 45-55C
Load 55-70C

this is a great thread by the way.  i've been trying to figure out how to get my laptop cooler...

---

### Post by Okami on 2006-07-08
Fujitsu-Siemens Amilo A
CPU 1.6 GHz
Idle 50-60 C
Stressed 60-70 (sometimes up to 84) C

I have a feeling the temperature is higher in Ubuntu 6.06. I wish it could be a little cooler actually.

---

### Post by disciple on 2006-07-08
Dell Inspiron 8200
Pentium 4-M 1.7 Ghz
GeForce 2 Go
768 Ram
Idle ~ 47- 52
Stressed ~53 - 60

(managed with i8kctl.. )

---

### Post by wiresquire on 2006-07-09
Mitac 8355
Mobile Athlon 64 3000+
RAM: 512MB

CPU idle normally just below 40°C (with light load - browsing etc): 
Medium: 40-50 °C. Fan (slow) comes on at 50, and blows till it's back down below 40.
load: 60 something? °C and the fan start the fan at high
room temp around 15-20°C.

Hard disk is a different story. Because laptop mode is not enabled and I have an older hard disk, it basically creeps up. Seems to level out around 53°C. Well, I've got a new hard disk on the way - was due for an upgrade :) -  so we'll see what happens...

ws

---

### Post by derakhshani on 2006-07-09
Sony Vaio VGN A230p
Centrino 1.6GHz
RAM 512 MB
ATI Radeon 9200

temperature: 52 C via acpi

---

### Post by printmkr on 2006-07-09
n00b question here... how are are you determining the CPU temperture of your machines? Is there a utility that does this? Thanks!

---

### Post by briguy on 2006-07-09
Gateway 200x
Centrino 1.4GHz

Idle (600MHz) 43-45C
Chugging (1.4GHz) 65-70C

---

### Post by mscman on 2006-07-09
> **printmkr said:**
> n00b question here... how are are you determining the CPU temperture of your machines? Is there a utility that does this? Thanks!
Use the command:
```
acpi -V
```

Also, how many people here are using chillhubs with their laptops?  I know that it makes a HUGE difference with my laptop... I'll run some tests and let you know what the actual numeric results are.

---

### Post by captainroin on 2006-07-09
57.0 C while browsing this page

Gateway. 1.17Ghz 512MB ram

---

### Post by reacocard on 2006-07-09
average at idle: 48
under heavy use: 60-70

pentium m 1.7ghz

---

### Post by m83 on 2006-07-10
IBM Thinkpad T23
Pentium III Mobile 1.13 Ghz
Using Linux kernel 2.6.15-25-686.

Idle: ~45°C
Heavy use (tested running glxgears for 5 minutes. This is a good test as the laptop doesn't have a good 3D video card, so opengl is software rendered by Mesa and it uses a LOT of CPU): ~74°C

---

### Post by djoelsson on 2006-07-10
44C when browsing this page
Core Duo T2250
Both cores running at 46% load

---

### Post by ExMachina on 2006-07-10
how do you figure out you laptops temp?
I have a sony vaio * see sig* and wanna help out.
Im going to dual boot it soon ^^

---

### Post by razahel on 2006-07-10
Idle: 64 C
Load: 94 C
Room Temp 30 C

the fan is most of the time off and when the temp reaches 90C the fan is not at full speed





Asus M6Ne
Pentium M 1.6Ghz 1024MB DDR
ATI 9700 mobile 64MB 
linux-image-2.6.15-25-686
fglrx 8.25.18+2

---

### Post by 11hjpphty76lkjj on 2006-07-10
Interesting to note, i installed the i8k app for my Dell Latitude and my temps dropped big time.

Was:

Idle 45-55C
Load 55-70C

Now:
 
idle 21-30C
load 30-38C

Max so far has been 44C.

Much cooler. :)

---

### Post by the_maassk on 2006-07-10
Specs: (see sig.)

Idle: 47-50 C
Under intermittent load: 55-60 C
Under heavy load (compile) for a few minutes: 67-70 C
With Laptop chillpad running: All temps drop by 4-5 C

Room temp: 27-32 C

---

### Post by Okami on 2006-07-10
> **mscman said:**
> Use the command:
```
acpi -V
```

Also, how many people here are using chillhubs with their laptops?  I know that it makes a HUGE difference with my laptop... I'll run some tests and let you know what the actual numeric results are.

What is chillhubs? :???: And, i8k, is that only for dell laptops?

---

### Post by Maggot on 2006-07-10
> **razahel said:**
> Idle: 64 C
Load: 94 C
Room Temp 30 C

the fan is most of the time off and when the temp reaches 90C the fan is not at full speed

That can't be good. I'd say there is something wrong. It shouldn't reach those temps.

> **kalosaurusrex said:**
> Interesting to note, i installed the i8k app for my Dell Latitude and my temps dropped big time.

Was:

Idle 45-55C
Load 55-70C

Now:
 
idle 21-30C
load 30-38C

Max so far has been 44C.

Much cooler. :)
Using i8k and gkrellm I manually speed my cpu fan to max and it dropped 4C cooler :)

---

### Post by ketsugi on 2006-07-11
Toshiba Satellite 2410
Temperature 55C

---

### Post by razahel on 2006-07-11
ok something new and terrible I posted my tem. yesterday but today I did some  work on the Asus laptop and at full load the system reaches incredible 

102°C

this is horrible because i love ubuntu butunder these conditions i must start windows i think because there under full load the tem reaches 80 at max

maybe some knows help but this is terrible

update:
with the 386 kernel the idle tem is 10°C lower but it should not be because my pentium m should run better under the 686 kernel, now i am completely confused 


regards razahel

---

### Post by madscience on 2006-07-11
This is getting ridiculous.  Is there any definitive answer as to what's causing this issue on so many different machines?  Is there a definitive fix?  My P-M Toshiba runs hot (not at the machine at the moment, so I can't post the exact temp. but it's definitely a lot hotter than when running XP.)  The fan constantly runs, and the battery life SUCKS.  How did this big of a bug slip by the laptop-testing team, and why is there no fix available after a month (especially for a 'LTS' release)?
There has actually been a bug report open on this since 09/23/2005!
[https://launchpad.net/distros/ubuntu/+bug/22336](https://launchpad.net/distros/ubuntu/+bug/22336)
If anyone knows of a decent (not-too-hackish) fix for this, please post in this thread, or at least point us to some definitive resources.
Sorry if I seem annoyed... but I *am* annoyed.

Thanks.

EDIT: This DID NOT occur under any previous Ubuntu release... NO, downgrading to Warty/Hoary/Breezy is NOT AN OPTION for this machine.  Thanks.

EDIT: This:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557)
Also seems to be related... and has been open since 02/05/2006!

---

### Post by didobuntu on 2006-07-11
Hi,

Temperature: 51°C while browsing ubuntu web site
Temperature Max.: 69~70°C with 100% CPU during a long time computation
room temperature: 26°C

Asus W2JC, T2500 (2GHz),
1,5 Go RAM, ATI Mobility X1600 (256 Mo viedo memory)
Screen: 17" WSXGA (1680x1050)

---

### Post by ShaLouZa on 2006-07-12
> **madscience said:**
> This is getting ridiculous.
Even more than ridiculous : it's getting unusable. I'm at 60°C on idle or low usage (net), it jumps to 70-75°C every time I do anything (even simply launching a wab browser), and I just can't push the cpu to 100% more than 3 minutes or the laptop shutdowns on critical temperature at 98°C. WTF did they put as voltages in these new kernels ? I'm on Ubuntu since the release of Hoary and I never had this problem before either. 

I even had two shutdowns on critical temperature when I was installing the system (new install from scratch with the official CD), and I had to wait until night with a external fan aimed to the laptop to be able to complete it.

Room temperature around 28°C. Ok it's hot, but I've seen nowhere on the Ubuntu disks "use in winter only".

---

### Post by fogster74 on 2006-07-12
zgoda - was a bit concerned about your post (re laptop fan running all the time). I had a colleague who had this on a Fujitsu-Siemens Amilio (I think was its name) - just before the laptop started powering itself off. Turned out the heat sink was rammed full of dust and the cpu was overheating. Would seriously suggest you check out (or get someone else to) the heatsink on your  processor to confirm the air channels aren't blocked.

Steve

---

### Post by mscman on 2006-07-13
> **ShaLouZa said:**
> Even more than ridiculous : it's getting unusable. I'm at 60°C on idle or low usage (net), it jumps to 70-75°C every time I do anything (even simply launching a wab browser), and I just can't push the cpu to 100% more than 3 minutes or the laptop shutdowns on critical temperature at 98°C. WTF did they put as voltages in these new kernels ? I'm on Ubuntu since the release of Hoary and I never had this problem before either. 

I even had two shutdowns on critical temperature when I was installing the system (new install from scratch with the official CD), and I had to wait until night with a external fan aimed to the laptop to be able to complete it.

Room temperature around 28°C. Ok it's hot, but I've seen nowhere on the Ubuntu disks "use in winter only".

I really recommend using a chillhub, as I suggested earlier. For those of you that don't know what a chillhub is (sometimes called a coolhub, chillmat, coolmat, etc...), it's a plate with fans in it that you use to draw excess heat away from your laptop. It's particularly effective when using your notebook on your lap, as it adds a gap between the computer and yourself.

I could be wrong and maybe you're using one, but it's worth a try. [Here is a link]("http://www.newegg.com/Product/ProductList.asp?N=2030260319+1276817102&Submit=ENE&SubCategory=319") to the section on Newegg.com's cooling section. I have a Targus ChillHub that also has a USB port replicator ($20 less will get you one without the port replicator). Definitely worth the $$$ if you're worried about overheating, as most of the laptop's heat builds up on the bottom due to the lack of space between the computer and the work surface. Also for those of you in hot climates, this will help get the air moving better.

---

### Post by matthew on 2006-07-13
I have been following this thread since I posted my data early on. I realized that my load temp was pretty high so I did a bit of digging. I discovered that the 686 kernel I was using was the SMP version for multiple processors rather than the single processor Pentium M that I have. I changed my kernel to the 386 version (2.6.15-26-386) and my load temps have dropped considerably, generally around 70-74 degrees and my desktop seems to run a lot smoother. If you are having similar problems you might try the same thing. If you do, don't forget the restricted headers for your new kernel, etc., if they are needed.

---

### Post by Peter76 on 2006-07-13
I'm running Dapper on an iBook g3; don't know how to get the temperature; but it is running really hot under Ubuntu; you can sometimes hardly touch the bottom. Also my fan is spinning up a lot of times. Never had this under OSX.
Has somebody filed a bug about this?

---

### Post by _profox on 2006-07-13
Sounds like ACPI issues.

My temp on IBM Thinkpad T40:

profox@kreafleur:~$ cat /proc/acpi/therm*/*/temp*
temperature:             44 C

Heavy openGL apps running? Well.. just AIGLX + Compiz and a video
Temperature is quite low on this laptop compared to my other one (Acer)
But the Acer is broken (Acer Aspire 1694wlmi - it was around 60-80° )

---

### Post by bierpullen on 2006-07-15
My laptop: Acer aspire 1522WLMi
CPU: AMD64 3000 (1.8Ghz)
NVIDIA GeForce FX Go 5700

CPU sensor (via ACPI)
IDLE: 50 °C
STRESSED: 60-85°C

* Room temperature is 20-28 °C

----------------------------------------
Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http:/www.antarctica-rbak.nl/ubuntu/acer_aspire.php](http:/www.antarctica-rbak.nl/ubuntu/acer_aspire.php)

---

### Post by Arnaud_B on 2006-07-16
toshiba-satellite m35-...
average is around 60-65 C 
can go around 70-75 C under load...
I was checking recently what could be creating such overheating and I noticed that throttling is not supported :-( could you check if you are in a similar situation... 
cat /proc/acpi/processor/CPU0/info
this could be the reason but no idea how to change that :-(
A.

---

### Post by blitzd on 2006-07-16
Running SLED 10 now but my temps are similar to when I run Dapper:

Dell M65 (T2500)
idle: 35-41 C
loaded with laptop display: 65-67 C
loaded with laptop display disabled: 58-61 C
ambient room temp: around 32 C (it's frickin HAWT)

I cannot for the life of me get the temp to go above 67, the fan kicks up to leaf blower mode and it just sticks there at 67. My system is also way cooler when I'm using my external monitor and have the laptop display basically powered off. Everything runs at about the same temps in Windows AFAIK (I avoid it if I can).

---

### Post by testube_babies on 2006-07-16
Alienware MJ-12m 5500
Pentium IV 3.4 Ghz
Ambient temp:  22-24°C
[Unsupported motherboard for CPU temp reading]

HDD:  Hitachi Travelstar 7200 rpm 60gb
Idle:  32°C
Stressed:  40°C
[Using laptop cooling pad]

For some reason, the hard drive always runs 4-8°C hotter in Windows than in Linux.

---

### Post by tonyo46 on 2006-07-17
My laptop :
HP Pavilion DV1000
Centrino 1.6 GHz
Idle: about 58° (at the begining) to 80° (after one hour)
Stressed : 70° to 95° !

I think I have a problem, see that [thread]("http://www.ubuntuforums.org/showpost.php?p=1263500&postcount=3")

if you know why I don't have "throttling control" and "limit interface"...

---

### Post by gamma on 2006-07-18
$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             53 C

My system used to run very hot. Idled at 60 and got up to 75C. Very hot... I want a new laptop, maybe a Macbook, but those seem to run hot also..

---

### Post by IcemanV9 on 2006-07-18
HP Pavilion ze5185
Pentium IV 2.4 GHz
ATI Radeon Mobility M6 LY (32 Mb)

_2.6.15-25 & before_
Idle: 59-62 C
Stressed: 68-72 C

_2.6.15-26_
Idle: 55-57 C
Stressed: 67-68 C

NOTE: I never seen it more than 72 C (or less than 55 C) since it is set to shutdown (gracefully) @ 72 C. Since I upgraded kernel to -26, I haven't a problem with overheating and/or shutdown. In WinXP, it was always overheating and shut off abruptly (no warning)!

---

### Post by catanzag on 2006-08-25
My laptop: Toshiba 2410-303
CPU: Pentium 4 M 1.7 GHz
NVIDIA GeForce4 420 Go

CPU sensor (via ACPI)
IDLE @ 1.2 GHz:  50 °C
LOADED @ 1.7GHz: 55°C

* Room temperature is about 27 °C

---

### Post by wvelez on 2006-08-25
Samsung X05
Idle: 38 - 40Cº
Max: 60 - 65Cº

Centrino based 1.4 GHz Pentium M

---

### Post by Melcar on 2006-08-25
I have only managed to get CPU sensors working:
Compaq V2000Z (Sempron 3300+ 2.0GHz)
idle 45-50*C
load 55-65*C

---

### Post by ghettobilly on 2006-08-27
HP Pavilian ZE1000
Mobile Athlon XP +1800

idle=500Mhz 60C-65C
load=1500Mhz 80C sets fan low 90C sets fan high

---

### Post by ysse on 2006-08-27
Fujitsu-Siemens Amilo Si 1520
Centrino Duo T2300 (2x1.6 GHz)
2.6.15-26-686

Browsing 45-50 C
Stressed 50-60 C
Fan turns on at 60 C, off again at 50.

This system runs cooler on Ubuntu than on WinXP Home.

---

### Post by arkangel on 2006-09-13
> **matthew said:**
> I have been following this thread since I posted my data early on. I realized that my load temp was pretty high so I did a bit of digging. I discovered that the 686 kernel I was using was the SMP version for multiple processors rather than the single processor Pentium M that I have. I changed my kernel to the 386 version (2.6.15-26-386) and my load temps have dropped considerably, generally around 70-74 degrees and my desktop seems to run a lot smoother. If you are having similar problems you might try the same thing. If you do, don't forget the restricted headers for your new kernel, etc., if they are needed.

DITO ..  when i upgraded to Dapper  The 686 kernel was scaring , the only diffe with Hoary was the kernel version 386 , now using 386 

Asus A6Va
centrino 1.86Ghz
1GB ram
Ati X700 128 
Idle :40 -50°C  798Mhz
middle 55 -65°C 
Max load: max 79°C  1.86Ghz (I never was able to heat it up more than 80 °C)

---

### Post by UltraMathMan on 2006-09-13
Dell E1505
Idle: 35-40&#730;C
Max: 60-65&#730;C

---

### Post by Devlin67 on 2006-09-14
Laptop: Acer Aspire 5002WLMI
Idle  : 45-50
Load  : 50-60

---

### Post by amo-ej1 on 2006-09-14
Toshiba Tecra S2
CPU: Intel Pentium M 2.0 Ghz
Graphic: GeForce Go 6600

* Temperature: you'd really think ACPI was working on this piece o' rubbish ?
* smartctl reports a hard disk temperature of 33 degrees

---

### Post by bierpullen on 2007-06-30
:pACER FERRARI 1000:p

Idle: 35-40&#730;C
Max:55-60&#730;C
Harddisk 37&#730;C

----------------------------------------------------------------------------------------
[http://www.antarctica-rbak.nl/ubuntu/acer_ferrari.php](http://www.antarctica-rbak.nl/ubuntu/acer_ferrari.php)

---

### Post by CrispyFried on 2007-06-30
compaq m2010

celeron m 1.3 ghz

idle 50-55 C
loaded 65-70 C

---

### Post by Kanariya on 2007-07-31
I know this is an old topic but

Idle: 69C°
In use: 78C°

It will constantly soar above 90C° but has yet to go into thermal shutdown. At times I will have to hold it in front of the A/C to get it to drop below 50C° but it'll only stay below that for a few minutes before rising again past 70C°

I'm getting very concerned.

---

### Post by brian j on 2007-07-31
Thermal 1: ok, 44.0 degrees C
     Thermal 2: active[0], 43.0 degrees C
Toshiba Satellite Multi Media
Intel Centrino 3.2ghz
1.25 Gig Ram

A Ok!

---

### Post by Paul820 on 2007-07-31
Acer Aspire 5101
Amd Turion 64
512 Mb

Idle 37 degrees C
In use 51 degrees C

---

### Post by ashvala on 2007-07-31
around 40 degrees Centigrade...

---

### Post by derjames on 2007-07-31
Philips X56  Core 2 Duo T5600

Idle 49 degC
Load 75 degC

---

### Post by Sunflower1970 on 2007-07-31
Thinkpad R40 P4M 2.0 Ghz, 1 Gig RAM. Using Feisty

It averages around 54°C-57°C idle with Compiz-Fusion, screenlets and AWN running and I'm idle.
When I'm working, the highest I've seen is right around 65°C. 

I haven't checked what it is without the 3D stuff on it....

Looking at these other temps, I'm beginning to wonder if mine's a bit high for idle...?

---

### Post by Aparatey on 2007-07-31
My laptop: Compaq Presario 1500US
CPU: Pentium IV (2.4Ghz)
ATI Mobility Radeon 7500 - 32MB

CPU sensor (via ACPI)
IDLE: 56 °C 
STRESSED: 60-77°C

* Room temperature is 23 °C

---

### Post by misfitpierce on 2007-07-31
I would if it actually read...=P acpi -V reads back 0.0 C so I guess its ultra cold

---

### Post by Neo0351 on 2007-07-31
Toshiba Satellite A-65-S126
2.8Ghz Celeron
Idle~45-50&#8451;
Stressed~60-70&#8451;
I stop whatever I'm doing if I ever reach above 80&#8451; which happens sometimes when my fan doesn't kick on.

---

### Post by Depressed Man on 2007-07-31
Is there any CLI command to show temperature? Right now I'm relying on a screenlet to do it. 

All I know is when it's stressed it's 60 degrees C

---

### Post by ramjet_1953 on 2007-07-31
Acer TravelMate 4101

CPU
Pentium M 1.6GHz
Idle 50-60 C @ 798 MHz
Stressed 65-70 C @ 1.6GHz

Fan cuts in around 65 C

HDD

40 - 55 C

Regards,
Roger :cool:

---

### Post by the_maassk on 2007-08-01
Config - See sig.

Idle: 46-54 C
Load: 60-65 C
Room Temp: 30-32 C

---

### Post by Sunflower1970 on 2007-08-01
> **Depressed Man said:**
> Is there any CLI command to show temperature? Right now I'm relying on a screenlet to do it. 

All I know is when it's stressed it's 60 degrees C

Try acpi -t

---

### Post by rax_m on 2007-08-03
I'm a bit concerned about my Toshiba Satellite P100 as well.. 

Normal load.. i.e. surfing, docs etc. : 45-65 C
But if I'm doing something "heavy" like gaming: 70-90 C  ; GPU got up to 86 C

This happenned when playing savage today. I played for an hour probably. The load average was only around 0.5 - 0.7 so I don't think the machine was struggling. But I decided to power into windows for a little while just incase. 

In my situation, I don't think the actual CPU temp is being read but rather something called "Thermal 1". If I boot into windows, and use Speed Fan I get a Thermal 1, CPU 1 and CPU 2 temp readings. Thermal 1 is almost always about 10-15 C higher than either of the CPUs. 

But it's definitely putting me off gaming on my Linux box at the mo. :( 

Ok .. I just rememberd something weird that happens :
When I just power into Ubuntu, the fan will kick in quite regularly.. but once the machines been idling for a while the fan doesn't seem to kick in at all. :-|

---

### Post by tschneiter on 2007-08-04
Dell 640m (e1405), core 2 duo @ 1.83ghz:
Room: 25-30c
Idle: 42-48c
Load: 60-68c

Running gkrellm w/i8k plugin. Definitely helps. Anyone know if there is a way to get the benefits of gkrellm without having it running in the foreground?

---

### Post by szako on 2008-04-27
ASUS A6VA - 2 years old with the new Hardy

CPU: Pentium M 1.73Mhz
GPU: ATI X700
Idle: ~60-65
Stressed 85-95

Something is not good. I'm worried :/

---

### Post by excogitation on 2008-04-27
szako, I'm having temperatures in the same region - Dothan 1,86 - X700
(Had up to 100°C - now only to 80sth...)

There are **some** threads on high temperatures with Hardy and at the moment there's no satisfactory solution **that I know of**.

What might help lowering the temperature is to set your GPU powerstate lower ($ aticonfig --set-powerstate 1) standard is 3.
Also you can check what programs are causing the highest loads using top/htop or sth alike and see what you can do about it :-)
Using powertop you can check what wakes up the CPU the most.
Also you could undervolt your CPU - but since you have to redo it with every new Kernelversion - it's just a pain (though I really think it helps a lot).
Using a different cpu frequency scaling demon like cpufreqd (standard is powernowd) and and and ...

But to be honest that's all just crap.
In my opinion you shouldn't have to do any of that - the OS should just take care of it for you - and especially on laptops the implementation of powersaving/load handling is just not optimal.

---

### Post by Monicker on 2008-04-27
IBM Thinkpad T30, running Hardy Heron 8.04

CPU:    Pentium 4 M 1.8GHz
Idle:   42-47c
Load:   70-75c

---

### Post by tempest on 2008-04-27
Laptop: Dell Vostro 1500
CPU: Intel Core2Duo T7500 (2.2Ghz)
GPU: NVIDIA GeForce 8600M GT

CPU (libsensors):
IDLE: 42 °C
STRESSED: 60-70 °C

GPU (nvidia):
IDLE: 45 °C
STRESSED: 60 °C

Room temperature: 21 °C

---

### Post by Sam Lars on 2008-05-30
Dell Inspiron 1525

Core 2 Duo T5550 @ 1.83 GHz
Idle ~42 C
Load ~ 60 C
The fan kicks into high around 60, and if I have the opening on the bottom unobstructed, it can sit at 60 with 100% on both cores.  I've noticed that Windows seems to have similar temperatures.
The hard drive is a Samsung HM320JI, and is usually 35-45 C, depending on conditions.

Room temperature maybe around 23 C.

---

### Post by ballin on 2008-06-28
Dell Latitude D620
(Core 2 Duo)

Idle:
CPU - 45-49C
GPU - 50-55C

Stressed:
CPU - 60 ish
GPU - 60-70

Interested in trying his i8k thing though, or maybe even a cool pad if things get worse.  Room is very hot which doesn't help (S.Spain no aircon hehe)

---

### Post by SuperHue on 2008-07-15
Hahaaaaa, this is nothing guys. Sorry ... 

My PC is with no programms running 76*C -82*C 
It's normaly when I drive a internet or two 83*C 
And my "record", is 92*C !!!!!!!!!!!!!!!!!!!!!!!

How shud this be fixed ? o.0 

It's a HP Pavillion dv6000 or someting, 10 months old and was this hot from the start ... Vista ...

Wanna see the normal temperature for my PC? youtube "the worlds hottest PC" thanks

---

### Post by Sam Lars on 2008-07-15
Clean your heat sink and fan.  Those things get dirty quickly and don't dissipate the heat as well.  You can also check the scaling on the processor to make sure it's lowering its speed if it can (you can use the applet for the Gnome panel).
Another possibility would be less than adequate installation of the CPU assembly, not enough thermal paste, etc.

---

### Post by wireless on 2008-07-16
Ever since i upgraded to hardy my thinkpad x60 laptop goes crazy hot when i run some programs (such as amule for example), and than it auto shuts down.
found in syslog the following:
Jul 13 20:09:50 TradeStation kernel: [ 6906.381828] ACPI: Critical trip point
Jul 13 20:09:50 TradeStation kernel: [ 6906.381836] Critical temperature reached (128 C), shutting down.
I went as far as opening up the case and cleaning the fan and making sure there is no dirt.
I allready posted about this issue and also i found a bug report with kinda same details.

appreciate any hint and assistance regarding this issue.
im very worried about my thinkpad wealth :)

---

### Post by alan.clements on 2008-07-20
[COLOR="Blue"]System:[/COLOR]ACER Aspire 3620
[COLOR="Blue"]CPU:[/COLOR]Intel Celeron-M 380
[COLOR="Lime"]Idle Temp:[/COLOR]52 c
[COLOR="Red"]High Load Temp:[/COLOR]90 c

Note that on rare occasion it has topped out at 96 c. At which time the system forces it to 200Mhz and the fan comes on loud enough to be heard until it gets below 90 c

---

