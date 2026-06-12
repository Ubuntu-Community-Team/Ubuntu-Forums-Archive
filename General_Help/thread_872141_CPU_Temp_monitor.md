---
title: "CPU Temp monitor"
date: 2008-07-27
forum: General Help
---

### Post by OMJD on 2008-07-27
Hi,

I am looking for a temperature monitor for my CPU, (Intel Q6600) preferably one which can sit on the taskbar. (Gnome) I searched on the forum and found many suggestions, but none of the suggestions work. 

Any suggestions would be appreciated.

Thanks. :)

---

### Post by coffeecat on 2008-07-27
Have you tried computertemp? It's a Gnome panel app and it's in the repositories. It should fit the bill nicely. Have a look in Synaptic.

It works for me.

---

### Post by cowboyup6983 on 2008-07-27
> **coffeecat said:**
> Have you tried computertemp? It's a Gnome panel app and it's in the repositories. It should fit the bill nicely. Have a look in Synaptic.

It works for me.

i just looked in synaptic and installed computertemp. where did it go 2. nothing open up on my panel?

---

### Post by jonian_g on 2008-07-27
Open a terminal and type:

```
/usr/lib/gnome-applets/computertemp
```

Close the therminal and it will appear on your applets list.

---

### Post by cowboyup6983 on 2008-07-27
> **jonian_g said:**
> Open a terminal and type:

```
/usr/lib/gnome-applets/computertemp
```

Close the therminal and it will appear on your applets list.

i type it in, and nothing happen. not even a new command line.

oh well its okay

---

### Post by cowboyup6983 on 2008-07-27
> **cowboyup6983 said:**
> i type it in, and nothing happen. not even a new command line.

oh well its okay



it was my fault i didnt wait long enough for a new command. i have it now on my top panel. question about the temps it says "hwmon0 (1), hwmon0 (2), hwmon0 (3), hwmon0 (4) all with different readers, which is the most important first says 11*C others are 0,7,2 i have AMD Dual Core 4800+ CPU?

---

### Post by cowboyup6983 on 2008-07-27
> **cowboyup6983 said:**
> it was my fault i didnt wait long enough for a new command. i have it now on my top panel. question about the temps it says "hwmon0 (1), hwmon0 (2), hwmon0 (3), hwmon0 (4) all with different readers, which is the most important first says 11*C others are 0,7,2 i have AMD Dual Core 4800+ CPU?

isnt that a little high for normal temps. im running a Zalman cooler, which should keep it really cool, plus room is air conditioned.

---

### Post by jonian_g on 2008-07-27
I don't think they are high. They look fine to me.

If you want you can try another applet with more sensors, not only cpu and you can chose which ones you want to be shown.

```
sudo apt-get install sensors-applet
```

---

### Post by pedrogent on 2008-07-29
I installed computertemp but it didn't work and now I've installed sensors-applet but that's only showing the GPU temp.

Anyone have any idea how to monitor CPU temps?

I'm interested to know because I fold and the CPUs are a little overclocked.

---

### Post by PmDematagoda on 2008-07-29
> **pedrogent said:**
> I installed computertemp but it didn't work and now I've installed sensors-applet but that's only showing the GPU temp.

Anyone have any idea how to monitor CPU temps?

I'm interested to know because I fold and the CPUs are a little overclocked.

Did you install lm-sensors? Install lm-sensors with:-
```
sudo apt-get install lm-sensors
```
and then run:-
```
sudo sensors-detect
```
after the probing is over, allow sensors-detect to enter the new entries and then reboot the PC, the CPU temperatures should now be available.

---

### Post by pedrogent on 2008-07-29
All I needed was a reboot. Thanks a lot.

---

### Post by gordintoronto on 2008-08-03
> **PmDematagoda said:**
> Did you install lm-sensors? Install lm-sensors with:-
```
sudo apt-get install lm-sensors
```
and then run:-
```
sudo sensors-detect
```
after the probing is over, allow sensors-detect to enter the new entries and then reboot the PC, the CPU temperatures should now be available.
The person who put together the computertemp package should have included the dependancy for lm-sensors.

---

### Post by cowboyup6983 on 2008-08-17
> **coffeecat said:**
> Have you tried computertemp? It's a Gnome panel app and it's in the repositories. It should fit the bill nicely. Have a look in Synaptic.

It works for me.

hi all, i installed this application no problem, i just wanted to know if there is a application i can use that is similar to this but monitors my CPU usage? something that i can add to my panel would be very helpful.

thanks in advance!

---

### Post by brian mcgee on 2008-08-17
> **cowboyup6983 said:**
> i just wanted to know if there is a application i can use that is similar to this but monitors my CPU usage? something that i can add to my panel would be very helpful

Add System Monitor to panel

---

### Post by cowboyup6983 on 2008-08-17
> **brian mcgee said:**
> Add System Monitor to panel

thanks its weird thought it usually just says processor 0-5% in usage even with firefox open. i guess its accurate, right now im using a celeron never knew they were so powerful

---

### Post by cowboyup6983 on 2008-08-25
is there an application that shows your graphic cards temperatures

---

### Post by cowboyup6983 on 2008-08-26
there are eight different temperatures listed here, please see attached picture, what do they all mean, which one is my actually CPU temp. i have AMD4800+ Dual Core and two 8800GTS cards.

---

