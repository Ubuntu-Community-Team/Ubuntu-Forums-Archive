---
title: "CPU Temp reaches temps over 84c!  (75c when browsing flash content)"
date: 2013-02-04
forum: Hardware
---

### Post by Landon1976 on 2013-02-04
I use Ubuntu 12.4. I have been using Linux for only 2 weeks now. I have noticed that when playing flash games on the internet my computer fan turned on louder then ive ever heard it in the 6 years ive owned this laptop. I installed the PSensors app and saw that the temp climbs to 75C when browsing the web and playing flash games? I just loaded a game called 0 AD on my computer and within 3 minutes I got a warning that me CPU temp was 84C. so I shut down the game and after 5 or 6 min the fan went off again. I apologize for starting this thread without much technical info i dont the the proper terminal commands to display processor info for you guys al though I am not getting a high temp on my GPU i do know how to display  relevent out put. and here it is.

01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9600M GT] (rev a1)
I am using the recommended by Ubuntu driver for GPU.

also,  my laptop is a HP Pavillion Laptop DV7. I have searched the forum for similar posts most require installing additional software, which I am open to. However I seem to believe that this is a configuration issue as my computer and processor are quite common in the world. Any help would be appreciated. I love Ubuntu and I also like the distraction of games i wish i could have them both.

---

### Post by Landon1976 on 2013-02-04
I just used a program called Cpufreq here is the output for "cpufreq-info"

cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.00 GHz:7.24%, 1.60 GHz:1.73%, 800 MHz:91.02%  (78519)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.00 GHz:13.74%, 1.60 GHz:3.91%, 800 MHz:82.35%  (76731)

I dont want to manually adjust my cpu frequency as I use my laptop? this program offers that option. I hope to find a solution that leaves that work to be done by the OS.

---

### Post by cybrsaylr on 2013-02-04
Are they HD games?

I use a 4+yr old core2duo Dell laptop which is plugged into my HDTV as a second monitor. I works great but whenever I watch HD videos on YouTube the CPU usage goes up along with the temps on the laptop and the cooling fans kick in. If I go out of HD mode CPU usage and temps drop but you lose the HD resolution.

---

### Post by Yellow Pasque on 2013-02-04
Hmm, 6 years old - Have you ever dusted the internals? Maybe it's time to redo the CPU heatsink with new thermal paste? (Manufacturers have the maddening habit of using a cheap thermal pad that breaks down over time.)
Basically, a laptop should never overheat, even under full load (though many are designed with inadequate cooling).

---

