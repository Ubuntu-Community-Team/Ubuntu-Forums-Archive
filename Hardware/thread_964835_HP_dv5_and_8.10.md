---
title: "HP dv5 and 8.10"
date: 2008-10-31
forum: Hardware
---

### Post by adcurtin on 2008-10-31
I just installed 8.10 on an hp dv5. All the essential hardware works for the most part. I had a couple questions. There is an infrared port on the laptop, and it came with a remote. How can I get that working? Also, more importantly, the audio has a strange glitch every time I shut down. It is IDT HD audio, and whenever I shut down, usually a second before the machine is actually off, the speakers emit a very strange cracking type sound, kind of like fireworks. How can I get rid of this, it sounds really bad, and may be damaging my speakers.

---

### Post by dima206 on 2008-12-02
Have same problems! :(

---

### Post by kezeb on 2008-12-03
i'm having the exact same problem on a dv4-1114nr

---

### Post by K3N8 on 2008-12-03
I have exactly the same issues.

HP Pavilion DV7 1120ed

---

### Post by yachoo on 2008-12-03
I have the same problems, but I have also some informations about rc. I don't want to rewrite everything so:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1000299&highlight=dv5](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1000299&highlight=dv5)

EDIT:
I worked it out by myself. After BIOS update to F.11 version it's automagically starting to work.
There is also wake-up problem after suspend. I read that F.21 version should solve that problem (and it's on the way).

---

### Post by Sylchat on 2008-12-04
About the remote control, it was working in Mplayer in previous release of Ubuntu. In 8.10, it seems useless now... I have the latest BIOS for dv9xxx

For the sound, same cracking noise (and be careful if you are shutting down your laptop with the ear plugs on).

---

### Post by dhmejia on 2008-12-05
I also had problems with the audio in a dv4-1125nr (audio intel), the solution was (in intrepid):

```
sudo gedit /etc/modprobe.d/alsa-base
```

add at the end of file:

*options snd-hda-intel enable_msi=1*

---

### Post by kezeb on 2008-12-08
that worked, but still i did two things i updated my bios to f22 and did that thing above and it worked, all i'm gonna say is adios vista adios!!!!!!!!!!!!!!

---

### Post by whichpaul on 2008-12-11
Yachoo, you said that you read BIOS update F.21 is coming, I assume you mean coming for the dv5, where did you read this?

I've got a bug open open for [suspend / resume failure on the dv5]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301353") and have been told that a new BIOS for the dv7 fixed its problems.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301353](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301353)

Basically the SATA drives won't wake up on resume.

Thanks.

---

### Post by K3N8 on 2008-12-13
> **whichpaul said:**
> .... and have been told that a new BIOS for the dv7 fixed its problems.I can tell you the new BIOS for the DV7 does not help the problems with hibernation or suspend. My keyboard still locks up.

---

### Post by Jorge_C on 2008-12-13
> I can tell you the new BIOS for the DV7 does not help the problems with hibernation or suspend. My keyboard still locks up.
Well, for me, the latest bios (F21) solves all my suspend problems in a hp dv7-1080es...

---

### Post by yachoo on 2008-12-15
And I'm sure that for me it'll solve suspend problem too. I'm waiting for a new BIOS (probably f.12)

---

### Post by kacike76 on 2008-12-15
Well the most current BIOS version F.21 did fix the suspend issue i was having.  However i have to always disable my wireless before i suspend. I have a dv7-1025nr 64 bit machine. I wonder if this is a wireless issue now.  The touch button that enables/disables the wireless card is constantly blinking between orange and blue.

---

### Post by sshlyk on 2008-12-16
> **yachoo said:**
> And I'm sure that for me it'll solve suspend problem too. I'm waiting for a new BIOS (probably f.12)

do you have any idea when it is out? 

Can you give me a link to HP web page with the latest bios.

I would never buy HP if I read this topic before. Linux FTW!

---

### Post by sshlyk on 2008-12-16
> **kacike76 said:**
> Well the most current BIOS version F.21 did fix the suspend issue i was having.  However i have to always disable my wireless before i suspend. I have a dv7-1025nr 64 bit machine. I wonder if this is a wireless issue now.  The touch button that enables/disables the wireless card is constantly blinking between orange and blue.


it blinks to indicate that data is transmitted. It is very annoying, I know. You can search on how to disable it

---

### Post by kacike76 on 2008-12-19
I can confirm that BIOS F.21 on a HP DV7-1025nr does fix the suspend issue.  The first time it resumed from suspend with this BIOS upgrade i didn't work.  I tried it a second time first disabling wireless and it resumed fine.  Now it just works everytime!!!

One thing i noticed on this laptop, however, is that sometimes when i login into vista and restart into Ubuntu the OS is unable to load.  I don't even make it to the login screen for Ubuntu and i get a black screen with a flashing caps lock.  Nothing works and i have to press and hold the power button.  

Has anyone else experienced this same issue?

---

### Post by jonbonjovi on 2008-12-27
I've just bought an HP DV5 notebook and I had the same problem with the annoying noise when rebooting. I solved it adding 3 lines at the end of "alsa-base" file. But now there are still some audio problems:

1- if I boot with headphones plugged-in and then I unplug them, the audio doesn't switch to normal speakers;

2- microphone doesn't work and, often, cause a gnome freeze.

Anyone knows how to fix them?? :confused:

---

### Post by jonbonjovi on 2008-12-30
> **jonbonjovi said:**
> I've just bought an HP DV5 notebook and I had the same problem with the annoying noise when rebooting. I solved it adding 3 lines at the end of "alsa-base" file. But now there are still some audio problems:

1- if I boot with headphones plugged-in and then I unplug them, the audio doesn't switch to normal speakers;

2- microphone doesn't work and, often, cause a gnome freeze.

Anyone knows how to fix them?? :confused:

up?

---

### Post by jewblahsky on 2009-01-06
same problems: ubuntu intrepid 8.10 won't wake from suspend/hibernate, cracking noise on shutdown, microphones don't work.
dv5t-1100

jonbonjovi,
what did you add at the end of the alsa-base file to prevent the cracking on shutdown? and what other audio issues are you having?

---

### Post by dexterslab on 2009-01-07
\\:D/

I just updated Bios from F.12 to F.22 and now my system comes back from either suspend or Hibernate.

I have a dv4 - 1117nr

---

### Post by jonbonjovi on 2009-01-12
> **jewblahsky said:**
> same problems: ubuntu intrepid 8.10 won't wake from suspend/hibernate, cracking noise on shutdown, microphones don't work.
dv5t-1100

jonbonjovi,
what did you add at the end of the alsa-base file to prevent the cracking on shutdown? and what other audio issues are you having?

I explained them very bad before.
The specific problems are:
- cracking noise on reboot (not on shutdown);
- when I plug an usb device (pendrive, usb mouse, etc) the right button of the mouse doesn't work, the keyboard doesn't work and the main menu doesn't appear.

Sorry for my english, but I'm Italian.

Any solution?

---

### Post by jonbonjovi on 2009-01-16
for the headphones/speakers problem: try this:


```
 sudo gedit /etc/modprobe.d/alsa-base

```

erase all its content and write in it ONLY the following:

```
alias snd-card-0 snd-hda-intel 
alias sound-slot-0 snd-hda-intel 
options snd-hda-intel model=hp-m4 enable_msi=1
```

then reboot. The switch between headphones and speakers sounds to work. :guitar:

---

### Post by ameseisch on 2009-01-19
> **dexterslab said:**
> \\:D/

I just updated Bios from F.12 to F.22 and now my system comes back from either suspend or Hibernate.

I have a dv4 - 1117nr

does anyone know how to update the bios if you no longer have windows on your system? maybe WINE can run the .exe that HP provides?

any suggestions are welcome. I would really like to be able to suspend my laptop

Update: I tried to find a reliable way to do this without resorting to reinstalling windows, but no luck. so I re-installed, did Bios update and put Ubuntu (actually LinuxMint this time) back on. Suspend and Hibernate now work perfectly on my dv4 1114nr

---

### Post by yrayad on 2009-01-25
Hey everyone... I have an Hp Pavilion dv5. I run Ubuntu 8.10 and I recently installed skype 2.0 on it. This computer has an integrated webcam and an integrated mic. I was able to fix the playback problem so i can now here sound using skype but for some reason people don't hear my microphone. The video component works perfectly.

---

### Post by _Atreides_ on 2009-01-26
Hey guys, I have looked through this whole thread and different posts but I cannot get answers to these questions:

1) I have the speaker crackle/static on restart too, how do i fix this?
2) My BIOS is at F1.1, for the hp dv5t is there a newer one? Sleep does not work but hibernate seems to work just takes a while.


