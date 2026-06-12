---
title: "eeepc 1005 HA ONLY - Microphone on Skype"
date: 2009-11-06
forum: Hardware
---

### Post by suibhne on 2009-11-06
Netbook - Asus eeepc 1005HA.

Karmic working well.

All problems fixed, except the microphone on Skype.

After 5 days, managed to get the sound recorder working (installed backports via synaptic)


But I have no int mic working in Skype.


Has anybody solved this problem yet?

(It has been reported as a bug via launchpad).

---

### Post by Wharf Rat on 2009-11-06
I have the same problem - same machine.

---

### Post by DannyB2 on 2009-11-06
> **suibhne said:**
> Netbook - Asus eeepc 1005HA.

Karmic working well.

All problems fixed, except the microphone on Skype.

After 5 days, managed to get the sound recorder working (installed backports via synaptic)




I am planning to buy a 1005HA-PU1X-BU from Amazon in the next few days.
[http://www.amazon.com/ASUS-1005HA-PU1X-BU-10-1-Inch-Blue-Netbook/dp/B002DYIXMS/ref=wl_it_dp_o?ie=UTF8&coliid=I1F98F1LW8FQ23&colid=3DGHT2L7ROWJZ](http://www.amazon.com/ASUS-1005HA-PU1X-BU-10-1-Inch-Blue-Netbook/dp/B002DYIXMS/ref=wl_it_dp_o?ie=UTF8&coliid=I1F98F1LW8FQ23&colid=3DGHT2L7ROWJZ)

Can you describe what steps you took to install backports or fix any other problems?  Can you describe the nature of any problems you had?  Do you know what specific packages you installed in synaptic?

Last April I put 9.04 on my older Eee Pc 900 and had to install a few backports and select front mic to get any sound.  I never did get good sound in Skype, but the sound "worked".  I could live without Skype, but I'm interested to know of any other problems.

Thank you.

---

### Post by suibhne on 2009-11-10
Reply to Danny D2

Its definitely a good buy. I just had to do some fixes to activate the hot keys etc.

most of what you need is in [this link]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/") (Except the skype instructions didn't work for me)


As for the backports, I can't remember the original way i fixed it, but if you have problems, try [Here]("http://unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala").

As I say, the machine is working great except for the skype problem (I haven't tried it with Ekiga yet)

---

### Post by alcio311 on 2010-01-06
I have same problem:asus 1005 ha with no skype mic.

IN this site [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/comment-page-1/]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/comment-page-1/"), on chapter Sound say:

```
Sound and microphone

The sound works perfectly out of the box. However, the microphone input is set to the microphone jack, rather than the internal mic by default. To change it, open Volume Control, hit Preferences, and enable all the Mic and Input Source options. Then, set the input source to “Int Mic” under the Options tab.

**_In skype, set your Sound In device to be HDA Intel (hw:Intel, 0). (Sound Out and Ringing should be set to ‘pulse’)_**
```

So, at first time skype work too. But after (some update??) in SKYPE SOUND OPTION, HDA Intel (hw:Intel, 0) disappear. Pulse only one!!! 

Does anyone now what it mean??

Sorry I'm italian :P I know english a littele bit, bit bit.;)

---

### Post by mayfer on 2010-01-07
I have solved this issue, I got skype microphone to work on my 1005HA.

Here are the steps:

1) ```
sudo apt-get install padevchooser
```

2) Load up padevchooser from Applications -> Sound & Video -> PulseAudio Device Chooser

3) You should see a PulseAudio applet icon in your notification area. Left click and choose Manager.

4) Go to the Devices tab. Under the Sources section, double click on the line starting with analog_input.

5) A window pops up. Adjust the volume.

6) Click on "Show Volume Meter". If you see any activity from your microphone there, your microphone now works with PulseAudio, and therefore works with Skype.

Cheers!

---

### Post by ScienziatoBestia on 2010-02-10
Hi guys,
I tried your instruction but my  mic  doesn't work too.
Maybe the problem could be due to the fact that there are two kind of asus 1005ha: one with CPU z270 and another with CPU z280 (and probably the audio card is different too).
I think that mic doesn't work on the version with z280: could you confirm this hypothesis? 
I have kubuntu karmic kaola 9.10 
please help me, this is my wife's pc. If mic doesn't work she wants use windows! :D
thanks

