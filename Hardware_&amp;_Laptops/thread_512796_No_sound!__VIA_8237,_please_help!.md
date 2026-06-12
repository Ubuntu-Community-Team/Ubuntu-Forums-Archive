---
title: "No sound!  VIA 8237, please help!"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by Mikitad on 2007-07-29
I am extremely new to Linux, but am learning fast.  I have installed Ubuntu on a Gateway MX3228, I've managed to get the wireless working, but nothing I do can get the sound working.  I've checked if it was muted, I've run "aplay -l"  and my sound card is there. "lspci" looked fine...I'm at a loss.  The laptop has a VIA 8237 sound card.  Any help would be GREAT!  

Thanks in advance.

---

### Post by kyphi on 2007-07-29
Hello Mikitad,

Have you tried this:   At the top left where you see Applications Places  System, go to System then Preferences and then Sound.  Put a tick in the boxes at the top.  At the bottom, where it says 'Default Sound Card', if there are more than one entry toggle to see which one works for you.

---

### Post by Mikitad on 2007-07-29
Hey, I tried changing the sound card to the other options and none seem to work.  :(

Any other ideas?:confused:

Thanks again for your help!

---

### Post by kyphi on 2007-07-30
> Have you tried this: At the top left where you see Applications Places System, go to System then Preferences and then Sound. Put a tick in the boxes at the top.

Did you do this to enable your system sound?

---

### Post by jlh68 on 2007-08-02
On my Acer Travelmate I had to tick the "surround" slide to get the sound from the speakers.

Go to the sound preferences and check each slide one at a time to see which one actually controls the sound.  I would start with "surround" as it was the culprit for my system.

---

### Post by zek725 on 2007-08-05
type **alsamixer** in terminal then see if your master volume is not muted. 
Increase volume by pressing the UP arrow key. Toggle Mute/Unmute by pressing M key.

---

