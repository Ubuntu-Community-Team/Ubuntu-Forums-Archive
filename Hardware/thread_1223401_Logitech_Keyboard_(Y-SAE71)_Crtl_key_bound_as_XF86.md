---
title: "Logitech Keyboard (Y-SAE71) Crtl key bound as XF86AudioPlay... or something"
date: 2009-07-26
forum: Hardware
---

### Post by Greyhaven7 on 2009-07-26
OS - Ubuntu 9.04 (Jaunty - 64 bit version) freshly updated on 07-25-09.

Keyboard's model name as it's written on the bottom of the keyboard:

Y-SAE71
SK-2930

*I'm new-ish to Ubuntu/Linux (been using it as my only OS at home on two comps for about 6 months now... LOVE IT btw), so please excuse my ignorance if the solution to this issue seems like it should be obvious.*

I've been trying to find the solution to this for several hours now without any success. Even searching Google and various forums for "Ubuntu" and "SAE71" at the same time returns virtually nothing useful (couple issues with function keys being broken, and a bunch of stuff in German, but nothing about the Ctrl key being broken... at least not in an English-speaking region). 

The Issue: System thinks Ctrl key is XF86AudioPlay and I don't know where to begin to fix it.

Issue presented with these symptoms:
Some (but not all) Keyboard shortcuts are not working properly. Keyboard shortcuts are a huge part of my user experience (I will use any and all of them that I can), so a few days ago when all Ctrl+___ shortcuts seemed to just stop working entirely I was rather frustrated. 

Several hours later I accidentally discovered that they hadn't all stopped working... some, e.g., Ctrl+C; Ctrl+V; Ctrl+Left; Ctrl+Right; Ctrl+S,  worked, but only if I pressed Ctrl... and then WAITED approximately 1 second before pressing the other key of the shortcut. All shortcuts that are Ctrl+Shift+___ or Ctrl+Alt+___ are still very much broken. 

One of the things I tried (among many others) was just re-doing all of the keyboard shortcuts with 'System -> Preferences -> Keyboard Shortcuts'. This revealed that my system thinks my Ctrl key (the left-hand-side one) is "XF86AudioPlay" and that the one on the right side isn't actually a real key, but rather, that it is a decoration to give the keyboard a more 'symmetric' appearance (it doesn't output anything at all)... except that in practice, the right-hand one works. 

Since I don't use the right-hand This would be no issue at all for me if I could just bind my shortcuts using "XF86AudioPlay" in place of the left Ctrl, but the keyboard shortcut editing tool won't let me combine it with anything (I guess you're only supposed to use Ctrl, Alt, and Shift in combo with anything). 

I thought my Keyboard layout might be set incorrectly but when I went to 'System > Preferences > Keyboard', in the 'Layout' tab, under Keyboard model, this keyboard isn't listed at all. 

*NOTE: By the way, right now, as I'm writing this, the "having to wait 1 second after pressing Ctrl for shortcuts to work" issue has gone away... but all other issues, e.g., no Ctrl+Alt+____ shortcuts, still persist... no clue what happened... I didn't change any settings on anything.*

Where should I begin solving this problem? 

Can I just re-bind it so it thinks Ctrl is actually Ctrl again? Everything worked with it up until a few days ago... and everything else that I care about still seems to work just fine (I don't really use the media-related keys at all). 

Could a recent update have changed or reset something?

*Also, thank you all for being such a wonderful, dedicated, (not to mention mature and professional) community. The transition from Windows has had some rough spots, but these forums have made most of them short-lived and virtually painless! I hope that one day I know enough to help people with issues on here.*

---

### Post by rhalaquist on 2009-10-07
Hello hopefully your problem has been solved by now. If not there is another option besides "Keyboard Shortcuts" I do not fully understand the program at the moment (just got it) but you might find Keytouch and its other part Keytouch-editor a perfect solution. I discovered it really by accident. I am trying to figure out a way to sign my password to either a key or set it in stone within a context menu, which no luck yet even with the Keytouch program. You can get the program through Synaptic Package Manager. Beware your keyboard is not in the list (you will know what I mean when it all happens) thats where the Keytouch-editor comes to action. Good Luck!

---

