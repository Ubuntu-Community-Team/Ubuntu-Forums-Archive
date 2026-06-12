---
title: "No sound from my laptop speakers."
date: 2010-09-25
forum: Hardware
---

### Post by Luckyman13 on 2010-09-25
I'm new to ubuntu and I have it installed on my laptop  and i can't get my speakers to play any sound but I can get sound from my head phone can anybody help me?

---

### Post by PresenceofMind on 2010-09-26
Have you checked your sound preference? right-click the speaker icon on the top right and select 'Sound Preference'. Make sure that all the 'Mute' boxes are unchecked (i.e. unticked).

Also go to System > Preferences > Start-up Applications and check to see if the PulseAudio Sound system is set to start up during boot.

---

### Post by Luckyman13 on 2010-09-26
yes I did all that already and i have read on here and other place about no sound and done what they said fix there problem like update install a mixer check to see if anything was mute and none of them work I can get sound out of headphones or speaker plug into the headphone jack just not out of my laptop speakers.:(

---

### Post by Luckyman13 on 2010-09-26
bump

---

### Post by Luckyman13 on 2010-09-26
bump plz help

---

### Post by Luckyman13 on 2010-09-27
does anybody have any ideas?

---

### Post by Luckyman13 on 2010-09-27
can anybody tell me something?

---

### Post by gordintoronto on 2010-09-27
Can you confirm that you installed Ubuntu 10.04? What brand and model of laptop is it? I had a similar problem with a new HP G62 laptop, but it went away.

By the way, you shouldn't bump a thread more than once a day.

---

### Post by Luckyman13 on 2010-09-28
I do have ubuntu 10.04 amd the make is compaq mode presario CQ62. If you could help me that would be grate.:)

---

### Post by rodrigogp on 2010-09-28
Hi,

I have the same problem with my new HP Laptop. I followed the sound troubleshooting guide but I couldn't solve the problem

Please heeeeeeeelp!!!! :-)

```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
        Subsystem: Hewlett-Packard Company Device 1425
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d4400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```Let me know if you need me to provide some more hardware information

Thanks and best regards

---

### Post by mastablasta on 2010-09-28
did you upgrade Alsa already?
Did you try to switch to Analog audio duplex in sound preferences?

---

### Post by rodrigogp on 2010-09-28
Hi,

I tried everything in sound preferences without success

I installed a fresh 10.04 i386 distro in my new laptop and there's no pending updates

As I said it's only a problem with the speakers. I can listen through the headphones

I have 9.10 in other laptop and I don't have any problem with anything

Any idea?

Thanks

---

### Post by gordintoronto on 2010-09-29
I reported a bug, and was told to add a launchpad audio-dev repository. It cleared up the problem, although it also means I get a new version of audio software quite frequently.

---

### Post by Luckyman13 on 2010-09-29
> **gordintoronto said:**
> I reported a bug, and was told to add a launchpad audio-dev repository. It cleared up the problem, although it also means I get a new version of audio software quite frequently.

> **mastablasta said:**
> did you upgrade Alsa already?
Did you try to switch to Analog audio duplex in sound preferences?

I have tryed both of these and the both don't work for me I just might have to keep using speakers plug in my headphone jack.

---

### Post by rodrigogp on 2010-10-01
Hi,

So now, what we can do? only to wait for the bug to be solved?

---

### Post by drifter2502 on 2010-10-07
> **rodrigogp said:**
> Hi,

So now, what we can do? only to wait for the bug to be solved?
You could try this....
[http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/](http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/)
I upgraded to Mint 9 a few days ago and ran into the same trouble but this fixed all my sound issues including 'Laptop speakers refusing to mute when phones plugged in.` 'Sound stream recording from internet.' and 'Recording sound from my line in.`

---

### Post by rodrigogp on 2010-10-10
Great!!!

Thanks a lot! 

I could solve the problem following that tutorial :-D so now I have 2 friends more using Ubuntu :-)

Thanks
byeeee

---

### Post by CiscoPixie on 2010-12-11
Hey

This is something I read so see if it works.. applications->accessories->terminal
then type:  sudo apt-get install linux-backports-modules-alsa-lucid-generic

Also, make sure backports are enabled in the update manager

---

### Post by metalman41 on 2011-01-06
If you have Windows Vista. 
Go to Control Panel, click on Task bar and Start Menu, open 
Notification Area. Tick Volume, click Apply and the Volume Icon will appear in the bottom right corner

---

### Post by lidex on 2011-01-07
Need more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Fableflame on 2011-01-08
> **lidex said:**
> Need more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

I'm having a problem similar to this one.
My sound works on start up, but eventually all sound will quit playing. I check my sound options when this happens, and nothing is ever muted. All it takes is a quick reboot to  fix this problem, but it happens several times a day, and it is quite irritating when I have to drop whatever I'm doing and reboot so I can hear my music or the person that I'm talking to on Skype.

I ran the script you mentioned, and here are the results:

[http://www.alsa-project.org/db/?f=3dca35c28afdd3f7a041dd5445ceabadff2f4b4c](http://www.alsa-project.org/db/?f=3dca35c28afdd3f7a041dd5445ceabadff2f4b4c)

---

### Post by lidex on 2011-01-08
@Fableflame
Try specifying a model in alsa-base.conf
```
echo "options snd-hda-intel model=ref" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

