---
title: "Lenovo G50-70 fan stops working at random"
date: 2015-04-22
forum: Hardware
---

### Post by asgard2 on 2015-04-22
Hi,

the fan is running fine, it stops and starts without any problems as I can see ... but I notice that after some time idle, the notebook fan maybe is not starting again.  
The core temp can grew up to over 80 degrees and nothing is happening. 
During a reboot, after the problem appears, the fan does still nothing and the problem continues. 
Only a power off can fix that, after powering on again, the fan starts on high speed.

First time I noticed that problem was after a memtest run over night, that was a few days after the notebook was in repair and they replaced the fan and updated the bios. 
The old fan was rumbleing from time to time.

The bios options are very limited, I can not find a fan control.
It seems to me, that it is not a hardware problem because the fan is running fine, the other time ...

But I have also no idea what it could be ... and I do not want to send this device in again.

Any help please? 

```
     *-cpu          Produkt: Intel(R) Core(TM) i5-4210U CPU @ 1.70GHz     
*-firmware          Beschreibung: BIOS          Hersteller: LENOVO          Physische ID: 0          Version: 9ACN29WW          date: 10/20/2014          Größe: 128KiB          Kapazität: 4032KiB          Fähigkeiten: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
```

---

### Post by dino99 on 2015-04-22
is the bios/uefi dealing with powersaving, or is it done by your ubuntu system ?

[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)
[https://wiki.ubuntu.com/Kernel/PowerManagementALPM](https://wiki.ubuntu.com/Kernel/PowerManagementALPM)

if you cant find a good setting, then warn again about the guaranty.

---

### Post by asgard2 on 2015-04-22
I did nothing to reduce power, only switching the governor to powersave and performance, but same problem at the performance mode.

Xubuntu 14.10 64Bit is installed, it boots in legacy mode.

---

### Post by asgard2 on 2015-04-22
...before I experiment any longer, is there a possibility that the fan is blocked on software level, so that the fan is not turning on during reboot?
When the problem appear, I can reboot to a live xubuntu and the fan is not working ...

If not, I would suppose, there are only two options, bios failure or hardware failure. 
But I hope someone is poping up with another theory. ;)

---

### Post by QIII on 2015-04-22
Hello!

You have provided these observations, none of which has anything to do with the OS:

The fan stops randomly.
Reboot does not start the fan.
Power off and back on starts the fan.
The previous fan was making noise and so it was replaced.
The BIOS was updated.
The behavior is present in a Live session -- which would have no fan control software installed.

I would suspect you have a hardware or BIOS issue.  It could be a simple thing like the fan wasn't properly plugged in, as frustrating as a bad BIOS flash or as catastrophic as a bad capacitor on the motherboard not charging the circuit for the fan for its initial spike in current draw and subsequently acting as a resistor - or a break - in the circuit.

On reboot or cold start, the fan is controlled by the BIOS/EFI, not the OS (assuming you have the OS set up to control fan speed.)  The OS cannot take over until it is running, which comes only after the BIOS turns over control to the OS loader.  This leads me to dismiss an OS problem for the moment.

You really need to rule out hardware/BIOS issues before you bang your head against the wall trying to see if it is the OS.

---

### Post by asgard2 on 2015-06-21
Thanks for your support, some time has now pased, but the problem is still present. :/

Updated the bios, this didn't solve the problem.

After that I send the notebook back in and described these fan backouts and also note, the outage appears randomly and maybe only after a few days. They replaced the whole mainboard, but a few days later, the same problem appears again.
I am even surprised, that the problem is not solved at this point. The device also received after repair a complete xubuntu 15.0464Bit reinstall.

On the next repair, the notebook came unrepaired back ... and they note a possible handling error.

From my point of view, there is no chance anymore that this can be a software error, but it is seems impossible to prove.

I can maybe create a video with "watch sensors" and show them, that the fan is not truning on at a high temperatures like 80°C, even after a reboot until the grub menu appears. But for this, I need to open the maintrance panel when the notebook is still running, maybe they would kill my warranty because of this?


So, I am out of options, can give me someone an advice?

---

### Post by QIII on 2015-06-21
Actually, it might be best to get a video of the BIOS screen at one of those times when the fan is not operating.  That would entirely eliminate the OS or software as the culprit.

Your BIOS screen will likely have something like a "PC Health" screen or something like that.  These will often show current temperatures and fan speeds.  Catch a video or still shot (with a smart phone if need be) of that when the temperature is high and the fan is not turning.

There should be no need to disassemble anything to determine this -- so there should be no reason to void your warranty.

                                      Viel Glück!

---

### Post by asgard2 on 2015-06-21
> **QIII said:**
> 
Your BIOS screen will likely have something like a "PC Health" screen or something like that.  These will often show current temperatures and fan speeds.  Catch a video or still shot (with a smart phone if need be) of that when the temperature is high and the fan is not turning.


Would be nice, but I can not find anything like that.

Here are some pictures from the bios, in case I miss something:
[https://www.dropbox.com/sh/nsj8yl02hosbet7/AAAoWBPtp9AT0xQTdZqGDRPGa?dl=0](https://www.dropbox.com/sh/nsj8yl02hosbet7/AAAoWBPtp9AT0xQTdZqGDRPGa?dl=0)

---

### Post by QIII on 2015-06-21
Well, that's not particularly helpful, is it?

is the fan running at all while you are viewing this?

---

### Post by asgard2 on 2015-06-21
> **QIII said:**
> Well, that's not particularly helpful, is it?

is the fan running at all while you are viewing this?

I added these pictures to show the available bios options, because I can not find anything about the fan.

Yes, the fan is currently running by viewing this.

---

### Post by QIII on 2015-06-21
What I meant was that the BIOS is not very helpful, not that the images weren't helpful.  :)

---

### Post by asgard2 on 2015-06-21
Oh sorry, it was a misunderstanding.

Is there anything else I can do?

---

### Post by asgard2 on 2015-07-31
Finally, the manufacturer was not able to repair and not willing to replace the device ..., but I could get rid of it over the seller.

It was a Lenovo G50-70, would be interesting if this was only (strange) single case ... ?

---

### Post by Evgueni on 2016-01-03
It seems that I may be having the exact same problem. Fan sometimes stops working during idle times and will not start back again. Only a power off fixes the issue and restarts the fan at full speed. Should I give up hope and ask for a replacement?

---

### Post by asgard2 on 2016-01-03
> **Evgueni said:**
> It seems that I may be having the exact same problem. Fan sometimes stops working during idle times and will not start back again. Only a power off fixes the issue and restarts the fan at full speed. Should I give up hope and ask for a replacement?

Based on my experience you can give up hope, if you can receive an replacement, you can give it a try. 
**If you get one, please let us know if it is gone.**

But in my case, the medion support did not (or want to) see the failure, even how much I tried to document or explain ... and refused to give an replacement.

---

