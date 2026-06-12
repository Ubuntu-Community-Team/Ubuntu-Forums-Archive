---
title: "Mic Issue with Acer Aspire One 10&quot; in Ubuntu Remix"
date: 2009-05-28
forum: Hardware
---

### Post by rreyes1316 on 2009-05-28
I have been looking for a solution to this problem and have been unsuccessful. My Mic does not work with Skype I have made sure that the mic is not on mute in the volume control and also tried to change the audio setting under the Preferences. I have done a complete reinstall and made sure to install medibuntu, restricted extras, keyring, and all codecs. This is just not working. I have tried to download the latest alsa drivers but do not know how to compile them for install or back up the old drivers just in case.

Hope someone can help.

---

### Post by Blackkitten on 2009-05-28
Just try to change sound input in skype's settings. That did the trick for me!
Don't forget to push the apply button!

---

### Post by rreyes1316 on 2009-05-28
I tried that but it did not work. It occurred to me that perhaps I should try another app. Sure enough, the mic did not record using other mic supported apps. So that rules out skype as the problem.

---

### Post by Blackkitten on 2009-05-29
I didn't understand. Does your mic works in other apllications, such as gnome-sound-recorder 2.26.0?

---

### Post by rreyes1316 on 2009-05-29
yes . . .that is correct.

---

### Post by Blackkitten on 2009-05-29
in this case it must work in skype.
For me, selecting HDA Intel(hw:Intel,0) for sound input in skype's settings did the trick.
And what you have as a sound mixer by default? In systems>parameters>sound?
I have HDA Intel( alsa mixer ).

---

### Post by rreyes1316 on 2009-05-29
My appologies. I have been too quick to respond on the forums using my phone without double checking my response. I meant to say that "yes" I tried the recorder and it did not work either. Those settings that you mention are the ones I have currently.  I had tested the mic using windows xp and everything works fine--so it is not the mic. 

Hope I was clear here :)

---

### Post by Blackkitten on 2009-05-30
Ok. In the beginning my mic also didn't respond.
Steps, that helped me:

1.Open Alsa mixer by clicking with right mouse button icon with dynamic then select sound regulator or something like that.

2.Next open parameters( there will be a button at the bottom ) where you can select channels. For me to activate mic I had to select Microphone and Microphone boost. Channels will become viewable and you will be able to tune them.

3.Also you have to select input source.I have two built-in mics so I selected two input sources.

4.Tune your mic sensivity and boost then go to tab called parameters and under input source select mic.

5. Try the sound recording program.

---

### Post by rreyes1316 on 2009-05-30
Thanks for your help.

When you say "Open Alsa mixer" do you suggest I install also mixer or alsa mixer gnome from the Add/RemoveApplications? I could not find anything in the preferences or administration that said also mixer. WHen I did install the alsa mixer from the add/remove it placed a ALSA Mixer icon in the Sound & Video tab. When I right click that all I get isExecute and Add to Favorites option I was confused when you said " . . .with dynamic . ." Anyway, when the app opens all I see are a bunch of "volume" controls for fron, headphone, capture, master, input, and pcm--they were all cranked up. I right clicked  on everyting here but no other options popped up.

The other thing I right clicked was the volume control on the panel. From here I saw preferences and Opem Volume Control. I tried to repeat everyting mentioned above but there were nothing that says "dynamic" or "regulator"

Now, the closest thin I found close to Parameters was the Preferences button. Here I was able to select tracks to be visible--I selected them all.  This allowed me to place an Option tab where I was able to view the Input Source. There is only one option (Front Mic) and it is selected already.

Anyhow, After each change I tested the Sund recorder with no success.


 by clicking with right mouse button icon with dynamic then select sound regulator or something like that

---

### Post by Blackkitten on 2009-05-30
I'm using russian version of linux, so sorry for mistakes.
And also my notebook is aspire 5920g.

Yes, input source is the thing I was talking about. But I have several options there and one of them ( mic ) works.

Do you have only front mic listed in preferences in volume control?
If yes - I don't know what to to. Maybe it's common problem for your laptop?
And also you can try to install latest alsa drivers [http://ubuntuforums.org/showthread.php?t=1151344&highlight=alsa]("http://ubuntuforums.org/showthread.php?t=1151344&highlight=alsa") maybe they will help.

And try to check this:
System>preferences>sound. There will be devices tab. For sound capture I have HDA Intel ALC1200 Analog ( alsa ) selected.

---

### Post by rreyes3000 on 2009-05-30
I have the Ubuntu Netbook Remix 9.04  on my Aspire One D150. Everything works great out of the box except for the mic.

I have done everything  so it must be my laptop. It just occured to me to check the bios. But that should not have anything to do with it considering I was dual booting. When I used Windows XP the mic works. So it is definitely the Ubuntu OS Drivers.

Thanks

---

### Post by trinetra on 2009-11-12
I also has the same problem, I installed Ubuntu Netbook remix edition on hp 110 mini, my mic is also not working. I found that alsa version is 1.0.20 which is latest. Can any one please help me in solving this problem. Thanks in advance

---

