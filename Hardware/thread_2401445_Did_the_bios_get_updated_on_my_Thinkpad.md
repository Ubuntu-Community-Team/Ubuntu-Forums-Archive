---
title: "Did the bios get updated on my Thinkpad?"
date: 2018-09-18
forum: Hardware
---

### Post by cdysthe on 2018-09-18
I'm on Ubuntu 18.04 with my Lenovo Thinkpad T460s. After an update a month or so ago I did a reboot after the update and I saw something which included the word "EFI" in the top left corner of my screen early during boot. Then everything went black and unresponsive.The laptop started system beeps every 5 seconds or so. I had no idea what was going on and tried to push the power button numerous times. I typed on the keyboard. Nothing. I was convinced something was terribly wrong. Nothing worked and since the laptop has a built in battery I could not cut power (probably a good thing in this case). After a few minutes the beeping stopped, power cycled and the laptop booted as normal. I had no idea what happened and whatever it was I was not given much forewarning or information. No way to see what it says while that message flashes by up in the screen corner.

I do know that a package with the word "firmware" in it was updated that day, but not exactly which one. I did check my bios and it's very new, from July 2018! This Thinkpad was bought at least 18 months ago. I updated bios back then on Windows, wiped the disk and put Ubuntu on it. No dualboot. I've checked by bios and it says: 

N1CET69W (1.37) 
2018-09-07. 

That is the latest bios I now can download from here: 

[https://fwupd.org/lvfs/device/42f29620-3d63-4f09-950b-9b7055570f28](https://fwupd.org/lvfs/device/42f29620-3d63-4f09-950b-9b7055570f28)

I downloaded it and it's the exact same version!

How did that end up on my laptop a month ago? I really like that I now can get bios updates on Linux since I never run Windows on my Thinkpads, but I do not like getting it updated without knowing  and with very little information about what was happening. If my Thinkpad didn't have built in battery I would probably have bricked it since the black beeping screen seemed like something I could only get rid of by fully pulling the plug on the machine. On the other hand I'm glad the process is that well protected against damaging user interaction. 

If I am wrong about all this, and got the bios some other way please let me know. What I do know is that I didn't know about LVFS until I saw it in OMG! Ubuntu a week ago or so.

---

### Post by oldfred on 2018-09-18
Possibly it did get updated.
Vendors & models supported, so far.
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

But I thought it was a separate notification?
**Ubuntu 16.04** and later natively will notify you for  BIOS updates. The system will regularly check for BIOS updates  automatically. When an update is available, a popup will be displayed to  flash the update

My Raspberry updates from standard update commands.

---

### Post by cdysthe on 2018-09-18
> **oldfred said:**
> Possibly it did get updated.
Vendors & models supported, so far.
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

My Raspberry updates from standard update commands.

If it did it's scary. I was THAT close to brick my Thinkpad. It should not be included with normal updates unless there are clear warnings and information about what will happen during reboot. I know the bios got updated somehow since there's no way I could have that version installed unless it was. It would be great if someone could tell me which package contains the bios updates.

---

### Post by oldfred on 2018-09-18
I would expect if from Ubuntu, there would be a log file somewhere.
It might have its own or be in dpkg logs?
Search thru this folder and dpkg.log,or other logs or folders.
/var/log

---

### Post by cdysthe on 2018-09-18
> **oldfred said:**
> I would expect if from Ubuntu, there would be a log file somewhere.
It might have its own or be in dpkg logs?
Search thru this folder and dpkg.log,or other logs or folders.
/var/log

Not sure what "would expect it from Ubuntu" really means :)

Anyway. I have been poking around in my logs and I now think it may be the fwupdate-signed package being behind what happened. See here:

[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)

This is all good except for the fact that I have no idea how it really works an if it can just do a bios update without informing the user. Especially since the symptoms of this update is so ominous I would expect some output to the user on what is going on. On Windows there's all kinds of warnings and information given when updating the bios. When mine allegedly got updated on Ubuntu there was something flashing by that I could not read and then a black screen with alarming system beeps that took several minutes to complete.

Would be great to have someone who knows more about this chiming in.

---

### Post by lisati on 2018-09-18
> **cdysthe said:**
> Not sure what "would expect it from Ubuntu" really means :)

I think what is meant is "would expect *if* from Ubuntu" - meaning that if something within your Ubuntu did something you might be able to find an entry in the system logs.

---