Again i have the hp dv5t regular edition. Thank you!

---

### Post by zengrits on 2009-01-26
I'm having the same problem on an HP dv3510nr.
Will try fixes above.

---

### Post by _Atreides_ on 2009-01-26
what fixes are you talking about? people have said to upgrade bios but im on F.11 and the hp site doesnt have anything newer.... and im still not sure what to even try for sound crackle on shutdown

---

### Post by zengrits on 2009-01-26
I just upgraded my bios to F12 for the dv3510nr. Haven't tried it yet in Ubuntu.

---

### Post by zengrits on 2009-01-26
Maybe the word "fixes" was too optimistic. But certainly jonbonjovi suggested a change in audio settings and others mentioned the bios update. I guess I was hoping these suggestions would be "fixes."

---

### Post by ninboy on 2009-01-26
Hello everyone!

I have a HP dv5-1125nr, with Ubuntu 8.10x64 installed.

@yrayad: What did you do to make the mic works? That's driving me crazy.

@everyone: My wireless icon in the quickPlay is always in orange color. Is this the normal behavior for everyone? In windows the "button" is blue when the wireless is on and orange when is off. In fact, Ubuntu doesn't seems to recognize at all when i click that part of the wuicplay bar, the same as the quickplay buttom. Is there some way to fix this?

