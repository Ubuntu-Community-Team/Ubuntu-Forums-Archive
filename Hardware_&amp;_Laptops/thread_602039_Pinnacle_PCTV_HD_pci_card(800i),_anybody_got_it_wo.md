---
title: "Pinnacle PCTV HD pci card(800i), anybody got it working?"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by PermuZero on 2007-11-03
Has anyone got this card working with linux.  Ive read on the linuxtv wiki that its not yet supported in linux but I have also read that it works fine for some people.  I cant get it to work at all, just a black screen in tv time.  If anyone has gotten it working please help.

---

### Post by bobpaul on 2007-11-05
I'm not sure if I have the 800i, but I do know it's a PCTV HD card. It shows up as:
```
bobpaul@bobpaul:~$ lspci | grep Conexant
01:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:08.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:08.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
```

I've never gotten a TV Tuner working under linux, but this is only my second tuner. In tvtime, I can right click and choose the Composite2 input, and then Composite mode works. I wouldn't be surprised if the Composite 1 is analog NTSC, with the Composite 3 and 4 being ATSC/QAM and the S-Video and they're just being interpreted improperly by tvtime. That's just a guess, though. I really have no idea how video4linux works...

---

### Post by Onurzaim on 2007-11-06
Hello,

I have Pinnacle PCTV hybrid pro pci  which is mentioned as 310i in common.

I can suggest you checking 

[http://linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29](http://linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29)

and 

[http://linuxtv.org/v4lwiki/index.php/Main_Page](http://linuxtv.org/v4lwiki/index.php/Main_Page)

Reading these pages can be tricky. I have em28xx showing up in lspci but Kaffeine (I strongly reccomend you using it) recgnized my card as Philips TDA 10046. So I tried to find apropirate firmware for it.

As a result I was able to watch dvb and regular TV broadcasts.

You can check how I solved my problem. 

[http://ubuntuforums.org/showthread.php?t=587474](http://ubuntuforums.org/showthread.php?t=587474)

Goodluck.

---

### Post by wizkey on 2007-11-18
> **bobpaul said:**
> I'm not sure if I have the 800i, but I do know it's a PCTV HD card. It shows up as:
```
bobpaul@bobpaul:~$ lspci | grep Conexant
01:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:08.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:08.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
```

I've never gotten a TV Tuner working under linux, but this is only my second tuner. In tvtime, I can right click and choose the Composite2 input, and then Composite mode works. I wouldn't be surprised if the Composite 1 is analog NTSC, with the Composite 3 and 4 being ATSC/QAM and the S-Video and they're just being interpreted improperly by tvtime. That's just a guess, though. I really have no idea how video4linux works...

Unfortunately, it's not quite that simple.

When the cx88xx driver starts up, it looks at the Vendor ID and subdevice ID to find a matching card definition. The card definition tells it what type of interfaces are on the card, like TV tuner, FM radio, S-Video, etc.

Since there isn't a working definition for this card yet, it defaults to an UNKNOWN card, which is set up for 4 Composite interfaces. In order for it to work properly, there would have to be a card definition for TV Tuner, Composite, S-Video, FM-Radio, and for recordings the mpeg interface also.

So no, it's not TVTIME that is at fault. It's actually working exactly as it should.

Unfortunately, the TV tuner on this card is a Xcevie Xc3028, which further adds complications since there isn't a driver for that under Ubuntu (yet).

Long story short, it might be a while before this card is supported. I do see work being done for the Xc3028, so hopefully in the near future the card will have a working definition and the Xc3028 is added to the main v4l tree.

---

### Post by bobpaul on 2007-11-19
> **wizkey said:**
> Long story short, it might be a while before this card is supported. I do see work being done for the Xc3028, so hopefully in the near future the card will have a working definition and the Xc3028 is added to the main v4l tree.

Cool, I can wait. I got it from a woot.com exclusive before pinnacle had released it to the rest of the public, so I didn't quite expect it to work out of box on nix. ;)

---

### Post by wizkey on 2007-11-19
> **bobpaul said:**
> Cool, I can wait. I got it from a woot.com exclusive before pinnacle had released it to the rest of the public, so I didn't quite expect it to work out of box on nix. ;)

The good news is that there are cards out there very similar, in particular one of the Pixelview cards is almost exactly the same. That card already is being worked on, so when that card and the Xc3028 tuner hit the main tree, it shouldn't be long after until this card can get supported.

---

### Post by taggesq on 2008-01-23
Support for this card is about to go onto the main repository tree.  I've kept myself up to date on the progress of this card.  I do have a major problem however...

I'm relatively new to Linux and don't quite understand exactly how to build driver patches onto the existing kernel.  I'm not even sure if I'm using the correct terminology.  Can someone explain the process?  I'm sure there are many out there that are confused.

I went to linuxtv for more information.  I believe I did it correctly, however, tvtime is still not recognizing the digital part of the card.  Do I need a separate driver?  Am I missing another tree?  Do I need v4l-dvb and dvb-apps?

Any help would be extremely appreciated... Thanks.

**Update:** I now believe I did it correctly, however, now Gutsy hangs after the splash screen.  According to the linuxtv developers, it looks like my nvidia driver is to blame.  Shocker there.  Does anyone know what the deal is here?  Is there a work-around or am I screwed for the time being the main tree is edited again?

---

### Post by weux on 2008-01-23
I am having the same problem although I haven't got any video to show up on tvtime or any other program.  The card shows up in tvtime but the channels dont show up.  MythTV freezes when I try to add the tuner card so I haven't tested it with MythTV.  

As for your problem with the boot up, just try rebooting until to works.  My computer freezes at what I believe is the same spot as yours does and it didn't start happening until I tried to get the TV tuner to work.  My freezes about 3 out of every 4 reboots.

---

### Post by cluepon on 2008-01-23
Yes. This is an issue. Nobody is sure yet if its the nVidia driver, or something in core-videobuf My advice is sign up for the v4l-dvb list, and add your voice to the list of people who already have been talking about this. The more people who bring it to light, the quicker it might get addressed. 

Id love for this to get worked out, and soon. Ive had the card half working for some time, but I would really like to use a more complete driver. =)

Of course, if anyone else has ideas to try, I am open to them. I have no problem being a guinea pig if it helps this along. =)

---

### Post by wizkey on 2008-01-23
I came back to this thread to report that support for the card has been accomplished, but see others have beat me to the punch. :)

