---
title: "Creative X-Fi Surround 5.1 USB"
date: 2008-10-25
forum: Hardware
---

### Post by tjodalv on 2008-10-25
I am looking for info to find out if anyone has successfully got this animal working fully, completely.  

It seems that the USB box does get recognized and it does work, however, I am interested in finding out if anyone has working the equalizer or any of the other sound functions.

Thanks.

---

### Post by mojorising on 2008-11-12
Hi. Glad to see this post reporting it works. I just bought one of these (also the USB version) for my awesome Mythbuntu box I'm building. 

I'll report my experience getting everything working here once I get it all together (that might be a while since I'm waiting for a hard drive to be delivered). 


Mike

---

### Post by mojorising on 2008-11-12
This might be good information for anyone interested in getting this device fully functional in Linux: [http://www.theinquirer.net/gb/inquirer/news/2008/11/07/creative-opens-linux-driver](http://www.theinquirer.net/gb/inquirer/news/2008/11/07/creative-opens-linux-driver)

Basically, Creative just released open source drivers and specifications on the hardware under the GPL. So the prospects look good for us to see the full power of this little baby unleashed with Linux in the somewhat near future. 


Mike

---

### Post by Daan on 2008-12-21
Which device are you talking about? Creative has chosen the names of its products in a very confusing way. At the bottom of my external Creative USB sound card, which has a X-Fi logo on it, it says "Model No. SB1090". At http://ask.creative.com/SRVS/CGI-BIN/WEBCGI.EXE?New,Kb=ww_english_add,Company={D0F19C16-3B20-4E69-BC69-7F708173173D},VARSET=ws:[http://nl.europe.creative.com/,VARSET=ws:http://nl.europe.creative.com,case=10846](http://nl.europe.creative.com/,VARSET=ws:http://nl.europe.creative.com,case=10846) it says

"This list is provided for your convenience for matching product model numbers with product names in case you need to download 
updated drivers, applications, or obtain product information."

And one entry in the list is 

Sound Blaster Surround 5.1  	                                 SB1090

However, there are no products to be found with this exact name elsewhere on the site. Nor does the model number yield any results, except for the list.

Anyway, the Creative open source driver spoken of above does not work with the USB card (SB1090). A generic snd_usb_audio Linux driver does work and gives stereo through analog and optical outs on the device. No 5.1 surround I think.

---

### Post by ilovemoon86 on 2009-01-07
hi guys!
I also have this USB soundcard...could you tell me how to make it work? :confused: 
I haven't managed to do this yet... :(

---

### Post by MrGrieves on 2009-01-12
I'm thinking of buying this item.  I'll however wait until I'm certain I can get it working with full 5.1.

I'd probably buy any low-cost usb to analog 5.1 device if only I knew that ubuntu was going to support it without too much pain.

---

### Post by quantenmetz on 2009-02-09
Hey,

I have it working using PulseAudio.
I used to have distortions and errors with ALSA and OSS, but with PA it runs perfectly so far. I have my sound system connected through the optical out though, can't give any information about surround sound with analogue speakers...

If you have mutliple soundcards and fear PulseAudios configuration files, there are small configuration tools (paconfig for example, I found it somewhere in the forums) that do the job for you. A restart seems to be required, though.

Greetings

Q

---

### Post by rique87 on 2009-03-03
hey i just bought that card, too.
it does work but not better then my onboard-card!
i'd like to enjoy the great sound i get when i use windows.
isnt there a linux driver that can at least enhance the sound? i'd like to use the remote as well but i dont mind if its not working anyway ;)

---

### Post by xjgnsdof on 2009-09-06
I just got this card and can't get it running right in 9.04. I get sound, but I can't control volume through the device/knob. Will the people who got this working elaborate on what they did? This isn't exactly plug and play.

---

### Post by Etheral_Reality on 2009-09-08
yea i just got this too, and would like to know if anyone got 5.1 working and how

---

### Post by xjgnsdof on 2009-09-20
Use PulseAudio to get the USB sound card to play suround sound.

1) Go to [this post]("http://ubuntuforums.org/showthread.php?t=789578") to set up your PulseAudio sound server properly.

2) Go to [this post]("http://ubuntuforums.org/showthread.php?t=795525") to set up surround sound. I did the "Easy Way."

If you don't hear anything when you play something (e.g., a YouTube video), that means the default sound server (usually ALSA) is playing the stream, not PulseAudio (which is what your USB sound card uses). To fix this, go into PulseAudio Volume Control and simply redirect the stream to the X-Fi Surround USB. 

