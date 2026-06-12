---
title: "No sound in Breezy, help please, need my sound!"
date: 2005-11-15
forum: General Help
---

### Post by Julian David Pitt on 2005-11-15
Since installing Breezy I have been totally unable to get any sound from my soundblaster live. I have been into Kmix and played around but to be honest there are so many things to adjust I don't know where to start. Suffice it to say all is quiet at present and any advice as to how to remedy this would be greatly appreciated.

---

### Post by manubreizh on 2005-11-15
hi,
just to help me to understand your problem, can you precise : 
- your installation of breezy was an upgrade of hoary or a full installation (which mean, sound was working in hoary or you don't even know ? so problem can be caused by hardware recognition)
- you have no sound, you mean no system sound (like notifications) but amarok or kaffeine can play, or you have no sound at all ? in some case, changes in "system settings > sound" can make it work (like choosing the output, or choosing between oss or alsa)
that was the first step i can see fro answering, maybee more precision make it better for other more advanced users than me
hope it helped

---

### Post by lmandrake on 2005-11-15
Try to max all output channels using alsamixer in a terminal. Hope this helps to find the right mixer.

---

### Post by Julian David Pitt on 2005-11-15
My install was a fresh one and not an upgrade. I have gone into system settings and tried changing the output, I also have checked all the settings in Kmix and still no volume. Amarok and Kaffeine also bring about no sound at all. When I test the sound in the system bell I can hear something from the PC speaker but that is it I am afraid. Cheers

---

### Post by guille0773 on 2005-11-15
Friends i'd have the same problem but i can explain a little bit more about my situation.
I had an HOARY in my laptop, when i tried to do an upgrade had some problems and did a full instalation. From this moment i don't have any kind of sound. Kaffeine, xmms, amarok, system bell, nothing. I switched from ALSA and OSS without good results. AMAROK plays everything but still without sound. Appreciate a lot your help. Thanks so much in advance. Guille.

---

### Post by kruz on 2005-11-15
xmms > output device> alsa
then ur hw config

if you have 2 sound cards
your onboard is 0
and ur pci is 1
try it

---

### Post by guille0773 on 2005-11-15
i tried to do it, but shows "Please check that"
Your soundcard is configured properly
you have the correct output plugin selected
no other program is blocking the soundcard.

I checked and there are not nothing about snd running.

---

### Post by mojorising on 2005-11-16
If you click K > System Info > Kinfocenter, then sound. do you see a sound adapter in there?

The third paragraph down should say card config and then describe your sound card. Mine, for example, says:

Card config:
ENSONIQ AudioPCI ENS1371 at 0x1040, irq 11

If there is a sound card in there. Your card might be all set and you just have to configure volume, etc. Since everything seems to play (but you can't hear anything) and you don't report any error messages, chances seem good that this is the problem. 

Try all (if there is more than one) the tabs in KDE's volume control programs to make sure you are adjusting the volume for the right thing. Turn everything all the way up just to test. 

Also, now might be a good time to double check all the silly things -- like making sure the speakers are powered on, plugged into the right socket on your sound card, the wires on the other end is plugged into the right sockets in the back of the speaker if it comes out from there, and the volume on the speakers themselves is turned up. 

Hopefully I helped at least a little. I know it doesn;t seem like much but in my experience sound problems are similar to this one unless error messages appear. 


Mike

---

### Post by Julian David Pitt on 2005-11-16
[QUOTE=lmandrake]Try to max all output channels using alsamixer in a terminal. Hope this helps to find the right mixer.[/QUOTE]
Just exactly how do I do that please, what commands do I need to input to a terminal, sorry to sound stupid but it is a steep learning curve at present. Cheers.

---

### Post by goldenboy on 2005-11-16
[QUOTE=Julian David Pitt]Just exactly how do I do that please, what commands do I need to input to a terminal, sorry to sound stupid but it is a steep learning curve at present. Cheers.[/QUOTE]

just open a shell and type "alsamixer"

this will start the program in the shell itself. To select the different channels navigate with the arrow keys pressing "up" increases the respective channel output v.v. Another way to do this is b using kmix - there normally is a small loudspeaker icon in the system tray - just click on it... Make shure all output channels are active espially "Master" and "PCM".
If that doesn't help try to disable the two "Jack Sense" switches under "Switches" this did the trick for my once

Just to get that correct, you can hear the jingle when testing the sound configuration via the control centre??

cheers

---

