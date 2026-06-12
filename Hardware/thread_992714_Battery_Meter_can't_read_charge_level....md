---
title: "Battery Meter can't read charge level..."
date: 2008-11-25
forum: Hardware
---

### Post by wardrich on 2008-11-25
Not sure what I've done here, but for some reason my battery meter says "Computer is running on AC Power.  Battery state could not be read at this time.  Battery charge is currently unknown"  I'm using a Lenovo Thinkpad R60, if that helps at all.  I'm not sure what I've installed that's made this happen, the last few packages I remember installing were MythTV, LMMS, and Hydrogen.

---

### Post by frankleeee on 2008-11-25
> **wardrich said:**
> Not sure what I've done here, but for some reason my battery meter says "Computer is running on AC Power.  Battery state could not be read at this time.  Battery charge is currently unknown"  I'm using a Lenovo Thinkpad R60, if that helps at all.  I'm not sure what I've installed that's made this happen, the last few packages I remember installing were MythTV, LMMS, and Hydrogen.

There is a add to panel battery applet have you checked to see if that one works.

---

### Post by wardrich on 2008-11-25
I just added that one... it says "No Battery Present".  The LED on the computer is also flashing.  Maybe it's something deeper than the OS.

---

### Post by frankleeee on 2008-11-25
If it was me I would with the computer plugged in, if on, remove the battery and put it back in and then see if it runs on the battery, or due a restart, or shut it down unplug it to see if it starts with the battery. Usually Linux programs don't need a restart to fix problems but I have had it work on numerous occasions. That is where I would start.

---

### Post by wardrich on 2008-11-26
So I restarted my computer today, it's not actually related to Ubuntu.  The battery led even flashes when the computer is first turned on.  Maybe if I leave my computer on and unplugged and kill the battery, then re-charge it, it will make a difference.

---

### Post by frankleeee on 2008-11-26
> **wardrich said:**
> So I restarted my computer today, it's not actually related to Ubuntu.  The battery led even flashes when the computer is first turned on.  Maybe if I leave my computer on and unplugged and kill the battery, then re-charge it, it will make a difference.

In the terminal run "acpi 1" this should give you a battery reading. I found this by typing in help battery in the terminal there are several other commands, like    "man -k battery"  this gave me the acpi 1 command. If your running a dual boot I would be hesitant to let the computer just run on the battery until it stops, basically because I have never used anything other than Linux which would probably not be effected adversely by this. I just installed BatMon from add remove and it works on my computer but I believe it reads the acpi there is a site link so read all the info to see if it is applicable, it downloaded 15 files to get it working.

---

### Post by wardrich on 2008-11-26
Thanks for the help, I've concluded that the issue itself is the battery, which I recently replaced maybe 2 months ago. The acpi command outputted:    
 Battery 0: Unknown, 0%

And the fact that even before Linux had started up, the battery light was flashing has lead me to strongly assume that this issue (unfortunately) lies deeper than ubuntu.  There was a battery recall a few years ago involving my laptop model (as well as many others).  There's a good chance my battery is one that was recalled, but I'm really not too sure.  My battery doesn't even look like the one on the lenovo site, so it could be a shady "made in china" kinda thing.  My dad actually was the one who purchased it, so I'll have to do some deep investigating to see what the deal is.

Thanks again for your help.  If I'm able to make any grounds on this situation, I'll try to keep this thread up-to-date.  Who knows, it may help somebody in the future.

---

### Post by Charbs on 2009-01-09
I have the same problem, a constant 0% battery notification. But I can use this battery for around 2 hours until it dies. And when it does die, theres no warning, the laptop just shuts off. Ive tried draining the battery fully, even putting it in the freezer for 6 hours. Nothings helping.

The battery obviously works if i can run off it for 2 hours. I just cant figure out why its stuck at a 0% reading.

---

### Post by icelord on 2009-01-10
> **Charbs said:**
> I have the same problem, a constant 0% battery notification. But I can use this battery for around 2 hours until it dies. And when it does die, theres no warning, the laptop just shuts off. Ive tried draining the battery fully, even putting it in the freezer for 6 hours. Nothings helping.

The battery obviously works if i can run off it for 2 hours. I just cant figure out why its stuck at a 0% reading.

Just simple reset hardware ACPI -
shutdown ubuntu
disconnect power cord
disconnect battery
press power button for 5 secconds
reconnect battery
reconnect power cord
turn on.... enjoy :)

---

### Post by Charbs on 2009-01-10
That sounded too good to be true. And it was, it didnt do anything for me. How am I supposed to know if it actually resets? Is the power light supposed to blink or anything?

How is that even possible with no power to the laptop?

---

### Post by icelord on 2009-01-10
> **Charbs said:**
> That sounded too good to be true. And it was, it didnt do anything for me. How am I supposed to know if it actually resets? Is the power light supposed to blink or anything?

How is that even possible with no power to the laptop?

no blinks, just keep key pressed for few seconds, power collected in capacitors have enough to reset acpi chip while power key pressed

i do this trick on my ideapad time-to-time

---

### Post by Charbs on 2009-01-10
Well it doesnt seem to be working for me on my Compaq Presario V2000. There is no change to the state of the battery meeter.

---

### Post by icelord on 2009-01-10
> **Charbs said:**
> Well it doesnt seem to be working for me on my Compaq Presario V2000. There is no change to the state of the battery meeter.

this sux... can you, please, show result of:

[FONT="Courier New"]
cat /proc/acpi/battery/BAT0/info

cat /proc/acpi/battery/BAT0/state
[/FONT]

---

### Post by Charbs on 2009-01-10
I have posted some more info in a different thread. It has the info you are asking for here:

[http://ubuntuforums.org/showthread.php?t=1035411](http://ubuntuforums.org/showthread.php?t=1035411)

---

### Post by Charbs on 2009-01-11
So what do you think, after checking out my other thread? Any clue?

---

