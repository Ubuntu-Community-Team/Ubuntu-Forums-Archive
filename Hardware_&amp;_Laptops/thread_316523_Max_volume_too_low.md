---
title: "Max volume too low"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by d3dtn01 on 2006-12-10
I was trying to watch a DVD on my plane ride home last night, but the volume was just too low to hear over the plane buzz. I had all the volume controls turned to the max (the system volume as well as xine volume). I know that my speakers can put out more b/c when I run the Windows OS on my machine the max volume is about twice as loud. I'm running Edgy now. Is there a way to address this?

---

### Post by mcduck on 2006-12-11
Are you using Gnome?

Open Volume Control (Applications/Sound & Video/Volume Control), and go to Edit/Preferences. Now, enable all possible controls for your sound card. Play with different settings, and you should be able to get a bit more volume out of your soundcard (for example, I have separate 'PCM' and 'Front' sliders that both effect the sound volume).

If that didn't give you enough volume, go to File/Change Device and see if you have other device listed there (most likely OSS device). Change to that and repeat the part about enabling controls..

---

### Post by d3dtn01 on 2006-12-11
I am using Gnome. I already had all my sound card controls available and had all the volumes on max. Switching from Alsa mixer to OSS mixer didn't help either. But thank you for the suggestions. Any other ideas out there?

---

### Post by mcduck on 2006-12-11
If the volume is low only when watching a movie you could check if the movie player you are using has an option to downmix surround sound into 2 channels. That might make the movie sounds louder when using headphones or laptop speakers.

---

### Post by d3dtn01 on 2006-12-11
Thanks for the second reply. I prefer to use xine for DVDs. Under its options menu I found Audio --> Channels. This gives a list of Off, Auto, 0, 1, 2, 3, etc. up to 14. Auto is currently checked. Should I check the 2? Will that accomplish what you suggested?

---

### Post by mcduck on 2006-12-11
In Gxine go to File/Configure/Preferences and in Audio/a52-tab there is a checkbox for surround downmix.

Also in the same tab is option for a/52 dynamic range compression, which is useful in noisy environments or if you need to keep the movie sound low. The dynamic range in movies is often designed for high volumes used in movie theaters so with lower volumes more quiet parts of a movie can become too quiet to hear what people are speaking. Compression fixes that.

Then there's the speaker setting in the Audio/Output-tab. That should be either Stereo 2.0 or Headphones 2.0

Edit: the audio channel option you mentioned is about different possible audio channels that the DVD might have (for different languages usually). Better keep that at 'auto'.

---

### Post by BKK on 2006-12-12
Hi,

I am having the same issue. However my max volume is MUCH lower than it is in Windows XP, in ALL applications. I tried looking in the menu for volume control and the option is not there. It IS checked in the ADD/REMOVE programs section! HMM? Also I went tnto Synaptic and typed "Volume Control". There was something called volumecontrol.app. I then installed that, now it seems I have lost all sound....and the Volume Control option still is not in the MENU.

---

### Post by mcduck on 2006-12-12
If the Volume Control is not in your menu, right-click on the menu and select 'Edit Menus', then browse down to Sound & Video and mark the checkbox next to  'Volume Control'.

You can also open the Menu Editor from System/Preferences/Menu Layout.

---

### Post by BKK on 2006-12-12
Thanks for the instruction on how to edit menus. I still have the low volume issue. I tried all of the suggestions in this thread. I have a feeling it has to do with drivers somehow. 

Peace

---

### Post by legolas on 2006-12-12
You know, I have noticed that xine plays my movies a lot louder than some of the other players- that is why I prefere xine- I like to blast my videos!

---