### Post by sloggerkhan on 2008-08-26
If you go to sensors-applet prefs, there will be labels for each gauge.
My comp has core0 core0 core1 core1 vcore 1 vcore 2 +3.3V +5V +12V -12V -5V Stby VBat fan1 fan2 M/B Temp CPU Temp Temp3 fan3 as available sensors. core0 core0 core1 core1 are all internal CPU thermo gauges that give false readings (if you look it up, internal thermal sensors are broken on some AMD CPUs) so I use the mobo CPU and M/B temps. They range from about 28C to 40C and on my comp, the CPU is usually cooler than the mobo on my comp, also.

---

### Post by cowboyup6983 on 2008-08-26
> **sloggerkhan said:**
> If you go to sensors-applet prefs, there will be labels for each gauge.
My comp has core0 core0 core1 core1 vcore 1 vcore 2 +3.3V +5V +12V -12V -5V Stby VBat fan1 fan2 M/B Temp CPU Temp Temp3 fan3 as available sensors. core0 core0 core1 core1 are all internal CPU thermo gauges that give false readings (if you look it up, internal thermal sensors are broken on some AMD CPUs) so I use the mobo CPU and M/B temps. They range from about 28C to 40C and on my comp, the CPU is usually cooler than the mobo on my comp, also.

where can i find these preferences. if i right click on the icon and go to preferences, this is what i see.. i cant label anything. i might be in the wrong location.

yes i had the problems under windows also, i get getting the wrong reads with programs like PC Wizard 2008, it would stay at 25C and under the bios when i reboot it says something like 38-40C.. i've never been able to get actual readings, i thought it was something i did with the thermal paste. i got a zalman on here so i think its cool enough, this paste weekend i removed the paste and re-paste with more expensive paste. 

here is a screen shot of the preferences i can see.. let me know if i am doing something wrong and thanks again!

---

### Post by sloggerkhan on 2008-08-26
oh, your using computer temp monitor. I was using the Hardware sensors monitor applet.
In computer temp monitor, I just see Kernal i2c sensors with cryptic numbers of hwmon sensors identified by number. My bad.

---

### Post by cowboyup6983 on 2008-08-26
> **sloggerkhan said:**
> oh, your using computer temp monitor. I was using the Hardware sensors monitor applet.
In computer temp monitor, I just see Kernal i2c sensors with cryptic numbers of hwmon sensors identified by number. My bad.

well can i use hardware monitor sensors, whatever works, this application isnt working for me, how do i uninstall and use hardware sensor monitor application.

---

### Post by sloggerkhan on 2008-08-26
just search synaptic for sensors-applet, install, and it should show up in the "add to panel" menu.
Once it's up, configure by right-click -> prefs.

Also, what is output of command "sensors" from the command line?

---

### Post by SkankinRatFink on 2008-10-30
Okay, I read this whole thread, and I have a stupid question ...

I, too, installed the computertemp package. How do I make it show up on my screen? I realize it's an "applet" that goes in a "panel."

I don't think I have any panels. And I can't find how to set one up. I'm using LinuxMint. Thanks!

---

### Post by oldsoundguy on 2009-03-03
you know, one of the simple questions has yet to be answered.
The LIST .. now just where IS hwmono0 (1-what ever) LOCATED?
In other words, which is which?(Why not NAMES instead?)
Am making the assumption that since I am running a hyperthreaded cpu on this box the highest temp on my list of the displayed 3 (#2) would be the processor. the second would be the board (#1).. not a clue as to where the third one is getting it's readings unless it is the PSU (#3) as that temp is LOW running a super efficient supply with dual fans.

---

### Post by oldsoundguy on 2009-03-03
once the applet is installed, you can get the temps by doing a mouse over.  The terminal work as to fan speed, etc .. no way I can see without constantly re writing the line of code (kinda lame, but better than NOTHING!)

---

### Post by oldsoundguy on 2009-03-03
I have items set up in my Linux Mint panel .. right click and "add to panel" does the trick ... now you still have to use synaptic to install the applet to make it available to add.

---

### Post by Ripose on 2009-03-03
Don't install computer-temp

Install:

   1. sensors-applet
   2. hddtemp (will ask if you want to run at startup) Yes
   3. sensord
   4. lm-sensors

Right click panel --> click Add to panel, Scroll down and click on Hardware Sensors Monitor

A single sensor should appear that probably reads 40 C

In a terminal type sudo sensors-detect
Answer YES to ALL questions
Exit Terminal

Reboot --> Enter BIOS --> Find your hardware monitor stats, take note of the temps as they will guide you in determining which temp is what in the sensors applet display.

Right click on sensor icon, click Preferences, click on an item, click properties, change Sensor Value Multiplier so temp changes to what what you saw in BIOS.

Change the label from Temp 3 to CPU or whatever matches your system.

---

### Post by oldsoundguy on 2009-03-04
as far as changing what the display says .. nope!! stuck with the hwmon0 (1,2,3,4,ad nausium!)

---

### Post by Ripose on 2009-03-04
> **oldsoundguy said:**
> as far as changing what the display says .. nope!! stuck with the hwmon0 (1,2,3,4,ad nausium!)
Can you post screen shots?

---

### Post by OldBitByter on 2009-03-25
I have tried all the above, but do not see the applet anywhere.

What am I missing?
[-o<

I should add that the hdtemp worked.

Oops, didn't notice that there were multiple pages, please ignore this until I've tried all.

Thanks

---