1) Look through the tabs until you see the active sound server--you can tell what it is because the sound bars will be moving left to right.
2) Click the down arrow in that section, which is off to the right.
3) Select "redirect stream" or something like that (I don't have it in front of me) and pick the X-Fi Surround USB. You'll have to do this only once for each sound source that picks the wrong (i.e., non-X-Fi)

---

### Post by Etheral_Reality on 2009-09-20
do you still get a crackling/popping noise when you do this?

---

### Post by xjgnsdof on 2009-09-20
Yes, occasionally when I stream videos off my hard drive, but I suspect that has to do with my WiFi network or media player (Totem) because YouTube sound is crystal clear. It's not frequent or irritating, though.

---

### Post by ceminino on 2010-02-12
I just can't manage to have surround sound on karmic with S/PDIF, the howto didn't help. I changed /etc/pulse/daemon.conf to have 6 channels but only the two front speakers work. Did someone manage to make it work?


EDIT: it seems impossible unfortunately for the moment...
[https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=xfi](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=xfi)

---

### Post by ODECiF on 2010-03-03
Hello everyone! My first port at Ubuntuforums.

I do have discovered that the Creative X-Fi USB 5.1 soundcard is supported in Ubuntu 9.10 (or well, at least the stereo-output) out-of-the-box!

I got surprised by this when I was using Slackware 12.2, because there I had to get into the blacklist at the /etc/init.d/-folder and blacklist my original onboard soundcard in order to make the USB-soundcard work. But in Karmic, all I needed to do was to get into System->Preferences->Sound (and in there it found the soundcard by itself), disable the onboard card, and then the X-Fi card just popped in automatically.

Also, I can adjust the volume in Ubuntu (or well, I can use the volume up, down and mute-button on my keyboard) and it works!

I hope that I've provided some information that may come in handy for someone else

//ODECiF

---

### Post by ceminino on 2010-03-04
> **ODECiF said:**
> Hello everyone! My first port at Ubuntuforums.

I do have discovered that the Creative X-Fi USB 5.1 soundcard is supported in Ubuntu 9.10 (or well, at least the stereo-output) out-of-the-box!

I got surprised by this when I was using Slackware 12.2, because there I had to get into the blacklist at the /etc/init.d/-folder and blacklist my original onboard soundcard in order to make the USB-soundcard work. But in Karmic, all I needed to do was to get into System->Preferences->Sound (and in there it found the soundcard by itself), disable the onboard card, and then the X-Fi card just popped in automatically.

Also, I can adjust the volume in Ubuntu (or well, I can use the volume up, down and mute-button on my keyboard) and it works!

I hope that I've provided some information that may come in handy for someone else

//ODECiF

Yeah stereo does work fine, but what's the point of having a surround sound card if it doesn't work... I have to watch my movies on zindowz... Moreover the crystalizer feature doesn't work either, and it really makes a world of difference...

---

### Post by ODECiF on 2010-03-19
I am currently using the X-Fi USB card for my laptop, since I broke the built-in soundcards output when I dropped it with a cable into it. So for me, it is a huge different :o)

---

### Post by szponzor on 2010-03-23
Can you use the remote control on Ubuntu?
I would like to buy a Creative Surround 5.1 and the remote control is important for me.
Did somebody tried it on Lucid?

---

### Post by l3lackEyedAngels on 2010-07-23
I would like to rip some vinyl, and the [Creative Sound Blaster X-Fi Surround 5.1 SB1090]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829102020") [SIZE=2][FONT=Arial]seems like the right device to connect to my laptop running 10.04 and get the job done. Can anyone report if, while running Ubuntu, they've been able to record through the line-in on this device at 24 bits and 96kHz?
[/FONT][/SIZE]

---

### Post by sabujakash on 2010-10-02
Can somebody confirm it the six channel audio works in fine in 10.04 ? I am planning to buy one 5.1 usb soundcard for my laptop. 
Or if somebody else can suggest someother 5.1 usb sound card where 6 channel audio would work flawlessly that would be also of great help.
Thanks...

---

### Post by ceminino on 2010-10-03
> **sabujakash said:**
> Can somebody confirm it the six channel audio works in fine in 10.04 ? I am planning to buy one 5.1 usb soundcard for my laptop. 
Or if somebody else can suggest someother 5.1 usb sound card where 6 channel audio would work flawlessly that would be also of great help.
Thanks...

yes it finally works with VLC.
 
