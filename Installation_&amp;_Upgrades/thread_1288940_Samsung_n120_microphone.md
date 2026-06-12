---
title: "Samsung n120 microphone"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by diggeles on 2009-10-12
Hi,

I am new to linux but I have installed the ubuntu netbook remix. All works great and many small configuration changes i can make later. I have one major problem which will make me have to go back to windows XP, the other problems i can either sort out eventually and/or live with

The problem is i cannot get the microphone working. I am using it as a travelling netbook so i must be able to use skype and keepass on it and other similar applications, managed to get keepass working (quite simple) but skype/microphone issue. Believe it or not the webcam works out of the box as does the sound (its extremely soft and i need that fixed to).

I have gone into the mixer and here were several options. 

I uncheck the microphone with a cross through it. I have 2 listings. microphone front and microphone, both have a corresponding boost aswell. 

I have tried everything and nothing works. With one it looks like it records but a computer tone comes out when i play sound. I am using the sound recorder packed with the netbook remix.

Could someone please help with this. Also i have done searching around here and i have not found any solution

---

### Post by QIII on 2009-10-12
Are you using alsamixer?

---

### Post by diggeles on 2009-10-12
I believe i am using the alsa mixer. When i click on the sound in the side the Device is listed as HDA Intel (Alsa mixer)....

I am sorry but new to linux and as such I am not to sure. If i click on the arrow different lists pop up:

Like Realtek (oss mixer) however the one which comes up when i open and close is the alsa mixer. So i am presumign i have that one selected as the default. I will try and attach a screen shot.

anyway let me know if you need any additional information. BTW you might be interested to know that the headphone socket works perfectly for ear plugs. even turns of the speakers automatically. Unfortunately i do not have a microphone to test the microphone socket. I am using the onboard mic. 

BTW i think we are in major different time zones as such request as much info as you want and i will do my best to supply an answer

---

### Post by diggeles on 2009-10-13
Someone please reply.

I was informed of Linux support and the ubuntu community being very good and strong. I tried linux a few years ago and was not happy as I could not get all the hardware items to work.

I thought with 9.04 this would change. The keyboard keys i was going to write an c app and shell script for to manage all keyboard shortcuts so thats no big deal, but i must have the microphone working.

---

### Post by QIII on 2009-10-14
This might be frustrating, but remember that we all are here voluntarily and help as we have time.  It is possible that there are people looking into it.  We don't want to leave you high and dry.

Which mic do you have selected as the digital  input source under the Options tab?

---

### Post by diggeles on 2009-10-14
I know its only volunteers but when your extremely excited things like this can get dissapointing. 

I was waiting for a long time to get the netbook etc and test it. Finally have it and been stuck for some time. Which options tab are you talking about? in the mixer or the program i am testing with?

I have opened the sound recorder and the record from input: Capture..

I do not have an option to select anything else.. Does this mean the mic driver did not install?

In the alsa mixer options tab the input source is mic.

---

### Post by diggeles on 2009-10-14
Ok, I have gone to the recording tab and something weird happens i uncross the microphone (remove the minature cross on the mic) close the alsa mixer. Open it alsa mixer go to recording tab and the mic has a cross through it again?

Please note all my testing is using the sound recorder packages with Jaunty.

---

### Post by QIII on 2009-10-14
What all do you see when you click the "Options" tab?

(Sorry, my daughter has my laptop (not a netbook, but it does use the Intel) for school, so I don't remember off the top of my head.)

I thought there was a choice to specify which mic...

---

### Post by diggeles on 2009-10-14
I see 2 input sources: Mic and front Mic.

I have tried doing both and neither option works. the list is a drop down list (not button check)

---

### Post by QIII on 2009-10-14
I think you probably want Front Mic ...

The change should take effect immediately.  I wish I could test this for you, but I can't.

I'm wondering if a shut down and restart would work (not that I think that SHOULD be required, mind you.  If it is, then that is definitely a bug!)

---

### Post by diggeles on 2009-10-14
I change it to front mic, and tried the recorder, again nothing was recorded, the weird thing. In the recorder Recording tab: it crosses (effectively mutes) the mic. When i unmute it and open up alsa it is muted again.

UPDATE:

Restarted the box and the front mic sorta works now. One thing is its soft and I have a lot of static. I believe this can be fixed through tuning? i.e. Also with the changes I am getting static through my earphones. The sound was extremely clear yesterday.. Is this feedback from my mic being played back into the speaker even when the sound recorder is off?

Static is present with everything now. I need to go home now.. but we are making good progress. will most likely log on tonight.

---

### Post by QIII on 2009-10-14
OK.

I'm going to have to do some more research.

You might want to look at [www.launchpad.net](www.launchpad.net).  There are search tools there.  Try a combination of things including "Samsung n120" and "mic", etc.

I have to hit the rack.  Have to get up and put my back to the millstone again to earn my daily crust of dry, maggot ridden bread tomorrow.

This is really something that I'd like to get to the bottom of.  I'd really like you to get a warm and fuzzy about Linux rather than being disappointed.  If you don't like Linux because you don't like it, that is one thing.  If you don't like it because of a frustration like this, it would be a shame.

Not everyone has a good experience, unfortunately.  I'm not a Linux evangelist, so I won't tell you that Linux is a cure-all wonder drug for the world of computing.

---

### Post by Sonsum on 2009-12-30
I'm running UNR 9.10 on my Samsung N120 as well. The problem still hasn't been fixed. If I find anything, I'll post here and let you know.

---

### Post by Moozillaaa on 2009-12-30
Some sound output modes use the microphone channel as a center-channel output. 

Look to see if you can adjust the sound output mode to 'basic' (or something similar), as opposed to advanced (Surround Sound, 5.1, 7.1, etc.).

---

### Post by Sonsum on 2010-01-01
> **Moozillaaa said:**
> Some sound output modes use the microphone channel as a center-channel output. 

Look to see if you can adjust the sound output mode to 'basic' (or something similar), as opposed to advanced (Surround Sound, 5.1, 7.1, etc.).

Okay, I looked in the sound settings, there were no options for surround sound. I changed the input connector back and forth between microphone 1 and microphone 2, but I still get no response from the built in mic.

Odd. It looks like when I plugged in an external mic, I got a response from mic 1. Then I switched to mic 2 and saw some response.

Now the internal mic works with skype, but even when fully amplified, is very faint.

---

