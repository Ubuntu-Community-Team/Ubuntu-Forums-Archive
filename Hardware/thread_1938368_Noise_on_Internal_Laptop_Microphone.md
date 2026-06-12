---
title: "Noise on Internal Laptop Microphone"
date: 2012-03-09
forum: Hardware
---

### Post by slharris910 on 2012-03-09
Hi all,    Just switched to Ubuntu 11.10 Oneiric after some Windows disasters; things are generally working great, but when I try to record using my laptop's internal microphone, I get terrible noise/static that practically drowns out voice.

Not sure what hardware information is relevant, but I have a Toshiba Satellite A505-S6965; Intel® Core2 Duo CPU P7350 @ 2.00GHz. The sound card is Realtek ALC272. Speakers and sound are working fine on the output end. 

I have tried using Skype and Sound Recorder to test the internal mic sound. Both give the same result. I do not own a headset, and I'm living abroad right now in a situation that makes it a bit of a headache to acquire one, so I'd prefer to use the internal. The mic works fine in Vista.  

Web searches have turned up some suggestions, such as opening alsamixer and experimenting with the Capture settings and using the Pulse Audio Volume Control to min/max the Left and Right channels, but nothing has worked so far. I can drop the amplification level enough so that the noise disappears, but at that point my voice is also too quiet to be audible.     

Any ideas are appreciated! If more info is needed on my system, please just let me know how to find it, as I'm brand new to Ubuntu.

---

### Post by Paddy Landau on 2012-03-10
I empathise with you. I have always had background-noise problems with laptops.

I finally resorted to getting a USB sound-reducing microphone, which solved the problem. I know it's not much help in your situation, sorry.

---

### Post by ibu on 2012-03-10
Try this:

Go to terminal. Type in *alsamixer* and press enter. Navigate to your internal microphone levels; you might have to press the tab key on your keyboard to see them. 

Press the up arrow key on your internal microphone levels so that the volume goes up all the way (unless you don't want the volume to be up so high). Then press the y key on your keyboard to bring all the noise down. Press esc to exit out of the alsamixer interface and then close the Terminal. Works for me.

---

### Post by slharris910 on 2012-03-11
> **ibu said:**
> Try this:

Go to terminal. Type in *alsamixer* and press enter. Navigate to your internal microphone levels; you might have to press the tab key on your keyboard to see them. 

Press the up arrow key on your internal microphone levels so that the volume goes up all the way (unless you don't want the volume to be up so high). Then press the y key on your keyboard to bring all the noise down. Press esc to exit out of the alsamixer interface and then close the Terminal. Works for me.

Thanks. This does help a little, but the noise is still way too prominent for a Skype conversation. Looks like I might need to get ahold of a headset and see how it goes.

---

### Post by Paddy Landau on 2012-03-11
> **slharris910 said:**
> Looks like I might need to get ahold of a headset and see how it goes.
I was told that you need a USB microphone to eliminate noise from a laptop. That could be nonsense, of course -- you have already told us that the microphone works perfectly in Vista.

Before buying the headset, take your laptop with you and test it.

Sorry we haven't been of much help.

---