Thanks to you all!!! I'l update the bios and test if now i can use the suspend function...

---

### Post by _Atreides_ on 2009-01-26
im sure if the internet is working its fine, mine flashes between blue and orange :/ my bios is already at f.11 what was yours at? isnt f.11 the oldest one?

---

### Post by ninboy on 2009-01-26
> **_Atreides_ said:**
> im sure if the internet is working its fine, mine flashes between blue and orange :/ my bios is already at f.11 what was yours at? isnt f.11 the oldest one?
Mine is f.22, I just upgraded it and it's the same... I clicked it and it disabled the wireless and now i cannot enable it lol the people against HP/Ubuntu...

---

### Post by _Atreides_ on 2009-01-26
> **ninboy said:**
> Mine is f.22, I just upgraded it and it's the same... I clicked it and it disabled the wireless and now i cannot enable it lol the people against HP/Ubuntu...

do you have an hp dv5t? if so where did you get the bios upgrade its not on the hp site? thankz

---

### Post by ninboy on 2009-01-27
It was in the HP site... Apparently, they only have it for AMD processors... [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-67532-1&lc=en&dlc=en&cc=us&product=3795326&os=2100&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-67532-1&lc=en&dlc=en&cc=us&product=3795326&os=2100&lang=en)

---

### Post by dhmejia on 2009-01-27
anyone has problems with long pauses in the beginning? I have a dv4-1125nr and in addition to the sound problems I have to wait about a minute to start the system.

Sorry for my English

Diego.

---

### Post by yrayad on 2009-01-27
Hey everyone... im still having issue with skype. I have a dv5 and the webcam works and i can hear the other person but i my microphone doesn't seem to work...
@ninboy, i was only able to fix the playback problem which means i can only hear what the other person is saying on skype...
the fix for that is this:

"Then, I found a solutions for my problem, execute all of this command on your terminal, here we go:

        * killall pulseaudio
        * sudo apt-get remove pulseaudio
        * sudo apt-get install esound
        * sudo rm /etc/X11/Xsession.d/70pulseaudio"

[http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/](http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/)

Peace...

---

### Post by ninboy on 2009-01-27
@yrayad: You're getting rid of pulseaudio... I don't know what the community thinks about that, but personally I want to think Canonical will improve sooner or later (more sooner than later) their pulse audio support.

Anyways, I fixed some things... First, the hibernations seems to get fixed with the F.22 BIOS, but sleep is still misbehaving (It goes to sleep and wake up, but the keyboard is unrecognized after it). And I fixed the playback and recording sounds in skype, so i have it fully functional now. I don't know ekiga, I've uninstalled it.

So, here I come, I hope this can help you all:

[SIZE=5][B]Fix Hibernation in Ubuntu 8.10 and HP dv5
[SIZE=3](Possible others notebooks too)[/SIZE][/B][/SIZE]

First, I fixed it with the lastest HP Bios version... Look in the HP webpage for your notebook and look for BIOS updates... Normally, they are named "WinFlash for HP Notebook System BIOS (for Notebooks with AMD Processors)" or "WinFlash for HP Notebook System BIOS (for Notebooks with Intel Processors)". Look if it is the F.22 version.

> If you want to activate hibernation in the fast-user-switch applet you can use gconf-editor (alt+F2 -> gconf-editor) and go to:
**Apps -> gnome-power-manager -> general**, and select the "**can_hibernate**" checkbox.[SIZE=5][B]
Get Skype Playback and Record in Ubuntu 8.10 and HP dv5
[SIZE=3](Possible others notebooks too)[/SIZE][/B][/SIZE]
 

