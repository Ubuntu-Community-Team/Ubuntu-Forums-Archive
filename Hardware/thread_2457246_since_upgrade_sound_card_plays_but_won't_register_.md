---
title: "since upgrade sound card plays but won't register in sound settings and can't record"
date: 2021-01-28
forum: Hardware
---

### Post by bjb19592 on 2021-01-28
I have a weird problem. my sound card worked fine for playing and recording in 20.04. it is the built in sound card from realtek listed as Family 17h in the sound settings. in 20.04 I was able to play through speakers and headphones and also record audio through the soundcard. I upgraded to 20.10, clean installs twice thinking I did something wrong, I can play music through the speakers and headphones but the VU meter in the sound settings that normally showed activity in 20.04 shows nothing for the analog soundcard now. The strange thing is if I use OBS studio I am able to record audio through the soundcard but not using Audacity any longer which is really weird since OBS is using the same soundcard shown in the sound settings under Ubuntu. Any idea why the soundcard recording works with OBS but not Ubuntu itself?

---

### Post by Autodave on 2021-01-29
Could you give us some info on your system please?  Do you know what kernel you are using in 20.10?  You may have to go back to 20.04.  Can you make a bootable disk with 20.04 and see if the sound works properly when booted to that?

---

### Post by bjb19592 on 2021-01-29
Not sure what info you would like on my system. it is an HP Omen with AMD Rizen 7 with 16 GB ram. I believe the built in audio was Realtek AC97 which was working for recording in 20.04 but not in 20.10. I decided to get a new soundcard in case it was a hardware issue so I purchased a soundblaster AE-7 and upgraded my kernel to 5.10 to get the proper drivers. the same thing happens in that the card works fine, even the external headphone/microphone dongle and plays flawlessly. I can even record audio using OBS studio and OBS Studio shows the vu meter of the audio card when audio is playing as does pavucontrol shows the vu meter when audio is playing. However, the regular ubuntu sound settings module, nor Audacity, show movement on vu meter when audio is playing. The microphone does, just not the audio which is why I know it isn't a hardware issue since I wouldn't be able to record audio using OBS studio if it was the soundcard. Having done 3 clean installs of 20.10 with the same result I believe it is an issue with Ubuntu and not the soundcards themselves but I have no idea what it could be or how to fix it. Also, in Audacity if I try to monitor the soundcard specifically I get an error code -9997 improper sample rate. but changing the rate doesn't help. I have never seen this before in all my years of using Ubuntu but the fact it works with OBS but not Ubuntu itself leads me to the "it's an Ubuntu" issue as opposed to hardware. Just may have to wait for 21.04 maybe?

---

### Post by Autodave on 2021-01-29
Please try booting 20.04 from either a DVD or USB stick and see if the sound works properly.  There were some issues with the 5.8 kernel and maybe they are continuing on with the 5.10 kernel as well.

I had to roll this machine back to a 5.4 kernel to get sound and internet working.  Try the 20.04 and report back.

---

### Post by bjb19592 on 2021-01-30
I'm pretty sure it works fine since it worked in the morning for recording but not in the afternoon after installing 20.10 and a new soundcard has the same issue. But I will install a vmware instance of 20.04 and test using that if that would do the trick and let you know. Also, just to reiterate my sound works fine through speakers and headphones, always has, the only thing not working properly is recording sound through Audacity or any other sound/music editing/recording software with the exception of OBS studio. So what OBS does that those others do not seems to work fine. So I can record a screen session on OBS, open it in avidemux and save the audio only, open the audio in Audacity and edit using that just can't record using Audacity so there are a couple extra steps but I can get it done.

---

### Post by bjb19592 on 2021-01-30
I just realized a problem with your request. since installing the soundblaster card the onboard soundcard is no longer available as an option and the soundblaster won't work on kernels older than 5.10 and I do not want to pull the soundblaster out of the box because it is a pain in the butt to do so. I can try but if the realtek does not show up I won't go overboard to try and test this since I am pretty sure it is an issue with Ubuntu and not the hardware.

---

### Post by bjb19592 on 2021-01-31
It works in 20.04 in a vmware install. sound card shows vu meter process in settings > sound But Audacity still does not show vu meter process when monitoring  the card and does not record but when I had it installed on my machine it did work with Audacity so not sure what that proves. probably something to do with the virtual install. Still pretty sure it is a 20.10 issue.

---

### Post by bjb19592 on 2021-02-05
I figured it out by doing more research and finding the answer on Reddit. in Audacity go into preferences and for devices and recording select pulse. open the pulse volume control (pavucontrol, install it if you don't have it installed) and go to recording, select applications from the bottom right drop down menu then select monitor drop down and choose your sound card listed. Voila, audacity now shows the sound card in monitor and you can record.

---

