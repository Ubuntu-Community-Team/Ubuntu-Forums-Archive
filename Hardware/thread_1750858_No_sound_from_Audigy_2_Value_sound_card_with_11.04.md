---
title: "No sound from Audigy 2 Value sound card with 11.04"
date: 2011-05-05
forum: Hardware
---

### Post by TetraElement on 2011-05-05
Hello all,

I am COMPLETELY green to Ubuntu and Linux in general. This is my very first install, and it definitely has not been smooth, but I am greatly enjoying the experience regardless. My problems have stemmed mostly from proprietary driver issues, but I've fixed everything except my sound issue. (though I'm sure you'll see lots of me and questions in the next few weeks as I attempt to run WoW on this old box)

I've checked a great many support posts over the web in the past two days, and none of them have quite nailed the fix, though I've gotten some ideas on where to look. I believe my problem may be very simple, so here's what I know!

Upon opening a terminal and asking for information on my cards, I this is what what was spit out

```
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
card 1: Audigy2 [SB Audigy 2 Value [SB0400]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
card 1: Audigy2 [SB Audigy 2 Value [SB0400]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
card 1: Audigy2 [SB Audigy 2 Value [SB0400]], device 3: emu10k1 [Multichannel Playback]
```

card 0 actually seems to be referring to my video card. So... my layman's view of things suggests changing this order would perhaps fix my problem. How can I do that? Alternatively, if this would not help me, can anyone here suggest something I can do to fix my problem? Very simply, I get no sound. At all. The only options available to me are "Internal Audio" and my ATI card in the sound preferences. Neither work. 

Thank you in advance!

---

### Post by TetraElement on 2011-05-06
Polite Bump for "OMG I can't hear anything!" 

Can anyone help me out?

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

### Post by TetraElement on 2011-05-06
Hi lidex,

Thank you for the reply. The following is the link for the output:

[http://www.alsa-project.org/db/?f=bb2bfe0602b67ebd6fc97ec97c70e1e253824c86](http://www.alsa-project.org/db/?f=bb2bfe0602b67ebd6fc97ec97c70e1e253824c86)

---

### Post by lidex on 2011-05-06
OK. Try this first to set audigy as default device:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Add these lines at the bottom:
```
alias snd-card-0 snd-emu10k1
alias sound-slot-0 emu10k1
alias snd-card-1 snd-hda-intel
alias sound-slot-1 snd-hda-intel
```
Save. Close. Reboot.

> Audigy
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind. ~markbuntu


---

### Post by TetraElement on 2011-05-06
No good, apparently. Sometimes I can hear faint noise behind a mask of white noise, lots of static. That is, however, the extent of my sound. I am open to any other suggestions, because I am so far out of my depth I need water wings. (very willing to learn, though! So throw anything you like at me, but you might have to speak slowly.)

---

### Post by lidex on 2011-05-06
Try toggling the checkbox in gnome-alsamixer. I have seen it work either off or on based on configuration.

---

### Post by TetraElement on 2011-05-07
well, the quality of the distortion changed slightly! I should note that I am using Unity as opposed to Gnome. Does this make a difference? Sorry, I'm very new at this!

---

### Post by lidex on 2011-05-08
Not that I'm aware of. Seems to be a regression on natty with this card. You should file a ticket on launchpad. Start with this:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by IcemanSR on 2011-05-08
oh for the love of god..
it is so easy but no one says it :S
everything was working by default for me after making Audigy to be default ..all left to be done is to switch analog/digital..BUT i could not find the button/command to do it..
AND it was M..
---
You will have to open the terminal and enter &#8220;alsamixer&#8221;. Use the right  arrow key to select the channel &#8220;Audigy Analog/Digital Output Jack&#8221;.  Press &#8220;M&#8221; to turn it on/off.
---

if it was just showed somewhere..

---

### Post by TetraElement on 2011-05-08
Hah! Yeah, I just got it myself. I was about to type out that I basically had no idea what I did, but I fixed it! In my case, running alsamixer from the Terminal and selecting Audigy2 from the menu as my preference for a soundcard worked. Attempting to do this in other ways previously did not work, but apparently that WILL fix it. Sound is running beautifully now. 

For anyone that comes across this in the future, please note that a RESTART is absolutely essential. 

Thank you for helping, lidex!

---

### Post by lidex on 2011-05-08
Not a problem. I seem to have spoken too soon on a regression issue. 
Please mark the thread solved using 'Thread Tools' up top so others will see the solution. 
I post here a link to info from someone who actually knows something about this card:
[http://ubuntuforums.org/showpost.php?p=10784896&postcount=38](http://ubuntuforums.org/showpost.php?p=10784896&postcount=38)

Thanks to mc4man

---

### Post by goras on 2011-06-02
This seems like a good place to ask for help with my problem:

I have a SB Audigy 2 Value card (SB0400), and I hear a horrible clicking sound each time I try to passthrough AC3 via the SPDIF.

I tried all sort of things, my guess is that ac3 passthrough via spdiff for this card is broken in alsa since it's probably different from the other more common Audigy cards.

I can post my configs and aplay outputs would that help?

Thanks

---

