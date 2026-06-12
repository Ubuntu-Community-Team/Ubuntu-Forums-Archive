---
title: "Battery will not charge"
date: 2010-03-09
forum: Hardware
---

### Post by rette7mich on 2010-03-09
I am running ubuntu 9.10 fully updated on a Dell inspiron 8600 laptop. and i am having issues with my battery.  i just purchased the battery last week, it was purchased used, but guaranteed working.  so i installed the battery, it was recognized immediately upon booting and came with a charge of 75%. i have used some juice and am now around 38%.. BUT when i hover over the gnome battery icon it says the battery is fully charged, but when i click the icon it confirms that the battery's charge is 38%. i confirmed in the battery settings that the batteries maximum capacity is 75%.

so since it says it is fully charged, it will not charge my battery. so far i have reinstalled acpi and updated to the latest bios version A14.

here is my acpi -V

Battery 0: Unknown, 38%
Battery 0: design capacity 6299 mAh, last full capacity 4726 mAh = 75%
Adapter 0: on-line
Thermal 0: ok, 43.5 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 90.0 degrees C
Cooling 0: Processor 0 of 10

---

### Post by sleepee on 2010-04-05
i have a similar problem as well on my hp dv7 running karmic 64.
im not sure if it's exactly the same though...
my laptop discharges fine and the power manager reads it fine...
connecting the power cord to charge it is where i get problems.
it seems like it just charges when it wants to.  it will get stuck at certain charge percentages and resume when it wants to.
eventually it charges all the way, but it doesn't charge continuously, but intermittently... if that makes any sense..
basically, the charging pauses randomly for no reason... and it just continues charging randomly as well..
when the charging pauses, the power manager applet says fully charged when i hover, but tells me the real charge when i click on it..  so we have the same issue as far as that..

i thought it might be the power cord, or maybe the battery... but this laptop is fairly new..  only had it for a couple months..
maybe i should test it out in windows to see if i get the same issue there..
ughhhh... i hate booting to windows..
anyway, when i do it, i'll post back again..

---

### Post by Eleshar on 2010-07-21
I have totally similar problem with Ubuntu 10.04 (Dell Latitude D410). 

Whenever the adapter cable is in, the battery status reads "fully charged". 

I installed some program to upgrade the battery status, so it says now "fully charged" but displays actual state of battery (3 % left), still no recharging though. 

And when looking at the battery properties, it says the battery should be rechargable to 98,6 % of its original capacity (brand new one, made by Sony for this Dell model - but it stopped recharging only very recently, before then, it recharged normally), so it does not seem to be a battery problem...

---

### Post by PhelanPKell on 2010-07-21
I too am having a similar issue, also with 10.04 in my case, fully updated.

In my case, it's with an older Thinkpad R40 Type 2681.

