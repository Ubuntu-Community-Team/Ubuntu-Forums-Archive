---
title: "Wireless network card not turned on"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by matthedane on 2007-05-05
My wireless network card (Intel 3945) doesn't turn on during start up. There is a led indicator and a manual wireless switch on the computer, but I can't turn on the led by pressing the button like in windows. I can get around the problem by booting in windows (which will make the led indicator turn on) and then reboot into Ubuntu Fiesty, but I would like to find a more permanent solution. I hope someone can help...

Matt

---

### Post by DagMan on 2007-05-05
what laptop brand and model is it?

---

### Post by matthedane on 2007-05-05
Fujitsu Siemens Amilo Pro V3405. 
I might also mention, that I couldn't find a BIOS option that allowed me to force on the network card by default.

Matt

---

### Post by EmilW on 2007-05-05
I have a similar problem with my Acer Travelmate 4400 laptop. Under Windows XP, software enables the built-in Broadcom wireless device to turn on (orange LED illuminates) and communicate.  But in Ubuntu (6.10 and 7.04) the LED never comes on.   BIOS has no switch to turn on the wireless device in the Acer, either.

---

### Post by Matthew521 on 2007-05-05
I have the exact same problem

---

### Post by DeadGuyAle on 2007-05-05
I'm having the same problem with a Dell Latitude D610

---

### Post by vs292 on 2007-05-05
I'd like to echo the others and say that I've got the same problem. 

I've got a Dell Inspiron 9300 and am using Kubuntu 7.04. I ran iwconfig and it says that the radio is off. What should I do to turn it on? 

:)

---

### Post by DarkN00b on 2007-05-05
What is your wireless connection called? Does it show up as (eth0, ath0, wlan0 etc)? Mine is eth0. So using my connection as an example, try this in a terminal: 

```
sudo ifup eth0
```

Replace eth0 with whatever your connection is and type in your password and hit enter.

---

### Post by Kweker on 2007-05-06
to vs292
To turn on/ off the radio use the "hardware-key", this is fn+f2
this works for me since i have the same laptop
note: you won't see the green WIFI-led like it does in windows, but it works, check iwconfig again to see

Greetz

Kweker

---

### Post by DagMan on 2007-05-06
There's a few things to look at that I can think of.
iwconfig as mentioned already.  you want to have the device name and essid correct so for example where "router" is the name of the ssid,
sudo iwconfig eth1 essid router
check out 'man iwconfig for more'

Also making sure that the module is loaded.  and in the following example only applying to the intel pro wireless 3945 card, yours may be differnat:
sudo modprobe ipw3945

But is sounds like for some of you perhaps needing enabling before any of that is turning on the wireless radio through the /proc or (possibly) /sys filesystems.  This can sometimes be done as the root user and usually through a file in /proc/acpi or a subdirectory thereof.  You'll need to google a bit to find out if there is a known problem with linux support on your laptop regarding acpi support.  In some cases an external module can be easily be built to enable a lot of features that aren't there right out of the box.  in some cases it might simply be that the large handful of scripts that ubuntu ships with in attempt to control these sort of interfaces aren't working the way they need to for your laptop and that making a script that's just a one liner specific to your system will solve it.

Don't give up on it, boot to Windows and then to Linux sounds really frustrating.  Do a bit of Googling about it and hopefully someone will post a fix for your specific laptop.
Also I forgot to mention that sometimes a bios update for a particular system can fix a thing or two.  If that's the case it's good to look and see if there's been other people with experience doing it good and bad as far as how it effects Linux installs.

I didn't recognise any laptops posted above as being similar to mine so I'm not of any further help here apart from saying that I've run into everything I've mentioned and have been lucky enough to always get things working one way or another.

---

### Post by vs292 on 2007-05-07
> **Kweker said:**
> to vs292
To turn on/ off the radio use the "hardware-key", this is fn+f2
this works for me since i have the same laptop
note: you won't see the green WIFI-led like it does in windows, but it works, check iwconfig again to see

Greetz

Kweker

Thanks, it worked:D I swear I tried it before and it didn't work...but yeah, it detects my network now. 

My problem now is getting it to actually connect to the damned thing, but I'll figure it out eventually. Enough thread hi-jacking from me I feel;)

---

### Post by matthedane on 2007-05-11
Thanks for the suggestions. I have tried following the guidelines that you have given me (ifup, modprobe and iwconfig) but I still can't get it to work. 

Kweker mentioned something about pressing FN+F2. In my case this takes my laptop into hibernation (handy shortcut btw), but as far as I can tell it doesn't change the state of the network card. Should I change any setting to get the trick to work?

The proc/acpi idea might be right, but after a bit of googling it became very clear that this is way beyond my capabilities. It appears that I am not the only one having this problem, so if someone could fix it with a simple script it would be greatly appreciated. 

What do you get out of the fact, that the network card works when I reboot from windows? 


Once again  thanks for your attempts to help me out...


Matt

---

### Post by Rob2Kx on 2007-05-13
> **DarkN00b said:**
> What is your wireless connection called? Does it show up as (eth0, ath0, wlan0 etc)? Mine is eth0. So using my connection as an example, try this in a terminal: 

```
sudo ifup eth0
```

Replace eth0 with whatever your connection is and type in your password and hit enter.

hi, what exactly does this command do?  I tried it out, and it allowed me to see wireless connections from the network manager (which I couldn't do before), but my wireless radio was still off....

---

### Post by DarkN00b on 2007-05-13
The command "ifdown" takes your card offline and "ifup" brings it back on line and reloads the firmware and/or drivers.

---

### Post by milco on 2007-05-26
same problem on my compaq presario V5201US

---

### Post by matthedane on 2007-08-30
I've got a solution! It turned out that it had to do with the modprobe after all. In order to turn on the wireless network card simply use this command:

sudo modprobe fsam7400 radio=1


In order to make it turn on every time you start up use these commands:


sudo echo fsam7400 >> /etc/modules

sudo echo options fsam7400 radio=1 >> /etc/modprob.d/options


It is that simple! The only flaw is that the button itself still doesn't work, but as long as I can turn on the network card I really don't mind that part...


Matt

---

### Post by I3allistix on 2007-09-02
> **vs292 said:**
> I'd like to echo the other and say that I had the same problem. 
I've got a Dell Inspiron 9300 and am using Kubuntu 7.04. I ran iwconfig and it says that the radio is off. What should I do to turn it on?


I had the same problem w/ my 9300. [This]("http://ubuntuforums.org/showthread.php?t=13576&highlight=ipw2200") thread walks you step by step on how to set it up. You have to do a little tweaking to directory names and such but it's really easy to follow.

---

