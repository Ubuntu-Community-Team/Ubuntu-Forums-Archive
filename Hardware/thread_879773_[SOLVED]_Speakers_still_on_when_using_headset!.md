---
title: "[SOLVED] Speakers still on when using headset!"
date: 2008-08-04
forum: Hardware
---

### Post by Lusse on 2008-08-04
Hi everyone,

I  have an HP COMPAQ nx6110 with Ubuntu installed (:)). It works quite well but when I plug in my headset(analog not usb) the speakers don't turn themself off(:() so it is sounding from both speakers and headset... I really need help with this since I use this computer to listen to music on the train (which I travel with 2 hours every day) and I don't think that the other passengers wants to hear my computer... Pleas help!

regards
//Linus

EDIT: I am using Ubuntu 8.04 LTS Desktop

---

### Post by kernelhaxor on 2008-08-04
I had the same problem on my HP Pavilion laptop .. havent tried yet to find a solution .. I will update this thread when I find a solution ..

---

### Post by Lusse on 2008-08-04
Thanks mate, hopefully we will find a solution. If I find one then I will (of course) post it here for you to read...

---

### Post by phidia on 2008-08-04
Sorry to be a wet blanket but with the pavilion & maybe the compaq is similar(?) it's seems to be a struggle to get working correctly. I did find a post by someone who installed the latest alsa from source and got jack sense  enabled.
With opensuse 11 it works without any additional configuration.
Still I'll watch this thread and if you find an easy way to get the mains to mute with earphoes plugged in I'll be happy to hear it.
I didn't want to hand compile alsa because it would be just another thing to run after a kernel upgrade. I'm using x86_64 btw.

---

### Post by stchman on 2008-08-04
> **Lusse said:**
> Hi everyone,

I  have an HP COMPAQ nx6110 with Ubuntu installed (:)). It works quite well but when I plug in my headset(analog not usb) the speakers don't turn themself off(:() so it is sounding from both speakers and headset... I really need help with this since I use this computer to listen to music on the train (which I travel with 2 hours every day) and I don't think that the other passengers wants to hear my computer... Pleas help!

regards
//Linus

What version of Ubuntu you using?  Also give us an lspci listing in this thread.

I had a similar problem with my Toshiba laptop and Hardy fixed it.

---

### Post by Lusse on 2008-08-04
8.04 LTS Desktop

---

### Post by Lusse on 2008-08-04
I SOLVED IT!!!

Mini how to:
1. Dbl-click the speaker in the right hand corner(Volume control).
2. Click the second tab("Växlar" in swedish version, something like "switches" might be it).
3. Check "Headphone Jack Sense".
4. Done!

Quick and Easy!

I hope it solves your problems :) Happy Ubuntuing!

---

### Post by Lusse on 2008-08-04
Btw if anyone can have use of this (lspci):
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

---

### Post by phidia on 2008-08-04
Yeah that doesn't work for me but I'm sure I don't have the intel audio.
Good that you got it working.

---

### Post by Lusse on 2008-08-04
> **phidia said:**
> Yeah that doesn't work for me but I'm sure I don't have the intel audio.
Good that you got it working.

Sorry to hear that...
Thanks.

Isn't this feature suppose to be on by default?

---

### Post by phidia on 2008-08-04
I don't think it is in Ubuntu but I can really only defer to the Ubuntu [sound wiki]("https://help.ubuntu.com/community/Sound"). I believe it requires set up from that guide.

---

### Post by Lusse on 2008-08-04
Is "JACK" and "Jack Sense" the same thing?

---

### Post by boppp on 2008-08-04
I got the same problem with the ear-phones and don't have the option in my preferences or anything to turn that on. (it did work in windows xp, some wile ago when i used that)

Is there a way to turn the option on or another place to look for it?
> 
bob@bob-laptop:~$ lspci | grep "Audio"
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


> 
bob@bob-laptop:~$ uname -a
Linux bob-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux


---

### Post by Lusse on 2008-08-04
> **boppp said:**
> I got the same problem with the ear-phones and don't have the option in my preferences or anything to turn that on. (it did work in windows xp, some wile ago when i used that)

Is there a way to turn the option on or another place to look for it?

Yes there are :)

1. Open volume-controll (dbl-clcik speaker in upper right corner)
2. Click the second menu ("Redigera" on swedish version, maybe "Edit")
3. Click the only option ("Instälningar" on swe ver, maybe "Settings" or "preferences")
4. Scroll until you find "Headphone Jack Sense", check it!
5. Now it will appear under the second tab(maybe "Switches").
6. Done, enjoy your new sound-thru-headphone-computer!

//Linus

---

### Post by boppp on 2008-08-04
> **Lusse said:**
> Yes there are :)

1. Open volume-controll (dbl-clcik speaker in upper right corner)
2. Click the second menu ("Redigera" on swedish version, maybe "Edit")
3. Click the only option ("Instälningar" on swe ver, maybe "Settings" or "preferences")
4. Scroll until you find "Headphone Jack Sense", check it!
5. Now it will appear under the second tab(maybe "Switches").
6. Done, enjoy your new sound-thru-headphone-computer!

//Linus

Yeah i tried that, but the problem is that i dont have in "switches" or "Headphone Jack Sense" option. Only the option to switch on the visibility to turn on "master". Mayb my sound card does not have this option enabled in the Salsa program?

[IMG]http://www.vilog.nl/Untitled.jpg[/IMG]

> 
bob@bob-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC861 Digital [ALC861 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by Lusse on 2008-08-04
Seems like card 0 device 0 is the only option... I'm sorry but i don't think that I can help you anymore :( I'm not that good at Linux as I think ;)

---

### Post by Lusse on 2008-08-06
On some machines it seems to be named "Headphone as line out", maybe not the same but this option should work too...

---

### Post by sporkubus on 2008-08-10
> **Lusse said:**
> I SOLVED IT!!!

Mini how to:
1. Dbl-click the speaker in the right hand corner(Volume control).
2. Click the second tab("Växlar" in swedish version, something like "switches" might be it).
3. Check "Headphone Jack Sense".
4. Done!

Quick and Easy!

I hope it solves your problems :) Happy Ubuntuing!
Lusse: awesome man, I've been trying to find a way to do this for a long time. Thanks!!

---

### Post by mediajunkie on 2008-08-13
HI, 

It has been a pretty big struggle to get the soundcard working on my Acer Aspire 8920G. Nevertheless, I finally got it working except that the speakers will still play when using headset. And this no matter what settings are used in the volume control panel. I"m using the HDA (ALSA mixer) and have tried every possible combination with no result on this issue. I guess I can confirm this issue and join the club. It is not a party blocker but very annoying when using skype-out.

When booting from second hard drive (win vista / xp) it seems to work, well the audio does except everything else LOL 

any ideas, hints or might-be solutions welcome. 

thanks, 
Media Junkie.

---

### Post by erani on 2008-11-11
No solution for me :(
I found in volume control in switches the "Headphone" checkbox, enabled it and no effect.
If checkbox is not checked then in my headset no sound, if checked the sound is hearing in headset and from front boxes.

Hardware:
Asus x50n, audio card is Intel one.
Ubuntu 8.10

---

### Post by gustavo321 on 2008-11-23
Hey guys,

I am using a laptop, asus x50n, and I have the same problem, when I connect the headphones, speakers still on.
I tryied all the recommendations, but I don't have this options...
:(
If anyone have ideia how to solve this, that will be great.
Gustavo

---