Probably one of the things biting people is not having the firmware for the tuner. This quite probably is the source of the hangs folks are experiencing. The driver will attempt to load the firmware for the tuner, but if the firmware isn't in the /lib/firmware/<YourKernelVersion> directory, it can cause the system to hang.

If you do not have the xc5000 firmware, you can get it at:

[http://steventoth.net/linux/xc5000/](http://steventoth.net/linux/xc5000/) 

for now. Follow the instructions in the readme.

That will get you the firmware you need for the tuner. If you don't have that firmware, then the tuner won't work and neither will anything else, and can even hang the startup process.

I am using the card to watch NTSC right now. I've got it working under TVTime, MythTV, VLC, and MPlayer. Getting both video and audio.

I'm not familiar with using DVB for tuning for the digital, but it should "just work" as long as the drivers and firmware load as they should. Reading the mailing list, it appears most folks are using the card for DVB. I didn't see anyone testing for NTSC, but I can confirm it works.

---

### Post by cluepon on 2008-01-23
> **wizkey said:**
> I came back to this thread to report that support for the card has been accomplished, but see others have beat me to the punch. :)

Probably one of the things biting people is not having the firmware for the tuner. This quite probably is the source of the hangs folks are experiencing. The driver will attempt to load the firmware for the tuner, but if the firmware isn't in the /lib/firmware/<YourKernelVersion> directory, it can cause the system to hang.

If you do not have the xc5000 firmware, you can get it at:

[http://steventoth.net/linux/xc5000/](http://steventoth.net/linux/xc5000/) 

for now. Follow the instructions in the readme.

That will get you the firmware you need for the tuner. If you don't have that firmware, then the tuner won't work and neither will anything else, and can even hang the startup process.

I am using the card to watch NTSC right now. I've got it working under TVTime, MythTV, VLC, and MPlayer. Getting both video and audio.

I'm not familiar with using DVB for tuning for the digital, but it should "just work" as long as the drivers and firmware load as they should. Reading the mailing list, it appears most folks are using the card for DVB. I didn't see anyone testing for NTSC, but I can confirm it works.
There are no real instructions in the readme, but, I'll try to figure it out. 

In the meantime, are you using an nVidia driver? That's one common thread I am finding.

EDIT: It works. Not sure about sound, KDE TV is still channel scanning. 

For those who arent sure how to fix the issue:

As for those who arent sure what to do...

Download two things from the link Wizkey supplied. 

1) [http://steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)

2) The extract.sh file. Just right click and "Save Link as..."

Once you have these two down, put them both into a folder, drop into a terminal cd to the folder you put them in and do the following: 

chmod +x extract.sh

./extract.sh

This will extract the proper firmware file. It will then tell you where you need to copy the file to, and how to do so. 

Go to your v4l-dvb source, make clean, make, and then make install (to be sure). 

Reboot. 

Mucho thanks to Wizkey. =)

---

### Post by PermuZero on 2008-01-23
awesome!:) got it working with the extract.sh and dvb-fe-xc5000-1.1 firmware files.  Unfortunately cant get any sound.

---

### Post by cluepon on 2008-01-23
yeah, I am having sound issues as well. Any solution for that?

---

### Post by PermuZero on 2008-01-23
nothing yet....

---

### Post by taggesq on 2008-01-23
It's working!  But no sound.  I'm happy that it works.  We're half way there.

Something about alsa?

---

### Post by cluepon on 2008-01-23
> **taggesq said:**
> It's working!  But no sound.  I'm happy that it works.  We're half way there.

Something about alsa?
More than likely. One of the biggest problems in Ubuntu/Linux ive had has been dealing with Multiple Sound Cards. 

Now, that being said, I have a Soundblaster 5.1 card, along with my 800i. I need them to play nice somehow. I have zero clue at the moment, as the alsa documentation is pretty heavy duty...