I started a thread here: [http://ubuntuforums.org/showthread.php?p=9617641#post9617641](http://ubuntuforums.org/showthread.php?p=9617641#post9617641) lastnight, and as I mention there I've heard of and researched some info, but found no conclusive fix as of yet.

As soon as I have a second, I will post links to the fixes I've found, in the even that they help you guys. To give you a lead on what I've found is the supposed problem, is that it has to do with Airplane Mode somehow kicking in and interfering with the A/C plugs ability to charge the battery.
It's weird, I know. :S

---

### Post by Eleshar on 2010-07-21
Lo! Be praised, o mighty saviour... Really, I am glad that I am not the only one having this problem, especially because I am quite a newbie to Ubuntu and Linux.

---

### Post by PresenceofMind on 2010-07-21
Hello guys,

Login to the terminal and try this out:

```
cd /proc/acpi/battery
```

It should have a directory called BAT1 or similar....change into that by typing:

```
cd BAT1 && ls -l
```

There should be 3-4 things in there...you can find out detailed info about your batteries through by using the cat command.

```
cat info
```

```
cat state
```

See what you find.

---

### Post by PhelanPKell on 2010-07-21
Here is the returns that I get from my Thinkpad R40


```
phelanpkell@GrinnerLo:/proc/acpi/battery$ cd BAT0 && ls -l
total 0
-rw-r--r-- 1 root root 0 2010-07-21 18:16 alarm
-r--r--r-- 1 root root 0 2010-07-21 18:16 info
-r--r--r-- 1 root root 0 2010-07-21 18:16 state

```



```
phelanpkell@GrinnerLo:/proc/acpi/battery/BAT0$ cat info
present:                 yes
design capacity:         57600 mWh
last full capacity:      56050 mWh
battery technology:      rechargeable
design voltage:          14400 mV
design capacity warning: 2802 mWh
design capacity low:     200 mWh
capacity granularity 1:  1 mWh
capacity granularity 2:  1 mWh
model number:            IBM-02K6928
serial number:            1647
battery type:            LION
OEM info:                Panasonic

```



```
phelanpkell@GrinnerLo:/proc/acpi/battery/BAT0$ cat state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mW
remaining capacity:      0 mWh
present voltage:         11971 mV

```


This info looks a lot like what I see in the Power Statistics window, which in essence only tells me that my battery should be fine, but that somewhere there's a "disconnect" of sorts. :S
I hope that you may be able to discern something additional from this that I cannot.

---

### Post by PhelanPKell on 2010-07-21
Here is one of the fixes that worked for others which I said I would post.

[http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/420-battery-not-charging.html](http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/420-battery-not-charging.html)

Something I've noticed with this bug, is that it has occurred in older versions of Linux dating back to 2007, and that it was supposed to be fixed in atleast one older kernel version...

---

### Post by Eleshar on 2010-07-21
Interesting - I think the battery issue came with my transition to Lucid Lynx... or with some actualisation... more probably the first one because very recently, I had to reinstall the system because of some trouble with Network Manager and it did not recharge even after clear install... I would try some older version, were I not so lazy.


Revenons à nos moutons...
I found that there is BAT0 and BAT1 in the directory. I list both of them just to be sure, but the BAT1 seems to be some secondary energy source I do not happen to possess...

My returns:

for 
**cd ****BAT0 && ls -l**
the same as PhellanPKell (with appropriately different date and time

**cd ****BAT1 && ls -l**
the same as PhellanPKell (with appropriately different date and time

**cat info** (for BAT0)
present:                 yes
design capacity:         6600 mAh
last full capacity:      6509 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 600 mAh
design capacity low:     200 mAh
capacity granularity 1:  66 mAh
capacity granularity 2:  66 mAh
model number:            DELL X5
serial number:           28
battery type:            LION
OEM info:                Sony

**cat info** (for BAT1)
present:        no

**cat state** (for BAT0)
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1 mA
remaining capacity:      201 mAh
present voltage:         10319 mV

**cat state** (for BAT1)
present:        no


addendum: Just tried the Aircraft Manager and it does not even seem to kick in, it is clearly for 8.10 and nothing later.

---

### Post by PhelanPKell on 2010-07-21
> **Eleshar said:**
> Interesting - I think the battery issue came with my transition to Lucid Lynx... or with some actualisation... more probably the first one because very recently, I had to reinstall the system because of some trouble with Network Manager and it did not recharge even after clear install... I would try some older version, were I not so lazy.


Now that you mention this, it occurs to me that I had just done the update to 10.04 on this laptop the other day, and this issue started roughly the same day...(technically I updated, powered down, and booted the laptop up 2 or 3 days later, which is when the issue started. But effectively that was the first boot under 10.04).

---

### Post by PhelanPKell on 2010-07-22
Here's another of the fixes I found.
FYI with this one, it requires PortIO to function

[http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/1955-fix-no-battery-charging-ubuntu.html#post15644](http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/1955-fix-no-battery-charging-ubuntu.html#post15644)

---

### Post by PhelanPKell on 2010-07-22
Bump

We all really need a resolution for this issue. :( It's kinda making the concept of a laptop pointless, if it can't be mobilized. :S

---

### Post by Eleshar on 2010-07-23
Er... and this portIO happens to be exactly what? And how do I make it function (supposing that it does not because the solution does not really... solve my problem, still not recharging). I tried to look it up, but everyone probably knows what it is and does not seem to consider necessary to explain it to anyone...;)

Also, is there no hard switch on this lovely airplane mode in ubuntu? I think I have seen one somewhere but I cannot remember where... or was it just during the installation that a motivation screen told me that the airplane mode is possible with Ubuntu?

---

### Post by PhelanPKell on 2010-07-23
> **Eleshar said:**
> Er... and this portIO happens to be exactly what? And how do I make it function (supposing that it does not because the solution does not really... solve my problem, still not recharging). I tried to look it up, but everyone probably knows what it is and does not seem to consider necessary to explain it to anyone...;)


My apologies for not better explaining those fixes.
Firstly, let me point out that these fixes aren't necessarily going to work for everyone. They did nothing for me, but they have worked for others.

PortIO, as I understand it, is a library that Python scripts can access in order to delegate a command or function based one what is appropriate for the device. Kinda like if the "Shutdown" function was different from two laptops, the Python script would tell PortIO to initiate "Shutdown" and it would command each laptop appropriate to their "shutdown" command structure.
[COLOR=Red]***Again, this is my understanding, which may not be correct***[/COLOR]

If you need a download of PortIO, let me know. I believe I bookmarked the download site for the library, and I can toss it up somewhere for you to download if you would otherwise prefer.

> **Eleshar said:**
> 
Also, is there no hard switch on this lovely airplane mode in ubuntu? I  think I have seen one somewhere but I cannot remember where... or was it  just during the installation that a motivation screen told me that the  airplane mode is possible with Ubuntu?

I've dug around quite a bit for everything from terminal commands, to programs. Thus far, I've found ZERO simple terminal switch commands, and 2 programs. The two programs (Aircraft Manager, and I think it was called Elmurato) have proven useless, which may actually be an incompatibility with 10.04 (there's plenty of documentation of them working in everything up to 9.04, but none that I've found for 10.04).



It's quite demoralizing to have to power down my laptop, disconnect the A/C, Pull the battery, reattach the battery and reconnect the A/C, all the while leaving the laptop off, just to be able to charge it.

I really wish we could get some attention to this issue.

---

### Post by PhelanPKell on 2010-07-23
I'm listing Install instructions for PortIO here, so as to avoid sifting through an entire large post.

It's actually pretty straight-forward. Grab PortIO [here]("http://linux.softpedia.com/progDownload/PortIO-Download-42907.html")
And I recommend extracting the folder inside the archive to your desktop, for arguments sake, to coincide with my process (unless you're comfortable doing otherwise).


All you have to do is open a terminal and make sure you are in the folder you extracted the PortIO install files to.

For arguments sake, the files are in the archive in a folder titled "portio-0.4"
Assuming you extract that to your Desktop, in the terminal type [COLOR=Red]cd Desktop\portio-0.4[/COLOR]
**With the capital on Desktop**

From this prompt, you want to type [COLOR=Red]Python setup.py install[/COLOR][COLOR=Black]

This should run the installation of PortIO.
There is one error I received that referenced "gcc" and "error 1" which when I googled it, the fix was to install a dev package from Synaptic Package Manager.
It is only necessary if you receive that error. I do apologize for not recalling the dev package necessary though. :(
[/COLOR]

---

### Post by Eleshar on 2010-08-01
I didn't really have time to try what you proposed, but yesterday I noticed an interesting turn of events... The battery finally reached the point of 0 % (and did nothing, as expected)... then I plugged it in and... heureka... it was recharging again! It reached about 17 % when I had to shut my laptop down. But... when I switched it on... it did not continue to recharge:(

---

### Post by rette7mich on 2010-08-01
thank you all for your posts, i have since discovered mine to be a hardware problem

---

### Post by PhelanPKell on 2010-08-01
> **Eleshar said:**
> I didn't really have time to try what you proposed, but yesterday I noticed an interesting turn of events... The battery finally reached the point of 0 % (and did nothing, as expected)... then I plugged it in and... heureka... it was recharging again! It reached about 17 % when I had to shut my laptop down. But... when I switched it on... it did not continue to recharge:(

In order to recharge my battery, I have to power down my laptop, disconnect the A/C, remove the battery. Place it back in, connect the A/C, and leave the laptop turned off. :S
End result of this story: I feel your pain. :(

---

### Post by kgas on 2010-08-01
there is a similar problem with hp dv5 laptop(one year old).battery was completely dead and with legacy OS also now not charging.:(, return to store for battery replacement. With old battery I will fiddle and post the result here latter.

---

### Post by jamincollins on 2010-08-06
I've been experiencing a similar problem with my T61p.  The laptop is normally connected to AC and can go for long periods (days) without me disconnecting it from the AC.  However, when I seem to see the problem every time I've left it running and connected to the AC for a day or more.  Once I disconnect it from the AC it runs on battery normally.  However, once I reconnect the power cord it almost immediately claims to be fully charged.

In each case I've found that if I reboot the laptop it charges properly.  I believe it's just a case of the OS getting confused on whether it should or shouldn't charge the battery.  I've install the tp-smapi-dkms package in hopes of getting better information next time it happens.

---

### Post by jamincollins on 2010-08-07
Just verified that with an uptime of less than a day, the laptop goes from discharging (off-AC) to charging (on-AC) just fine.


$ uptime
 14:04:15 up 19:40,  4 users,  load average: 0.15, 0.17, 0.10


$ cat /sys/devices/platform/smapi/BAT0/state 
charging

$ cat /sys/devices/platform/smapi/BAT0/remaining_percent
56

Guess we'll see how it goes once it's been up for a day or two.

---

### Post by tushi on 2010-08-12
Battery 0: design capacity 4400 mAh, last full capacity 942 mAh = 21%

This is the output from acpi -i

tushi@tushi-laptop:/proc/acpi/battery$ cd BAT0 && ls -l
total 0
-rw-r--r-- 1 root root 0 2010-08-13 02:04 alarm
-r--r--r-- 1 root root 0 2010-08-13 02:04 info
-r--r--r-- 1 root root 0 2010-08-13 02:04 state
tushi@tushi-laptop:/proc/acpi/battery/BAT0$ cat info
present:                 yes
design capacity:         4400 mAh
last full capacity:      942 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 108 mAh
design capacity low:     67 mAh
capacity granularity 1:  41 mAh
capacity granularity 2:  834 mAh
model number:            EV06047
serial number:           37767
battery type:            LION
OEM info:                LGC-LGC
tushi@tushi-laptop:/proc/acpi/battery/BAT0$ cat state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      1028 mAh
present voltage:         12491 mV
tushi@tushi-laptop:/proc/acpi/battery/BAT0$ 


Why it is only charging at 21%?

---

### Post by Eleshar on 2010-08-28
And so it seems that my brand new Sony battery, after b eing discharged to 0 percent has left us in her quest for eternity (read: it is finally dead - the energy management displays no battery). I wish I knew at least whom to blame... as the problems seemed to be connected with the installation of Lucid Lynx (but installation of an older version that was supposed to allow to run the aircraft manager, which by the way was unsuccessful, díd not help either)...

---

### Post by Eleshar on 2010-09-06
Not a clue what is happening - my battery seems to be recharging again?!

---

### Post by lesbakker on 2011-03-11
Hi guys. I bought a new battery a few weeks ago since my old one couldn't hold a charge for very long. Starting a few days ago, the new battery won't charge from 0%. Any idea why? 

when I use the cat info and cat state commands, I get very vague information. Any and all help is greatly appreciated!


```

cat info
present:                 yes
design capacity:         unknown
last full capacity:      unknown
battery technology:      rechargeable
design voltage:          unknown
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  90 mAh
capacity granularity 2:  90 mAh
model number:            Primary
serial number:           
battery type:            Lion
OEM info:                Hewlett-Packard 

cat state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            0 mA
remaining capacity:      0 mAh
present voltage:         0 mV
 
```

---

