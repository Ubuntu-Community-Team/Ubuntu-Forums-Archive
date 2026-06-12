---
title: "DV8000t and a few questions/help needed"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by jka/v on 2006-06-30
I have a dv8000t HP notebook, 2ghz intel core duo, 2gb 533mhz ram, 256mb Nvidia go7400, 80gb 5400rpm sata drive, intel 3945a/b/g and bluetooth.  

Installed Ubuntu 6.06, updated it, installed 686smp kernel for the core duo, installed nvidia-glx for the video, and modified my network/interfaces file for wpa connection to my wireless.  Works incredibly well!

I have a few questions though:

1.  Audio output is very low, even at max volume.  Dual booted, the xp side is really great for audio...?

2.  I have a few pci errors that pop up when ubuntu loads.  And my sd card read doesn't work.  How do I diagnose these and fix them?  (says cannot allocate memory in region 7, region 8 etc)..

3.  when I run lspci, I have a few items that are listed as unknown, but in ubuntu, they are working.  Is this something to worry about? (here is my lspci output:  
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d8 (rev a1)
0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:08:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:08:06.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:08:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:08:06.3 0805: Texas Instruments: Unknown device 803c
0000:08:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 01)


Thanks for any and all input!

---

### Post by jka/v on 2006-07-11
Anyone have any input on the questions I asked?  Help would be greatly appreciated.

Thanks

---

### Post by Amaranth on 2006-07-31
1. No known fix, very annoying.
2. You can ignore the errors, it's usplash poking around. The SD card reader supposedly works in edgy.
3. sudo update-pciids

---

### Post by Amaranth on 2006-07-31
2. The SD card reader does not currently work in edgy. This might change, if a driver actually exists for it.

---

### Post by a_hippie on 2006-08-06
I have a similar system: hp pavilion dv5000 series.  Memory reader doesn't work, nor does the unknown WIFI.  Still looking for info on what the WIFI is.  Some think it's broadcom, I really don't know at this point.

Good luck.  /me digs further into google

---

### Post by monkster on 2006-08-16
I have an HP dv5000t, similar to the dv8000t. With Dapper, Wifi/Bluetooth worked out of the box.

However, the Texas Instruments SD Card Reader does not work, lspci:

```
0000:08:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:08:06.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:08:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:08:06.3 0805: Texas Instruments: Unknown device 803c

```