So, if someone has any ideas, I am all ears. =)

---

### Post by taggesq on 2008-01-24
[B]Ok... An update.
[/B]
I turned on my computer this morning and bam, there was audio from the TV.  It was grainy, popping and echoed but lets not get too picky here.  At least the damn thing was working.  Apparently though, the video doesn't work now.  Frustrating... I do admit, I'm having fun learning the ins and outs of this stuff.

I'm going to restart and see if the video comes or I lose the audio.

Since we are just dealing with analog stuff right now, I hate to ask anyone if they know about digital and DVB because I'm trying to find some local HDTV channels but it doesnt seem to be finding any.  I know this card can find them because it discovers them well on XP.  Can someone point me to a good wiki on DVB other than linuxtv.  It is scanning but finding nothing.

---

### Post by cluepon on 2008-01-24
> **taggesq said:**
> [B]Ok... An update.
[/B]
I turned on my computer this morning and bam, there was audio from the TV.  It was grainy, popping and echoed but lets not get too picky here.  At least the damn thing was working.  Apparently though, the video doesn't work now.  Frustrating... I do admit, I'm having fun learning the ins and outs of this stuff.

I'm going to restart and see if the video comes or I lose the audio.

Since we are just dealing with analog stuff right now, I hate to ask anyone if they know about digital and DVB because I'm trying to find some local HDTV channels but it doesnt seem to be finding any.  I know this card can find them because it discovers them well on XP.  Can someone point me to a good wiki on DVB other than linuxtv.  It is scanning but finding nothing.
Well, I got my sound working. It's simply a matter of piping the right /dev/dsp into your primary sound card with arecord and aplay. 

Here is a good place for info on these issues:

[http://linuxtv.org/pipermail/linux-dvb/2008-January/thread.html](http://linuxtv.org/pipermail/linux-dvb/2008-January/thread.html)

The specific post where it's explained to me how to get sound...

[http://linuxtv.org/pipermail/linux-dvb/2008-January/023230.html](http://linuxtv.org/pipermail/linux-dvb/2008-January/023230.html)

Hope this helps. =)

---

### Post by wizkey on 2008-01-24
For those asking about sound...

There are a number of issues about sound. Some apps are ALSA aware, some are OSS aware, some can only take OSS for audio input but can do ALSA for audio output, blah blah blah...

Most of the time, you can just map to the OSS emulated device. As alluded to a little earlier by some posters, there should be an additional device in your /dev folder for the sound. So if your sound card is /dev/dsp, then chances are your sound from your TV card is being mapped to /dev/dsp1. With that info, you can simply tell most programs to pull the audio from that device directly.

For example, here is what I tell MPlayer to do:

mplayer tv:// -tv driver=v4l2:chanlist=us-cable:adevice=/dev/dsp1:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=NTSC-M:buffersize=128

Notice I tell it the adevice is /dev/dsp1 for the audio input. So it reads from that device for the audio and then it outputs audio to whatever is the default in your mixer, which is normally your sound card.

MythTV is the same, just point it to the proper /dev/dspX device under the Capture Card settings for the back-end, and it will play the audio just fine if you configured the front-end for ALSA:default for the mixer.

TVTime doesn't have any way of specifying what device to get audio from. You can use little tricks like using sox to pipe things directly like this:

sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

However, the audio and video will never stay in synch by doing this. So I don't recommend it as a solution. TVTime is nice, but just doesn't appear to be able to deal with this type of audio setup where the audio is DMA transferred off the TV card instead of being piped out via an audio jack that is looped into the sound card.

VLC also works just fine, as long as you point it to the proper /dev/dspX device for audio and /dev/videoX for video. On my system this is /dev/video0 for the TV and /dev/dsp1 for the audio. It might be possible to specify an ALSA hardware ID for audio, but I didn't dig deep into it. Using the OSS emulation works just fine.

So for those doing NTSC (or PAL), I would recommend using MPlayer, VLC, or MythTV for watching TV. MPlayer and VLC you'll have to spend some time setting up for doing stuff like changing channels or using an IR remote. MythTV you don't have to do this of course, but MythTV requires a lot of set up on its own. All these programs do some buffering and mixing that keeps the audio and video in synch, so they work decently.

But once you are over the first hurdle of getting audio and video, everything else is just getting down to playing with configs for your favorite TV apps.

BTW, the IR remote also works pretty much. Hitting the Mute button on the remote actually mutes the audio, the volume buttons work, the shutdown button even brings up the dialog box for shutting down the computer. Number keys all work. So if you haven't put the batteries in the remote yet, hunt them down and have some fun playing around with it. :)

---

### Post by cluepon on 2008-01-24
And now, to see if we can get the radio tuner working somehow. =)

---

### Post by weux on 2008-01-24
Just checked back, tried the firmware and it works great.  I still am unable to tune HD channels though.  Has anyone got it working?  If you have I would be interested in hearing how.

Update:  I also got sound working, but it sounds horrible.  I am wondering if I did it right.  Has anyone got the sound to sound good?

---

