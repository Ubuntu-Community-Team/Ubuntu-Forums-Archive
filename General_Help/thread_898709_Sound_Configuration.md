---
title: "Sound Configuration"
date: 2008-08-23
forum: General Help
---

### Post by G9M29 on 2008-08-23
Hello all. 
First I think I should say that my true ( mother ) language is not English, so please don't judge me if I have any mistakes.

The real reason I write here is that I can't find help anywhere else but let's start from the beginning. 3 days ago I decided to "take down" the old Windows XP and installed Linux Ubuntu 8.04. I installed a lot of updates and needed programs but form here start the problems.
Today I think about something and decide to make video tutorials on my language. 
1. I start skype and tried to talk with a friend of mine but the problem was that MY MICROPHONE was too quiet ( like the opposite of noise but I don't know how it's written ). My friend was turn his speakers on MAX and the sound was almost zero.

2. Then I start to record my desktop ( on music ) and when I safe the project and start to view it - the sound again was too quiet. 

I've got my CD DRIVE ( Realtec '97 - think so ) but I don't know how to install it. 

Can u tell me the reason and how can I fix this s**t.

[-o<[-o< Please I want to talk freely and made good videos. Please

---

### Post by colobix on 2008-08-23
I too have that problem and havn't solve it yet.
I guess u just have to play around with the volum control settings.

---

### Post by colobix on 2008-08-23
Oh, and your englesk is good btw, but here you have a side that can help you if you want to write in your own language and translate the text automatically into English if you find it more comfortable.
[http://translate.google.com/translate](http://translate.google.com/translate)

Btw, what is your default language?

---

### Post by mb_webguy on 2008-08-23
Type the following command in the terminal:```
sudo apt-get install padevchooser libao-pulse libasound2-plugins libsdl1.2debian-pulseaudio
```

Now go to Applications->Sound & Video->PulseAudio Device Chooser.  This will put a new icon in your notification area in the top left of your screen (assuming you're using the default Gnome setup).  Click on the new icon (which should look something like an audio jack), and select Volume Control.  Click the Input Devices tab, and move the volume sliders up until your microphone volume is loud enough for you.

---

### Post by Dave Otter on 2008-08-23
Right click on Volume control-Speaker Icon on toolbar
   Left click volume control >Edit>preferences
    Tick Mic Boost

 should increase volume of mic

---

### Post by colobix on 2008-08-23
Wow thanks.

---

### Post by G9M29 on 2008-08-24
It still don't work. #-o !. I think about ( for 3 days having linux I can't even try to do something but .. ) what could I do and I know that the answer is there but I just can't find it.

All I can make off was to: 
Please can someone take screenshots of that places ( I mean the configurations u made there ) :

System => Preference => **Sound**
System => Preference => **Volume Control**
Applications => Sound & Video => Pulse Audio Device Chooser => In main toolbar => Click on the icon and in **Volume Control** take a screen.

(* I made all that mb_webguy say but it still f**k with me *)

---