I understand that work is being done in the kernel to get this device working. [http://www.ubuntuforums.org/showthread.php?t=48551](http://www.ubuntuforums.org/showthread.php?t=48551)

Most disappointing is that the audio is very soft as described in this thread by the owner of the dv8000t. I have the exact same problem. Is there any hope that could improve?

Still, very happy with using Ubuntu on this laptop. If I could get the audio problem fixed, I'd be happier. :)

---

### Post by monkster on 2006-08-16
I should have run update-pciids first. Now the interesting part of lspci looks like this:
```
0000:08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0000:08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0000:08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0000:08:06.3 0805: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

Still can't get it to work, though. Again, I am more concerned about the audio not being able to be turned up fully. Can this be fixed, does anyone know?

---

### Post by brk3 on 2006-08-16
Hi, sorry I just posted a topic about the sound issue in the sound/video section, didnt see this topic!

At least theres some other people out there with the same problem, please tell me theres a fix. I dont like the sound of the:

1. No known fix, very annoying.

How do you know this..?

---

### Post by bryhawks on 2006-08-16
Hey, here is the fix for your broadcom... I am using a DV8000 and this post will get you up and running wirelessly very quickly. [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom)

---

### Post by Amaranth on 2006-08-17
> **brk3 said:**
> Hi, sorry I just posted a topic about the sound issue in the sound/video section, didnt see this topic!

At least theres some other people out there with the same problem, please tell me theres a fix. I dont like the sound of the:

1. No known fix, very annoying.

How do you know this..?
I know there is no fix because the guy that does all the audio work in the Ubuntu kernel worked with me to try to fix it, we couldn't do it. Thus, no known fix.

---

### Post by monkster on 2006-08-17
> I know there is no fix because the guy that does all the audio work in the Ubuntu kernel worked with me to try to fix it, we couldn't do it. Thus, no known fix.
__________________
Travis Watkins

For the record, then, my dv5000t, which is similar to the dv8000t of this post is a great hp pavilion laptop, but under Ubuntu Linux 6.06, 1) the Texas Instruments 5-in-1 multimedia card reader does not work, 2) the microphone does not work (I just found out), and 3) the sound output is too low. I really appreciate all the great work people put into Ubuntu, but for the time being, for me it's like this: :-({|= 

It might be important to include this output from dmesg, which was also mentioned by the thread starter:

```
[17179570.680000] pnp: PnP ACPI: found 10 devices
[17179570.680000] PnPBIOS: Disabled by ACPI PNP
[17179570.680000] PCI: Using ACPI for IRQ routing
[17179570.680000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.680000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.680000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.680000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.680000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.680000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.680000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.680000] PCI: Cannot allocate resource region 0 of device 0000:06:00.0
[17179570.716000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.716000] PCI: Bridge: 0000:00:1c.0
```

This "cannot allocate resource" seems symptomatic. (?)

What about "pci=routeirq?" I entered that at the command line, but it did not seem to help. Maybe I am missing something here. Can someone help?

Finally, a [lame, perhaps] suggestion: you can fiddle with the preamp in xmms to boost the volume slightly. But there is distortion if you don't also turn down the pcm in gnome-volume-control.

---

### Post by Amaranth on 2006-08-17
I have all of those problems on my dv8000t as well. The dmesg log you posted has nothing to do with sound, as far as I can tell. It's just telling you it's using ACPI to handle interrupt requests. Everyone likely gets that message in their dmesg output.

---

### Post by brk3 on 2006-08-17
Well, thats a good enough answer for me. Really dissapointing though, looks like im screwed for linux until this gets fixed.
At least it doesnt stop you from using the system, but working without proper music just cant be done :(

I read somewhere that someone had no problem using usb earphones.. Does usb  sound not require a soundcard? Could this be a solution?

---

### Post by kantai on 2006-08-19
USB sound is a separate soundcard (and a separate ALSA device for that matter.)

My biggest concern though is the card reader. It'd be nice not to have to lug around a usb card reader :frown:

---

### Post by brk3 on 2006-08-20
I just ordered a cheap usb sound adapter, think it should be a handy solution :) Will post my results when it comes.
As for the card reader, I never really have the need for it, but I thought it was fairly well known that there are just no linux drivers for these at the moment? So its not really the laptops fault? Or are there some drivers in progress?

---

### Post by KrakensDen on 2006-08-20
I also have a dv8000t, and out of curiosity, has anyone gotten suspend-to-RAM working? I got hibernate to function (see [this thread]("http://ubuntuforums.org/showthread.php?t=201960&page=2")), although it kills my sound support afterwards.

---

### Post by brk3 on 2006-08-21
No my one suspends but the screen just stays black once it wakes up and I have to hit the power button. That said I havent messed around with it yet, people are meant to get good results with the 'suspend2' package but not sure how to set this up. The sound issue is more a priority for me. Though the suspend is very essential also..

---

### Post by proselyte on 2006-08-25
does an external sound card correct the sound problem?

---

### Post by jka/v on 2006-08-31
Finally got my DV8000t back from HP for repairs, of course, the keyboard still doesn't work right...

But I digress.

I'm now going to reload 6.06, and compile a new kernel, and then try some of the suggestions out there.  I got the wireless working (very well btw), so for me, just keyboard shortcuts, multimedia keys, card reader, and sound are my only issues.  Everything else works perfectly.

---

### Post by brk3 on 2006-09-01
Just to tell everyone that I got my usb sound adapter today and it works perfectly! :) I would suggest this as a very good and cheap(got mine for less than a tenner)solution while we're waiting for a fix for the soundcard.

jka/v, I noticed you didnt list hibernation as one of the things that doesnt work for you, if you could post how you got this to work I would be extremely grateful. Mine goes to sleep but wont when it wakes it just does nothing and stays at a black screen..

---

### Post by ese5 on 2006-09-02
For those of you dual-booting windows, here is another (awkward and annoying) workaround I've found:


1..  Boot linux
2..  Hibernate (has to be hibernate, just restarting won't work)
3..  Turn the computer back on and boot into windows
3..  Make sure all the levels are up
4..  Restart windows and choose linux when GRUB comes back up

Volume should be working now.   Pain in the fukkin cheekz, but works.

---

### Post by Amaranth on 2006-09-02
Too bad hibernate has never worked for me. :/

---

### Post by brk3 on 2006-09-06
Does anyone have any proper advice on how to get hibernate working? Im sure its possible..

---

### Post by last2kn0 on 2006-09-11
I had a similar occurance to what ese5 suggested.  The dv8000 has the set of media buttons on top which include volume up and down buttons as well as mute.  

While I was in windows, I had muted the sound using the media button and then I booted into linux.  I could not get my sound to work at this point.  The only solution was to reboot into windows, unmute the sound and then reboot into linux.

I'm not quite sure how it works but maybe this suggests that its not volume control software in linux (to an extent) but maybe that when in windows, the hardware is being controlled in someway rather than software to control volume?  That would explain why levels in windows would affect the levels in linux.

When I'm in windows, I usually keep the master volume pretty low and just control the softwares (ex: winamp) individual volume.

If all of this is true, then that would be why my linux volume is low.

---

### Post by Amaranth on 2006-09-11
My random thought on the matter was that the sound controller saves it's state somehow (battery, I guess) and Windows sets up the state correctly while Linux is missing something. When you hibernate the driver for the sound apparently doesn't do all the setup things it does on normal boot so the Windows state is preserved. Thus, your volume is loud like it was in Windows. Fun way to see this: Put the volume at 50% in Ubuntu, hibernate, turn the volume all the way up in Windows, resume Ubuntu, watch the sound come out full volume until you adjust it. (even though it should be 50%)

---

### Post by last2kn0 on 2006-09-11
So is there some way to implement a software solution for linux?  Oh and is this only a problem with the dv8000 and the associated sound cards?

---

### Post by gazedo on 2006-09-13
to get hibernate working install the hibernate package, atleast worked for me

---

### Post by last2kn0 on 2006-09-20
I e-mailed linuxant about the problem and they responded to it relatively quick. Its too bad I have no clue what they were talking about!! Here are the e-mails, maybe you guys understand and could test the solution!

I wrote:
> I have a HP dv8000 notebook computer with a Conexant HDaudio
softmodem.
> When under linux, the volume is very low. The maximum volume is much
> lower than it is while in windows. Is there any fix for this?

He responded with:

Hi,

I assume that you are talking about the digital progress sound. Please
try with the 'AT &F M3 L3' init. string to see if there is a
difference.

Regards,


Jonathan
Technical specialist / Linuxant
[www.linuxant.com](www.linuxant.com)
[email]support@linuxant.com[/email]

---

### Post by nrwilk on 2006-09-23
> **last2kn0 said:**
> I e-mailed linuxant about the problem and they responded to it relatively quick. Its too bad I have no clue what they were talking about!! Here are the e-mails, maybe you guys understand and could test the solution!

I wrote:
> I have a HP dv8000 notebook computer with a Conexant HDaudio
softmodem.
> When under linux, the volume is very low. The maximum volume is much
> lower than it is while in windows. Is there any fix for this?

He responded with:

Hi,

I assume that you are talking about the digital progress sound. Please
try with the 'AT &F M3 L3' init. string to see if there is a
difference.

Regards,


Jonathan
Technical specialist / Linuxant
[www.linuxant.com](www.linuxant.com)
[email]support@linuxant.com[/email]

I don't understand.  You think the sound problem stems from the modem?

I did a google search for 'init string' and almost every single lik I found had to do with modem init strings (except for one link to a Goa Trance producer called 'init string.'  He was actually pretty good!).

I'd like to know more about this.  Anyone know how to interpret the response that linuxant gave?

nrwilk

---

### Post by nrwilk on 2006-09-23
> **brk3 said:**
> Just to tell everyone that I got my usb sound adapter today and it works perfectly! :) I would suggest this as a very good and cheap(got mine for less than a tenner)solution while we're waiting for a fix for the soundcard.
May I ask where you got it, and what model you got?  I want to get one as well, to use until this is fixed.

nrwilk

---

### Post by A. J. Rimmer on 2006-09-23
Re: the response from Linuxant, yes, that is a modem init string.  Sounds as if they did not fully understand the question you were asking.

I am using a dv5000-series machine (Centrino Duo, Intel 3945 WiFi, etc.) which seems to share all the Ubuntu quirks with the dv8000.  I accidently got my microphone input to work recently.  I was in Windows and unmuted the microphone in the audio controls (the software panel that comes up when you double click the speaker in the system tray).  Then I restarte and booted into Ubuntu, and the mic input worked.  However, if I boot directly into Ubuntu after a full shutdown, it doesn't work again.

Despite the quirks, I'm enjoying Ubuntu on this laptop.  I don't listen to music on the computer, so the sound isn't that much of an issue.  I'm looking forward to the day when both Ubuntu and I  mature sufficiently that I can dump Windows entirely.  (We're both getting close, although I have a bit to go....)

---

### Post by iox on 2006-09-24
> Vernon: Hello Iox
Vernon: Welcome to HP Total Care for Pavilion Notebooks . My name is Vernon. How may I help you today?
Iox: Hello, Im having a problem with the linux audio support
Iox: The sound works but the volume is much lower than in windows
Vernon: I am sorry to tell you that this support is only for windows.
Vernon: HP do not support linux for its notebooks.
Iox: Well, I imagined that. Anyway, I would like to complain for that.
Vernon: Is there anything else I can assist you with today?
Vernon: We are working here according HP's policy.
Vernon: We are not authorzed to go beyond HP's policy.
Iox: Yes. Please tell anyone who cares that your lack of support is an offense and that I am going to buy a different laptop. Thank you for your time.
Vernon: Thank you for using HP Total Care and providing us an opportunity to serve you through Real-Time Chat.

I'm having the same problem with a dv2000. I was bored and decided to give a try to their support system. They are so nice...

---

### Post by A. J. Rimmer on 2006-09-24
"I'd like to know more about this. Anyone know how to interpret the response that linuxant gave?"

Strange -- when I woke up this morning, this popped into my mind again, and I realized my response last night was incomplete.

Not only is this a modem initialization string, but it is one that will set the volume on the modem speaker (so that you can hear the DTMF tones and the modem handshaking).  Has nothing to do with the output of the sound card when doing non-modem things, unfortunately.

A Google search for "modem AT commands" will provide more information for those who are curious.

---

### Post by last2kn0 on 2006-10-08
Well I do think I have brought enough noise to this subject to find some sort of solution, although I am not sure it takes care of mic and headphone problems yet.  

I submitted an ALSA bug report recently and I have had a linuxquestions.org post on this topic open for sometime.

It was suggested to use Pototskiy's patch on the ALSA bugreport page.  

This patch can be found here:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485)

Those who posted on my topic reported increased volume and more options after applying the post. They also said that kmix does not work properly with it but thats just a minor annoyance!

You can see the two threads down below.  The first is about how to apply the patch and the other is about the sound problem.

[http://www.linuxquestions.org/questions/showthread.php?p=2452647#post2452647](http://www.linuxquestions.org/questions/showthread.php?p=2452647#post2452647)
[http://www.linuxquestions.org/questions/showthread.php?t=473668](http://www.linuxquestions.org/questions/showthread.php?t=473668)

Good luck guys!  Let me know how it goes!

---

### Post by brk3 on 2006-11-17
Well just upgraded to edgy today in anticipation of finally hearing loud music from linux. sound is still crap, well done all

---

### Post by Amaranth on 2006-11-17
You can get loud sound by hibernating Ubuntu, booting Windows, and then resuming Ubuntu. If you want to get it fixed get the output of ```
cat /proc/asound/card0/codec#0
``` before hibernating and after resuming and filing a bug with this output.

---

### Post by brk3 on 2006-11-23
i still cant get hiberbate to work.. Why cant intel realease the info needed to get this card working i thought they were good players in the linux field seen as their wireless cards work well etc

---

### Post by KrakensDen on 2007-02-09
The audio issue is fixed in the latest ALSA release/on Feisty, if anyone still cares.

---

### Post by nrwilk on 2007-02-10
> **KrakensDen said:**
> The audio issue is fixed in the latest ALSA release/on Feisty, if anyone still cares.

It is?  YYYEEESSS!!!

Thanks for the tip! :grin: :grin: :grin:

---

### Post by Amaranth on 2007-02-10
Yep, after going back and forth with possible fixes we finally got a real working driver. Hell, the mute button even lights up now. :)

It helps when a kernel dev has the same hardware as you. :D

---

### Post by nrwilk on 2007-02-10
> **Amaranth said:**
> Yep, after going back and forth with possible fixes we finally got a real working driver. Hell, the mute button even lights up now. :)

It helps when a kernel dev has the same hardware as you. :D

Word, I bet.  Nice job, guys! :)

EDIT: What's this Kernel dev working on next?  It would be great if he was able to get suspend-to-ram to work for us HP laptop owners. :p :lol:

---

### Post by CaptSaltyJack on 2007-08-30
Windows XP finally died on my HP dv8000t.  I'm strongly considering putting Feisty on it.

Can anyone report how well Feisty works on the dv8000t?

---

### Post by Amaranth on 2007-08-30
Everything seems to work fine. Well, I haven't tested the bluetooth (it is detected) or the modem (doesn't seem to be). But the wireless, video, sound, suspend, etc all seem to work.

---

### Post by CaptSaltyJack on 2007-08-30
Great!  Looking forward to getting rid of Windows. :)

---

### Post by CaptSaltyJack on 2007-09-02
So, anyone know how to get MythTV working on the dv8000t using the HP Analog Tuner card and remote control??

---

