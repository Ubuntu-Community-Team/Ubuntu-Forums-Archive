---
title: "Skype problem with audio playback 8.10"
date: 2008-10-26
forum: General Help
---

### Post by josemaster2228 on 2008-10-26
Hi everyone just upgraded to 8.10 FTW:guitar:
well i have this problem I installed Skype and when i start skype up there is no login sound and when i try to call someone it tells me that there is a problem with audio playback and i need skype to work because i need to help him upgrade to 8.10 anyone know the answer i have moved and try every setting in the skype settings but nothing i have tried to move the ALSA mixer around but nothing and skype is the only thing that dosen't work cheers not sure if i will have to downgrade:confused:

---

### Post by genlies on 2008-10-28
go to the sound devices setting,select the sound device for sound in,sound out and ringing.
I selected the device "HDA intel(hw:intel,0)",then skype can working. But the sound out is mono.

---

### Post by thegrimgod on 2008-11-01
Good post genlies. Same problem tho with mono sound. Here is my audio device
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by thegrimgod on 2008-11-01
Well, I just uninstalled pulse audio, and used the default device settings, and everything works :D. Hope it helps u guys too.

---

### Post by splint-84 on 2008-11-02
Removing the package pulseaudio also did the trick for me. For any new users the command to use is:

sudo apt-get remove pulseaudio

and then restart skype and it worked straight away :)

----------------------EDIT-----------------------------------

As myself and other users discovered this is NOT a good idea. If you do this you probably won't be able to log in to Ubuntu after. If you have experienced this problem you can fix it by hitting CTRL+ALT+F5 - type your login and pass and reinstall pulse audio by entering:

sudo apt-get install pulseaudio

hitting enter and then flick back to your normal login screen by using CTRL+ALT+F7.

Like krazykookmany setting the devices under skype to use pulse is a much better idea, and also fixed my problem... Without breaking my OS.

---

### Post by bigoten on 2008-11-02
I confirm: removing pulseaudio DOES work.
Good job!:guitar:

---

### Post by seeklinux on 2008-11-02
While uninstalling Pulse Audio will probably in most cases fix the problem, I wanted to avoid that. By going into the Skype **Options** and clicking on **Sound Devices** and changing the settings, I was able to get the test call working.  This is what I ended up setting:
[LIST]
[*]Sound In: HDA Intel (hw:Intel, 0)
[*]Sound Out: HDA Intel (plughw:Intel, 0)
[*]Ringing: HDA Intel (plughw, Intel, 0)
[/LIST]
So basically I had to experiment with the possible choices. I not totally sure about the Ringing (not sure if that is utilized on the Test Call or not).

Note that I am using a regular headset I plug in to the sound and mic jacks. I am using a Thinkpad.

---

### Post by rhenium3 on 2008-11-02
I removed pulseaudio successfully, but then ubuntu (8.10) would not load, saying it couldn't find the pulse audio file (duh).  I tried to reinstall it, and did the skype settings above, but that did not work...

Any ideas?

---

### Post by krazykookmany on 2008-11-02
//

---

### Post by rhenium3 on 2008-11-02
Thank you KrazyKookmany, that worked!  At least the mic is working now... the sound is still a bit choppy when I hear skype speak, but I suppose I should just mess with the volume settings?

---

### Post by wildrabbit on 2008-11-02
None of the above did work for me but **reinstalling** pulseaudio worked.

sudo apt-get remove pulseaudio
sudo apt-get install pulseaudio

All settings in skype are set to pulse (in audio tab)

---

### Post by krazykookmany on 2008-11-02
//

---

### Post by krazykookmany on 2008-11-02
//

---

### Post by Bott on 2008-11-02
> **rhenium3 said:**
> I removed pulseaudio successfully, but then ubuntu (8.10) would not load, saying it couldn't find the pulse audio file (duh).  I tried to reinstall it, and did the skype settings above, but that did not work...

Any ideas?