I have the package of skype of Medibuntu... If you don't have that repo, what are you waiting for? hehe. Possibly, the two first steps are not necessary, but I include them here so we can isolate any problem easily.


[LIST=1]
[*]First, we have to check what Media is ubuntu using by default.
> In **System -> Preferences -> Sound** check that you have **Autodetect** in Sound Playback (In music and movies, and in audio conferencing). In Sound capture select **PulseAudio Sound Server**. Close that.
[*]Double click in the Volume control. Click **Preferences**, and make sure you have selected **Digital Mic 1** and **Digital Input Source**. Close Preferences and you'll probably see 2 new tabs in the volume control window.
 In the new tab **Recording** check that the **Digital mic 1** is not muted. The right icon is useless for me, and the scrolling volume bar too, just be sure the left icon is not muted.
In the **Options** tab, in **Digital Input Source** select **Digital mic 1**.
[*]Now, in Skype:
> Open the preferences (Ctrl+O)
In the **Sound devices** select:
* **Sound In: **HDA ATI SB (hw:SB,0) (it could be another if you have a different sound card, check that you use the one that have (hw:SB,0)
* **Sound Out:** pulse.
* **Sound In:** pulse

[*]Make a test call, and see if you have record and playback sound!
[/LIST]

Tell me if this works for any of you, I think that no matter what DVX notebook is, HP internals all works the same...

And sorry for my english, I'm not a english native speaker, hehe.

---

### Post by tjpoe on 2009-02-27
the above worked perfect to get Skype working for me. very nice guide, awesome.

---

### Post by dserodio on 2009-02-28
For me, the wireless button works flawlessly, even changing its color (the mute button works but its light not).

Has anyone got the **QuickPlay** button to work? I'd like it to launch XBMC...

I've tested it with xev(1) and there is no event.

---

### Post by papatrexas on 2009-03-14
> **ninboy said:**
> In System -> Preferences -> Sound check that you have Autodetect in Sound Playback (In music and movies, and in audio conferencing). In Sound capture select PulseAudio Sound Server. Close that. 

ninboy, I tried this on my pavilion dv5-1120ev and it didn't work. I wanted to use recording of Ubuntu 10.8. Only when I chose HDA Intel STAC92xx Analog (ALSA) instead of PulseAudio Sound Server worked... I don't know if I help anyone, but your post didn't help me as much as I would like!!! But the other configurations are very right

---

### Post by grogo on 2009-03-16
dv4-1117ca

Audio issues fixed by using the alsa update script and adding the following to /etc/modprobe.d/alsa-base

options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

If anyone's had success in getting the IR to work on a dv4/dv5/dv7 please advise.  I've updated the bios and still no go, nothing that looks like an IR receiver in my lspci or lsusb output :(

The IR worked out of the box on the the dv6627ca, but that's the gf's computer and mine has 2x the ram and 2x the hd :)

---

### Post by dan00ss on 2009-03-26
I have a dv5-1017nr with the Intel Processors... I am still having trouble when it returns from hibernate/suspend... a box appears in the middle of the screen with lots of [][][][][][][[][][][].... and the title menus dissapear.

I currently have F.11 BIOS and the F.22 is not available for the Intel, The most current BIOS is F.14A.

Is there anything else i can do, should i update to F.14A??

Thanks,
Dan

---

### Post by fignig on 2009-04-01
> **dan00ss said:**
> I have a dv5-1017nr with the Intel Processors... I am still having trouble when it returns from hibernate/suspend... a box appears in the middle of the screen with lots of [][][][][][][[][][][].... and the title menus dissapear.

I currently have F.11 BIOS and the F.22 is not available for the Intel, The most current BIOS is F.14A.

Is there anything else i can do, should i update to F.14A??

Thanks,
Dan

if i'm not mistaken that might be a font issue.

---

### Post by NazarXG on 2009-04-03
> **adcurtin said:**
> whenever I shut down, usually a second before the machine is actually off, the speakers emit a very strange cracking type sound, kind of like fireworks. How can I get rid of this, it sounds really bad, and may be damaging my speakers.

Take a look here: [http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/]("http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/"). Solved in my dv4.

---

### Post by dan00ss on 2009-04-04
> **fignig said:**
> if i'm not mistaken that might be a font issue.

what you be mean by a 'font issue'??

I updated to the F.14 BIOS and I still have problems

---

