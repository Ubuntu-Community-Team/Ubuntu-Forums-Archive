---
title: "Speaker volume control and headphones not working"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by jeroach on 2008-01-01
I was on an airplane and decided to watch a movie with my new hp pavillion 2620ca and the headphones didn't work and I couldn't turn the volume off the laptop speakers (they didn't shut off once the headphones were plugged in.

Needless to say, I am not able to use multimedia while I travel until I get this fixed.

Any ideas?

---

### Post by mouseboyx on 2008-01-01
if you goto applications > sound/video > sound recorder > file > volume control > then there should be a tab called switches and there should be a headphone switch.

---

### Post by Casual Fan on 2008-01-01
This may be obvious, but did you right-click on the volume icon in the panel, select "open volume control," and adjust/mute the headphones or speakers?

---

### Post by jeroach on 2008-01-02
Thank you for your replies.  I went in there and there is no headphone switch.  I looked all over the place and I don't see any reference to headphones anywhere at all so I am wonder if this is a hardware issue.  Suggestions?

---

### Post by scamper_22 on 2008-01-02
Hi,

I had a similar issue.

In the case of my laptop the following applied in the volume control

Master volume controls my laptop's internal speakers.
Headphone volume controls the line out.

If I just want to just use the headphone, I have to set the master control to 0% and the headphone volume to whatever (100%)

Try that.

---

### Post by jeroach on 2008-01-02
I am a bit confused - I don't have a headphone volume control.  Are you saying the line out volume control IS my headphone volume control?

Actually, I don't have a Line Out volume control or switch either.  From what I can see, the OS is not recognizing my headphones at all.

---

### Post by scamper_22 on 2008-01-02
hmm, if there is not headphone volume control, then I don't know.

If you go system-preferences-sound what device do you have seledted.
I have the ALSA selected.

Double click the volume control icon.
Click on Edit-preferences
Make sure Master headphone and PCM are checked.  


Then try and adjust the volume.  hopefully they show up.

---

### Post by jeroach on 2008-01-02
I did as you said and I had ALSA as well.  PCM and master are there and checked.  No workee.

---

### Post by JakeSpeare on 2008-01-02
Try adding the volume control to your panel.  That should allow you to configure your headphone settings directly.

---

### Post by jeroach on 2008-01-02
The volume control is in the panel.  That is where I have been looking for everything.  There is no recognition of my headphones at all anywhere on the machine.

---

### Post by JakeSpeare on 2008-01-02
OK, good.  Did you go into preferences and enable Headphone Jack Sense?

Also, if you have more than one audio device listed, you may want to check all to ensure that the headphone is enabled and up on all.

---

### Post by jeroach on 2008-01-03
What is Headphone Jack Sense?  I haven't seen that anywhere in the OS.

---

### Post by jeroach on 2008-01-03
Okay, I am home now and plugged it (headphone jack) into my speakers and this is what I now know: headphones work with volume controlled by both PCM (what does that stand for?) and Master (of course) volume control.  

I still can't get the PC speakers to shut off when the headphones are plugged in which is the problem that would prevent me from using this in a public place.  I also still don't see "headphone" anywhere in the OS.  Is that normal?

Any ideas on how to get my PC speakers turned off without turning off the headphones?  Why would the PC speakers still be on with the headphones plugged in?  I have never seen that before.

---

### Post by Aurora@FleetBuzz on 2008-01-04
The threadstarter's problem is very similar to one that I had encountered and thanks to the timely advice of **ugm6hr**, I went into alsamixer and enabled everything, maxed it out.  I not only have my headphones and microphone working, it works independent of the external speakers.  The key was enabling "sigmatel" in altamixer.  Don't know if this will work for you, but give it a shot.  Here's the thread I started earlier and **ugm6hr's** comments.

[http://ubuntuforums.org/showthread.php?p=4073942#post4073942](http://ubuntuforums.org/showthread.php?p=4073942#post4073942)

---

### Post by jeroach on 2008-01-04
Excellent!  Thank you.  But what is alsamixer and how do I find it?

---

### Post by Aurora@FleetBuzz on 2008-01-05
I'm just a recent convert, but alsamixer appears to allow one to manipulate the sound card settings.  Just open a terminal and type "alsamixer" at a terminal.  You get a program that appears to be a throwback to the old MS DOS days.  It looks like a vertical bar chart.  Each of those bars controls a different function.  Just follow** ugm6hr's** instructions on the thread I linked earlier and you'll be able to manipulate the controls.  It's actually very easy, but make sure you keep a running record of the changes you make.  You may have to restore it back to the original if you screw something up.  Nonetheless, I was amazed at how easy this was.

Good luck.  Let us know if you succeed.

---

### Post by jeroach on 2008-01-05
Okay, I tried that and now I have no audio at all and any program I run, such as amarok, that requires audio freaks out and then crashes.

---

### Post by Aurora@FleetBuzz on 2008-01-05
I suggest that you restore the alsamixer settings to the original configuration and re-boot.  You should at least be back to where you were.

---

### Post by Yellow Pasque on 2008-01-05
Hi. Would someone who has this problem like to volunteer and try the OSSv4 sound system to see if that fixes the problem? Follow the link in my sig. I believe once you get it running, you can control the headphone jack/volume independently of the external speakers with ossxmix.

---

### Post by jeroach on 2008-01-05
So I should install that program, Ossv4, to fix my problem?  Where do I get it?

---

### Post by Yellow Pasque on 2008-01-05
> **jeroach said:**
> So I should install that program, Ossv4, to fix my problem?  Where do I get it?
Click the first link in my signature.

---

### Post by jeroach on 2008-01-06
Well, right off the bat, I don't know what I am looking for here [http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html) (I have an AMD Turion 64 but running ubuntu 32)

---

### Post by Yellow Pasque on 2008-01-06
It looks like you have nvidia high-def audio on geforce 7150M (MCP67). This device is supported with the generic hdaudio module, so proceed with installation. (To be sure of your audio, you can run the following and look for the name of the audio controller):
```
sudo update-pciids
sudo lspci
```

---

### Post by jeroach on 2008-01-06
I found the name of the audio controller but where do I find the device number?  What is ossinfo and where does it tell me the device number?

I ran through these hoops and the first time the deb extracted fine but the sudo soundon produced errors.  Now I am back in the full OS and I don'\t understand what these instructions are telling me to do.  Sound is working through both my headphones and speakers but I am back to the beginning with no control over either.

Nowhere in these instructions can I find out what OSS even IS.  Is it a software program?  A device driver?  What am I even looking for?

---

### Post by Yellow Pasque on 2008-01-06
> Nowhere in these instructions can I find out what OSS even IS. Is it a software program? A device driver? It's a sound system (OSS stands for open sound system), which means it includes drivers and the interface/API developers use to write software for it.

> but the sudo soundon produced errors
Do you remember the error?

> Sound is working through both my headphones and speakers but I am back to the beginning with no control over either.
You need to control the volume with a program called ossxmix. In the terminal, type ossinfo. Now you'll see a section called mixer devices and the device(s) are numbered. Choose the number of the device you want to control. That's the number you want (probably 0). Now you can run ossxmix -d<that number> in the terminal. If you don't want to type a command in the terminal each time you want to change the volume, add an application launcher to your panel...

Here's how to replace your current volume/speaker icon with the correct one:
Remove your current volume icon from the panel. (Right click it for that option)
Then right click on the empty space left behind and select "Add to Panel"
Click the button that says custom app launcher.
In the command field, type ossxmix -d<mixer number>
Select whatever name and icon you want (I use /usr/share/icons/gnome/32x32/status/stock_volume-max.png for the icon and "Mixer" for the name)
And, of course, hit OK.

I guess the part about the mixer was a bit confusing, though no one else seemed to have a problem with it.

> What am I even looking for?
I don't understand what you're asking here.

---

### Post by jeroach on 2008-01-07
Your responses are helpful and thank you for sticking with me on this.  Here's where I am at currently:

1.  I don't remember the eerror but I can't reproduce it by following the steps from the beginning.  Invalid somethingorother.  If I could have copied and pasted from the failsafe terminal, I would have.
2. ossxmix in terminal produces: No device root node
3. ossinfo in terminal produces the following:
Version info:   (0x00000000) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 (jeff-laptop)

Number of audio devices:        0
Number of audio engines:        0
Number of mixer devices:        0


Device objects


Mixer devices

Audio devices

So, as you can see, there is no device number for me to use so I haven't gotten any further in your instructions to play with headphone control or panel icons.

---

