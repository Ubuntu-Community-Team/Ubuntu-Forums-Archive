---
title: "Plantronics DSP-500 Findings!!!!!!"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by John Hughes on 2007-06-21
Ok so this is something interesting that happened to me earlier today.......
Ok so last night i went on here to find how to get my DSP-500 headsets to work everywhere i read ohh the inline volume wont work!!! This held true until about 30 minutes ago or so.... 

Now i followed this guide that was on ubuntuguide.org which i will post the exact guide here what i did and what changes i made preferences etc.....

First off we want to View available soundcards...

These comamnds are all done in terminal (obviously)..... 

sudo asoundconf list

this gives a view of all soundcards on your system currently 

you should see if your using the DSP-500 something like this....

Names of available sound cards:
CK8
Headset

CK8 being your onboard soundcard or whatever else it is and Headset is the DSP 500......

now we want to switch over the default soundcard to actually be the dsp-500 so we type....

sudo asoundconf set-default-card Headset

and hit enter....

ok now then we exit terminal as it is no longer necessary.....  Ok After this go to System > Preferences and Sound......  Preferences are as follows....

Sound Events : Sound Playback - AutoDetect  

Music And Movies : Sound Playback -  AutoDetect

Audio Conferencing : Sound PlayBack - Auto Detect       Sound Capture -  Alsa (Advances Linux 
Sound Architecture)

 Default Mixer Tracks : Device - Plantronics Headset (Alsa Mixer) 

Make sure PCM is highlighted after.....  Now then we move onto the sound settings on the speaker icon in the upper right..... Right click the speaker and click preferences..... Select Device and track to control .... Change this to Plantronics Headset (Alsa Mixer) Again make sure PCM  is highlighted.... and then close it... 

Right click the speaker again and open volume control....  File > change device > Plantronics Headset (Alsa Mixer)  in this window edit > preference and make sure these are all selected.... 

Bass , Treble,  PCM , MicroPhone , Auto Gain Control..... dont touch anything in the actual window other then that treble and bass is fine as is muting and unmuting the mic these are your call ultimately.... Now your headset will work properly....

However you will find that the inline control doesnt work. Test this out by playing a few audio files after you are sure the headset is working restarted your computer entirely and boot linux back up.... After this we need to install a program.... Skype (yes you heard me right i said skype..) 

[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

this is the download page for Skype Linux..... now i'm assuming you have 7.04 (feisty fawn...)  Install this (it installs some libraries or some such)  and start it up make up a name log in and make sure your mic works by running a test call with the bot they have setup. After this close Skype and play some audio and try to adjust using your inline volume control or volume control on your keyboard either will work. And Viola hopefully this will of worked for you. This is the same thing i did between last night and today and thats all i did and all is working fine :D.

Hope this helps all those out that are having issue with the Plantronics DSP headsets out there and it should work for stuff other then the DSP 500 as well in the DSP series :)!

---

### Post by John Hughes on 2007-06-22
I must thank my friend lina for helping me sort out my mic etc and her working with me. We helped each other out and t his ended up as the result again i really hope it helps you folks out i know the headset is an awful pain to get working totally!!!

---

### Post by John Hughes on 2007-06-22
Just a heds up if anyone tries this and it succeeds or fails please let me know me and lina have very similar computer setups and this has only been substantiated on our systems so far so i'd like some feedback as to if its working or not working for other people :D!

---