---

### Post by ScienziatoBestia on 2010-02-11
Hi guys, thank you but I found the solution for this problem.
For me was sufficient to install the package linux-backports-modules-alsa-karmic-generic and then restart.
bye

---

### Post by weematt on 2010-03-05
New solution:

I had no mic in skype, but it worked fine in sound recorder.  I installed the backports, but it didn't seem to help (at least not immediately).  I installed the pulse audio device chooser, ran it, and finally got skype working by (get this) unlinking the stereo inputs for the mics and setting one (doesn't matter which) to zero and the other to the appropriate volume.  If they are the same level, it seems like they cancel out, but if one is high, the other low, it seems to work for me.

Hope this helps.

Matt

---

### Post by olayak on 2010-03-16
it didn't work for me.  by installing alsa backports, I got my mic working, but I followed your instructions about skype and the mic still doesnt work in skype!

---

### Post by scottro on 2010-03-20
Trying the various solutions, weemat's solution worked for me. 

Many thanks.

---

### Post by maquinadecafe on 2010-03-21
> **weematt said:**
> New solution:

I had no mic in skype, but it worked fine in sound recorder.  I installed the backports, but it didn't seem to help (at least not immediately).  I installed the pulse audio device chooser, ran it, and finally got skype working by (get this) unlinking the stereo inputs for the mics and setting one (doesn't matter which) to zero and the other to the appropriate volume.  If they are the same level, it seems like they cancel out, but if one is high, the other low, it seems to work for me.

Hope this helps.

Matt

Thank you very much !! That worked for me... have been a long time trying to find a working solution and that did it ! Thanks for sharing it !!!
Also...
I have a eeepc 1005ha and also i would like to say here that i fixed the suspend/resume problem.... after suspend/resume i had no wifi, even it didnt detected no wlan to connect to, so i was forced to reboot. Fixed this by installing kernel 2.6.33 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)
Now wifi works fine after a suspend/resume and sound (microphone) works great in skype.
Now everything works well on my eeepc 1005 ha, both in GNOME and KDE 4.3

---

### Post by wizard10000 on 2010-03-21
> **ScienziatoBestia said:**
> Hi guys, thank you but I found the solution for this problem.
For me was sufficient to install the package linux-backports-modules-alsa-karmic-generic and then restart.
bye

This worked for me on a Compaq (HP) Mini 110c netbook but I was told somewhere else to also install pavucontrol and it worked when I installed both, so pavucontrol may not be required.  Didn't hurt anything, though ;)

---

### Post by RastaCalavera on 2010-03-23
> **mayfer said:**
> I have solved this issue, I got skype microphone to work on my 1005HA.

Here are the steps:

1) ```
sudo apt-get install padevchooser
```2) Load up padevchooser from Applications -> Sound & Video -> PulseAudio Device Chooser

3) You should see a PulseAudio applet icon in your notification area. Left click and choose Manager.

4) Go to the Devices tab. Under the Sources section, double click on the line starting with analog_input.

5) A window pops up. Adjust the volume.

6) Click on "Show Volume Meter". If you see any activity from your microphone there, your microphone now works with PulseAudio, and therefore works with Skype.

Cheers!

Hey there! I tried everything you said and I don't even see a analog_input option. I also just tried looking for my mic with normal audio options instead of pulse audio. no luck. I took some screen shots so hopefully they load and you could tell me where i went wrong [IMG]http://i79.photobucket.com/albums/j135/RastaCalavera/device-1.png[/IMG][IMG]http://i79.photobucket.com/albums/j135/RastaCalavera/micissue.png[/IMG][IMG]http://i79.photobucket.com/albums/j135/RastaCalavera/pulseaudio.png[/IMG]
[IMG]http://%3Ca%20href=%22http://s79.photobucket.com/albums/j135/RastaCalavera/?action=view&current=device-1.png%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i79.photobucket.com/albums/j135/RastaCalavera/device-1.png%22%20border=%220%22%20alt=%22ubuntu%22%3E%3C/a%3E[/IMG]  [IMG]http://ubuntuforums.org/%3Ca%20href=%22http://s79.photobucket.com/albums/j135/RastaCalavera/?action=view&current=micissue.png%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i79.photobucket.com/albums/j135/RastaCalavera/micissue.png%22%20border=%220%22%20alt=%22ubuntu%22%3E%3C/a%3E[/IMG] [IMG]http://ubuntuforums.org/%3Ca%20href=%22http://s79.photobucket.com/albums/j135/RastaCalavera/?action=view&current=pulseaudio.png%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i79.photobucket.com/albums/j135/RastaCalavera/pulseaudio.png%22%20border=%220%22%20alt=%22ubuntu%22%3E%3C/a%3E[/IMG]

