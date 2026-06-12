---
title: "Sound Problem on 11.04 (Dell Studio XPS)"
date: 2011-05-03
forum: Hardware
---

### Post by cipher_neo on 2011-05-03
Hi guys,

I have been dabbling with a lack of sound issue for the last few days.

I recently installed ubuntu 11.04 on my dell studio XPS PP35L.

The result of lspci -v shows my soundcard:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 0272
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at fc400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


The problem is that there is no sound coming from the speakers, but the headphone jacks are working fine.

I have checked that all channels have been unmuted in alsamixer, and have played around with different settings in the audio preferences dialog. 

I do know that some people have solved the problem by adding an "options" line to alsa-base.config for their particular sound card. I have tried

options snd-hda-intel model=dell-m6
options snd-hda-intel model=dell
options snd-hda-intel model=dell-bios

but to no avail.

Has anybody got any insights as to how to fix this issue?

thanks,

Lee

---

### Post by jepperstone on 2011-05-04
I may have a similar problem. Here's the output of my lspci -v:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 022e
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f6ffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

any ideas? what's the deal with the "Capabilities: <access denied>" line? I'm trying to get sound to play with my Logitech USB headset.

---

### Post by cipher_neo on 2011-05-04
Still no budge on this problem yet...

---

### Post by cipher_neo on 2011-05-06
any gurus out there? I am at the end of my tether trying to fix this problem.

---

### Post by cipher_neo on 2011-05-06
sorry jepperstone, I have no idea what the "Capabilities: <access denied>" line means. Still waiting for somebody to help out. What are you running ubuntu on?

---

### Post by lidex on 2011-05-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by cipher_neo on 2011-05-07
Thanks for the reply lidex.

Here is the upload: 

