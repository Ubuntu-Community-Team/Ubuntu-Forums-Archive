---
title: "The Toshiba Headphone / PC Speaker Issue - Solved!"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by pbwalker on 2007-07-07
This was the last thing I needed to resolve so I would have a fully functioning laptop. 

Laptop: Toshiba Satellite a135-S4427


Step 1:
Download the Alsa-Driver (1.0.14 - no RC's!)

Step 2:
Download this patch
[http://launchpadlibrarian.net/8330756/patch_realtek.c](http://launchpadlibrarian.net/8330756/patch_realtek.c)

Step 3:
Replace all existing 'patch_realtek.c" files with the above downloaded one.

Step 4:
cd into the alsa directory

Step 5: 
# ./configure

Step 6: 
# make

Step 7: 
# make install

Step 8:
Edit the /etc/modprobe.d/alsa-base file and remove "3stack" and replace it with "lenovo". 

Step 9: Reboot

Rejoice in knowing that when you plug in your headphones, your PC Speakers will shutoff!

:popcorn:

---

### Post by gaelfx on 2007-07-07
OK, is there any chance you could be a little less vague? Where should I download the drivers from? Is there an easy way to replace every instance of the realtek patch files? I'm sorry, but I still need someone to hold my hand here, I'm very unsure about doing this because the wiki is rife with spelling/grammatical errors and makes numerous assumptions about my system that are false. Frankly the entire ALSA wiki is quite atrocious, so it would be nice to see some Ubuntu forum info about how to easily update this driver. I have a Compaq Presario V3000 (V3169AU), and the HDA card has been a pain about allowing the mics to work, but Synaptic still shows ALSA as being version 1.0.13.

---

### Post by pbwalker on 2007-07-08
gaelfx,

I didn't think I was being vauge...sorry if it wasn't claer enough...

You can download the drivers at the Alsa site. alsa-drivers. 

The best way to replace the patch_realtek.c file is to search for them, check the properties of the file (to show you full path) and replace...

Seeing that your problem is a MIC issue, I don't know if this will work for you...I don't have, nor do I use a mic...so it may not even work...

---

### Post by farbird on 2007-07-08
trying this patch for my hp tx1000 laptop..

hopefully, i can use this to get my headphone jack working

---

### Post by Cuppa-Chino on 2007-07-09
> **farbird said:**
> trying this patch for my hp tx1000 laptop..

hopefully, i can use this to get my headphone jack working

let us know if it works

---

### Post by farbird on 2007-07-09
sorry..

it didnt work....

pity..

i hate to watch porn with the speakers on...

---

### Post by gwanath on 2007-07-12
Didn't work on my A135-s4527 toshiba laptop. Is it unusual not to have any "patch_realtek.c" already on my computer to replace it? I couldn't find any and maybe that is why this won't work.

---

### Post by gaelfx on 2007-07-16
I'm really sorry, I just re-read my post and I see that it may have come off as a little terse. I assure you, I was not trying to be rude, I was just annoyed at having so much trouble getting those drivers to compile properly. I did update my drivers, but alas, there is still no mic support. There are many mentions of "improvements" on the HDA-Intel cards, according to the track changes on ALSA's site, but strangely, any mention of the card is void in the changes from rc4 to the new stable version of the driver. Totally not anyone's fault, but still not happy that I have two useless holes above my screen on my laptop. I guess I just have to wait for ALSA to get the info they need to make these cards useable.

---

### Post by gwanath on 2007-07-16
WOOW...Finally...I got sound from my headphone ONLY....Thanks a lot pbwalker...I would gladly tattoo "pbwalker" on my forehead if it was acceptable at work ;)

---

### Post by pbwalker on 2007-07-31
Glad to hear gwanath!! lol

gaelfx - Sorry to hear man...I don't use my mic, so I don't even know if it works. If you can post the output of 'lspci', I can see what I can find out for you!

---

### Post by interknighterrant on 2007-08-01
Thank you so much pbwalker... because of this thread and one other piece of info I was able to get the irritating sound bug on my Toshiba Satellite R25-S3513 resolved-ish.

I think it should be mentioned that in Step 8, the file potentially doesn't have the line in it yet... so for those that don't have the line, add this to the bottom of the alsa-base file:
options snd-hda-intel position_fix=1 model=lenovo


For my laptop, it doesn't actually mute the speakers when I plug in the headphone.  BUT what it does enable me to do is mute the speakers (under the name front) and still have the audio come out of the headphones.  So, I just set up my audio mixer to mute / unmute the speakers with the button on my Toshiba and I've got a solution that is tolerable for me.  I do enjoy listening to my music loud, through external speakers, and now don't have to be concerned with harming the internal ones.... thank you again pbwalker.  Great step by step, once I got over my newbie problems of understanding exactly what I was doing.

**Tips for other Newbies:**
For all of those who are like me, the patch_realtek.c files are in the Alsa 1.0.14 folder that you just downloaded.  So, search there and replace those files.

Open the terminal for steps 4 through 8, typing in exactly what pbwalker said (without the #<space>).  Step 7 didn't work for me first time through, so I had to go "sudo make install" and then put in my password.  Make sure to edit the alsa-base file by doing "sudo gedit /etc/modprobe.d/alsa-base".

Hopefully that helps the next person that looked at those instructions and went "what?".  They are actually a lot easier than they first looked, at least to me.

---

### Post by JS Lemming on 2007-08-05
Thanks pbwalker! This fixed my headphone/speaker problem to a certain extent. Unlike you, my laptop is a Satellite A135-S4**5**27. The only problem I have now is that whenever I change the volume when my headphones are plugged in, the front speakers kick in again. I can temporarily solve the issue by ripping out and replugging my headphones or using ALSA Mixer to mute "front" but again, anytime I change the volume it just unmutes it.

Do you have any suggestions on how to fix this annoying problem.

---

### Post by jr.gotti on 2007-09-14
> **JS Lemming said:**
> Thanks pbwalker! This fixed my headphone/speaker problem to a certain extent. Unlike you, my laptop is a Satellite A135-S4**5**27. The only problem I have now is that whenever I change the volume when my headphones are plugged in, the front speakers kick in again. I can temporarily solve the issue by ripping out and replugging my headphones or using ALSA Mixer to mute "front" but again, anytime I change the volume it just unmutes it.

Do you have any suggestions on how to fix this annoying problem.

Not to revive a dead thread...actually...that is exactly my intention... but I have the same issue. Is there anyway to prevent this? The volume control is a dial on the front of the laptop, so if it brushes against anything (which happens a lot if im in bed watching a movie) the front speakers kick in. It would be as much an issue if the volume control was an actual button, but I have little to no control over the hardware situation :P

---

### Post by nevhood on 2007-11-24
> **jr.gotti said:**
> Not to revive a dead thread...actually...that is exactly my intention... but I have the same issue. Is there anyway to prevent this? The volume control is a dial on the front of the laptop, so if it brushes against anything (which happens a lot if im in bed watching a movie) the front speakers kick in. It would be as much an issue if the volume control was an actual button, but I have little to no control over the hardware situation :P

I am having the exact same issue!  Any known solutions or fixes, because this is quite an irritating bug for me... I am using a Toshiba Satellite laptop (A135-S4727) with Realtek High Definition Audio (snd-hda-intel).

---

