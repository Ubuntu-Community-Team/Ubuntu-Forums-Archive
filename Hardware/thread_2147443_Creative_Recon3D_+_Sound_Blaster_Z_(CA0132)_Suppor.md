---
title: "Creative Recon3D + Sound Blaster Z (CA0132) Support"
date: 2013-05-22
forum: Hardware
---

### Post by mmstick on 2013-05-22
[COLOR=#000000]I have discovered a solution:[/COLOR]

[COLOR=#333333]Someone noted that the 32-bit kernel plays just fine, but that the 64-bit kernel needs a special fix in /etc/rc.local. Add the following before exit0:[/COLOR]

[COLOR=#333333]rmmod snd_hda_intel[/COLOR]
[COLOR=#333333]modprobe snd_hda_intel position_fix=1[/COLOR]

[COLOR=#333333]Reboot and it will work. Someone in the ALSA team simply needs to get this patch upstream. The sound is amazingly beautiful along with the pulseaudio equalizer. Much better than Windows.[/COLOR]

---

### Post by mantisdolphin on 2013-05-22
I added a Sound Blaster Z card (model SB1500), turned off the motherboard integrated audio, and *poof* no sound in Ubuntu. *Sigh*  So there is no support for this card in Linux, right?

In Windows, which I dual-boot and use for gaming, when installing the Creative software for the card, my system returned an error. So in the BIOS I turned off the integrated audio on the motherboard, and then the Creative software installed just fine. Plugged my headset and speakers into the Z card, and voila, sound! Trippy kick-ass sound too: Watching Game of Thrones and a guy going through the woods at night, I was hearing the relative *range*, the distance of background sounds, hoots, and howls. It was an awesome audio experience.

But now in Linux, I'm head-scratching. I think I'll turn the integrated audio back on and see what happens.

---

### Post by mmstick on 2013-05-22
All I can say is in Ubuntu, use integrated audio with a finely tuned qpaeq equalizer. These cards simply do not work in Ubuntu.

---

### Post by mantisdolphin on 2013-05-22
Saw this helpful and hopeful post--semi-hopeful--about Sound Blaster Z card at Mint forums:
[http://forums.linuxmint.com/viewtopic.php?f=49&t=125941](http://forums.linuxmint.com/viewtopic.php?f=49&t=125941)
---
Re: Any compatible drivers for Sound Blaster Z in 64bit?
Post by craftkiller on Mon Apr 29, 2013 4:40 am

I realize this thread is a little old but it looks like Linux 3.9 might be adding support for the Sound Blaster Z. According to alsa_info.sh my Sound Blaster Z uses the CA0132 codec, which accord to [http://www.phoronix.com/scan.php?page=news_item&px=MTMwODM](http://www.phoronix.com/scan.php?page=news_item&px=MTMwODM) support for that DSP is getting added to 3.9.

---

### Post by mmstick on 2013-05-22
Sorry, but it doesn't. As I have posted in the original post, I'm using kernel 3.9 (Ubuntu 13.10 development branch) right now. It doesn't work. I'm thinking about compiling kernel 3.10 soon.

---

### Post by mmstick on 2013-05-22
I'm afraid that no, compiling kernel 3.10 didn't help at all.

---

### Post by mantisdolphin on 2013-05-22
Dang. Well, good try. Creative used to support their cards for Linux fairly well. Lots of positive posts on the web where people felt good about using SB cards with Linux. Creative, 2008, made a driver for their well regarded and widely used Titanium card. I'm wondering what it will take, and how long, for a driver to be created for the SB Z card.

---

### Post by ZombieApocalypse on 2013-05-30
I'm having the same problems with this card. I've tried 3.10rc3, but still no joy. Card works fine in Windows. No way I'm swapping which sound card my speakers are plugged into each time I switch operating system!

---

### Post by mmstick on 2013-05-31
I'm pretty much stuck between a rock and a hard place over this Creative Recon3D and several other problems with Linux. Linux gives me significantly faster processing capabilities with my AMD FX CPU (I've seen up to 4x faster processing in Linux compared to the same thing running in Windows), it also gives me significantly better OpenCL performance with my Radeon HD 7950 (at reduced power consumption). I do a lot of BOINC projects 24/7 on a lot of machines, so operations per second and energy savings means a lot to me. However, my main problem is fglrx drivers for GCN hardware is almost completely broken, and I can't get the amazing sound of my Recon3D in Linux. Pulseaudio with a pulseaudio equalizer on this high end integrated sound chip in my Sabertooth 990FX simply can't compete. I get a lot of latency issues with pulseaudio in general as it is.

---

### Post by mmstick on 2013-05-31
I made a post in the creative forums: [http://forums.creative.com/showthread.php?t=699670](http://forums.creative.com/showthread.php?t=699670)

---

### Post by Yellow Pasque on 2013-06-01
Those who don't learn from history are bound to repeat it (*cough, X-fi)...

---

### Post by mmstick on 2013-06-01
> **Temüjin said:**
> Those who don't learn from history are bound to repeat it (*cough, X-fi)...

Actually, Creative did an amazing job with the drivers for CA0132 cards...on Windows. The only problem this time around is there is still no support for Linux.

---

### Post by Yellow Pasque on 2013-06-01
The last post had nothing to do with Windows drivers. I was referring to Creative's lacking/lagging X-fi support on Linux.

---

### Post by mmstick on 2013-06-06
Linux kernel 3.10-rc4 still doesn't support outputting sound.

---

### Post by mmstick on 2013-06-15
I have discovered a solution:

[COLOR=#333333]Someone noted that the 32-bit kernel plays just fine, but that the 64-bit kernel needs a special fix in /etc/rc.local. Add the following before exit0:[/COLOR]

[COLOR=#333333]rmmod snd_hda_intel[/COLOR]
[COLOR=#333333]modprobe snd_hda_intel position_fix=1[/COLOR]

[COLOR=#333333]Reboot and it will work. Someone in the ALSA team simply needs to get this patch upstream. The sound is amazingly beautiful along with the pulseaudio equalizer. Much better than Windows.[/COLOR]

---

### Post by davidisanoob on 2013-06-17
> **mmstick said:**
> I have discovered a solution:

[COLOR=#333333]Someone noted that the 32-bit kernel plays just fine, but that the 64-bit kernel needs a special fix in /etc/rc.local. Add the following before exit0:[/COLOR]

[COLOR=#333333]rmmod snd_hda_intel[/COLOR]
[COLOR=#333333]modprobe snd_hda_intel position_fix=1[/COLOR]

[COLOR=#333333]Reboot and it will work. Someone in the ALSA team simply needs to get this patch upstream. The sound is amazingly beautiful along with the pulseaudio equalizer. Much better than Windows.[/COLOR]

I just tried it with the 3.8 kernel on a fresh install and it doesnt seem to work. Installing 3.10 rc5 right now!

---

### Post by mmstick on 2013-06-17
It's been reported that this doesn't work with Sound Blaster Zs, but does work with Recon3Ds like I have. I'm using a low latency 3.8 kernel right now myself. Someone in the ALSA team seems to have finally took notice of things and all the 'ruckus' I started around places seems to be producing some results at the moment.

---

### Post by davidisanoob on 2013-06-17
> **mmstick said:**
> It's been reported that this doesn't work with Sound Blaster Zs, but does work with Recon3Ds like I have. I'm using a low latency 3.8 kernel right now myself. Someone in the ALSA team seems to have finally took notice of things and all the 'ruckus' I started around places seems to be producing some results at the moment.

well poop. i guess this thing is going back to best buy tomorrow. I just want surround sound to work with ubuntu. i shoud have researched more before buying but returning it shouldnt be that much of an issue.

guess ill just have to order an asus xonar

---

### Post by mantisdolphin on 2013-07-11
Boy, I wish this worked for me, but alas, no. 

Linux V-Studio-XPS-9100 3.2.0-49-generic #75-Ubuntu SMP Tue Jun 18 17:39:32 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Do I really need to roll my own Kernel?

---

 Quote Originally Posted by mmstick View Post
I have discovered a solution:

Someone noted that the 32-bit kernel plays just fine, but that the 64-bit kernel needs a special fix in /etc/rc.local. Add the following before exit0:

rmmod snd_hda_intel
modprobe snd_hda_intel position_fix=1

Reboot and it will work. Someone in the ALSA team simply needs to get this patch upstream. The sound is amazingly beautiful along with the pulseaudio equalizer. Much better than Windows.

---

### Post by Yellow Pasque on 2013-07-11
Creative's not a Linux-friendly company. You'll have better luck with Asus Xonar.

---

### Post by taklap on 2013-07-12
recon3d works fine here @Mint 15 Olivia [http://ubuntuforums.org/showthread.php?t=1961257&p=12703386#post12703386](http://ubuntuforums.org/showthread.php?t=1961257&p=12703386#post12703386)

---

### Post by mmstick on 2013-07-12
It's not guaranteed to work or keep working once you get it to work. My recon3d stopped putting out sound after a reboot a week ago. Even tried reinstall Ubuntu 13.04 but no luck.

---

### Post by taklap on 2013-07-13
using the pc almost every day with no problem.....and mint 15=stock everything,i havent change anything to make the recon3d work...its just works out of the box.....strange.

---

### Post by mmstick on 2013-07-16
I'm reporting with Linux kernel 3.11-rc1, it finally works. Anyone with Sound Blaster Zs got sound?

---

### Post by mmstick on 2013-07-17
And now it stopped working after 2-3 reboots. I don't know what gives.

---

### Post by mmstick on 2013-07-30
I created a Windows partition on my SSD and the only thing installed on it is Steam for my 500 or so Steam games. I notice that when setting options in the creative recon3d control panel in Windows, those options are also carried out in Ubuntu. As well, sound in Ubuntu works after booting into Windows and then booting back into Ubuntu.

---

### Post by uncleswaz on 2013-09-05
having trawled through a number of blog posts about the Recon3d I started thinking I had made a big mistake - but I tried this simple suggestion (not even knowing what it meant) and it worked first time - MANY MANY THANKS - crystal sound!

(13.04)

---

### Post by imrazor on 2013-10-26
Working here with an SB Z, Ubuntu 13.10 and kernel v3.11. Sounds much better than Windows, which is saying something. Only gotcha - I can only get front panel audio working in stereo, no surround sound. Sounds fabulous though.

---

### Post by imrazor on 2013-10-26
UPDATE: Simply adding a couple of lines to rc.local doesn't do it for me. I have to login, open a terminal, type "sudo telinit 1". I then get dropped to single user mode. There I have to type in:

# rmmod snd_hda_intel
# modprobe snd_hda_intel

Then I can type "telinit 2" to reload the GUI. I have no idea why rc.local is incapable of performing this function. From dmesg it seems as if rc.local isn't even getting loaded.

---

### Post by imrazor on 2013-10-28
UPDATE 2: I knew there had to be a better way. Do this:

1) Disable pulseaudio. I accomplished this by editing /etc/pulse/client.conf, uncommenting the "autospawn" line and setting it to "no". Reboot.
2) From the Unity desktop, open a terminal (CTRL-ALT-T), then type "sudo alsa force-reload". On my system this caused several audio modules to reload, including snd-hda-intel. If pulseaudio is running, snd-hda-intel will *NOT* reload.

Problems: No volume control on desktop. Volume control buttons on keyboard will not work. If you have multiple sound devices (including any HDMI ports), you may have to manually config your media player to output to the appropriate ALSA device. Only front panel audio works.

---

### Post by caymus on 2013-12-23
Ubuntu 13.10 64bits 3.11.0-14-generic

Sound Blaster Z

Wat i do is:

```

sudo kill `ps uax |grep pulseaudio | grep -v grep | awk '{print $2}'` ; sudo rmmod snd-hda-intel; sleep 3; sudo modprobe snd-hda-intel

```

& i have sound on my headphone on front panel port only, after this.

Now i have a question relating 24 bits / 96 khrz

This is realy a mess to manage sound :s

1rst i use Audacious beceause it is easier to swap between pulseaudio & alsa

```

cat /proc/asound/card0/pcm0p/sub0/hw_params
or
cat /proc/asound/Creative/pcm0p/sub0/hw_params

```

if i use pulse audio:

```

access: MMAP_INTERLEAVED
[COLOR=#ff0000]format: S16_LE[/COLOR]
subformat: STD
channels: 2
rate: 44100 (44100/1)
period_size: 8192
buffer_size: 16384

```

if i use alsa output

into audacious plugin preference:

PCM device: plughw:CARD=Creative,DEV=0
Mixer device: hw:0 (HDA Creative)
Mixer element: Master

Bit depth: Floating point

```

access: MMAP_INTERLEAVED
[COLOR=#ff0000]format: S32_LE[/COLOR]
subformat: STD
channels: 2
rate: 44100 (44100/1)
period_size: 2048
buffer_size: 8192

```

i have edited & reboot OS

/etc/pulse/daemon.conf
```

; default-sample-format = s24le
; default-sample-rate = 96000
; alternate-sample-rate = 96000

```

but if i use pulseaudio i see 16 bits in use instead of 24bit

& for 96khrz.... i m stuck at 44khrz

Some 1 know how to at least use 48 or 96 khrz?

no matter if it is alsa or pulse or direct hw.

Managing sound is already tricky when everything work fine, but with CA0132 soundblaster z, this is really like hell :s

---

### Post by caymus on 2013-12-23
Ok, now seem to work fine at moment, i have reinstalled my 64bit OS

SB Z
```

sudo kill `ps uax |grep pulseaudio | grep -v grep | awk '{print $2}'` ; sudo rmmod snd-hda-intel

```
some time i need to use this command twice, to be sure  i need to see

Error: Module snd_hda_intel is not currently loaded

And only after this:
```

sudo modprobe snd-hda-intel

```
```

cat /proc/asound/Creative/pcm0p/sub0/hw_params 
access: MMAP_INTERLEAVED
format: S32_LE
subformat: STD
channels: 2
rate: 96000 (96000/1)
period_size: 4096
buffer_size: 8192

```

I probably have broken something in pulseaudio before.

---

### Post by sherLOCK999KHz on 2014-01-06
Hi, caymus. I've done all the actions that you specified, but the sound did not hear, only clicks when switched to alsamixer <HP/Speak>, I have installed Ubuntu 13.10 x64, kernel 3.11.0-14-generic. can you describe your actions in more detail, if possible step by step.

---

### Post by stephan4 on 2014-03-12
Same here, I only get noisy scratchy sound over my catalyst hdmi output. The Analog lines are quit.

What can  advise?

---

### Post by caymus on 2014-04-26
> **stephan4 said:**
> What can  advise?

Only front analog audio, &  mic jack on card are working, opticals, all others jacks & 600ohms jack are not working for me.
Sometime i need to shutdown computer, wait 5 sec & restart if rmmod is busy, rmmod/modprobe is the first thing to do on desktop, else if you open something using audio before, you need to shutdown, restart computer, login, rmmod & modprobe, & only after you need to check if pulse audio is muted or not, if alsa is ok etc...

YOU CANNOT BE IN PEACE with this ****** sound card.


ONE ADVISE?

Dont hope to much from creative labs, they dont care about gnu/linux, sell your ca0132 card & buy one Asus xonar.

The positive thing, now i have tested Asus sound card,  a little more expensive,  sound is great with my Sennheiser headphones,  a better quality than sound blaster Z for audiophiles, & work fine under gnu/linux.
My first creative labs sound card was on early 1990, & now this is definitivly my last from this company.


analog stereo work here only for me with HD-audio connector from the case
[IMG]http://www.buycoms.com/Article/8226/Creative_Sound_Blaster_Z-03.jpg[/IMG]

Mic work here only for me (1rst jack from left side)
[IMG]http://www.buycoms.com/Article/8226/Creative_Sound_Blaster_Z-04.jpg[/IMG]
Dont forget to look into alsamixer if one or both HP/Speaker & AMic1/DMic are enable, & next if pulseaudio is not muted also in pavucontrol, if you use pulseaudio.

---

### Post by jak_amneziak on 2014-10-13
Good evening. 

Sounds like I am not the only one having issues with sound blaster cards. I have bought a computer with a sound blaster ZX (SB1506) model. I am trying to find the drivers as I regularly deal with vinyl restoration and need the best quality I can afford (so no onboard sound). 

any suggestions will be welcome please as the creative website (proverbially) laughed in my face when I asked about Linux.

---

### Post by mmstick on 2014-10-13
You will not be able to use your Creative sound card on Linux. There is no support at all. You will have to buy an ASUS sound card or resort to using an external DAC/AMP.

---

### Post by Adrian_Hugo on 2015-05-11
I really like the SB zx card myself - I think the sound quality is brilliant and it solved some problems I was having with the onboard sound. Having said that, like so many other people I do dual boot between Linux and Windows - the only reason I even have Windows is that it is still the best platform for gaming ( while so many games use Direct X, love it or hate it the reality is that Windows will always have the monopoly in the world of PC Gaming).  

Of course, the z series of Sound Blaster cards are not full supported so rather than continuing trying to tinker with the sounds settings and scripts ( which potentially could only make the problem worse ), I simply use this work around : - I got myself a Sound Blaster Live USB Sound Card and when using Linux,  I simply plug in this USB Card and it works like a charm.  I am able to have quality sound and even have the ability to use a microphone if I want to. This is even easier than having to turn on and off the on-board sound, to switch between Linux and Windows.  

I paid about $ 35 dollars for this USB Card, however on Ebay I have seen other no-name brand cards that claim to work with Linux for under $ 10.  I can't say how good they are, but if you are budget minded it might be an option for you.

---

### Post by paulogdemitri on 2015-08-23
Im having problems with the HP jack. Any tips? It wont work at all.
I tried:
-alsamixer
-hdajackretask

It only work if i connect to the light green one.
Z87 Stinger here with 4.0 kernel under ubuntu...
[IMG]http://i.imgur.com/dOeRmCG.jpg?2[/IMG]

---

### Post by imrazor on 2016-04-03
I wanted to report that I *finally* got this card working with 64-bit Linux. However, like 32-bit Linux only the front panel header works. There is a missing firmware file, ctefx.bin, that I downloaded from alsa-project.org. I made sure I downloaded the firmware tarball for my version of ALSA (v1.0.28) then extracted the firmware file from alsa-firmware-1.0.28.tar.bz2. For good measure I also grabbed the other ctspeq.bin file from ca0132 directory. I then put both files into /lib/firmware. So far the audio has come up consistently at every boot, though sometimes the MATE mixer shows the audio muted after a reboot. I also haven't yet figured out how to enable the back panel audio outs. I should note that I'm using Debian 8.3 64-bit. I'm hopeful that this trick will work with Ubuntu as well.

UPDATE: Well it seems putting these firmware files in /lib/firmware ONLY work if you boot into Windows first. They work great as long as you use Windows to "initialize" the card. Back to the drawing board...

---

### Post by fabio37 on 2016-06-03
Hello, I'm an owner of that bloody card too. Can I help someway to get this piede of silicon to work on Linux? I'm not a dev, but I know some basic programming skills.

---