### Post by robert shearer on 2013-02-04
**Only** 84c...? Luxury !
[http://www.youtube.com/watch?v=Xe1a1wHxTyo](http://www.youtube.com/watch?v=Xe1a1wHxTyo)
[http://en.wikipedia.org/wiki/Four_Yorkshiremen_sketch](http://en.wikipedia.org/wiki/Four_Yorkshiremen_sketch)

My old Toshiba Tecra A2 running Wattos (energy conservative ubuntu derived distro) reaches **91c** when viewing flash or updating via Synaptic.
Yes, last week I cleaned the heatsink and reapplied thermal paste.
Prior to that it was crashing synaptic and browsers immediately on opening. **:-)**

You could try managing the performance parameters via Jupiter...
```
sudo apt-get install jupiter
```
where you can set (and monitor) for cpu performance. 
Imho better than Cpufreq and having several other handy configuration options like wifi and extended desktops over multiple monitors.

---

### Post by Drenriza on 2013-02-04
**Hightower**
I'am using Ubuntu 12.04 LTS with a core 2 duo P6600 or E6600 (cant remember if its P or E), where i have a passive 1kg cooling block on, which only get cooled from the airflow.

When i run HD video i get a temp of 35-40 celsius.
EVE Online 40 celcius.
Max temp HD video + games, less then 50 celsius.

To compare
Windows 7 i had a temp on 40+ in idle mode with a active 12cm cooling fan mounted directly on the cooling block. And a max temp of 60+ but less then 70 celsius.

So i don't think this is a directly Ubuntu issue.

**Laptop**
Also laptops do in general just get very hot.

My Mac Book Pro gets 41c hot when browsing and reading mails.

---

### Post by Landon1976 on 2013-02-04
> **Temüjin said:**
> Hmm, 6 years old - Have you ever dusted the internals? Maybe it's time to redo the CPU heatsink with new thermal paste? (Manufacturers have the maddening habit of using a cheap thermal pad that breaks down over time.)
Basically, a laptop should never overheat, even under full load (though many are designed with inadequate cooling).
Actually I have recently (5 months ago) taken it completely apart removing motherboard and all components and modules also the screen and of course keyboard, my main purpose was cleaning. (interestingly it was immaculately clean at all levels of disassembly.) i dint not at the time reaplly thermal compound based on the condition of the interior and the knowledge that I have never had temperature issues in the past.
As a side note to others reading this, I do not recommend this course of action unless as a last resort. Complete disassembly of laptop is a huge undertaking and should not be done without a deep understanding of computer components and how they age over time and of course experience.

---

### Post by Thee on 2013-02-04
Maybe consider buying a laptop cooling pad. Some laptops just have too high temperatures right from the start. But first, try this [http://www.youtube.com/watch?v=N9Gc4PHFBQg](http://www.youtube.com/watch?v=N9Gc4PHFBQg)

---

### Post by Landon1976 on 2013-02-08
> **Thee said:**
> Maybe consider buying a laptop cooling pad. Some laptops just have too high temperatures right from the start. But first, try this [http://www.youtube.com/watch?v=N9Gc4PHFBQg](http://www.youtube.com/watch?v=N9Gc4PHFBQg)

[Thee]("http://ubuntuforums.org/member.php?u=1753868") a Laptop cooling pad is a good suggestion however my issue is not lowering the temp temporarily so much as it is prevent it from running this hot. This is WAY above a acceptable range and i think anyone would agree, im not being to overprotective. keep in mind that I am shutting it down when psensors tells me I am at 84c who knows what it will reach if i didnt? Also, it barely hits 65-70c under MAXIMUM stress in windows.

---

### Post by Landon1976 on 2013-02-08
> **Drenriza said:**
> **Hightower**
I'am using Ubuntu 12.04 LTS with a core 2 duo P6600 or E6600 (cant remember if its P or E), where i have a passive 1kg cooling block on, which only get cooled from the airflow.

When i run HD video i get a temp of 35-40 celsius.
EVE Online 40 celcius.
Max temp HD video + games, less then 50 celsius.

To compare
Windows 7 i had a temp on 40+ in idle mode with a active 12cm cooling fan mounted directly on the cooling block. And a max temp of 60+ but less then 70 celsius.

So i don't think this is a directly Ubuntu issue.

**Laptop**
Also laptops do in general just get very hot.

My Mac Book Pro gets 41c hot when browsing and reading mails.
hmmm ... thank you for your input I do appreciate it Drenriza. That is good info. I also have very good performance numbers in window playing extremely taxing game on this laptop it can handle Guild wars 2 at 85% max with a frame rate over 25 if thats not a test i not know what is? farcry 2 no probs hours on end but when I boot into Ubuntu I overheat on flash content! I also want to mention again that it is processor heat and not gpu that is hitting the high numbers. Im not and never did suggest that there’s a fault with Ubuntu. It is more realistically a simple configuration that I dont know how to access? However it is so critical that i will not be able to use my Ubuntu on this laptop unless its resolved? 84c is close to 200 degrees Fahrenheit and that simply not good for my expensive hardware.

---

### Post by Landon1976 on 2013-02-08
> **robert shearer said:**
> **Only** 84c...? Luxury !
[http://www.youtube.com/watch?v=Xe1a1wHxTyo](http://www.youtube.com/watch?v=Xe1a1wHxTyo)
[http://en.wikipedia.org/wiki/Four_Yorkshiremen_sketch](http://en.wikipedia.org/wiki/Four_Yorkshiremen_sketch)

My old Toshiba Tecra A2 running Wattos (energy conservative ubuntu derived distro) reaches **91c** when viewing flash or updating via Synaptic.
Yes, last week I cleaned the heatsink and reapplied thermal paste.
Prior to that it was crashing synaptic and browsers immediately on opening. **:-)**

You could try managing the performance parameters via Jupiter...
```
sudo apt-get install jupiter
```where you can set (and monitor) for cpu performance. 
Imho better than Cpufreq and having several other handy configuration options like wifi and extended desktops over multiple monitors.
Thank you for the suggestion i will look into this software and see if perhaps it will lead to a solution. I am convinced that the thermal connection between processor and heat sink is still satisfactory because i am not even reaching 15-20 degrees below these numbers in Windows Vista on this laptop. Also I have disassembled the laptop recently with the intention of cleaning and reaffirming all connections were sung and true.
LOl also ill add that at first i was confused at the relevance of the youtube video to attached inside your signature but shortly became amused with it thank you for the laugh. Monty Python used to be so popular here in the US when I was young (im 36 now) now it just seems like only the older crowd remembers the fun times we had watching!

---