In Sound Preferences, select "Analog Stereo Duplex" (don't ask why!)
In VLC preferences, select "All" in "Show Settings" and go to audio options
Enable "Use S/PDIF when available"
Set "Force Detection of Dolby Surround" to "Off" (should be standard)
In "Output Modules", select ALSA
In the "ALSA" tree node, I selected "SB X-Fi Surround 5.1: USB Audio #1 (hw:1,1)"

---

### Post by Corin-EU on 2010-10-23
Has anybody got LIRC working with this USB sound device?

---

### Post by mndar on 2010-10-24
I have the volume knob working fine with Lirc. This is how you can get it working. [http://mndar.phpnet.us/usbxfi/](http://mndar.phpnet.us/usbxfi/)
I don't have a remote. Can you check if the remote works with the changes given there.

---

### Post by Nightwolf on 2010-11-02
I just bought a Creative X-Fi Surround 5.1 USB and can't get 5.1 work. I followed the instructions of ceminino and also created a .asoundrc in my home directory as described [here]("http://linux-tipps.blogspot.com/2010/06/creative-x-fi-surround-usb-guide-for.html"). After Logout/Login it is still stereo when I choose Alsa in VLC and audio doesn't work via Pulseaudio at all. I don't want to remove Pulseaudio completely, because I don't want to mess up the settings with my internal stereo audio card. Any suggestions?

Edit: Seems like everything works correctly if the card is plugged in when booting the computer.

Edit2: I just tried to get my volume knob and the remote working. I followed [mndar's howto]("http://mndar.phpnet.us/usbxfi/") but when I run irw and turn the knob or press any buttons on the remote, I see no codes at all. Does this maybe have something to do with having know mixer for the device in alsamixer (at least it is listed there)? Would be cool, if you (mndar) or anyone else could help me here. :-)

Edit3: syslog says "cannot open hw:S51: No such file or directory"

---

### Post by mndar on 2010-11-05
After applying the patch, can you compile alsa-driver-1.0.23 with debug enabled?
You have to pass "--with-debug=full" to the configure script to do so. 

Once its compiled and installed, rmmod all sound modules, reload snd-usb-audio (or just reboot) and check dmesg and  /var/log/messages. Turning the volume knob (and probably pressing buttons on the remote) should generate messages like
*[COLOR="Gray"]ALSA mixer.c:1994: status interrupt: c0 00[/COLOR]*.

Just to confirm, you used [alsa-driver-1.0.23](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2) from [http://alsa-project.org/main/index.php/Main_Page](http://alsa-project.org/main/index.php/Main_Page) , right?
[quote=Nightwolf]Edit3: syslog says "cannot open hw:S51: No such file or directory"[/quote]Run **cat /proc/asound/cards** 
What does that say?

To confirm that lirc has the alsa_usb driver, run
**lircd --driver=help**

Edit: [quote=Nightwolf]Does this maybe have something to do with having no mixer for the device in alsamixer[/quote]Nope. Its got nothing to do with that.

Which Ubuntu version are you using? With 8.04, I use ```
./configure  --with-cards=usb-audio,hda-intel --with-debug=full --with-moddir=/lib/modules/2.6.24-24-generic/ubuntu/sound/alsa-driver/
``` then do make and make install. Make sure you backup /lib/modules/2.6.24-24-generic first. 

Also, blacklist the module for your existing sound card in /etc/modprobe.d/blacklist and comment the line [COLOR="Gray"]*options snd-usb-audio index=-2*[/COLOR] in /etc/modprobe.d/alsa-base so that this card can become your first card.

---

### Post by Nightwolf on 2010-11-06
Thanks for your help. I actually came to the conclusion that I don't really need the remote and the volume knob, so I won't put any more time in this. Sorry that I didn't write this before your post, mndar.

---

### Post by mndar on 2011-01-06
The latest stable kernel release (2.6.37) from [http://www.kernel.org/](http://www.kernel.org/) has support for both, the volume knob and Power/Status LED 
I tested it and everything works fine.

Edit: alsa-driver-1.0.24 too has these changes but I haven't tested it yet.

---

### Post by axel22 on 2011-01-17
> **sabujakash said:**
> Can somebody confirm it the six channel audio works in fine in 10.04 ? I am planning to buy one 5.1 usb soundcard for my laptop. 
Or if somebody else can suggest someother 5.1 usb sound card where 6 channel audio would work flawlessly that would be also of great help.
Thanks...

Ubuntu 10.04, kernel version 2.6.34, pulseaudio.

It detects the sound card, works fine for me, UNTIL you turn on skype/vlc/flash browser plugin. At this point it pops whenever something changes on the screen (e.g. desktop change, animations, opening a terminal, and don't even dream about xbmc). I am dying at this point.

If anyone knows how to solve this, I'd be extremely grateful.

---

### Post by Forlong on 2011-04-29
> **mndar said:**
> I have the volume knob working fine with Lirc. This is how you can get it working. [http://mndar.phpnet.us/usbxfi/](http://mndar.phpnet.us/usbxfi/)
I don't have a remote. Can you check if the remote works with the changes given there.
Since I'm on natty, I already have the proper kernel but I don't know anything about Lirc.

What "Remote control configuration" should I choose when setting up Lirc for the first time?

---

### Post by mndar on 2011-04-30
> **Forlong said:**
> What "Remote control configuration" should I choose when setting up Lirc for the first time?

The creative lircd.conf that comes as part of the lirc package works for this volume knob. Its location is *[COLOR="DimGray"]/usr/share/lirc/remotes/creative/lircd.conf.alsa_usb[/COLOR]*

You need to start lircd as root.

However, I am yet to test the volume knob under Natty.

---

### Post by Forlong on 2011-04-30
> **mndar said:**
> The creative lircd.conf that comes as part of the lirc package works for this volume knob. Its location is *[COLOR="DimGray"]/usr/share/lirc/remotes/creative/lircd.conf.alsa_usb[/COLOR]*
Right, I got that. It's just, when you install lirc for the first time, it asks you what "Remote control configuration" you want to use.

Anyway, I chose "None" for now and copied that config over to /etc/lircd.conf
> **mndar said:**
> You need to start lircd as root.
Thanks, OK, i did that. But when I run irw now, there's no feedback in the terminal whatsoever, neither from the knob nor the remote. :(


edit: just to clarify: the soundcard itself works fine and the 'Power LED' entry in alsamixer works too (there's no other volume control beside that).

---

### Post by mndar on 2011-04-30
> **Forlong said:**
> 
edit: just to clarify: the soundcard itself works fine and the 'Power LED' entry in alsamixer works too (there's no other volume control beside that).

If the 'Power LED' control works, the volume knob should work as well since the patch for 'Power LED' was submitted after the one for the volume knob.

> **Forlong said:**
> 
Anyway, I chose "None" for now and copied that config over to /etc/lircd.conf


Did you do this
*cp /usr/share/lirc/remotes/creative/lircd.conf.alsa_usb /etc/lircd.conf*
and then restart Lirc?

---

### Post by mndar on 2011-05-16
Here is the LIRC config posted on the alsa-devel mailing list
[http://mailman.alsa-project.org/pipermail/alsa-devel/2011-May/039764.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2011-May/039764.html)

---

### Post by jjpdijkstra on 2011-06-06
Dear Axel,

have you found a solution to the soundproblems with pulse and x-fi. I am really looking for a solution. Please respond with steps and maybe attached asound.conf or .asoundrc

Thanks

---

### Post by wkpalan on 2011-06-09
The speaker starts to screech the moment Ubuntu starts. It keeps on screeching when any music is played through it. If anyone have any clue of how to fix this, please post it.

I'm running Natty, and using a creative Inspire T6160, the sound works normally in windows.

---

### Post by puetzstef on 2011-06-26
I can confirm the problems in Natty. Also tried Oneiric live cd with the new 3.0 kernel. Problem still exists. It seems that the x-fi usb is only recognized as a usb 1.1 device instead of usb 2.0 and the bandwith is too small then. 
There is a bugreport in launchpad already and I wrote the last comment. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798795?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798795?comments=all)

---

### Post by RussianNeuroMancer on 2011-12-07
Did anyone get remote control working with Natty or Oneiric? I was try this [http://permalink.gmane.org/gmane.linux.alsa.devel/85007](http://permalink.gmane.org/gmane.linux.alsa.devel/85007) and this [http://lirc.sourceforge.net/remotes/creative/RM-850](http://lirc.sourceforge.net/remotes/creative/RM-850) config but remote control doesn't work anyway (irw is keep silence). I dunno where is the problem: on ALSA level or on LIRC level?

---

### Post by burned_ on 2011-12-07
I didn't get the remote/volume knob working since i read your post now. I added the config from your first link to my /etc/lirc/lircd.conf and restarted lirc and now if I start irw the volume knob triggers some events:

```
$ irw
0000000000000010 00 vol+ RM-1500
000000000000000f 00 vol- RM-1500
000000000000000d 00 mute RM-1500
```I don't have the remote here, so I can't try it right now.

---

### Post by RussianNeuroMancer on 2011-12-07
Can you post please your hardware.conf and Ubuntu version?

---

### Post by burned_ on 2011-12-07
Oo ... I just noticed, that it already worked (must have something to do with the last dist-upgrade, because last time i tried it didn't work)
...anyway, my hardware.conf:

```
REMOTE="Creative USB IR Receiver (SB0540)"
REMOTE_MODULES=""
REMOTE_DRIVER="alsa_usb"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="creative/lircd.conf.alsa_usb"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

I think this should already do the trick ;)
(I'm using Kubuntu 11.10)

---

### Post by RussianNeuroMancer on 2011-12-07
Thank you! REMOTE_DRIVER="alsa_usb" did the trick. Looks like there is no need for external config. You can just install LIRC, select "Creative USB IR Receiver (SB0540)" remote, "None" transmitter, and replace REMOTE_DRIVER to "alsa_usb" after installation. Then RM-850 detected like RM-1500. Almost all necessary buttons (and knob too) work except Left and Right buttons on remote. Looking at lircd.conf.alsa_usb I can say probably this two buttons have right codes in config:```

        up        0x1d
        left      0x1e
        ok        0x1f
        right     0x20
        down      0x21
```But Left and RIght not detected anyway. There is any way to find right codes for this two buttons?

---

### Post by RussianNeuroMancer on 2011-12-07
I found right codes for Left and Rigtht buttons. It's a 0x27 for Left and 0x28 for Right. To get remote control working with Creative X-Fi Surround 5.1 install lirc package, While installation select None receiver, and None transmitter. After installation set REMOTE_DRIVER="alsa_usb" and START_LIRCD="true" in /etc/lirc/hardware.conf. Download [this lircd.conf]("http://www.mediafire.com/?9n9bsez1e5p8go2") to /etc/lirc (I also put crystalizer and cmss buttons to config, so you can use this buttons for other applications).

---

### Post by DemonSpeedster on 2011-12-12
I'm sorry for replying an old post.

> **jjpdijkstra said:**
> Dear Axel,

have you found a solution to the soundproblems with pulse and x-fi. I am really looking for a solution. Please respond with steps and maybe attached asound.conf or .asoundrc

Thanks

[QUOTE=wkpalan]
The speaker starts to screech the moment Ubuntu starts. It keeps on screeching when any music is played through it. If anyone have any clue of how to fix this, please post it.

 I'm running Natty, and using a creative Inspire T6160, the sound works normally in windows[/QUOTE]

I managed to minimize the crackling by lowering the default sample rate. Open /etc/pulse/daemon.conf , then find

*[INDENT]; default-sample-rate = 48000[/INDENT]*

change it to:

*[INDENT]; default-sample-rate = 44100[/INDENT]*

save, and restart pulseaudio

---

### Post by adonp on 2012-08-08
Hi,

I would like somebody confirm if output analog audio signal (I don't mind digital) will be working properly for a 5.1 speaker setup following all the above instructions  from previous posts. 
I would like to connect that usb sound card with s750 gigaworks but using only my Linux OS not Windows.

I have Ubuntu 11.10 oneiric (3.0.0-23-generic)

Thank you.

---

### Post by DemonSpeedster on 2012-08-09
> **adonp said:**
> Hi,

I would like somebody confirm if output analog audio signal (I don't mind digital) will be working properly for a 5.1 speaker setup following all the above instructions  from previous posts. 
I would like to connect that usb sound card with s750 gigaworks but using only my Linux OS not Windows.

I have Ubuntu 11.10 oneiric (3.0.0-23-generic)

Thank you.

[this]("http://outhereinthefield.wordpress.com/2011/08/24/surround-sound-on-maverick-meerkat-with-creative-sb-x-fi-5-1-surround-pro-and-logitech-z506/") is what i did with XFi 5.1 USB and Logitech Z506 on 10.10. I recently found out that while the analog out works normaly, the analog in/mic in doesn't always work. I'm still trying to figure out why. The analog in (and headphone out) is connected to a Razer Chimaera wireless headset. BTW I also have this setup works under 12.04

---

### Post by adonp on 2012-08-12
DemonSpeedster thks for help and the link. 
Although I was about to buy this nice creative sound card, finally rejected my decision because my speakers suddenly failed again (after my first repair..)  and then just noticed that my laptop has 5.1 capable analog audio with its "realtec ALC665" integrated card but gives only stereo on ubuntu 11.10. Hence, I'll try fix the 5.1 issue on alc665 card first, and if I fail, or if I succeed but sound quality sucks, I'll go for creative solution.

---

