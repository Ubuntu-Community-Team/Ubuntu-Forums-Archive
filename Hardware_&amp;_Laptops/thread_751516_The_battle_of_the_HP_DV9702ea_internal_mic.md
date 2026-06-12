---
title: "The battle of the HP DV9702ea internal mic"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by sijo2000 on 2008-04-10
I am currently fighting a war against a new HP DV9702ea laptop in an attempt to get it to run Ubuntu. Pleased to say that the Hardy beta has been an almost out of the box sucess. Only two major problems with the default install, wifi card and microphone.

After a lot of reading on these forums the wifi problem was solved by installing a patched version of the madwifi driver ([http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679), although i had to downgrade to 32 bit Ubuntu). So only the battle of the internal mic remains before the war is won and Ubuntu is crowned the glorious victor.

This seems to be a common problem on the forums but none of the solutions have worked for me. So far i have tried all the settings in the volume control, installing the Hardy backports module, building the latest alsa driver from source (with and without the hda_intel configuration oftion).

The DV9702ea has an nVidia MC65 chipset with Conexant CX20561 (Hermosa) chip and I am running a fully up to date Ubuntu 8.10 beta 4 32 bit. The output from alsa-info.sh can be found here ([http://pastebin.ca/978960](http://pastebin.ca/978960)). Audio outputs are working great, including speaker mute when headphones are attached.   

As far as I can tell there is no way to enable the internal microphone. The volume control (all options displayed) for the alsa mixer device shows three mics (Internal, Docking and external) under the playback tab, only a Digital device under the recoding tab, and only one IEC985 under the switches tab. Some other posts have talked about the digital recording slider setting recording volume while the source is selected on the switches tab, this seems not to be the case here.

With the digital recording slider up to max I am able to record a faint hiss in sound recorder and skype test calls but no amount of shouting into the mic (don't know what my neighbors think) results in any recognizable sound.

Has anyone got any ideas how i might go about debugging this problem? This is as much a learning exercise for me as it is about getting the mic to work so I'm open to any suggestions. I'd love to get it working though since I'm longing for an early night and fiddling with this problem has managed to keep me up to at least 3 every night this week, would be best to get it working before my girlfriend organizes an Ubuntu intervention!

Thanks for your help

Simon

---

### Post by sijo2000 on 2008-04-13
I've now had a chance to test out the laptop with a USB Logitech Quickcam with built in mic and this works correctly.

The Quickcam mic is detected and appears as a usb device in volume control with the expected recording tab to adjust capture volume and AGC switch .

This does seem to suggest that the mixer settings and general alsa installation are ok but there is something about the structure of the audio hardware in this laptop that prevents the mic being properly detected (it defiantly works under windows).

Anyone any ideas how to go about debugging this?

---

### Post by ivanmladek on 2008-04-14
I have the exact same problem on my DV6000z with Linux ivanmladek-laptop 2.6.24-14-generic #1 SMP Thu Apr 3 04:16:51 UTC 2008 x86_64 GNU/Linux and the output of alsa-info.sh on [http://pastebin.ca/985059](http://pastebin.ca/985059). I have run out of possibilities, have tried almost everything. Anybody can help?

---

### Post by link141 on 2008-04-15
First off, I'm using 64-bit kubuntu on a Compaq Presario F756NR with the same audio chipset as you.  I had to recompile ALSA to get the headphone jack sense working and the mics listed.  In KMix, it lists the same three mics as you in both the playback and recording tabs, but the only one I can record from is the external microphone jack.  In alsamixer, it looks similar to KMix, but I can't select the recording source using my spacebar as I can on my desktop.  You're supposed to be able to select the appropriate source and get it to say "capture" underneath it.  

I was able to get the microphone working once on a live-cd somehow, but I can't remember what I did.

On a side note, I was able to get my Atheros AR5007eg wireless card working well on my 64-bit system using ndiswrapper.   If you decide you want to move back to a 64-bit system sijo2000, I can help you get you card working.

Hope this helps,
link141

---

### Post by dave333 on 2008-04-15
Hey link141 - would you be able to give me a hand with getting the wifi up and running? Vista is doing my head in - it took 20 minutes of "preparing my pc" and installing useless programs before I could even USE the laptop!

I've downloaded the patch and drivers from the website, but i'm guessin I can just copy certain files out of my windows system folder for ndiswrapper?

Cheers,
Dave

---

### Post by link141 on 2008-04-16
> **dave333 said:**
> Hey link141 - would you be able to give me a hand with getting the wifi up and running? Vista is doing my head in - it took 20 minutes of "preparing my pc" and installing useless programs before I could even USE the laptop!

I've downloaded the patch and drivers from the website, but i'm guessin I can just copy certain files out of my windows system folder for ndiswrapper?

Cheers,
Dave

Sure, I can help.  Just make a new thread with all the specs of your wireless card, and send me a Private Message with a link (or make a new post).

<anti-microsoft>
Yeah, Vista is a pig.  It took about 20 minutes to configure itself out of the box, and about an hour to update itself.  When I burned my rescue CDs, it took about 15 GB of DVDs.  Then I had to go through and delete the crapware that HP so kindly gave me.  The Windows Vista rating for this laptop is only 2.5 and it's a pretty powerful machine.  Vista can't even keep up with me dragging a window.  On Kubuntu, I can run compiz at almost maximum settings without it even slowing down.
</anti-microsoft>

---

### Post by dave333 on 2008-04-16
Thanks for the help - I'm using a new HP DV9702ea

Vista reports it as having a AR5007 wifi adapter, but after runing **lspci** on Ubuntu it is shown as AR5006EG

I've noticed when booting, this message is displayed:
```
wifi%%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
```

After doing a bit of Googling for a working Windows driver to use with ndiswrapper, I found with the files net5211.inf / .sys.

I installed these with ndiswrapper and after doing **ndiswrapper -l** it came back with the following:

```
net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)
```

Then, blindly following some instructions on the net, I then did:
```
sudo depmod -a
``` 
and 
```
sudo modprobe ndiswrapper
```

Then I tried  **iwconfig** to see if the wifi card was working, but no luck. Even after restarting networking. 

I'm running off of the Gutsy LiveCD at the moment (so I can't reboot!) as I want to completely wipe Vista off the laptop - but I can't do that until I can be sure I can get Wifi working!

Really appreciate any advice!

---

### Post by link141 on 2008-04-16
[noparse]Before you follow these instructions, boot into Vista and open a command prompt.  Then type "ipconfig /all" and copy the information for your wireless card to a text file.  You can also run "ipconfig /all > C:\Users\USERNAME\Desktop\wireless-information.txt" (where USERNAME is your Windows username).  Make sure you can access this file from the live-cd by either putting it on a flash drive, or reading it from your hard-drive.  The main thing your concerned about in this file is where it says "Physical Address" under the heading for your Wireless card.  This is your mac address.

Our card is really and Atheros AR5007, but Ubuntu incorrectly lists it as an Atheros AR5006.  There is a really usefull howto for getting it to work on [/noparse] [this page](http://ubuntuforums.org/showthread.php?t=512828).  [noparse]It guides you through compiling the latest NDiswrapper (the Ubuntu one doesn't work correctly), and installing the driver.  I recommend that you follow that first, and then try some of my tips if it doesn't work.

Here's some things you might find useful:

1. First, you have unload the Atheros Hal.  To do this, open a terminal and input "sudo modprobe -r ath_pci".  

2. When you get to the rebooting step in the howto, you should be able to just restart networking.

3. After following the Howto and restarting the networking system, run "ifconfig -a" in a terminal and check your mac address (listed as HWaddr under Wlan0).  If it's all 0s, then you'll be able to see networks, but not connect to them.  To fix this, I had to comment out the "auto wlan0" line in the file /etc/network/interfaces and add the line "pre-up /sbin/ifconfig wlan0 hw ether xx:xx:xx:xx:xx:xx" to the bottom of the file (where xx:xx:xx:xx:xx:xx was my mac address).  Make sure you use ":" instead of "-" to separate the numbers.  After that I restarted networking and was able to connect to my routers.  It took me about a month to realize that my mac address was wrong, and that I had to change it.

Post any problems you run into, and I'll see if I can help.  We really should make a new thread, as this might be considered hi-jacking someone elses thread.

Hope this helps[/noparse]

---

### Post by dave333 on 2008-04-20
Wicked - worked a treat! Many thanks!

---

### Post by Vegetarianrage on 2008-05-04
> **link141 said:**
> First off, I'm using 64-bit kubuntu on a Compaq Presario F756NR with the same audio chipset as you.  I had to recompile ALSA to get the headphone jack sense working and the mics listed.  In KMix, it lists the same three mics as you in both the playback and recording tabs, but the only one I can record from is the external microphone jack.  In alsamixer, it looks similar to KMix, but I can't select the recording source using my spacebar as I can on my desktop.  You're supposed to be able to select the appropriate source and get it to say "capture" underneath it.  




Does this mean your jack sensing now works and that you can record using the internal mic? This is my last big issue to fix. What exactly did you do?

---

### Post by cespinal on 2008-05-06
> **Vegetarianrage said:**
> Does this mean your jack sensing now works and that you can record using the internal mic? This is my last big issue to fix. What exactly did you do?

I guess I am stuck in the same place as you!! how frustrating!!  I am not able to enable capture using the spacebar on alsamixer... please help me on this

---

### Post by ravl on 2008-06-13
I installed Kubuntu 8.04 on my HP Pavillion dv6810, and pretty much everything worked right out of the box, including Quickplay buttons and IR remote control.
The internal mic is another story though. I have the same problems mentioned above, with the Conexant Hermosa chip on an Nvidia card. No tutorial I've found has worked.
I hope someone solves this soon.

---

### Post by freakwillie on 2008-06-14
I'm facing the same microphone issues on a dv6768se with a CX20561 Hermosa sound card. 

One possible solution is to upgrade the ALSA drivers to the latest version on their repositories. I'm trying to do this for a long time but haven't succeeded yet. If any of you get to do that post the results here.

---

### Post by Vegetarianrage on 2008-06-14
I'm already using the latest drivers and it didn't fix anything at all. May I direct everyone's attention to this other thread. 

[http://ubuntuforums.org/showthread.php?t=784597](http://ubuntuforums.org/showthread.php?t=784597)

It seems to me that ALSA is not detecting our cards correctly, which of course could be the root of all of the problems. Does anyone know how to force it?:twisted:

---

### Post by ravl on 2008-06-18
I just installed the 2.6.24-29 kernel, and now alsamixer shows 3 mics: Docking, External, and Internal.
Internal was at 0 volume, I turned it up and Audacity now shows red bars on the mic monitors. But still, no sound is recorded.

maybe there is some progress...

---

### Post by freakwillie on 2008-06-20
I just upgraded to the latest stable kernel (2.6.25.7) and the latest alsa version (1.0.7rc2) and the internal mic still isn't working. :confused::(:mad:

---

### Post by cespinal on 2008-06-20
Still in the same boat... I gave up to this long time ago. I think I willjust waint until ALSA builds new drivers for this soundcards.

---

