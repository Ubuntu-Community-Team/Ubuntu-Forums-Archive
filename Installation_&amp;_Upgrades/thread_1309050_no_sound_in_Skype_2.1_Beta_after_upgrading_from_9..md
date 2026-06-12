---
title: "no sound in Skype 2.1 Beta after upgrading from 9.04 to 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by stz_comp on 2009-11-01
Hi,

I can't figure out, where the problem is. Please help. 
After upgrading AMD64 Jaunty to Karmic my Skype stopped making sounds. I have tried to change the "sound device" in skype's settings, but there is no other option except pulseaudio. All controllers in the new sound mixer are on and even in the "Applications" page the Skype appears when making sound, but nothing is heard.

Thanks for any advice.

---

### Post by Martin_sensei on 2009-11-01
Hi,

I had a similar issue with my mic, I could hear sounds but no one could hear me.  It seems you have to have pulse audio in Skype, which seems to read the default settings in your sound preferences.  

Try opening the sound preferences from the volume icon (top pane on the right by default) then checking the default devices for input and output are correct and not muted.

Sorry that sounds simple but one radio button can make all the difference sometimes!

Hope that helps!!

---

### Post by jas007 on 2009-11-12
> 
Try opening the sound preferences from the volume icon (top pane on the right by default) then checking the default devices for input and output are correct and not muted.

Sorry that sounds simple but one radio button can make all the difference sometimes!

Hope that helps!! 

Thank you so much, I tired everything else, including going back to 2.0. Had to open up volume control, than clicked on the recording tab, unmuted the mic symbols, now working. My mic was already working outside skype. After reopening the volume control panel the symbols are muted again, but the mic is still working in skype - don't understand that.

Thanks again.

---

### Post by David Oxland on 2009-11-13
I believe that I have a similar problem.
On every start up the sound preferences chosen device changes to "Internal Audio Analog Stereo"; (my sound device should be Quickcam Communicate STX Analog Mono). Changing it back gets Skype sound working fine but it keeps reverting. I'm not sure if it's after a shutdown or hibernate. It has not happened while in a call.  Don't know how to stop this.
Using Skype beta and Karmic 64bit.

---

