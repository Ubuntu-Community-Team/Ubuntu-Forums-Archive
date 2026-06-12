---
title: "Ubuntu Install has altered my bios!!!"
date: 2009-08-30
forum: Hardware
---

### Post by studiodude on 2009-08-30
Is this possible?   I have installed Ubuntu studio on my main Studio Computer intending to run it past all my pro hardware.  It has taken a while to get set up and I am still having problems with the drivers for my hardware but I am happy to work through these bit by bit.  The main problem I have is that I have the machine dual booting quite happily with XP pro but somehow the bios has been altered and I am not sure how to rectify it as the settings that have changed are no longer options.  

I have had some freezing in XP and uncharacteristic CPU overload spikes when running cubasesx3. Diagnostics have shown up that I appear to be overclocking my ram which could be the cause of the freezes.  I jumped into the bios to check the settings - I would not have overclocked by choice - and guess what - all the settings for clock speeds, FSB etc have GONE! Not even showing what the settings are.  I am certain this has happened since the Ubuntu installation but despite re-flashing the bios I still have no access or info on my systems FSB, cpu clock speed, video aperture etc, it seems that whole page has disappeared and the bios is now a very slim set of options whereas before it was quite comprehensive.  Has anybody ever come across this before??  
System info:

Acer Aspire 9424 1.8ghz dual core Intel
2gb Ram
Nvidia  256mb Video ram

Pheonix bios 1.24 from acer re flashed after ubuntu install to try and get my bios settings to what they were before. 

Thanks in advance for any answers as always.   Ubuntu Studio runs awesome on this machine by the way, despite not seeing my hardware yet and I look forward to the day I can ditch windows altogether.

---

### Post by cascade9 on 2009-08-31
Technically, its possible to change BIOS from an OS. I've never heard of it happening without some software, its not something an OS should 'just do'. Even if it did change settings, it shouldnt have flashed your BIOS. Since your suddenly missing options from your BIOS, and flashing the BIOS doesnt get them back, I think your BIOS must have been flashed, and whatever new version is on your machine doesnt have the options you are used to. All really weird.

If your running any Acer software in windows, I would check to see if there is a BIOS flashing capability...its just possible that you got some update from Acer thats flashed your BIOS.

The only other thing I can think of is to try to flash your BIOS to an earlier version. You might get your options back then.

---

### Post by howefield on 2009-08-31
Sounds more like a case of a little knowledge being a dangerous thing.

I doubt that Ubuntu will have "altered" your bios settings without explicitly telling you, more likely something you have done or changed.

---

### Post by metallus on 2009-08-31
it is not possible for ubuntu to change your bios settings without you explicitly telling it to. chek for enable/disable switches that might "hide" your options.

---

