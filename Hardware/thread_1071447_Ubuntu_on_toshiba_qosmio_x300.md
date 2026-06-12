---
title: "Ubuntu on toshiba qosmio x300"
date: 2009-02-16
forum: Hardware
---

### Post by EDDYG1234 on 2009-02-16
Hello, im new to ubuntu and i want to install ubuntu to my laptop
toshiba qosmio x300. 
1. Did any of you tried to install ubuntu on this kind a laptop

2. Where can i find driver for my laptop(vga,wifi,sound...)

ill be glad for any help...

Tnx

---

### Post by shameful on 2009-02-16
Wahey a fellow x300 users. Ive installed the latest ubuntu along with windows using dual boot. and everything gets picked automatically that ive found so far. only thing that needs doing is to activate the proprietary nvidia drivers if you want to use them. Also using latest kernel my sound stopped working. Having to use 2.6.27-9-generic until i can found out whats causing it. other than those two things. works brilliantly and am using it now.

---

### Post by Ryuki_NdranC on 2009-02-16
> **shameful said:**
> Wahey a fellow x300 users. Ive installed the latest ubuntu along with windows using dual boot. and everything gets picked automatically that ive found so far. only thing that needs doing is to activate the proprietary nvidia drivers if you want to use them. Also using latest kernel my sound stopped working. Having to use 2.6.27-9-generic until i can found out whats causing it. other than those two things. works brilliantly and am using it now.


Hi there, I have a qosmio x305 q705 and so fari only got two magor problems.

Are you sure your speakers are all working??? Because i noticed that the internal subwoofer is not working and im almost sure just that 2 of the 4 front speakers are the only ones working. Besides the fact that your headphone jack doesnt "mute" the audio of the speakers when you plug in a headphone on it.

The second major thing is, that i installed compiz git, and i have to say (even with propietary drivers) that the performance is quite below my expectations... Under windows im running 3 month old graphic hugers games at the best quality (some times even with x8 anti alising) and the run smooth, but the cube seems very pixelated and when transparency is ON it feels slugish. It still works fine... but doesnt seem to be working like it should.

The are other minor stuff, Bluetooth seems to not be working, and from the outside butons, only the play, stop, prev, next are working.

I barely could fine any info related to this problems on the forums, and what i found is that maybe the sound problem is related to an outdated alsa driver. Since im still very new to the linux world, when i tried to follow a tutorial to update the drivers my audio got worse and i had to format because i had no idea how to fix it back :p 

Im trying to know if im the only one that has this problems, and to know if you experince something alike. Any ideas on where i could find more info? Im kinda desperate, I disliked vista before using it, but now i hate it with my guts. I wish i wont have to start a new thread for this.

Thx for reading and bearing.:p

---

### Post by shameful on 2009-02-17
> **Ryuki_NdranC said:**
> Hi there, I have a qosmio x305 q705 and so fari only got two magor problems.

Are you sure your speakers are all working??? Because i noticed that the internal subwoofer is not working and im almost sure just that 2 of the 4 front speakers are the only ones working. Besides the fact that your headphone jack doesnt "mute" the audio of the speakers when you plug in a headphone on it.

The second major thing is, that i installed compiz git, and i have to say (even with propietary drivers) that the performance is quite below my expectations... Under windows im running 3 month old graphic hugers games at the best quality (some times even with x8 anti alising) and the run smooth, but the cube seems very pixelated and when transparency is ON it feels slugish. It still works fine... but doesnt seem to be working like it should.

The are other minor stuff, Bluetooth seems to not be working, and from the outside butons, only the play, stop, prev, next are working.

I barely could fine any info related to this problems on the forums, and what i found is that maybe the sound problem is related to an outdated alsa driver. Since im still very new to the linux world, when i tried to follow a tutorial to update the drivers my audio got worse and i had to format because i had no idea how to fix it back :p 