---

### Post by MadBillyGoat on 2010-03-24
hello, 
I installed the pulse audio app first. It did not work.  Then I installed the backports and bingo....  It worked.  I have no idea if it was one or both of them.  All I know is that it works now with skype...  atleast with the echo test.  Thanks all for the info.

:popcorn:

---

### Post by RastaCalavera on 2010-03-24
How do you install the backports? I couldn't figure out how to locate it synaptic but i downloaded the tr.gz file and extracted it to the desktop. I than ran terminal to sudo install (folder name) and it didn't work. I went through the individual folders to the alsa-update and tried to install that but no luck. Help please total noob!!

---

### Post by suibhne on 2010-05-22
This is now solved for me under 10.04.

Install skype-ubuntu-intrepid_2.1.0.81-1_i386

Install PulseAudio VOlume Control

Go to input tab in PAVC

Move, and lock, the right hand channel to zero.

Make sure you disallow skype in relation to automatic adjusting of volume controls.

Also, if your menu in skype is too dark, there is a setting in the options which allows you to change themes.

---

### Post by dondada on 2010-06-30
Just like weemat and suibhne, drop one of the audio input sliders in pulse audio volume control

I am so freakin' happy that I got this working on my 1005 HAB that I'm ready to go riot in the streets.

---

### Post by bobbb on 2010-07-04
It worked also for me. 

So I used not the initial volume control applet that appears in the top bar, but I tiped pavucontrol, and there, inside input tab, I set the right volume to zero. 

Before, in skype; sound device option, I cancelled the option "allow skype to automatically adjust my mixer levels".

---

### Post by enigmatichus on 2010-10-13
It worked for me, thank you very much!!! I tried everything without success, but now everything works! Thanks again!! :)

---

### Post by osfight.de on 2011-01-20
> **weematt said:**
> New solution:

I had no mic in skype, but it worked fine in sound recorder.  I installed the backports, but it didn't seem to help (at least not immediately).  I installed the pulse audio device chooser, ran it, and finally got skype working by (get this) unlinking the stereo inputs for the mics and setting one (doesn't matter which) to zero and the other to the appropriate volume.  If they are the same level, it seems like they cancel out, but if one is high, the other low, it seems to work for me.

Hope this helps.

Matt

Same situation for me and solution worked! Strange though. 

Thx

---

### Post by sabutuga on 2011-02-10
Hi there,

I'm trying to add the statux.org repository so that I can get the hot keys working properly by installing the packages eeepc-tray and eeepc-laptop-dkm but the repository doesn&#8217;t seem to exist anymore!

Any ideas how to solve this?

---

### Post by shamanccc on 2011-03-10
it worked for me too. thank you guys...

---

### Post by Phelixfil on 2011-03-14
Don't know if this is where I should post this but I'm having a lot of problems with Skype on Ubuntu.  More specifically the mic does not work at all on calls to other computers and sounds like a Dalek on calls to land lines.  I have encountered numerous references to similar problems but from some years back.  I've tried various solutions from these posts but to no avail.  Anyone got any ideas?

---

### Post by tubunu on 2011-09-25
> I installed the pulse audio device chooser, ran it, and finally got skype working by (get this) unlinking the stereo inputs for the mics and setting one (doesn't matter which) to zero and the other to the appropriate volume. If they are the same level, it seems like they cancel out, but if one is high, the other low, it seems to work for me.

This even works for Asus EeePC 1005 PE. THANKS! :)

---

