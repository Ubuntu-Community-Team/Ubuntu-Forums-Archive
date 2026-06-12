---
title: "CD Playing woes.."
date: 2005-11-20
forum: General Help
---

### Post by amohanty on 2005-11-20
Hi All,

So after waiting for some time, I finally bit the bullet and upgraded to Breezy. I did a complete reinstall (my home is on a second drive and I put all my config mods in cvs, so its a breeze - no pun intended). Everything went smoothly and I was up to warp speed in no time, except this itsy bitsy glitch. 

I cant play any audio cds. My test CD is a store bought classical music thingy (out of copyright work). No warnings about Mac/PCs, FBI notices and the like. To give some background it worked fine on hoary with gnome-cd. The problem was that the CD mounted and played but there was no sound in gnome-cd, sound-juiceror goobox. However it worked fine in totem-xine. I still does.

My first attemp was to look at whether I was in the cdrom group. I was.
Then I turned off DMA on the CD drive which I had turned on during installation. No go.
Then I hunted the forums and found that possibly I didnt have cable connection between the CD drive and my sound card (Audigy 2ZS). So I went out, bought an analog audio connector from CompUSA, put it in and rebooted. 

However now theres another problem, whenever I hit the play button in gnome-cd, sound juicer or goobox I get the following error:
<code>
Error playing CD.

Reason: Could not open resource for writing.
</code>
twice!!

So now I am at my wits end as to what I should do. Any help would be greatly appreciated.

Thanks.
AM

---

### Post by soulestream on 2005-11-20
if you have more than one cdrom, make sure the correct one is the default.

you can also try to chmod the device


soule

---

### Post by MarcDM on 2005-11-20
ok, so I've gotten that ```
Reason: Could not open resource for writing.
``` error before but that was with totem on my Thin Client. 

I've found out that the cd-player in breezy doesn't send audio out thru the cd-rom's audio out. It goes digital and comes out thru the wav device. 

So you might want to try fiddling with the settings Under : System -> Preferences -> Multimedia Systems Selector

Also, since it's now played as wav, I think that means it needs esound. So make sure esd is running. I like to killall esd explicitly and then start it up with ```
esd &
``` just to hear that startup sound it makes.

IF that doesn't help, u could always try goobox (a cd player program). I have it installed (think it came from universe), and it's kinda cool as a cd-player. I use it instead of the default.

HTH.

---

### Post by amohanty on 2005-11-21
<beats his head against the wall>
damn it should have known. I explicitely turned of esd because it caused a whole world of trouble with my sound editing stuff, and just used alsa. 

turning it on fixed it. is there any way to pipe sound-juicer output to alsa instead of the esd sink.

thanks.

AM

---

### Post by amohanty on 2005-11-21
Ok now I know what happened. 
while logged in I issued as 'halt' as root. that seemed to have reset most of my user settings. so I dont need to use esd as long as a valid alsa sink is defined.

Thanks.

AM

---

### Post by hollowhead on 2005-11-22
I'm having the same problem with audio CD's I don't believe its a protected copyright thing -I don't think we have this in europe.  The CD plays but no sound appears -but the sound is defintely working cause I get system sounds.  Aslo totem does not play DVD's I get a weird error message (that I cannot remember) since I'm not sitting in front of the system.  I wondered whether this might be a geographical area code thing with totem configured for the US, but I cannot play MP3 downloaded from the BBC (perfectly legally) and get the same error.  Its not a permissions thing on totem either since I've tried it as root.

---

### Post by amohanty on 2005-11-27
Did you try MarcDM's suggestion regarding setting the Multimedia selector to the right sinks.

AM

---