Im trying to know if im the only one that has this problems, and to know if you experince something alike. Any ideas on where i could find more info? Im kinda desperate, I disliked vista before using it, but now i hate it with my guts. I wish i wont have to start a new thread for this.

Thx for reading and bearing.:p


Hello.

Just been having a play.  and all of my speakers do work. but only within players such as totem. And I have to set the preferences up as a 4 speaker system.   Not got headphones handy so will have to try them when i get home later tomorrow.  For the buttons. I did look into that a while ago and found that you had to manually map the buttons to commands. Again when im home ill look and see if i can find the links towards that goal.

Im not sure about your video performance. Its been running great on here. One of the things i was very impressed with when i first got it installed.
Im using the below if that is of any use to you.
Ubuntu 8.10 x64
2.6.27.-9-generic kernel
177.82 Nvidia

---

### Post by Ryuki_NdranC on 2009-02-17
> **shameful said:**
> Hello.

Just been having a play.  and all of my speakers do work. but only within players such as totem. And I have to set the preferences up as a 4 speaker system.   Not got headphones handy so will have to try them when i get home later tomorrow.  For the buttons. I did look into that a while ago and found that you had to manually map the buttons to commands. Again when im home ill look and see if i can find the links towards that goal.

Im not sure about your video performance. Its been running great on here. One of the things i was very impressed with when i first got it installed.
Im using the below if that is of any use to you.
Ubuntu 8.10 x64
2.6.27.-9-generic kernel
177.82 Nvidia

Thanks for your reply, Im about to install again ubuntu amd64 8.10, I dont remmeber the kernel's version but i believe is the most updated one. I heard about the keymapping thing before, but so far i haven't realy look that deep for it because im more interested in the sound/video.

Ok are you complitely sure about the subwoofer? I really tested it with a youtube video (i played the same video under vista) and although the youtube sound quality is not so great, touching the laptop's subwoofer output with my hand proved it wasnt working at all (al though in vista it was). I never tried with any media player because it was a fresh install without any propietary codecs i would need to use for my videos.

The speaker problem seems to be a really messy one to solve, involving updating (off-oficial repository) the alsa drivers. That meens your driver may get deleted if you autoupdate through your repos your alsa driver again. Of course so far im really repo dependant in a way, because im still not very used to the linux ways of things (and i want to work on it so badddd) so maybe is not that hard.

Well about the video performance, would you would you suggest me a way to really test it? i though maybe was the compiz git fault, maybe that copy of compiz git was some how "unstable" or "unproperly installed", i though of a game, but it would involve using wine and it might take several reserch to make it work, i really dont know any other graphical heavy application that may help me to test my video card performance under linux.

Everything else seems to work just fine, and really smooth. Errr well if you dont cound the bluetooth. Im going to start using this port as a feedback thread for the results i get with my laptop. I would appreciatte a reply if you find anything else that helped you before.

Yet again thanks for the reply.

---

### Post by Blou_Aap on 2009-03-12
I got a Qosmio x300-T11 and upgraded my Vista to Intrepid ;)

I have some similar problems that Ryuki_NdranC has.

Is there any way to fix the Following problems ?

1. 
The On-board Blue tooth does not work, not even through a VM.

2. 
The sound is VERY unpredictable. Sometimes it works, then sometimes it doesn't. It works with certain applications and with others it does not at all. 

eg : If I watch flash videos(like you-tube) on-line there is NO SOUND, but if I download that video and watch it immediately through media player you hear the sound. Sometimes there is sound when watching youtube.
Very unreliable. :(

Plugging in some head phones do not switch off the Laptop speakers. :/

3.
Maybe have a way to switch On/Off the lights behind the top most speakers via the media keys, like I could do in Vista.

4.
Have some of the media keys work or able to bind them to a function, like the 'Dolby', 'Camera' and 'Media Centre' keys.

---

### Post by Ryuki_NdranC on 2009-03-22
> **Blou_Aap said:**
> I got a Qosmio x300-T11 and upgraded my Vista to Intrepid ;)

I have some similar problems that Ryuki_NdranC has.