[http://ubuntuforums.org/showthread.php?t=963914&highlight=Remove+Pulseaudio](http://ubuntuforums.org/showthread.php?t=963914&highlight=Remove+Pulseaudio) is a thread that gives a fix for that.  To summarize:

> killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo Nautilus

and then browse and remove "/etc/X11/Xsession.d/70pulseaudio"

---

### Post by pepik on 2008-11-02
I'm having this issue too, on a Sony Vaio laptop. Removing and then reinstalling pulseaudio did nothing, changing all these various settings seemed to allow me to make calls but the mic didn't work.

Seems like there is a real issue here with Skype and Ubuntu 8.10.

---

### Post by rhenium3 on 2008-11-02
> **Bott said:**
> [http://ubuntuforums.org/showthread.php?t=963914&highlight=Remove+Pulseaudio](http://ubuntuforums.org/showthread.php?t=963914&highlight=Remove+Pulseaudio) is a thread that gives a fix for that.  To summarize:



and then browse and remove "/etc/X11/Xsession.d/70pulseaudio"

Great, did this, set up skype settings to HDA Intel 0 and it works and is not so choppy.  No problems restarting either, thanks!

---

### Post by asdir on 2008-11-12
I had the same problem as the others and for sounds and output setting the config to "pulse" worked.

As for the input I had to sound settings and under "options" had to set one of the input sources to "front mic" which is the only mic working on my computer. It seems that after an update Ubuntu did not recognize my front mic. This might be because it was not plugged in at that time and my mic-port can also be used as an out-port.

Hope that helped someone.

---

### Post by Uncle Che on 2008-11-15
I tried anything and everything and the only thing that worked was removing pulseaudio and installing esound. I am looking for another fix, but this is at least letting my Skype work.

---

### Post by oonska on 2008-11-15
[http://mattions.wordpress.com/2008/11/09/skype-and-ubuntu-810/](http://mattions.wordpress.com/2008/11/09/skype-and-ubuntu-810/)

This post here solved my audio out problem, and I hope it'll help others too.

---

### Post by frigaut on 2008-11-19
Indeed using apt-get remove pulseaudio will mess up your X session and you will not be able to log in. This is because -and that's a bug- /etc/X11/Xsession.d/70pulseaudio is left after the remove, being somehow considered as a config file. It is not.

However, doing a 

sudo apt-get purge pulseaudio

which means remove, including all config files, works well and remove 70pulseaudio too (and a bunch of other pulseaudio config files).
In general, it is not a good idea to remove files from underneath the package manager. Although in that case, I could be safe to do what you advertise.

Everything works well without pulseaudio. What I wonder is: pulseaudio being in the regular 8.10 release, is that needed for some other functionalities? aren't we shooting ourselves in the foot by removing this package?

---

### Post by wakaru on 2008-11-19
> **krazykookmany said:**
> Here's what I did:

Sound In: Intel ICH6 (hw:ICH6,0) (it's under pulse)
Sound Out: Pulse
Ringer: Pulse

it all works fine for me without getting rid of Pulseaudio

perfect solution!!!

thank you

---

### Post by frigaut on 2008-11-19
yes, it did too for me until I got problems with:
1) other applications interfering (banshee, vlc)
2) no sound after suspend/hibernate

but there seems to be alternative solutions around, like installing skype static. For me, removing pulseaudio altogether seem to have done the trick (with apt-get purge). But as I said earlier, I'm not sure what consequences I might have overlooked.

---

### Post by Tmi on 2008-11-20
I can also confirm that purging pulseaudio and installing esound worked for me. Now I can finally use skype again.

---

### Post by dj620129 on 2008-11-21
> **Bott said:**
> [http://ubuntuforums.org/showthread.php?t=963914&highlight=Remove+Pulseaudio](http://ubuntuforums.org/showthread.php?t=963914&highlight=Remove+Pulseaudio) is a thread that gives a fix for that.  To summarize:

and then browse and remove "/etc/X11/Xsession.d/70pulseaudio"

I am using Ubuntu 8.10 on Thinkpad X60.

I did the above and then in Multimedia System Configuration, I selected ALSA for output and input, and in Skype I selected default for in, out, and call.

It works fine.
I restart Skype, it works
I reboot, it works fine.

But, I wonder what pulseaudio is for?

Anyway, I hope you all can fix the Skype problems following what I did.

---

### Post by nwstephens on 2008-11-21
> **krazykookmany said:**
> Here's what I did:

Sound In: Intel ICH6 (hw:ICH6,0) (it's under pulse)
Sound Out: Pulse
Ringer: Pulse

it all works fine for me without getting rid of Pulseaudio

The following configuration worked for my Logitech QuickCam Pro 9000 on my old Dell Dimension 3000.  The audio and video both work great.

Sound In: USB Device 0x46d:0x900 (hw:U0x46d0x990,0)
Sound Out: Pulse
Ringer: Pulse

After setting both "sound out" and "ringer" to pulse, I played around with the "sound in" until it worked.

---

### Post by JustBCoz on 2008-12-02
* Sound In: HDA Intel (hw:Nvidia, 0)
    * Sound Out: HDA Intel (plughw:Nvidia, 0)
    * Ringing: HDA Intel (plughw, Nvidia, 0)

THIS WORKED FOR ME

Removing Pulseaudio was a bad idea, It crashed X.

---

### Post by raulricardo21 on 2008-12-07
> **wakaru said:**
> perfect solution!!!

thank you

Same for me...

Esta solución si me gustó, aunque previamente me todo

sudo aptitude remove pulseaudio
sudo aptitude install pulseaudio ubuntu-desktop

I like this solution because keep the structure of my system

---

### Post by lordnino on 2008-12-12
in ubuntu 8.10, System - Preferences - Sound - Devices - Audo Conferencing: Test your sound playback & Sound capture(Mic). Use Other if ever test failed. If everything works fine, Go to Skype - Options - Sound Devices: try to set Sound in,Sound Out,Ringing to "pulse" setup. Try "Make a test sound" . If heared sound then try "Make a test call". if ok. apply the exit!!

---

### Post by ComputekPR on 2008-12-13
> **krazykookmany said:**
> Here's what I did:

Sound In: Intel ICH6 (hw:ICH6,0) (it's under pulse)
Sound Out: Pulse
Ringer: Pulse

it all works fine for me without getting rid of Pulseaudio

This work for me Thanks......:guitar:

---

### Post by patond on 2008-12-13
Hi. I solved this by going to Options within Skype (or CTRL O) and selecting Sound Devices.  Sound In, Sound Out and Ringing are all set to pulse by default - or it was for me.  You need to know what your sound card is.  Mine is Intel IHCH5 - I set them all to Intel ICH5 and this made Skype Test Call work properly.  In ALSA Mixer it may also help to set MIC Boost.

---

### Post by oyejorge on 2008-12-14
I tried a number of things and settled on just dumping pulseaudio. 
```
killall pulseaudio
```
**Note** Don't run this command when Rhythmbox or other sound applications are running, they could crash.

I didn't want to uninstall pulseaudio though because of the reboot/configuration issues so I just run this each time I start my computer. You can automatically do this by adding the command to session startup programs

System > Preferences > Sessions > Startup Programs (tab) > Add

It's a bit of a hack, but it's working.

---

### Post by TheSnowSnake on 2008-12-18
> **krazykookmany said:**
> Here's what I did:

Sound In: Intel ICH6 (hw:ICH6,0) (it's under pulse)
Sound Out: Pulse
Ringer: Pulse

it all works fine for me without getting rid of Pulseaudio

Good start but I had to add mike boost before it was usable now is good.
 Open your volume control (upper right) then click preferences add Mic Boost 20 db switch then turn it on in the switch panel ....You should be good to go.


Also I turned off allow skype to adjust mixer levels..

---

### Post by jamesisin on 2008-12-25
This page will walk you through correctly setting up PulseAudio in both 8.04 and 8.10.  There is no reason to remove it.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Once you have gone through the steps outlined on this page your PA will fuction as promised (multiple volume mixing and simultanious sound device connections).  You will see that many applications will need their preferences/options tweeked to point toward PA and away from ALSA or OSS.  This is because more than one application cannot access an audio device at any given moment.  PA provides a layer in which audio is combined before PA then accesses the audio device.

That being said, I am having troubles with Totem not using PA.  So if anyone can offer a post where that is discussed I'd be most appreciative.

---

### Post by njdube on 2008-12-25
One solution that I found worked for me was to install the skype-static-oss package replacing the skype package.  I didn't have to fool with any other settings or configuration.

I used this repo... [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

---

### Post by hominoid on 2009-01-03
The following posting talks about an alternate solution:
[http://tips4nongeeks.blogspot.com/2009/01/skype-sound-problem-in-ubuntu.html](http://tips4nongeeks.blogspot.com/2009/01/skype-sound-problem-in-ubuntu.html)

---

### Post by jamesisin on 2009-01-03
> **hominoid said:**
> The following posting talks about an alternate solution:
[http://tips4nongeeks.blogspot.com/2009/01/skype-sound-problem-in-ubuntu.html](http://tips4nongeeks.blogspot.com/2009/01/skype-sound-problem-in-ubuntu.html)

Did you find these instructions useful?

I just don't see how "Pick the right devices for 'Sound In', 'Sound Out' and 'Ringing'" is going to be very helpful.

I downloaded the package directly from Skype (Debian version) and allowed the package installer to do its thing.  The only other help I needed was to follow the definitive guide (created by a mod here) I posted to above.

I recommend that guide as your first step in getting your PulseAudio working properly.  (It includes a section on configuring Skype correctly.)

---

### Post by rkouere on 2009-01-10
Hi all

I have just discovered why I didn't seem to be able to have my mic working when trying to call with Skype. For some reason, skype was turning down the volume of my Alsa capture settings when I was trying to call. 

I managed to fix it by unclicking the option "Allow Skype to automatically adjust my mixer levels" under the Sound Devices opion in Skype. I then chose the pulse drivers for Sound in and Sound out and, voila! It works fine.

I hope this works.

---

### Post by Sauli on 2009-01-16
By setting the Skype Sound Devices options Sound In, Sound Out and Ringing as advised by several posts did help to make the Skype Test Call but not real Skype calls. In my case the killall pulseaudio did not solve the problem either.

Finally I followed Jamesisin's advice and the instructions on [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) and this did solve the problem. Thanks.

Sauli

---

### Post by jamesisin on 2009-01-16
Glad to be of service, if only as a signpost.

---

### Post by salinon on 2009-01-22
> **krazykookmany said:**
> Here's what I did:

Sound In: Intel ICH6 (hw:ICH6,0) (it's under pulse)
Sound Out: Pulse
Ringer: Pulse

it all works fine for me without getting rid of Pulseaudio
thanks krazykookmany, worked perfectly.
I used pulse for all 3 options.

---

### Post by m4lte on 2009-01-30
I got things working using

Sound In: HDA Intel (hw:intel,0)
Sound Out: Pulse
Ringer: Pulse

In the Ubuntu Sound Preferences everything is set to autodetect except for Sound capture, which I set to "HDA Intel CONEXANT Analog (ALSA)".
The Default Mixer Track Device is "HDA Intel (Alsa mixer)"

---

### Post by rahaman.naik on 2009-02-08
> **genlies said:**
> go to the sound devices setting,select the sound device for sound in,sound out and ringing.
I selected the device "HDA intel(hw:intel,0)",then skype can working. But the sound out is mono.
Hi geniles,
       Your solution worked out ... i can speak and hear the sound .. :). Thank you

---

### Post by juansho on 2009-02-14
> **oyejorge said:**
> I tried a number of things and settled on just dumping pulseaudio. 
```
killall pulseaudio
```
**Note** Don't run this command when Rhythmbox or other sound applications are running, they could crash.

I didn't want to uninstall pulseaudio though because of the reboot/configuration issues so I just run this each time I start my computer. You can automatically do this by adding the command to session startup programs

System > Preferences > Sessions > Startup Programs (tab) > Add

It's a bit of a hack, but it's working.


YEAHH, this work fine in my DELL inspiron1420.
```

killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio 
```

in volume control check (input source:mic)
in skype sound device: (default)

Thanks for the ideas

---

### Post by cmay on 2009-02-14
i have installed the ubuntu studio kernel on intrepid ibex since i use my computer for audio recording. its a laptop i just got  and i had the same problem with skype. si what i diod to make it work was i have a lot of apps and mixers for making music.

 i just used the alsa mixer and used alsa for skype. i got tired of the really low sound in my skype headset and the constant tuning and swithing sound devise in prefernece to use skype on this laptop so i uninstalled it and use my little asus eeepc instead.  

my point is that i think it should be possible to use alsa for this instead of removing pulseaudio . you can finetune the audio input to use alsa for audio conference in audio settings like i did. its just very annoying for me to do since i have to work with to many devises and mixer settings. i would however really like to know what  others think about this soulution and if there is something more easy i would like to try installing skype on my laptop again maybe.

---

### Post by Peewee58 on 2009-02-15
First of all, I would like to thank everyone for the info. I'm a first time user & now a firm believer in Unbutu (8.10). I'll never go back to that Windows garbage again. I'm still learning how to drive this OS.

I have a Optima Laptop with AMD Sempron 2600. A good ol' girl. It has a little known MoBo from 'Uniwell'

My settings for Skype to work are-
Sound In - Pulse
Sound Out- Pulse
Ringing- Pulse.

Now all I have to do is to figure out how to get the video to work.

Again, many thanks to all.
Peewee58

---

### Post by donmatas on 2009-02-16
> **krazykookmany said:**
> Here's what I did:

Sound In: Intel ICH6 (hw:ICH6,0) (it's under pulse)
Sound Out: Pulse
Ringer: Pulse

it all works fine for me without getting rid of Pulseaudio

I use this settings and it works:

Sound In: Intel ICH6 (hw:Intel,0)
Sound Out: Pulse
Ringer: Pulse

---

### Post by suaf on 2009-02-19
Well, I tried many things and put everything on default and it works when I turn the Skype on BEFORE the music player (I'm using AMAROK, but it also makes problems with my video payer and some other applications). When I turn on FIRST the audio player and then the Skype, the audio works, and the Skype makes trouble. This makes me think that the problem is in the very Skype, and not in the Ubuntu or something else. Any suggestions?

---

### Post by xjgnsdof on 2009-02-20
I got it to work on [my laptop]("https://wiki.ubuntu.com/LaptopTestingTeam/MSIPR200") by setting everything to "pulse."

---

### Post by KimJarvis on 2009-03-02
I can play the test sound by setting to pulse as described.

Sound in HDA Intel(plughw:Intel,6)
Sound out pulse
Ringing pulse

However, I cannot fix the microphone problem. Skype seems to set the capture audio off in the Alsa mixer.  That is, after starting skype the capture slider in the Recordings tab of the ALSA mixer is at the bottom and there is an X over the microphone icon.

Starting skype in a terminal produces the following errors:

ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)

---

### Post by rkarthik on 2009-03-02
It worked for me with the following setting, without removing pulse..

Sound In: HDA Intel (hw:Intel,0)
Sound Out: pulse
Ringing: pulse

---

### Post by Digrgrl on 2009-03-08
Hello!

I JUST got Ubuntu last night and am trying to figure out how to get skype to work, as I use it just about every day and would really like to get it up and running ASAP. 

I have tried removing pulseaudio and installing esound. That didn't work.

I've fiddled with the Skype Options, that didn't work.

I've currently got things set to:
[B]Sound In: Pulse
Sound Out: Pulse
Ringer: Pulse [/B]
And I can hear but not speak via skype. I cannot seem to find the "HDA Intel (hw:intel,0)" option for my "Sound In." Any suggestions?

(Also, would LOVE help on how to get an Acer Extensa 4420 Crystal Eye webcam to work!)

Thanks!

---

### Post by ProNux on 2009-03-08
> **Digrgrl said:**
> Hello!

I JUST got Ubuntu last night and am trying to figure out how to get skype to work, as I use it just about every day and would really like to get it up and running ASAP. 

I have tried removing pulseaudio and installing esound. That didn't work.

I've fiddled with the Skype Options, that didn't work.

I've currently got things set to:
[B]Sound In: Pulse
Sound Out: Pulse
Ringer: Pulse [/B]
And I can hear but not speak via skype. I cannot seem to find the "HDA Intel (hw:intel,0)" option for my "Sound In." Any suggestions?

(Also, would LOVE help on how to get an Acer Extensa 4420 Crystal Eye webcam to work!)

Thanks!

Maybe you can check the installation/configuration of your PulseAudio here.
Also try other combinations from the Sound Devices in Skype.  You may refer to the first few posts of this thread.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

About your Acer camera, is it Skype that you want it to get working?  I am using Acer 4710 with a Suyin camera with Ubuntu 8.04.

Try installing the following.

libjasper1
libjasper-dev
libjasper-runtime

Good luck.

---

### Post by Digrgrl on 2009-03-08
Just got the camera working! (I have no idea how, but I reinstalled Cheese and all of a sudden Skype and Cheese liked it!)

I think my microphone is working but VERY faintly. It seems like installing medibuntu could do the trick, but I'm tried doing that and got a little scared by the intense amount of coding involved. Is there an easier way to do that? Would it even help my problem?

Thanks!

---

### Post by ProNux on 2009-03-09
> **Digrgrl said:**
> Just got the camera working! (I have no idea how, but I reinstalled Cheese and all of a sudden Skype and Cheese liked it!)

I think my microphone is working but VERY faintly. It seems like installing medibuntu could do the trick, but I'm tried doing that and got a little scared by the intense amount of coding involved. Is there an easier way to do that? Would it even help my problem?

Thanks!

Have you checked the MIC volume level?  You can double-click the Volume Icon on your panel.  Check also the OPTIONS Tab to select what Mic will you use - Front Mic (built-in mic) or Mic (External mic)...

By the way, I am on Hardy, might be a little different on Intrepid.

---

### Post by skumar25dec on 2009-03-11
Hi,

I used the following setting and it works for me.

Sound in: HDA ATI SB(hw;SB,0)
Sound out: pulse
Ringing: pulse

I am using AMD64.

Thanks,
Sumit.

---

### Post by listerdl on 2009-03-15
Hi I got it to work by trial and error and i got lucky...

I am running Dell Inspiron 6400 if anyone is using that, (factory settings - interpid ibex though)...

Sound in: HDA Intel (hw:Intel,0)
Sound Out: HDA Intel (hw:Intel,0)
Ringing: HDA Intel (hw:Intel,0)

---

### Post by vatsakatta on 2009-03-18
Well no need to remove pulse audio, this is what i did to make it work.

Go to skype "Options" (Ctrl + O) -> try out different options given for sound in/out

(for me setting both in and out to 'pulse' did a trick)

Do test it using the "test sound" feature it does work.

Cheers!!
Katta

---

### Post by black drongo on 2009-03-19
hi 
 i had the same problem.
setting that works
in sound preferences,(system>preferences>sound)
everything is set to alsa mixer
then in skype sound settings
sound in    Intel 8280 1 DB-ICH4 (hw;I82801DBCH4,0)
sound out   Intel 8280 1 DB-ICH4 (hw;I82801DBCH4,0)
ringing     Intel 8280 1 DB-ICH4 (hw;I82801DBCH4,0)

setting everything to pulse, including skype settings, my mic was not working

---

### Post by kennedyjch on 2009-03-25
I had no problems until my daughter started using audio applications and when I switched back to my session, Skype no longer functioned. However specifying the outputs go to pulse seemed to do the trick!

---

### Post by zabudarda on 2009-03-25
i got it working without removing pulse audio by skype setting 
sound in - HDA Intel(hw:intel,o), 
sound out - pulse 
ringing - pulse

---

### Post by oserdavid on 2009-03-28
sound in - HDA Intel(hw:intel,o),
sound out - pulse
ringing - pulse 

Also exactly as above, with Ubuntu 9.04 Beta (Jaunty) but after following the advice given here:

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

Works a treat... (the advice also cured my Flash sound problem - which re-emerged after I upgraded).

So now no need to remove Pulse - as I had previously done.
David

---

### Post by cybermaniack on 2009-03-30
I had the same problem. I sovle this by selecting "pulse" in skype-> options->sound devices.

---

### Post by kurotsuno on 2009-04-05
Ok I've read all of the posts in this topic and they are all over the place. I have tried changing pulse audio settings none of which have done the trick I've tried removing pulseaudio which worked for a bit. The major problem here and the one I can't see a single person even explain is why the audio seems to disappear. 

I've removed the pulse audio installed esound it worked but the mic suddenly stops working. 

So would someone please list the definite fix for this issue. I use skype a lot and so far I've had to keep booted in vista till I get this issue resolved. I would rather be on ubuntu but this problem is forcing me onto windows vista.

I'm on a Acer aspire 5052 with a AMD 64bit processor and ubuntu 8.10 32bit

---

### Post by frigaut on 2009-04-05
The definitive fix for this issue: have skype bebuild their software against the latest versions of pulse, ESD, etc.. the latest skype for linux has been released, what, a year ago, or more. That's 2 version of ubuntu ago. And pulseaudio was much less mature than now.
Of course, even better would be to have a open source skype (and no, I'm not talking ekiga here).

---

### Post by jamesisin on 2009-04-05
kurotsuno - I repeat:

This page will walk you through correctly setting up PulseAudio in both 8.04 and 8.10. There is no reason to remove it.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Once you have gone through the steps outlined on this page your PA will fuction as promised (multiple volume mixing and simultanious sound device connections). You will see that many applications will need their preferences/options tweeked to point toward PA and away from ALSA or OSS. This is because more than one application cannot access an audio device at any given moment. PA provides a layer in which audio is combined before PA then accesses the audio device.

---

### Post by hobo14 on 2009-05-10
> **oserdavid said:**
> sound in - HDA Intel(hw:intel,o),
sound out - pulse
ringing - pulse 

Also exactly as above, with Ubuntu 9.04 Beta (Jaunty) but after following the advice given here:

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

David

+1 in 9.04 and in 8.10, _without_ following the advice in the link.
All I did was change the settings in Skype, didn't install any packages, and have never installed those packages.
Skype sound is now fine.

EDIT: my Skype is 2.0.0.72-1 from medibuntu intrepid repos.

---

### Post by mr. udang on 2009-05-31
I had the same problem twice. First time I changed my Options->Sound Devices setting to this and it worked: Sound In: plughw:Intel,0  Sound Out: plughw:Intel,0 Ringing: plughw:Intel,0  Then a few days later the problem came back, now my setting is this and it works: Sound In: hw:Intel,0  Sound Out: pulse Ringing: pulse  I use Ubuntu 9. HP Pavilion dv6000 laptop.

---

### Post by epidemiks on 2009-06-02
sound in - HDA Intel(hw:intel,o)
sound out - pulse
ringing - pulse 

worked a charm in 8.10

---

### Post by kditty on 2009-06-29
> **krazykookmany said:**
> Here's what I did:

Sound In: Intel ICH6 (hw:ICH6,0) (it's under pulse)
Sound Out: Pulse
Ringer: Pulse

it all works fine for me without getting rid of Pulseaudio


this worked well for me. i had to experiment with preferences in the audio menu (line in, line out, headphone jack etc.) ICH5 for me but used same exact setting and it worked.

THANK YOU!

---

### Post by ken5 on 2009-07-09
worked for me as well... thanks to you krazykookmany!

---

### Post by prsinghdua on 2009-07-15
> **seeklinux said:**
> While uninstalling Pulse Audio will probably in most cases fix the problem, I wanted to avoid that. By going into the Skype **Options** and clicking on **Sound Devices** and changing the settings, I was able to get the test call working.  This is what I ended up setting:
[LIST]
[*]Sound In: HDA Intel (hw:Intel, 0)
[*]Sound Out: HDA Intel (plughw:Intel, 0)
[*]Ringing: HDA Intel (plughw, Intel, 0)
[/LIST]
So basically I had to experiment with the possible choices. I not totally sure about the Ringing (not sure if that is utilized on the Test Call or not).

Note that I am using a regular headset I plug in to the sound and mic jacks. I am using a Thinkpad.
Thanks! This thing now also works flawlessly in 9.04!:guitar:

---

### Post by wagaboy on 2009-07-16
> **wildrabbit said:**
> None of the above did work for me but **reinstalling** pulseaudio worked.

sudo apt-get remove pulseaudio
sudo apt-get install pulseaudio

All settings in skype are set to pulse (in audio tab)

This partially did the trick for me. It fixed audio in. In fact, I am able to hear on both the speakers. 
Audio out wasn't working by setting it to 'pulse'. So I changed to 'SiS Sl7012  (hw:Sl7012,0)' and everything works fine now !

---

### Post by ssk.green on 2009-07-18
hey thanks man !

---

### Post by ssk.green on 2009-07-18
thanks:popcorn:

---

### Post by the mighty windle on 2009-07-18
I found I had the same Skype audio playback error with **i386 Ubuntu 8.04** and managed to solve it like this:

**STEP 1:** Download skype-common and skype-static packages from the Medibuntu Repositories
```

$ wget http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu1.1_all.deb http://packages.medibuntu.org/pool/non-free/s/skype/skype-static_2.0.0.72-0medibuntu1.1_i386.deb 
```
**STEP 2:** Install the downloaded packages
```

$ sudo dpkg -i ./"skype-common_2.0.0.72-0medibuntu1.1_all.deb" ./"skype-static_2.0.0.72-0medibuntu1.1_i386.deb" 
```
**STEP 3:** Finally install alsa-firmware package and configure sound
```

$ sudo apt-get install alsa-firmware 
```
Make sure that all the Skype audio options are set to default (Main Menu > Options > Sound Devices) and Open volume control (double click the speaker icon on the top panel) and click on File > Change device. Make sure the Alsa mixer is selected and try the Skype test call. 

This worked for me and I hope this is of help to someone :D

---

### Post by shiva.n on 2009-07-27
Yes works perfectly. After trying several tweaks including configuring .asoundrc, I finally had the longest conversation on Skype 2:40hours yesterday with no video or audio issues. 
 
I havent tried how Skype behaves while running other audio applications. 
 
Wondering if last weeks pulseaudo fixes, fixed something?
 
Edit: Im on Jaunty on DELL Inspiron 6400

---

### Post by Professoryk on 2009-08-09
> **splint-84 said:**
> Removing the package pulseaudio also did the trick for me. For any new users the command to use is:

sudo apt-get remove pulseaudio

and then restart skype and it worked straight away :)

----------------------EDIT-----------------------------------

As myself and other users discovered this is NOT a good idea. If you do this you probably won't be able to log in to Ubuntu after. If you have experienced this problem you can fix it by hitting CTRL+ALT+F5 - type your login and pass and reinstall pulse audio by entering:

sudo apt-get install pulseaudio

hitting enter and then flick back to your normal login screen by using CTRL+ALT+F7.

Like krazykookmany setting the devices under skype to use pulse is a much better idea, and also fixed my problem... Without breaking my OS.

Thank you [splint-84]("http://ubuntuforums.org/member.php?u=190992") it is work!:))

---

### Post by trayzz on 2009-08-11
> **krazykookmany said:**
> Here's what I did:

Sound In: Intel ICH6 (hw:ICH6,0) (it's under pulse)
Sound Out: Pulse
Ringer: Pulse

it all works fine for me without getting rid of Pulseaudio


setting all devices on 'pulse' did indeed work for me (so sound in didn't matter in the end). try that before deinstalling pulseaudio.

cheers krazykookmany! :popcorn:

---

### Post by littlegirl63 on 2009-08-22
im just using what was built into my laptop and this fixed my problem thanks
i have an hp...

that was thanks to seeklinux btws

---

### Post by crgutierrez on 2009-08-29
Works for ICH9 on HP Pavillion dv 4 on Jaunty 64amd as well
Many thanks!

---

### Post by grj23 on 2009-12-13
> **krazykookmany said:**
> Here's what I did:

Sound In: Intel ICH6 (hw:ICH6,0) (it's under pulse)
Sound Out: Pulse
Ringer: Pulse

it all works fine for me without getting rid of Pulseaudio

Worked for me too!  Thanks!

---

### Post by PauPau on 2010-02-10
Hey guys, i read over most forums vigoriously, but I think I have quite a special problem.

I have OSSv4 installed and no ALSA or PulseAudio, since my card 
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
does not work with anything else, but OSS.
I am running Karmic and the 

Only options in the sound devices in Skype are:
Microphone: default device (default)
            hdmi (unkknown)
            rawbluetooth (bluetooth)
            bluetooth (plug)

Nothing works... Is there anyone out there who understands this enought to help?

Thanks

---

