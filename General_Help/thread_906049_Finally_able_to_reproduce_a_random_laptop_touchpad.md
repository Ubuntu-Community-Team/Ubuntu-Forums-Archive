---
title: "Finally able to reproduce a random laptop touchpad bug - help please?"
date: 2008-08-31
forum: General Help
---

### Post by dai_vernon on 2008-08-31
I'm running hardy on a Compaq Presario F700 and occasionally my touchpad loses some functionality.  I lose the ability to drag (ie touch and drag does not select or scroll, can't move windows, etc) and I can no longer scroll by running my finger along the side of the pad (the cursor doesn't even move.

I recently discovered that this occurs whenever I hit Caps Lock with no target.  IE, if I have no text field that is prompting me to type and I hit caps lock this happens.

It also happens whenever I hit the button that above the pad that disables the trackpad (ie when I hit it again to reactivate it, it reactivates with the same symptoms as above).

I retain the ability to do these things with a USB mouse no matter the state of the trackpad, but I prefer it and would like to use it over a mouse.

Has anyone encountered this before?  What can I do to solve it.

---

### Post by dai_vernon on 2008-09-01
This is a pretty nasty bug - somebody help*please?

---

### Post by valmi on 2008-10-13
I had the same bug for a while, running Xubuntu 8.04 on an HP Pavilion dv6000, that I wasn't able to replicate--and kept wondering why it happened mostly after my girlfriend (a bad typist) had used the computer. You are right, it happens when I deactivate Caps Lock when no text input is "under focus".

As a matter of fact, when this happens, all Synaptics Touchpad settings from /etc/X11/xorg.conf are lost. I noticed the bug because I have 	*Option "TapButton1" "0"* set, and after the bug occurs tapping the touchpad makes a left-click. This basically forces me to restart X as I am personally unable to use the touchpad with this setting.

---

### Post by valmi on 2008-10-13
If that may be of help to someone, I tried the *synclient -l* client before and after replicating the bug, and as far as synclient is concerned there is no bug at all: it still shows *TapButton1 = 0 *and everything else seems the be exactly the same.

---

### Post by commonplace on 2008-11-17
At least I know I'm not alone! This is one of the first things I try in each new version of Ubuntu. Sadly, it's still present in 8.10 (Intrepid). No one has a fix or workaround for this?

/Kevin

---

### Post by valmi on 2008-11-17
I don't get it anymore since I updated to 8.10. I thought it was because HAL had taken over synaptic settings.

I don't know anything about HAL, but I suppose you could look into xorg.conf&#8212;if synaptic settings are still there, maybe your system isn't using HAL for some reason, and maybe you should look into using it.

Don't ask me how, though. ;-)

---

### Post by dai_vernon on 2008-11-19
I actually no longer get most of this bug in Intrepid.  The computer still siezes up and the audio skips for several moments, as though the bug was to occur, but the trackpad remains functionsl.

---