Is there any way to fix the Following problems ?

1. 
The On-board Blue tooth does not work, not even through a VM.

2. 
The sound is VERY unpredictable. Sometimes it works, then sometimes it doesn't. It works with certain applications and with others it does not at all. 

eg : If I watch flash videos(like you-tube) on-line there is NO SOUND, but if I download that video and watch it immediately through media player you hear the sound. Sometimes there is sound when watching youtube.
Very unreliable. :(

Plugging in some head phones do not switch off the Laptop speakers. :/

3.
Maybe have a way to switch On/Off the lights behind the top most speakers via the media keys, like I could do in Vista.

4.
Have some of the media keys work or able to bind them to a function, like the 'Dolby', 'Camera' and 'Media Centre' keys.

O.O an answer... wow... *cough*

Anyway, yes i vaguely recall a youtube problem related with the sound. To be honest so far i had to wipe linux and work under vista while the current semester was on the way. In a week from now im gonna be off and ill be trying again to fix the ishues. So far it doesnt look good. Most of the problems just seem to be related to the lack of driver support due to the fact this model seems to be very "new". Im even trying to find out if the n

ew ubuntu 9.04 is gonna include some fixes related to this laptop and if they arent, im trying to find a way to make a some sort of oficial way to let them out in the open. Im fairly new in the linux OS and even newer in the ubuntu comunity, so if anyone knows how to address this problems by proprer "channels" plz feel free to do so or at least point us in a direction.

I found a website outside the ubuntu comunity disscusing this laptop model under linux. It looks promesing in some ways. Im gonna post the link if you feel like investigating there.

Link: [HERE!]("http://www.linlap.com/wiki/toshiba+qosmio+x305#comment__f2a0f2afc7672e0a3e13f3edb09b6445")

VENT: To be honest im starting to regret have bought this laptop, is really awesome and all... but not been able to run linux in a decent proper way is frustrating. I dont live in USA and its very hard for me to get my hands in any laptop at all (thats to chavez <.<) im really trying to make this one work.

BTW how about your video card performance? do you have compiz or compiz-git installed? do you notice any "interrupted" or "pixelated motion" when you take the cube out for a spin with transparency on?

---

### Post by Blou_Aap on 2009-03-23
My Compiz Works fantastic, no glitches and smooth. Just make sure you have proper nVidia Drivers from nVidia.com and not the ones you get through the updates in Ubuntu.

As for the sound, well I got that sorted out quite nicely, some guy on this very forum wrote a script that updates your ALSA drivers and that worked
great.

Even though the On-board Bluetooth Still doesn't work, the USB Bluetooth that I have does work.

I guess It's right what you said, this Laptop is VERY new so drivers will come along soon I hope.

> 
3.
Maybe have a way to switch On/Off the lights behind the top most speakers via the media keys, like I could do in Vista.

4.
Have some of the media keys work or able to bind them to a function, like the 'Dolby', 'Camera' and 'Media Centre' keys.

Those 2 things I still haven't figured out yet.
But I love this laptop even more without bloody Vista, I can still
play my Multiplayer games like I want with Cedega and Wine.

Games That I play: COD4, Warcraft TFT, WoW.

---

### Post by Ryuki_NdranC on 2009-03-24
> **Blou_Aap said:**
> My Compiz Works fantastic, no glitches and smooth. Just make sure you have proper nVidia Drivers from nVidia.com and not the ones you get through the updates in Ubuntu.

... why didn't i though of that. I though the nvidia drivers were the ones offered by ubuntu "hardware detection". Thx for the tip, im gonna try it out.

> As for the sound, well I got that sorted out quite nicely, some guy on this very forum wrote a script that updates your ALSA drivers and that worked
great.

Do you mind elaborate on this? and maybe post the direct link to the thread where the script is? I used two already and they didnt work as expected. Also, what do you mean exactly with "nicely" ;P all the speakers + subwoofer works now? flash video audio (youtube) doesnt glich anymore? headphone jack?

In the matter of media keys, i got a friend who has an idea on how to map those keys but so far i havent found anything already done in this area.

I also wanted to aske you if you know if the new alsa drivers are gonna be included in the new april release? i guess im a little reluctant to the manual driver update because with the new release so close i dont want to format my pc twice in less than a month (yes, i format each time an ubuntu distro comes out)

Thx for reply

---

### Post by Blou_Aap on 2009-03-24
Well the sound is not 100%, more like 90%. There is a few faults, but those might be more application specific. All speakers work and work well.
For the headphone there is a check-box to switch it on/off, for some reason mine works automatically.

Link to the ALSA UPGRADE SCRIPT:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
Read carefully and follow the steps and it will work, I'm sure.

Haven't even looked at the new release yet so won't know what to tell you there.

---

### Post by Ryuki_NdranC on 2009-03-24
> **Blou_Aap said:**
> Well the sound is not 100%, more like 90%. There is a few faults, but those might be more application specific. All speakers work and work well.
For the headphone there is a check-box to switch it on/off, for some reason mine works automatically.

Link to the ALSA UPGRADE SCRIPT:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
Read carefully and follow the steps and it will work, I'm sure.

Haven't even looked at the new release yet so won't know what to tell you there.

Wow that was fast. Ok im installing and updating my ubuntu right now, as soon i get some results ill reply back. I noticed that we have a slight diferent model (mine's x305) but i hope my end results be as good as yours.

Thx again for such a fast reply.

---

### Post by Ryuki_NdranC on 2009-03-24
I don't know if you tried the obvious stuff, but have you tried this? (key mapping the multimedia keys)

[LINK!]("http://tehpost.blogspot.com/2007/01/ubuntu-gnome-mapping-logitech-access.html")

Its been a while since i used linux on the x305 but i think i tried this and i was getting no "hex direction" for the multimedia keys when i pressed them. Im not sure tho. I do recall that play, stop and forward/backward.

Im really surprised that is this dificul to fix this small problem.

BTW, when you say 90% of the sound, you mean just 90% of the volume power? or 90% of the regular sound quality? (compared to vista i guess)

 ------- EDIT --------
PS: OMG i double posted. Im srry.

PS2: I also found out about the alsa drivers in jaunty and it seems its gonna come with 1.0.18 (hardy has 1.0.17a) while the latest package version is 1.0.19 according to [LINK!]("http://distrowatch.com/table.php?distribution=ubuntu") no idea if it may get upgraded to 1.0.19 before release.

---

### Post by Blou_Aap on 2009-03-25
No I mean 90% as in there is only like 10% 's worth of problems, like the youtube glitch might spring up now and then for example. Sound driver is only like 90% stable, that's what I meant.

As for the Media keys, well they work fine, It's just the keys that say : "Dolby" , The key with the camera picture and then the "Media Center" key  that do not work also the key that switches the 'Backlights' on/off don't work and then the "Mute/Unmute" key don't wok either. 
The "Play/Pause", "Stop", "Back", "Forward" work fine.

---

### Post by Ryuki_NdranC on 2009-03-25
Well i installed ubuntu...

I installed the pre-release NVIDIA drivers 180.41 and everything works fine.

I also used the alsa script you suggested and the sound seems "ok". But a new problem came up >.<
Now my volume wheel on the side of the laptop doesnt work. The OS shows me the volume up/down animation when i spin it, but the volume doesnt change at all. The only way to change the volume is through the gnome volume control icon on the system tray and even so, i noticed that the volume increase/decrease ratio is out of proportion. I mean when i put the volume on 80%ish it sounds like i just muted the whole thing to 0%.

Do you have this same problems? The other things i notice with sound but i need yet to confirm is the volume maximun strengt (compared to vista) and really check if the subwoofer is working (im guessing is not)

The sound/video is a big close dealer for me, hell those were one of the main reasons i bough the laptop. I hope HDMI works o.o

--------- EDIT ----------
Yep, i checked, the sub-woofer isn't working.

And i forgot to clarify that the headphone jack works correctly now.

OK, now i fixed my volume wheel problem. The out of proportion volume change and the non working subwoofer are still there, but at least now i think is a lot more better. Im gonna try to find a solution for the subwoofer.

... After several hours reading and testing, so far i think all of the remaining problems are just one big. I was wrong before, only the front speakers (just the two next to the touch pad) work. The Rear speakers, the subwoofer and the hdmi audio doesn't work. What im still trying to find out if it is a bad configuration thing, or the acl262 intel chipset isnt quite supported yet. Ill give it another chance when i have another day off, but right now its really frustrating.

Thx for reading.

---

### Post by Blou_Aap on 2009-03-26
Ya the Volume on the side changes my PCM Volume, which is fine every thing
 I use goes through PCM any way. The Volume knob changes the volume smoothly as well. All my speakers work though and is just as loud as it was when I had Windoze.

I have the x300-11t Afaik yours and mine uses the exact same Mobo, just yours have a faster CPU and GPU with more ram.

---

### Post by Ryuki_NdranC on 2009-03-27
> **Blou_Aap said:**
> Ya the Volume on the side changes my PCM Volume, which is fine every thing
 I use goes through PCM any way. The Volume knob changes the volume smoothly as well. All my speakers work though and is just as loud as it was when I had Windoze.

I have the x300-11t Afaik yours and mine uses the exact same Mobo, just yours have a faster CPU and GPU with more ram.

Im interested about the speakers part. When you do something like

```
speaker-test -Dplughw:#,0 -c6  // # is 0 in my case, just aplay -l if you dont know yours but something tells me you do know
```  
or
```
speaker-test -D surround41 -c6
```

do you get sound in every speaker? In my case only the "front right" and "front left" are working.

Maybe im doing the wrong tests, or maybe i setup something wrong. I actually played a media file for a while a tested each speaker covering it with my hand trying to feel the sound waves and im 90% sure just the front ones work. I also played an ogg video file with a deep sound, and in vista my crystal table actually vibrated with the bass, and in linux it didnt. (i know, silly unprofesional test, but i work with what i know :$)

When i installed the alsa drivers the script finished without any ishues i could see from the trace i was doing to the instalation log.

My sound card knowledge is pretty limited, i never worried before for stuff like hdmi or even surround 4.1 lol :p, i fixed the volume ishue and i set it to control the master volume rather than the pcm.

BTW i really apreciate you to been sticking around for a while after you fixed your problems. I don't know anybody with this type of sound card and it doesnt seem to be a lot more over the web.

---

### Post by Blou_Aap on 2009-03-27
Sigh There was an update(xorg), after the Update I have the same problem as you.
:(
The speakers at the screen doesn't play anything.
Only the speakers in-line with the Touch-pad works and they aren't even stereo.

I feel your pain now, I tried reinstalling etc, but nothing works.
Guess we just have to wait a little. At least the Headphones work fine, with stereo too. :confused:

---

### Post by Ryuki_NdranC on 2009-03-27
> **Blou_Aap said:**
> Sigh There was an update(xorg), after the Update I have the same problem as you.
:(
The speakers at the screen doesn't play anything.
Only the speakers in-line with the Touch-pad works and they aren't even stereo.

I feel your pain now, I tried reinstalling etc, but nothing works.
Guess we just have to wait a little. At least the Headphones work fine, with stereo too. :confused:


hmmm... wow man i srry for that. Wait.... xorg? i though xorg was the whole GUI, what does that have to do with alsa? o.o

Im gonna try to reinstall ubuntu again and try to selectively try each undate. I got 1 kernel update and several 250mb worth updates.


BTW do you have the same chip code, and audio card? ACL272??? SND-HDA-INTEL (ICH9)???

------------ EDIT -------------

Well... this is crazy, im gonna start to read some more about pulseaudio and alsa and what not because im pretty confused right now.

I installed ubuntu 9.04 beta, and updated right after. When i do a simple audio test i get sound from every speaker but the LFG one (i guess thats the subwoofer). The thing is i dont know why, because acording to gnome mixer the current drivers only detect "front speakers". I even changed the default channels in the /etc/pulse/daemon.conf and still the same.

Crazy thing. Right now, i dont even know what to do.

---

### Post by Blou_Aap on 2009-03-31
Updating xorg updated some config files maybe. But there was other updates too, so I'm not too sure why my sound started to fudge out.

Yes my Sound chip is the same as yours.

---

### Post by Blou_Aap on 2009-04-07
Ryuki_NdranC , Please tell me how you got the Volume wheel on the right of the Laptop to control the MAIN volume and not the PCM or Front channel.

---

### Post by ruien on 2009-05-02
Hi.

I have a Qosmio G40 with a ALC262 sound chip and I had to do this in order to get proper sound: make or edit rc.local in /etc and put this in it: /sbin/modprobe -r snd-hda-intel && modprobe snd-hda-intel model=auto  and put exit 0 on next line. You could also try model=fujitsu if you still have issues with sound. Auto should work in most cases.

This make the sound work properly with headphones and speakers. I have a 41 system and every speaker works including subwoofer. 

When it comes to internal bluetooth it does exist drivers for it. Fedora 10 loads the drivers properly and the internal bluetooth works out of the box on a fresh install. But on ubuntu or any other distro i've tried dosent find the internal bluetooth on this laptop at least. I don't run Fedora now because it's a slow sluggish system in my opinion so i cant give any output regarding bluetooth. But i think it should work fine on x300 also. Try a livecd and see how it goes.

---

### Post by DudeMiester on 2009-07-25
I can confirm that Bluetooth works with Omnibook, Ubuntu 9.04 and the Toshiba Qosmio x300.

Follow these instructions found here: [http://ubuntuforums.org/showthread.php?t=316358](http://ubuntuforums.org/showthread.php?t=316358)

You will need to set the "ectype" parameter when loading omnibook however, as the x300 is not directly supported. "ectype=12" seems to work fine for me.

Now the bluetooth icon will show up and you can start pairing devices.

However, there are still problems with bluetooth on Ubuntu 9.04 with certain mouse and keyboard hardware. I have a Microsoft Bluetooth Notebook Mouse 5000, and it does not connect properly by default. Here's the workaround:
> 1) Add the package "bluez-compat" from the package manager

2) Add your mouse/keyboard using the bluetooth applet. It will appear to succeed, but you may notice your hardware is still is pairing mode and doesn't work.

3) In a terminal run:
sudo hidd --search

Now it should work. Be advised that for some people the device doesn't always automatically reconnect on reboot, and disconnects after a period of time. Just re-run "sudo hidd --search" in this case, and it should be fine. I also want to stress that this is a workaround, not a solution, as bluez-compat is deprecated. I imagine a future version of bluez will fix this problem.

I got this info from the following bugs:
[https://bugs.launchpad.net/ubuntu/+bug/347512](https://bugs.launchpad.net/ubuntu/+bug/347512)
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727)

EDIT: Warning, I've experienced a lot of soft lockups and tainted processes after doing this. I'm going to see if I can extract only the code that turns on the bluetooth from omnibook and put it in a separate module.

EDIT 2: I modified omnibook so that it recognizes the X300 automatically, but I've only turned on bluetooth as I don't know which other feature is causing the crashes. For all I know, even just having bluetooth working will cause them. It's early days yet. I need more time to make sure it really is stable.

EDIT 3: Had some more lockups, but this time only in xorg. I updated my Nvidia drivers to the latest on their website, and haven't had a problem since. Do remember when updating to deactivate any restricted drivers you may have activated in Ubuntu's administrative settings. Then crtl-alt-F1 a console, log in as root, "/etc/init.d/gdm stop", install the driver, "/etc/init.d/gdm start". Afterwards, you may also want to restart.

---

