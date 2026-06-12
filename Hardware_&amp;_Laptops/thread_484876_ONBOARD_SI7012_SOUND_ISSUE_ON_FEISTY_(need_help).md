---
title: "ONBOARD SI7012 SOUND ISSUE ON FEISTY (need help)"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by inoxllor on 2007-06-26
Hello
I have an old OEM Laptop with onboard audio. The problem is when I first boot to Ubuntu 7.04 I can't get sound, but If I restart or If I boot windows XP, I can get it to work.

When the sound isn't working, using **"sudo asoundconf list"** returns > no sound card. The same command when the sound is working, returns > SI7012 (which uses the snd_intel8x0 alsa module).

Using **"aplay -l"** returns  > device_list:222: no soundcards found...

But if I enter **"lspci -v"** the system detects the following:
> 00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Wistron Corp. Unknown device 2000
        Flags: medium devsel, IRQ 18
        I/O ports at 1c00 [size=256]
        I/O ports at 1800 [size=128]
        Capabilities: <access denied>

Adding  "snd-intel8x0" to etc/modules doesn't produce any change.

The access seems to be blocked(?) There must be a way to force Feisty to always access the onboard sound card. (although restarting or booting to windows XP seems to unblock it)

Does anyone have an idea how to solve this issue?

---

### Post by inoxllor on 2007-08-29
I could use some help with this issue.
It is somehow annoying... :(

---

### Post by inoxllor on 2007-11-08
SOLUTION:
(Tested on Gutsy Gibbon 7.10)

1st: **sudo gedit /etc/modprobe.d/alsa-base**
find "options snd-intel8x0 index=-2" and set it to "=0"

2nd:  
[B]sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa[/B]

3rd: **Reboot**
The sound should be working by now.

NOTES: 
I've found that activating the software modem drivers may conflict with the soundcard.
"snd-intel8x0m" is for SI7013 modem

If the above still doesn't bring audio to your system try this:
**sudo apt-get install linux-backports-modules-generic**

**sudo chmod a+rwx /dev/dsp**

**sudo gedit /etc/groups**
*edit the line that says: *
audio:x:29:haldaemon,root,yourusername

**sudo gedit /etc/modprobe.d/alsa-base**
*add line in the end:* 
options snd-intel8x0 ac97_quirk=3

---

### Post by cyberdoo on 2007-11-08
Thank you very much!

This worked exactly on my mythbuntu box!

---

### Post by ZorgTheDestroyer on 2008-06-23
:) Hey I've had the same problem and been searching around for some time without finding a solution. I followed your advise and I've got sound!!! YEARHAAA!!!!

Thanks a million Inoxllor

---

### Post by psylocyn on 2008-06-27
thank you so much! 8.04 LTS Hardy Heron, working :)

---

### Post by jimloomis on 2008-07-07
I have the same soundcard on my E-machines M5414 and I tried the given instructions and it didn't work.

I tried the alternate instructions "sudo apt-get install linux-backports-modules-generic" and got an error saying that it didn't exist.

Any ideas?

Thanks!

---

