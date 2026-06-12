---
title: "Sound problem on nForce4 , Realtek ALC850"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by aneeshm on 2005-06-07
I'm on a nforce4 machine , AMD Athlon XP 64-bit 3200+ , and I have a problem with the soundcard ( Realtek ALC850 , according to the manual ) . The card is capable of 8-channel sound , yer I get only single-channel . Is there any way to fix this ? Any driver/configuration help ?

---

### Post by aneeshm on 2005-06-08
Any help , anybody ? 

*bump*

---

### Post by aneeshm on 2005-06-09
Could someone please help me ? First time someone has not answered for two days , now almost three .

Another *bump* .

---

### Post by PryGuy on 2005-06-09
That's 'cause you gave us not much information.
What do you mean saying "I get only single-channel"? Do you have the volume control icon on the panel above your desktop (it's there by default if you have the sound card installed of course), do you hear ANY sounds?

---

### Post by krusbjorn on 2005-06-09
[QUOTE=aneeshm]I'm on a nforce4 machine , AMD Athlon XP 64-bit 3200+ , and I have a problem with the soundcard ( Realtek ALC850 , according to the manual ) . The card is capable of 8-channel sound , yer I get only single-channel . Is there any way to fix this ? Any driver/configuration help ?[/QUOTE]

Do you mean that you can only hear one sound at the time? If so, check this thread out:

[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

---

### Post by aneeshm on 2005-06-10
Okay , I'll give more info , as asked .

The machine is an ASUS A8N-E motherboard , where the onboard soundcard is a Realtek ALC850 . The processor is an Athlon 64 3200 + . I'm running Ubuntu 5.04 for normal x86 , not Ubuntu 5.04 for x86_64 .

When I go to the Volume control , it shows these entries for Realtek ALC850 rev 0 OSS :

Playback : PCM , Speaker

and 

Capture : Volume , Line-in , Microphone , and CD .

One the other device , called NVidia CK804 (Alsa Mixer) , I get :

Playback : Master , PCM , and PC Speaker .

and 

Capture : Line-in , CD , and Microphone .

I have a set of creative speakers , 4.1 channel ( two front , two rear , and a woofer ) . I'd like to ask how to enable the rear speakers . I just cannot get sound out of them while using either of these devices .

I have ports at the back of my computer case , labelled :

Line In , Mic In , Front , Rear Spk , Side Spk , and CTR Bass .

I've tried plugging the input cord for the second set of speakers into both the rear and the side speaker ports , yet they do not work . The provided set of drivers have options under windows to enable four , six , and eight channel sound . But no linux driver is provided .

I hope this is enough information for those who can help .

---

### Post by PryGuy on 2005-06-10
I don't think I can help, I have a typical stereo :). Think the other channels are probably muted. Have you tried to unmute them?
Another question? How do you test them?

---

### Post by aneeshm on 2005-06-10
How exactly do you unmute the channels ?

I dual-boot windows , so the driver coming with the onboard soundcard worked ( that's how I test them ) .

---

### Post by aneeshm on 2005-06-15
Anyone who can help me here ? I hope I've given sufficient details , if not , please tell me what further information is needed .

And another *bump* .

---

### Post by DancingSun on 2005-07-04
If you haven't fixed this yet, try this:

Use the ALSA mixer.  Goto preferences, and check off surround.  Unmute it, and see if it works.  I don't have surround speakers that have separate line outs for each speaker, so I don't know if this works or not.

---

### Post by aneeshm on 2005-08-03
[QUOTE=DancingSun]If you haven't fixed this yet, try this:

Use the ALSA mixer.  Goto preferences, and check off surround.  Unmute it, and see if it works.  I don't have surround speakers that have separate line outs for each speaker, so I don't know if this works or not.[/QUOTE]
 Thank you !

I used the amixer command to unmute all the channels I could find in ALSAMIXER , and then used ALSAMIXER to increase all the channels' volumes to full . Then I used "sudo alsactl store" to store the settings . My sound now works flawlessly . Thanks again .

---

### Post by DancingSun on 2005-08-03
Sweet! Good to know that works!  Now I know what to do if I ever decide to buy new speakers :D

---