### Post by hppyfngy on 2007-06-26
Darn, I followed you step by step and it did not work for me.  :(

Feisty doesn't like my configuration and I had to go back to Edgy so maybe that's why...

DSP-500s work fine, but will not control volume, nor will my keyboard.  

Thx for the work on it, but does anyone have a fix for old Edgy?  :popcorn:

---

### Post by John Hughes on 2007-07-03
Well thats the problem it works with feisty i dunno about edgy nor do i know if its other games or what have you that i have installed all i know is its definately working on my end :( Its hard to tell what exactly what =/..... I tried it out on 2 computers but we have close to the same stuff installed etc.... I think it will eventually work quite easily with Ubuntu in a few versions or so not sure....

Well good luck :( I hope that stuff works out on edgy :( not sure what the diff could be.

---

### Post by tipsqueal on 2007-07-09
Holy crap man. Thank you, thank you, thank you!!!!!!!!!!!!!

Wow, I've seriously been trying to get my headset working for about a month, not the mic, just the headset. I had it kinda working, GAIM and Exaille would output to it, but what you showed me made the thing fully functional, even the volume control buttons!

Thank you. Seriously this made my day.

---

### Post by John Hughes on 2007-07-12
Well im glad to hear this worked for someone other then me and my friend but also sad that it doesnt work on previous versions of ubuntu.... However at least it is working in fiesty and that is good.

Enjoy :)

---

### Post by Quasimodo316 on 2007-07-13
This worked great for me to (DSP-550).  Even the mic works (if I use oss).  Have you managed to get yours to work with alsa or aoss?  I tried to run Teamspeak with aoss without any results.  Thanks again for the walkthrough though, at least it works one at a time!

---

### Post by John Hughes on 2007-07-15
wtih teamspeak you need to make sure your settings are configured properly...  In options you should see other and type this in the box  /dev/dsp1

I didnt have to fiddle with any other settings other then changing that. and everything worked fine :)!

---

### Post by Hammystyle on 2007-07-21
Thanks a lot John Hughes!!

Everything worked. I was wondering how to get my DSP400 to work under Ubuntu Feisty. All I needed was the command to switch from one card to the other in Terminal. Made a script to switch back and forth.

This is awesome, thanks again!

---

### Post by John Hughes on 2007-07-23
No Problem at all :). The main point of the work around was to get everything fully functioning including the inline volume control which was a major hassle for most people. It really doesnt seem like it would be until you find yourself having to go and manually adjust the volume each and every time.

I am very happy to hear this is working for other people as well as other models in the DSP series its very nice to hear all of this :).

---

### Post by bfallik on 2007-07-29
> **John Hughes said:**
> No Problem at all :). The main point of the work around was to get everything fully functioning including the inline volume control which was a major hassle for most people. It really doesnt seem like it would be until you find yourself having to go and manually adjust the volume each and every time.

I am very happy to hear this is working for other people as well as other models in the DSP series its very nice to hear all of this :).

Anyone get this to work on the DSP-400?  My mic seems completely unresponsive.  i can't get it to record using any method.  Ideas?

---

### Post by John Hughes on 2007-07-30
What exactly are you trying to use your mic in if you tell me that it may help!!!! There are some changes that need to be made in certain programs.... And you need to follow the directions to a T as far as i've seen.... Also as noted previously by posts from other people this only seems to work with 7.04 so make sure  you have that before attempting it..... Aside from that let me know what apps your trying to use the mic in and make sure its not muted in the settings etc :).

---

### Post by jasidog on 2007-08-01
Just wanted to say thanks for the various bits of info in here John. It's all been very useful/helpful. I have a slightly [different model of headset I think]("http://www.amazon.co.uk/Plantronics-Audio-500-USB-semi-open/dp/B000GET9Q6/ref=pd_ys_iyr1/202-2762429-5759048") but the problems were the same. 

The only problem I have now is that I can't have two sound sources at once. So If I'm talking in skype I can't get sound from a youtube video for example or system sounds etc. I know I can get multiple sound sources in windows so I think there must be a way round that. 

If I ever do find that solution I'll report back.

---

### Post by John Hughes on 2007-08-03
Yeah be sure to let me know As I myself would like to know that one as well..... Its fine using a normal soundcard i believe so i think there has to be a way....

---

### Post by evallesg on 2007-11-30
Hi,
Everything seems to work under Gutsy as well, but ... .there's always a but..... sound disappears after 10 seconds, no matter what I'm listening to:mp3, youtube audio or whatever. Any suggestions?
Thanks in advance

---

### Post by John Hughes on 2007-12-01
Hmmm thats a tricky one i havent had that happen to me yet... I've had video screw up but thats about it =/.... Sorry i cant help but maybe someone else knows whats going on!

---