[http://www.alsa-project.org/db/?f=de7b2abb873fef85b5852044fca48afbd6daeba3](http://www.alsa-project.org/db/?f=de7b2abb873fef85b5852044fca48afbd6daeba3)

---

### Post by lidex on 2011-05-08
How about dell-eq ? Quickly test:
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=dell-eq" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by cipher_neo on 2011-05-09
thanks, but that option does not seem to do the job. 

I have inserted the line into the alsa config file.

The speaker now makes a crackling sound when it is attempting to play sound?

any other ideas?

thanks for the help

---

### Post by lidex on 2011-05-10
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by cipher_neo on 2011-05-11
I am pretty sure I have followed your guidelines exactly, but I still here no sound. 
How did you arrive at dell-eq as being the right option?

This sound problem really is getting on my nerves at this stage!

---

### Post by lidex on 2011-05-11
What profile is selected in 'Sound Preferences' on the hardware tab? Which sound card is selected? Did you try toggling the 'Connector' on the output tab? Can you post an new alsa-info with the dell-eq model quirk please?

---

### Post by cipher_neo on 2011-05-11
I have tried both "Analog Stereo Output" and "Analog Stereo Duplex" in the profile selection drop down. 

I have tried these two settings with every combination of "Connector" in the output tab. The options in "Connector" are: "Analog Output", "Analog Speakers" and "Analog Headphones".

I have ran that command again, while having the "dell-eq" quirk set, and the following is the output:

[http://www.alsa-project.org/db/?f=4e1519178a7ecdaa814deaaaca5d3327bc0fa448](http://www.alsa-project.org/db/?f=4e1519178a7ecdaa814deaaaca5d3327bc0fa448)

---

### Post by lidex on 2011-05-11
> **cipher_neo said:**
> I have tried both "Analog Stereo Output" and "Analog Stereo Duplex" in the profile selection drop down. 

I have tried these two settings with every combination of "Connector" in the output tab. The options in "Connector" are: "Analog Output", "Analog Speakers" and "Analog Headphones".

I have ran that command again, while having the "dell-eq" quirk set, and the following is the output:

[http://www.alsa-project.org/db/?f=4e1519178a7ecdaa814deaaaca5d3327bc0fa448](http://www.alsa-project.org/db/?f=4e1519178a7ecdaa814deaaaca5d3327bc0fa448)

Gotcha. I have one more to try. Remove that line from alsa-base.conf and replace with this:
```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m6 enable_msi=1
```
Reboot after saving.

---

### Post by cipher_neo on 2011-05-11
Ok, tried the above, and then had a play around with the "Profile" and "Connector" settings after a reboot. Also checked alsamixer to make sure no channels were muted, but still no joy.

Here is another version of my config after adding those 3 configuration lines and deleting the dell-eq one:

[http://www.alsa-project.org/db/?f=c1cd776ef7331dffbccbce254d781d15d9e10e47](http://www.alsa-project.org/db/?f=c1cd776ef7331dffbccbce254d781d15d9e10e47)

---

### Post by lidex on 2011-05-11
You don't think the 'Speaker'0 level might have anything to do with it:
```
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-48.00dB] [on]
  Front Right: Playback 0 [0%] [-48.00dB] [on]
```

---

### Post by cipher_neo on 2011-05-11
I have turned up the volume with alsamixer and ran the command again:

[http://www.alsa-project.org/db/?f=a643502efe454e5e5756abc4b80736c07be575f9](http://www.alsa-project.org/db/?f=a643502efe454e5e5756abc4b80736c07be575f9)

I must have ran that last command before going into alsamixer

---

### Post by lidex on 2011-05-11
I can't find anything wrong with your alsa-info. Your levels are not muted, no error messages. Not a lot of audio problems associated with this machine. Latest ubuntu release alsa. 

Try the alsa-upgrade script from the link in my sig after removing those edits to alsa-base.conf. I don't think I can help you any further than that.

---

### Post by cipher_neo on 2011-05-12
I am going to give that a go now. 

Just an FYI, but the volume icon has been removed from the right top hand bar where the time is... could this mean anything?

---

### Post by cipher_neo on 2011-05-12
ok, so I tried the alsa upgrade script and still no joy :(

The speaker still makes a crackling sound when attempting to play audio. 

I suppose I will just have to use headphones.

I appreciate all the help. Thank you

---

### Post by lidex on 2011-05-12
> **cipher_neo said:**
> I am going to give that a go now. 

Just an FYI, but the volume icon has been removed from the right top hand bar where the time is... could this mean anything?
What happens when you right-click on the panel, select add to, indicator applet?
You were changing profiles via the preferences menu then?

---

### Post by Seahades on 2011-05-12
Thx, last post solved the problem for me! 
I also have options snd-hda-intel model=dell-m6 in alsa options.

---

### Post by cipher_neo on 2011-05-13
> **lidex said:**
> What happens when you right-click on the panel, select add to, indicator applet?

I cannot right click the panel at the top right of my screen, it doesn't respond to right clicks.


> **lidex said:**
> You were changing profiles via the preferences menu then?

Yes, I went to right top corner panel and clicked the power button, then system settings, then sound, and was changing profiles in there.

---

### Post by lidex on 2011-05-13
Ah yes, the unity panel.
Make sure this is installed:
```
sudo aptitude install indicator-sound
```
Logout/in

---

### Post by cipher_neo on 2011-05-14
Ok, I can see the sound icon now in the top right. That's all well and good, but I still have no sound :(

---

### Post by cipher_neo on 2011-07-04
I still have not solved this problem.

There is a line in dmesg however which says:

hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj

Would this be a hint into what is going on?

---

### Post by HorseHero on 2011-07-04
Dear Ciper_neo,
 
Try this: in the top right corner button icon => system settings => Sound => in tabs select one of the tap where select the desk top speakers in place of Hands free.
 
I think this will solve your proble.
 
regards
HorseHero

---

### Post by cipher_neo on 2011-07-04
Im not sure I follow what you mean?

---

### Post by nsznaj on 2011-11-07
hi all

i've been trying to troubleshoot this same problem and can't find any solution...

has someone solved this?

my audio device is

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

and my laptop is Dell Inspiron 1545 

On windows everything works fine, the problem on Ubuntu 11.04 was after plugging the headphones... then everything changed...


Help would be appreciated!

Cheers
Nahuel.

---

### Post by Superdarion on 2011-11-08
Hi guys.

I have a dell xps 16 laptop and I had issues with the audio.

After trying everything on these forums (everything I could find, at least), I found this wonderful site:

[http://www.linlap.com/wiki/dell+studio+xps+16]("http://www.linlap.com/wiki/dell+studio+xps+16")

It gives you a few workarounds for the xps 16 laptop and linux. In particular, in the "audio" part there is a line to add to the alsa-base.conf file, which is as follows:

options snd-hda-intel model=dell-m6 enable_msi=1

This worked wonders for me: The speakers work when nothing plugged to the jacks; if I plug speakers or headphones, the built-in speakers mute and I get sound from the external speakers or headphones. Hope it helps.

Note: I had already tried the dell-m6 part to no avail. Seems the enable_msi did the trick.

---

### Post by nsznaj on 2011-11-14
> **Superdarion said:**
> Hi guys.

I have a dell xps 16 laptop and I had issues with the audio.

After trying everything on these forums (everything I could find, at least), I found this wonderful site:

[http://www.linlap.com/wiki/dell+studio+xps+16](http://www.linlap.com/wiki/dell+studio+xps+16)

It gives you a few workarounds for the xps 16 laptop and linux. In particular, in the "audio" part there is a line to add to the alsa-base.conf file, which is as follows:

options snd-hda-intel model=dell-m6 enable_msi=1

This worked wonders for me: The speakers work when nothing plugged to the jacks; if I plug speakers or headphones, the built-in speakers mute and I get sound from the external speakers or headphones. Hope it helps.

Note: I had already tried the dell-m6 part to no avail. Seems the enable_msi did the trick.



Hi !
I wonder how could I write that line for my Dell Inspiron 1545....
Shall I put "model=dell-m6 enable_msi=1" just like you did?



Cheers,
Nahuel

---

