---
title: "How to install Audio driver for Realtek ALC268 (HDA) on Acer Aspire 4710 laptop on Ha"
date: 2008-08-03
forum: Hardware
---

### Post by vigyani on 2008-08-03
How to install Audio driver for Realtek ALC268 (HDA) on Acer Aspire 4710 laptop on Hardy 8.04.1

Make sure that your system is updated (including the kernel and libncurses5-dev) and ready to compile the drivers: update and then use the following command to make sure that all the libraries and packages are installed for compiling the sound driver:

To update the package cache and checks for broken dependencies
```
 sudo apt-get check

```

To resynchronize the package index files from their sources
```
sudo apt-get update 
```

To install the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list, Packages currently installed with new versions available are retrieved and upgraded;
```
sudo apt-get upgrade 
```

To prepare systems to compile driver; we need to insall the following package:
```
 sudo apt-get install build-essential checkinstall automake linux-headers-generic libncurses5 libncurses5-dev xmlto gettext

```


Download the realtek audio driver from the following url:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs)

Alternate Location:

[http://122.146.118.42/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://122.146.118.42/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Look for HDA Drivers and accept the License and then Go to the Linux/Unix section and then clink on one of the download site links for Linux driver (2.4 or 2.6), download and save this file on your hard disk in a folder:

Open a terminal; change to folder where you saved the driver.
to unpack use the command:

```
 tar -jxvf "downloaded-driver-file-name" 
```

It shall extract and create a folder with the name "realtek-linux-audiopack-X.XX"

change to the folder and to compile and install the driver run
```
 sudo ./install 
```

It would show lots on info on the screen while driver is complied and installed;
After the driver is installed a configuration screen pops up

Configure the system according to your preference:

It would play a sound; if you hear the sound; it working; Enjoy.

You may have to configure front speaker and headphone volumes.

If jack sense does not work i.e. headphone plug does not mutes the speakers;
added the following options line to the file /etc/modprobe.d/alsa-base:

```
 gksu gedit /etc/modprobe.d/alsa-base 
```

at the end of above file add the following line:

options snd-hda-intel model=acer

Report back if it works or not.

Cheers:guitar:

---

### Post by saffagirl on 2008-09-07
Hi,

you seem like you have had a lot of success with installing this card.

I've got the same card in a vostro 1310. I've managed to unpack the tar and install, however I got a few errors at the end of the script to do wiyh alsa mixer and no config screen came up. SO far , I have no sound, mic, webcam etc. working ...I've attached the script for you.Could you please advise?
(I am a noob at ubuntu )

Thanks in advance.

FYI- your link didn't work for me, it's now 5.07 driver?

---

### Post by vigyani on 2008-09-19
Which release of Ubuntu are you using?

---

### Post by saffagirl on 2008-09-19
> **vigyani said:**
> Which release of Ubuntu are you using?

Hi Vigyani
I'm on Hardy.

Don't stress, since this post I've got my sound working with your post thanks....only thing is that the mike and sound is very quiet. Otherwise a very happy camper , thanks.

---

### Post by congtq on 2008-09-21
Hi everyone.

I am new to Ubuntu and -nix things. I've just installed Ubuntu 8.04.1 a few hours ago.
And then got to know that the sound didn't work. :(
I followed above steps, and at the last step, when run ./install, I got this error:

make[2]: Entering directory `/home/congtq/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory


Currently, I am living in Japan so I set zone to Japan, but the language is still English.

Can you help me fix this problem ?

---

### Post by saffagirl on 2008-09-21
I'm on ubuntu newbie too:)

I remember when I installed my soundcard drivers I had to restart and voila the sound came into effect, I also got quite a few error message...other wise best to let someone more proficient help

With regard to your language

It's not with area settings.

Go to System, then, Administration and then Language Support
From there let it install the language packs, then tick Japanese it should install some more files and let you change your preferred language....Hope this helps,

---

### Post by congtq on 2008-09-22
I try to change languange to Japanese, but it is still the same.
I think there was something wrong when the code is compiled.
But I'm not good at shell. I'll try again later.

Thanks for your answer.

---

### Post by congtq on 2008-09-22
After some search, I found this 
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

It work really well for me :(

---

### Post by jesuisbenjamin on 2008-10-10
Hey Saffagirl,

So it worked out for you right?
Installation didn't on mine, there were some errors - am not sure why. And then no configuration screen came up...

So my mic is still sleepy... :(

---

### Post by saffagirl on 2008-10-10
> **jesuisbenjamin said:**
> Hey Saffagirl,

So it worked out for you right?
Installation didn't on mine, there were some errors - am not sure why. And then no configuration screen came up...

So my mic is still sleepy... :(

Bonjour benjamin,

yup it worked for me. Like I said a bit on the quiet side, but working...

I remember I had a lot of errors coming off, but went through the whole thing (I'm still a bit of a noob at Ubuntu)...anyway, went through the whole process as detailed. Didn't get a config screen, but when I restarted my machine I had sound and mic (I didn't have either before)....so it's worth checking it out.

---

### Post by jesuisbenjamin on 2008-10-12
Salut,

it really didn't work out for me, however i just thought about your issue of having a faint sound level.
My version has 3 distinct sound tracks: master (MPC), headphone and front, you should make sure all your tracks are visible, then if you are amplifying the sound (as in my case) then you should make sure to increase headphone volume.
Most computers i had before would end playing on its own speakers as soon as a jack is plugged in...

hope it is that simple and helps you out.
cheers

---

### Post by saffagirl on 2008-10-13
> **jesuisbenjamin said:**
> Salut,

it really didn't work out for me, however i just thought about your issue of having a faint sound level.
My version has 3 distinct sound tracks: master (MPC), headphone and front, you should make sure all your tracks are visible, then if you are amplifying the sound (as in my case) then you should make sure to increase headphone volume.
Most computers i had before would end playing on its own speakers as soon as a jack is plugged in...

hope it is that simple and helps you out.
cheers

Salut ,

c'est domage que le solution ne marche pas pour toi.

merci bien pour ton répons, j'ai les controles regardée .il ne marche pas pour moi aussi. 

 I had a look at all the volume controls, they're all on the highest sound level . Strange it didnt work for you though= my jacks stop as soon as headphones are in though; bizarre. I'm just trying to amplify the sound to a decent level on the laptop- the sound is much better in Vista and I had the 1400 before (this is a replacement laptop because an NVIDIA graphics card issue)- the sound on that is a million times better than on this machine.

Good luck, sorry I couldn't help more and thanks for thinking of me to look at the controls ;0)...

---

### Post by dawei888 on 2008-10-13
Hi! Thank you for taking the time to help us install audio on Ubuntu. I'm a newbie and having a lot of trouble installing audio. I installed the "Hardy". After that I unzipped the realtek-linux-audiopack-5.07 zip file. After that I clicked on "install" and "run in terminal". when the install is running in the terminal i see some error, cannot find, or something like that, messages flashing really quickly on the screen. Then, it suddenly closes and the configure screen never comes up. Can you help me? It seems a lot of people have had luck with your thread. 

Thanks so much,
Dawei888

---

### Post by deepesh on 2008-12-14
Thanks for your helpful post.

I have a Toshiba Sattellite Pro, Chip - Realtek ALC268. Sound was working fine but mic was not working.
After checking this post, added following to /etc/modprobe.d/alsa-base

options snd-hda-intel model=toshiba

Rebooted the laptop and it worked. Not sure if reboot was required.
I am using Hardy 8.04, kernel version 2.6.24-22.

Yet to encounter a problem, not resolved using this forum :-).
Thank you all.

---

### Post by wrongnumber on 2009-01-09
Hello,
can someone please tell me, whether the driver from realtek also work on kernel 2.6.27-9?

many thanks,

---

### Post by saffagirl on 2009-01-29
Wrong number I'm not sure- I've been struggling since 2.6.24-22 to get my sound back. I've just tried the workaroun in -23 and have not had any joy.

2.6.24-19 was the last kernel where I got the sound to work with this solution.

---

### Post by raunhar on 2009-02-09
Ubuntu 8.10
Dual Boot with Win XP
I am new to UBUNTU or LINUX. I installed Ubuntu 8.10 last week. Was much satisfied with it. But while my kid was playing games on Childsplay, the sound vanished. All there was hissing sound.
Tried removing and reinstalling alsa-base etc, but no success.

On clicking on restart or switch off, the beep sound is well heard.
Currently a hissing sound is heard , when ever I try any sound in Ubuntu.

While working on Win XP, sound works.

Please suggest or else I will have to reinstall Ubuntu 8.10

---

### Post by vigyani on 2009-04-17
Hi

If you encounter error: alsaconf not found  or cannot stat `t-ja.gmo': No such file or directory

then you need to install some more packages.

Install the following packages:

libncurses5-dev xmlto gettext

use the following command:

sudo apt-get install libncurses5-dev xmlto gettext


after installing above packages run the following command after changing to the audio driver directory:

sudo ./install

Happy listening.

It works on Jaunty as well.

---

### Post by rggavubt on 2009-10-19
I have 9.10 Beta NBR installed on my Acer Aspire One 150 and I get the following error when I install the audio driver :

./install: 102: alsaconf: not found

From my reading at various sites, apparently alsaconf is no longer used by Ubuntu because of the problems it caused.  It is not part of the alsa-utils in synaptic package manager.

---

### Post by markackerman8@gmail.com on 2009-11-01
Hey Guys I am having real problems with sound too after a clean install of karmic on my HP laptop and have tried everything!!!

Everything that points to an output device only shows the"dummy" (WITH PADEVICECHOOSER or system/preferences/sound_preferences),

but when I:

ack@Titan:~$ gnome-alsamixer ... it shows "Realtec ALC268"

or
ack@Titan:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 0/1
Subdevice #0: subdevic

or
ack@Titan:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Hewlett-Packard Company Device 30cc
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

ANY SUGGESTIONS?????

---

### Post by JBAlaska on 2009-11-01
Did you try this;

Change /etc/modprobe.d/alsa-base.conf

[COLOR="Blue"]# Power down HDA controllers after 10 idle seconds
options snd-hda-intel model=dell-3stack[/COLOR]

```
sudo alsa force-reload
```

[COLOR="Red"]In 'Sound Preferences' -> 'Hardware' set Profile -> Analog Stereo Duplex[/COLOR]

---

### Post by Tavathlon on 2009-12-01
Thanks JBAlaska! That brought my sound back after installing Karmic.  =D

---

### Post by sinith on 2011-01-03
Vigyani you have done a wonderful job by writing everything in detail. It has helped me too. I was not using the audio player in Ubuntu for long due to some error in the driver.
Thank you very much...............
):P

---

### Post by amont on 2011-02-20
Hi all,

I found this thread after some searching because I couldn't hear with the headphones. But after doing things as described by Vigyani, I have no sounds at all. No sound cards, nor sound drivers seem to exist:

$ alsa-info.sh: command not found
$ aplay: device_list:223: no soundcards found...
$ alsamixer
cannot open mixer: No such file or directory

Also the "Indicator Applet 0.3.7" don't show any devices. Before doing all that alsamixer works and sound was present. I have no idea what I have done bad (?).

Laptop: Toshiba Satellite A200-1DY
OS: Ubuntu 10.04 lucid-lynx

Thanks for any help or suggestion you can give.
Toni

---

### Post by amont on 2011-02-20
Solved.

After installing package:

"linux-backports-modules-alsa-lucid-generic", whose description says:

"This empty package allows people to keep their alsa-driver snapshot
up-to-date when upgrading their Linux kernel." 

And reinitializing, everything works: headphones and speakers.

---