### Post by PermuZero on 2008-01-26
Thanks for the help everyone! I got the video and sound working great.

---

### Post by cluepon on 2008-01-30
So, has anyone had any success in getting the Radio Tuner working at all? 

Ive tried with KRadio, and a few others...with no luck.

---

### Post by wizkey on 2008-02-01
> **weux said:**
> Just checked back, tried the firmware and it works great.  I still am unable to tune HD channels though.  Has anyone got it working?  If you have I would be interested in hearing how.

Update:  I also got sound working, but it sounds horrible.  I am wondering if I did it right.  Has anyone got the sound to sound good?

I also found the audio to be of poor quality.

In order to get halfway decent sound, I set the treble and bass down, as well as reducing the master volume. I used the volume control on the speakers to increase the volume.

When playing audio from other applications, I set it back to the previous levels.

---

### Post by michaeld003 on 2008-02-09
I believe I have installed the firmware and driver correctly but when I open tvtime and scan for channels I get nothing but a blue screen, anyone know what I am doing wrong?

---

### Post by tommyp on 2008-02-13
I too have installed the drivers and firmware.   My card is now recognized in Mythtv.  What type of card should it be called in the backend setup?  PC HDTV?  Analog v4l?  DVB?

I have not been able to get OTA digital TV (scanning for channels has not worked).  Has anyone else got it working?

---

### Post by xphelanx on 2008-02-14
I too am having some issues with this card. I am trying it with Time Warner Digital Cable. I checked the specs on my STB and it does QAM64/QAM256. I should supposedly be able to tune those channels with this card, correct? I scan with it set up as DVB scanning Cable High / QAM64 and it finds several channels. Upon choosing "watch tv" in the mythbuntu menu, I am able to choose the dvb input and tune to the channels that were added when I scanned. However, there is nothing on these channels and I get a message saying that I should have gotten a channel lock already and I can change inputs/cards. If it leave it at that message then it comes up with an error saying there was a problem displaying the video and it bumps me back to the main menu. I can then go back into "watch tv" and change my card to the analog tuner. This works great with two exceptions: there is no sound (I have tried using sox to listen to dsp1, but it loses synch and it just keeps playing if I pause or rewind) the next exception is only that it has a mildly nasty bit of crackle at the top of the screen. Well, I think that pretty much sums up just about any problem anybody has ever had with this card. Lucky me. If anybody can help me out, I would be forever grateful.

EDIT: I fixed the audio and am now realizing exactly what I'm up against. I am only going to be able to tune unencrypted channels (If I'm wrong, please let me know) At least now I have everything set up properly, edited out the untuneable channels and all I need to do is fix the static at the top.

---

### Post by wizkey on 2008-02-19
In regards to scratchy, tinny sound:

I've found that the OSS emulation for capture off the TV card is responsible for the poor sound, at least on my system. So if you use /dev/dspX as your audio input, it may sound like crap. If instead I specify to use the ALSA capture, it sounds smooth as silk.

So for example, mplayer using OSS:

mplayer tv://54 -tv driver=v4l2:chanlist=us-cable:adevice=/dev/dsp1:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=NTSC-M:buffersize=128:width=720:height=480

mplayer using ALSA:

mplayer tv://54 -tv driver=v4l2:chanlist=us-cable:alsa:adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=NTSC-M:buffersize=128:width=720:height=480


Not all programs can use ALSA for audio input. For example, I don't believe MythTV can.

So if your sound is crappy, give the ALSA capture a try if it is an available option.

---

### Post by destructar on 2008-02-19
I'm having issues with this now as well. I've followed all instructions found here:
[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29)

I've been trying to install MythTV all day.
I was able to get video working via the AV cables, but no audio. Audio works for everything else in the system, but not the capture card.
I'm also completely unable to get any HD channels.
Using VLC I was able to get some really terrible audio. I looked for help in #ubuntu and was told to upgrade my ALSA drivers (to 1.0.16 i believe).

After doing this the only change was a lack of audio in VLC (while using the capture card that is).

I'm pretty much at my wits end. Should I just return this card or am I missing a step?

Relevant system information:
AMD 64 processor
Asus M2A-VM HDMI motherboard
Ubuntu 7.10
Pinnacle PCTV HD PCI capture card

---

### Post by wizkey on 2008-02-21
The crappy audio in VLC is due to the fact that VLC can't handle ALSA input, so you have to use the OSS emulation device that ALSA creates, which will be something like /dev/dspX. Same goes for MythTV.

They can both *output* to ALSA, they just can't get their audio *input* from ALSA.

The crappy sound is because of the OSS emulation. I found this out when I changed mplayer to use ALSA for the input instead of the /dev/dspX device. You can look at my previous post for an example of how to specify ALSA for the audio input device.

To find out what the ALSA ID is, go to a terminal and type:

arecord -l (that's a lowercase L)

You should see something like this in the list:

card 1: CX8801 [Conexant CX8801], device 0: CX88 Digital [CX88 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So the ALSA ID, in my case, would be hw.1,0. The 1 specifies the card #, and the 0 specifies the subdevice.

That is how to get the audio directly from the card.

A lot of the newer cards output audio via DMA, instead of having an audio out jack that you then have to loop to your line-in on your soundcard. This is one such card.

Unfortunately, a lot of TV apps just can't do ALSA audio input. That's why ALSA creates an OSS emulation device, so those apps that can only do OSS for audio input can get sound. The problem with that is the sound is really crappy from that emulation device.

I settled on using mplayer, since it can handle ALSA audio input. The sound is night and day better using ALSA directly instead of using the OSS emulation.

---

### Post by jmore9 on 2008-03-24
[SIZE="5"]After several hours of trying different apps to make a channels.conf i finally got one for this card using the standard scan command.  I then fired up tv time and i have a whopping 2 channels.  I guess tv time does not do qam.  Kaffeine just would not work for me.  would not find device nor find the channels.conf  file.  So now i need to find a viewing apt for this card other than tv time.  I was thinking of Klear so i might as well give it a try.  Any ideas  there are more than 2 channels out there.

jeff[/SIZE]

---

### Post by caviidae on 2008-03-26
This card works really great for me with MythTV, **after installing the afore mentioned firmware!**

NTSC over the air uses v4l on /dev/video* (Conexant chip)
- reception is ok
- sound is funny if /dev/dsp1 is used (OSS emulation)
- 'alsamixer -c1' can be used to adjust input so sound is not so tinny

ATSC over the air uses dvb (Samsung chip)
- reception is really great
- sound is perfect
- HDTV works fine (uses neraly all of old 1.8Ghz processor)

Radio doesn't seem to work, no /dev/radio*. I don't have cable so I can't comment on QAM but the internet tells me it works.

EDIT: QAM may have few channels because with cable they are often encrypted. Call you cable company and ask. If you have an encrypted cable system a STB with firewire out is the path of least resistance.

---

### Post by jmore9 on 2008-03-28
Hello !

I have gotten all the way through the qam scan with this card and it sees about 55 channels on qam (comcast) I would believe from using it in windows that only about 15 or so are in the clear.  But it does not display the ones it finds (the locals) as it does in windows.  I am looking into that.  It does show a couple of channels under the analog cable area using tvtime to view.  so i have aways to go to get it working properly in kubuntu.  I am using 8.04

---

### Post by bulldog885 on 2008-04-13
I have  a pctv i800 under Heron (2.6.24-12) the video works, but tuner sound device does not even show up in the sound card liisting or even dmesg..... anyone  have this problem?
 

cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe024000 irq 18

nvidia is my sound card

I using the vldl-dvb tree through hg (mercu..) and firmware

any help would be appreciated

---

### Post by jmore9 on 2008-04-16
I am still trying to get the channels.conf for this cad.  I ran w_scan and got the following any ideas ?

jeff@c-71-205-135-55:/usr/local/src/w_scan-20080105$ ./w_scan -fc -k >channels.dvb
w_scan version 20080105
Info: using DVB adapter auto detection.
Info: unable to open frontend /dev/dvb/adapter1/frontend0'
Info: unable to open frontend /dev/dvb/adapter2/frontend0'
Info: unable to open frontend /dev/dvb/adapter3/frontend0'
main:2401: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.
jeff@c-71-205-135-55:/usr/local/src/w_scan-20080105$ 

The scan with dvb-utils sees the tuner and scans but only gives me a initial-tuning-data.txt file.  I have no idea how to turn this into a kaffeine usable channels.dvb or channels.conf. anyone have any ideas ?  I am lost on this

I also get some of the following :

warning: filter timeout pid 0x1ffb

Hope someone has some ideas.

---

### Post by jmore9 on 2008-04-16
In addition to my post above this is some of the scan output:

jeff@c-71-205-135-55:~$ scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256 >initial-tuning-data.txt
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 57000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 63000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 69000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 69000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 79000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 79000000:QAM_256 (tuning failed)

WARNING: >>> tuning failed!!!
>>> tune to: 525000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 531000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 537000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 543000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 549000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 555000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 561000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 567000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 573000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 579000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 585000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 591000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 597000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 603000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 609000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 615000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 621000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 627000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 633000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 639000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 645000000:QAM_256
WARNING: filter timeout pid 0x1ffb
>>> tune to: 93000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 93000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!

>>> tune to: 801000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (373 services)
Done.
jeff@c-71-205-135-55:~$ 

Just pices of the scan outpur not all of it

---

### Post by jmore9 on 2008-04-16
And here is some of the intial-tuning-data.txt file:

[0001]:621000000:QAM_256:1984:1985:1
[0003]:621000000:QAM_256:2048:2049:3
[0002]:621000000:QAM_256:2112:2113:2
[0003]:627000000:QAM_256:1984:1985:3
[0002]:627000000:QAM_256:2048:2049:2
[0001]:627000000:QAM_256:2112:2113:1

[0003]:651000000:QAM_256:1984:1985:3
[0005]:651000000:QAM_256:2048:2049:5

[0008]:705000000:QAM_256:1984:1985:8
[0023]:705000000:QAM_256:2048:2049:35
[0029]:705000000:QAM_256:2112:2113:41
[0003]:705000000:QAM_256:2176:2177:3
[0011]:705000000:QAM_256:2240:2241:17
[000f]:705000000:QAM_256:2304:2305:15
[002b]:705000000:QAM_256:2368:2369:43
[000d]:705000000:QAM_256:2432:2433:13
[0015]:705000000:QAM_256:2496:2497:21
[0013]:705000000:QAM_256:2560:2561:19

[000b]:759000000:QAM_256:1984:1985:11
[000c]:759000000:QAM_256:2048:2049:12
[0010]:759000000:QAM_256:2112:2113:16
[000f]:759000000:QAM_256:2176:2177:15
[000d]:759000000:QAM_256:2240:2241:13
[000e]:759000000:QAM_256:2304:2305:14

Are these actual channels or what , anyone have any idea ?

---

### Post by jmore9 on 2008-04-16
I started a new thread under multimedia called ME TV.  Should check it out that app works very good and does most of your work for you

---

### Post by jmore9 on 2008-04-20
I have a list of stations in the left pane of kaffeine but i still am not able to get kaffeine to tune any channels.  Any ideas ?

---

### Post by rgb1701 on 2008-04-28
> **caviidae said:**
> This card works really great for me with MythTV, **after installing the afore mentioned firmware!**

NTSC over the air uses v4l on /dev/video* (Conexant chip)
- reception is ok
- sound is funny if /dev/dsp1 is used (OSS emulation)
- 'alsamixer -c1' can be used to adjust input so sound is not so tinny

ATSC over the air uses dvb (Samsung chip)
- reception is really great
- sound is perfect
- HDTV works fine (uses neraly all of old 1.8Ghz processor)

Radio doesn't seem to work, no /dev/radio*. I don't have cable so I can't comment on QAM but the internet tells me it works.

EDIT: QAM may have few channels because with cable they are often encrypted. Call you cable company and ask. If you have an encrypted cable system a STB with firewire out is the path of least resistance.

I assume this card we are talking about in this thread is:

[http://www.bestbuy.com/site/olspage.jsp?skuId=8512424&type=product&id=1186005934822&ref=06&loc=01&ci_src=14110944&ci_sku=8512424](http://www.bestbuy.com/site/olspage.jsp?skuId=8512424&type=product&id=1186005934822&ref=06&loc=01&ci_src=14110944&ci_sku=8512424)

Could you post your step-by-step for getting HD over the air to work in Myth?  

I downloaded the firmware from:

[http://steventoth.net/linux/xc5000/](http://steventoth.net/linux/xc5000/)

and copied to my /lib/firmware/$KERNAL directory, then ran MythTvsetup from MythBuntu Control Center (using MythBuntu 8.04, Hardy Heron):

2. Capture cards -> (New capture card) ->  Card Type : DVB DTV capture card (V3.x)

Nothing is available in the "DVB Device Number:" field.  What do you put there?

Also, the next field reports:

Frontend ID: Could not get card info for card #0 Subtype: Unknown 

What else do I need to do?

---

### Post by rgb1701 on 2008-04-29
To further elaborate on what I tried, I found the v4l site for this card here

[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29)

I downloaded the latest v4l-dvb driver set from
[http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

I extracted from the tar.gz file, then did the 

make 

then 

sudo make install

both without issue.

I rebooted, then ran Myth Backend setup again, selecting the same DVB option for capture card, but got the same results as te last post.

What options do you set in Myth setup or myth config fil(s) to get Myth to recognize and work with this card for ATSC and analog OTA?

---

### Post by rgb1701 on 2008-04-30
Do I need to add anything to the /etc/modules file to make Myth recognize the Pinnacle 800i for ATSC (DVB)?

---

### Post by caviidae on 2008-05-05
After **upgrading to 8.04** this card will stop working. See [bug #220857]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/220857") for details.

For those in need here is a quick list of getting this card working.

Get the firmware from the windows driver. [Driver file and extract.sh]("http://www.steventoth.net/linux/xc5000/") put it in /lib/firmware/<kernel version>

Get [v4l]("http://linuxtv.org/hg/v4l-dvb/summary"). un-tar, make, sudo make install

Read [Bug#220857]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/220857") so you know the consequences of this next part.
```
sudo rm -rf /lib/modules/`uname -r`/ubuntu/media/cx88
sudo rm -rf /lib/modules/`uname -r`/ubuntu/media/saa7134
sudo depmod -a
```

That gets digital broadcasting and the remote working for me, but YMMV.

---

### Post by eelliott884 on 2008-05-24
Ok i've been working on this forever!!! i am running hardy with a pinnacle 800i and CANNOT get the sound to work.  If i play an mp3 file or such it works, but whenever i try to watch tv i can only get a picture with no sound.  i followed the above mentioned steps with no success.  i am using an asus p5w motherboard with onboard sound.  does anyone have any ideas as to how to get the sound to work?  

if i do cat /proc/asound/cards it will only list the onboard sound and if i do modprobe cx88-alsa it says that there is no such module.  Any help would be much appreciated.

---

### Post by jjwhitte on 2008-05-27
Hi,

I have the same audio problems as these people: 


> **bulldog885 said:**
> I have  a pctv i800 under Heron (2.6.24-12) the video works, but tuner sound device does not even show up in the sound card liisting or even dmesg..... anyone  have this problem?
 

cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe024000 irq 18

nvidia is my sound card

I using the vldl-dvb tree through hg (mercu..) and firmware

any help would be appreciated

> **eelliott884 said:**
> Ok i've been working on this forever!!! i am running hardy with a pinnacle 800i and CANNOT get the sound to work.  If i play an mp3 file or such it works, but whenever i try to watch tv i can only get a picture with no sound.  i followed the above mentioned steps with no success.  i am using an asus p5w motherboard with onboard sound.  does anyone have any ideas as to how to get the sound to work?  

if i do cat /proc/asound/cards it will only list the onboard sound and if i do modprobe cx88-alsa it says that there is no such module.  Any help would be much appreciated.

I installed Mythubuntu 8.04, then followed the procedure given here (firmware and v4l driver):

[http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29](http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29)

Then:

sudo rm -rf /lib/modules/`uname -r`/ubuntu/media/cx88
sudo rm -rf /lib/modules/`uname -r`/ubuntu/media/saa7134
sudo depmod -a

I found that I do get audio when using DVB, but the volume is extremly low or "tinny". Using alsamixer, I put all the volume to 100 and turned my speakers up as loud as possible, but the volume is still low - sound quality seems good though.

I get no audio in analog. How do you get the sound capture portion of the 800i card to be recongized? Does anyone have a sound solution? Please post!!!

Thanx!!!

---

### Post by boyd98 on 2008-06-22
Bumpity - I have the same exact sound problems - 

Has anyone figured this out.  Im using analog only and I have no sound.

My tuner card does not show up in /proc/asound/cards.  Just my soundblaster live card??  /dev/dsp?  Do i need to see it in /asound/cards - should it exist as dsp2?



If anyone has fixed this, please shed some light.  I just about have my linux box where i want it, except for this stupid tuner card...


TIA,

Boyd

---

### Post by Marsupilami23 on 2008-06-24
I've found the issue that cx88-alsa is not being built in the updated v4l-dvb. Not exactly sure why this is, no errors while building the rest of the modules. I'm not a developer, just a user/meddler. But I can share with you I'm really disappointed in Ubuntu at this time. Might have to go back to using Gentoo. :(

---

### Post by boyd98 on 2008-06-25
hmmm - yea i agree with your assessment since when i install the v4l drivers they remove my cx88 from /proc/asound/cards

im holding out for a little while, but so many ppl seem to have the same issue, there's got to be a workaround; but like you, im no developer

---

### Post by MrMunkily on 2008-06-29
So, from what I understand, there is a fairly serious issue with trying to compile & install recent or possibly any cx88-alsa module with a current ubuntu kernel. I got bitten by this because I needed to recompile to use my 800i - and it's knocked out sound for my analog pcHDTV HD5500 input as well, since both cards analog audio need this module - and NEITHER has a audio out jack so that I can do the old outside loop to line in trick.

v4l didn't compile it by default, which was odd.

So, I tried adding the option to compile the cx88-alsa module to the v4l tree (add a line saying ```
CONFIG_VIDEO_CX88_ALSA=m
``` to the .config file in the v4l subdirectory) and recompileing. This DID build a cx88-alsa.ko but with warnings of undefined symbols. I think I remember reading that it's compiling against the wrong alsa version.

When I try to load the module, it fails.

---

### Post by Marsupilami23 on 2008-06-30
That's interesting... Maybe compiling ALSA separately than the kernel would fix this problem. I've decided to move on to MythDora instead, i'll let you know how well it works..

---

### Post by MrMunkily on 2008-06-30
Well, here's the thing - it would be nice to be able to run a 2.6.25 kernel on Hardy - that would avoid the need to mix n' match like this, though I'm pretty sure the core of the problem would remain, at least the hardware would work.

I wonder if Intrepid is usable at this point. I like ubuntu enough that I'd rather roll my own Myth on top of vanilla ubuntu, even if it's alpha quality, than have to learn another distro...

---

### Post by MrMunkily on 2008-07-02
An update:

I have this working - with analog sound as well.

I installed a stock 2.6.25 kernel from kernel.org, which supports the device. I had to enable a lot of disabled stuff in the kernel including basically everything in ALSA and DMA Audio for CX88.

I also had to recompile nVidia drivers, which need patching to work with 2.6.25. Lirc kernel modules were also not part of the build so I built those from source after the fact.

I'm actually a bit astounded that it booted - but it seems to be working just fine, actually.

Links:
Compile howto: [http://blog.gunbladeiv.com/2008/05/ubuntu-kernel-2625-on-hardy.html](http://blog.gunbladeiv.com/2008/05/ubuntu-kernel-2625-on-hardy.html)
nVidia: [http://www.nvnews.net/vbulletin/showthread.php?t=110088](http://www.nvnews.net/vbulletin/showthread.php?t=110088)

---

### Post by boyd98 on 2008-07-03
Is there not an easier way - is waiting for a new v4l package or ubuntu kernel not likely a fix?

---

### Post by MrMunkily on 2008-07-03
It's not going to be fixed in Hardy. Intrepid should have support built in, though.

You could try installing an intrepid kernel package on Hardy... but that's a 2.6.26 kernel and I would doubt it would work. Not something to be done lightly on a machine that sees any real use. I could distribute my vanilla kernel package, but I have no idea if it will work on machines other than mine. It's x86_64 anyway.

---

### Post by PS5000 on 2008-07-13
MrMunkily,

I compiled and installed Kernel 2.6.25 for my AMD 64 machine, as you suggested, and I am pleased that the computer actually boots up!

But I have not had any success with MythTV...  After "make menuconfig," I selected all of the options (including ALSA) under the Device Drivers|Sound tree to get  audio to work.  However I did not see how you enabled DMA Audio for specifically for CX88?

Also, I am unable to get a lock on any channel in MythTV, and I just get a blank screen.  (Previously, under Hardy, with the default kernel, I was able to view the video, without sound, of course).

Do I have to manually install the v4l-dvb driver after installing Kernel 2.6.25?

Are there any other tips you can suggest?

---

### Post by MrMunkily on 2008-07-13
Well, it *should* work... Let me try to be more explicit with what I enabled.

When you say you can't get a lock - do you mean digital channels? If so... audio should work even with the stock hardy kernel + v4l-dvb so I don't know what's up. This problem with the cx88-alsa.ko is only for analog. If you mean that you can't tune analog channels - maybe you should investigate whether the appropriate v4l device is working.

Try it in xawtv or tvtime to (with mythbackend shut down) to see if you can tune channels. Look in the /dev directory to make sure /dev/video1 or video2 or whatever actually exists.

In any case, you should definitely reset your mythtv tuners in mythtv-setup after recompiling the kernel because device nodes may move about and such.

You should definitely **not** need to install v4l-dvb.

So, in menuconfig, I enabled: 

Device Drivers->Multimedia devices->Video capture adapters->
Everything except: Enable advanced debug functionality, Autoselect pertinent, Siemens-Nixdorf..., Philips-Semiconductors...
This is the cx88-alsa option: Conexant 2388x DMA audio support

Device Drivers->Sound->Advanced Linux...-> ALSA, OSS Mixer API, OSS PCM API, OSS PCM API plugin system

Also, there were issues with my ALSA system afterwards. I had to reorder the cards:

in /etc/modprobe.d/alsa-base at the end of the file:

```
options cx88_alsa index=2,3
```

I have 2 cx88 cards, so this line tells alsa to load them into indexes 2 and 3, because index 0 needs to be the output device, which for me is snd-hda-intel. It may be different for you.

```
options snd-hda-intel index=0
```

makes my output card grab index 0.

Then you're going to need to select the proper /dev/dsp[index] device in mythtv-setup.

---

### Post by jonrober18 on 2008-07-13
I have a question for those who have the card working.  I'm having the problems with lack of sound, though have followed various instructions and have both the Pinnacle card and my normal sound card in /proc/asound/cards.  The device exists, but trying to use in mplayer gives no sound (and a note of "Audio: no sound").  

Where I'm really confused though is the Cx88 page on the v4l wiki at [http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x](http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x)) which says:
audio data dma (i.e. recording without loopback cable to the sound card) is supported since 2.6.16 (CONFIG_VIDEO_CX88_ALSA). It only works with boards with function 01 enabled. To check if your board supports it, issue lspci -n. If supported, you should see a 1471:8801 or 1471:8811 PCI device.

When I do "lspci -n | grep 1471" I get nothing.  I'd thought that meant that okay, this card isn't actually able to work for analog sound since it has no interface for a cable to the soundcard either.. but then I saw various people here saying they have it working.  My question is, is the wiki wrong/out of date, or perhaps is the function enabled on some runs of the 800i but not on others?  Could someone with working analog sound do the above grep and tell me if you have any matching lines, so I know if I should take it back or beat my head into this a little more?

---

### Post by MrMunkily on 2008-07-14
I get nothing here, and mine's working fine.

---

### Post by Marsupilami23 on 2008-07-19
OK. so following the instructions above and through much headache, I have it work with sound. The sound isn't loud but it's fine (might be my sound card Intel HD Sound, inboard) Also, does everyone have a funky bar at the top? how is the video quality?

Thanks for the help.

---

### Post by MrMunkily on 2008-07-19
You mean a black and white bar with lines and dots? That's a normal part of the signal that's cut off on regular TVs. Just scale up the output -  what program are you using?. Look up "overscan."

---

### Post by Marsupilami23 on 2008-07-20
That suggestion didn't work, it's not black line with dots... it's more like a blue bar that has movement when watching tv. Almost like video is playing on it but all funky. :)

---

### Post by Marsupilami23 on 2008-07-22
OK, so a little reading up and it is the overscan. I can live with it. Now I'm working on getting the remote to work. I have gotten the number buttons to work, the pinnacle button, mute button, not too sure about the power button. But what I want to get to work are the media buttons. Any ideas?

---

