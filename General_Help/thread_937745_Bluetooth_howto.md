---
title: "Bluetooth howto?"
date: 2008-10-04
forum: General Help
---

### Post by rapattack1 on 2008-10-04
I have a bluetooth dongle plugged into the pc and a bluetooth phone(Samsung SGH-D500) and both things see each other. The phone asks for a pin code but I have never had one. I looked at the manual of the phone and it is not there. Someone told me that I have to get ubuntu to see the phone as a drive or something and that I don't need a pin code. I am not sure what he means really as I am too much of a beginner yet. I looked at System>Bluetooth preferences and maybe there is something there that I should configure as that is the app that appears when the dongle is plugged into the usb port. Has anyone got any ideas as I am new to the Bluetooth idea.

---

### Post by jespdj on 2008-10-04
Try "0000", that's often the default pin code.

---

### Post by rapattack1 on 2008-10-04
Didn't work I am afraid:(

Oh hang on it worked. Took a few goes and the desktop thing said one thing and the phone contradicted it. Anyway it said that it transfered the mp3. I navigated to the music folder but the file was 0kb and when I tried to play it, it said that the file was unsupported.

I just tried to convert the file again and noticed that it is outputting as 0kb's. I also looked at the mp3's on the phone in the music folder and their bitrate is 40kbs, one is 30 secs and 151kb. The actual ringtones are mmr and smaf is mentioned. Not that I understand these formats too well.

Ah this is odd....I have tried to convert to wav and agp or whatever for mobiles and the outputs are always 0kb's. I did check to see if the original files are of some size and they are. They are two files I am trying this on that I transfered from my older mobile.

---

### Post by rapattack1 on 2008-10-04
Well I have mastered how to transfer files over now so I am pretty happy. It is just a matter of persisting a lot and it works well. 
The issue of converting the file types for a ringtone is another thread so I will leave that to that one as that is not solved. Thanks so much :D

---

### Post by fragos on 2008-10-04
I recommend you install the GUI bluetooth manager blueman. It made life much easier for me. If I'm not mistaken, the default pin code for Linux is "1234".

---

### Post by niteshifter on 2008-10-04
Hi,

In 7.10, to get full BT functionality (OBEX push-pull) I had to install the package "gnome-vfs-obexftp". Don't know if 8.04.x comes with it or not, worth checking for it Synaptic.

Even then some devices (like my Palm TX) couldn't transfer. Installed the "gnome-bluetooth" package (learned this in 6.10).

As to what a BT capable phone can do and what music file format it likes - it depends upon the phone model and where (what service provider) you got it. Some providers cripple the phone (Verizon comes to mind). 

To see what capablities your phone has with BT: The bluez package should be installed (standard from 7.04 onward). It contains some useful tools:

Within the phone's menu set it to be discoverable (usually called Find Me) then run this in a terminal:
```
hcitool scan
```
It will trundle for several seconds and should output a line or lines like this:
```
11:22:33:44:55:66       SomeTextThatNamesTheDevice
```
The left part is the device's MAC address, the right is the name of the device. What is output will be different from the example above.

Using the MAC address, find out what the phone can do:
```
sdptool browse 11:22:33:44:55:66
```
This can be a few screenfuls, so these are handy:
```
sdptool browse 11:22:33:44:55:66 | less
```
Page up and page down keys will let you scroll, press Q to quit viewing.
```
sdptool browse 11:22:33:44:55:66 > PhoneCap.txt
```
You can then print the file or view it with an editor like gedit or nano.

As to file formats the phone can deal with: Experiment. If the phone has some .mp3 files already, pull them off the phone into your home folder and inspect the properties of the file. That will give clues as to bitrates and such.

---

### Post by rapattack1 on 2008-10-04
I am finding the whole bluetooth transfer thing quite easy now so no worries there. I won't bother installing anything else.

I did the scan thing and I got this:
carla@carla-desktop:~$ hcitool scan
Scanning ...
	00:15:B9:AA:A1:6A	SAMSUNG SGH-D500
carla@carla-desktop:~$ sdptool browse 00:15:B9:AA:A1:6A
Browsing 00:15:B9:AA:A1:6A ...
carla@carla-desktop:~$ sdptool browse 00:15:B9:AA:A1:6A | less
carla@carla-desktop:~$ sdptool browse 00:15:B9:AA:A1:6A > PhoneCap.txt
carla@carla-desktop:~$ 

So it looks like I got nowhere?

The pincode was for the phone not linux and I went another way so I didn't need it. The phone is accepting mp3's but I can't convert amr files to mp3 using winff. It is just not working. They output as 0kb's and I have tried this with 2 different files i took from my nokia phone.

---

### Post by rapattack1 on 2008-10-04
Oops just thought of something else. How do I save the contact list or address book on the phone to the pc? I heard Evolution does this but can't see how. Was spending a lot of time looking at Evolution last night. I also have Kaddressbook and Korganiser installed as well.

---

### Post by niteshifter on 2008-10-05
Hi,

spdtool should have given you some result. It occurs to me that you might have to grant permission on the phone itself for the remote device (your computer in this case) for access to the phone when sdptool runs.

ffmpeg will do amr to mp3 and vice-versa. It may need to be loaded from the mediabuntu repositories.

---

### Post by rapattack1 on 2008-10-05
I have access. I have been transferring stuff to the phone and taking stuff off the phone.
ffmpeg is the command line part of winff so I have it. It is not working!

---

### Post by niteshifter on 2008-10-05
Hi,

ffmpeg comes in two versions here in Ubuntu-land for each version of Ubuntu.
The version from the Ubuntu repository does not do all conversions!
You need the version from the medibuntu repositories.

Check what version you have installed via Synaptic. From the description shown in Synaptic:
> This package is built with the "risky" option, to enable mp3/mp4/h264/amr
support. Therefore, it is in Medibuntu as it might violate patents.


Examples:
Gutsy (7.10) the version from the Ubuntu repos is: ffmpeg 3:0.cvs20070307-5ubuntu4.1
From the Medibuntu repos is: ffmpeg 3:0.cvs20070307-5ubuntu4.1**+medibuntu1**

Hardy (8.04) Ubuntu repos: ffmpeg 3:0.cvs20070307-5ubuntu7.1
Medibuntu repos is: ffmpeg 3:0.cvs20070307-5ubuntu7.1**+medibuntu1**

As an alternative to using Synaptic, check ffmpeg's version direct. In terminal:
```
ffmpeg -version
```
Something like this should show:
> FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 [COLOR="Red"]--enable-amr_nb --enable-amr_wb[/COLOR] --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Aug 10 2008 11:11:16, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896

If the parts highlighted in red aren't present then amr is not supported.

---

### Post by rapattack1 on 2008-10-05
Ah yes I have heard of that as I have Ubuntustudio on my other hard drive. I think I have medibuntu there and will check but this is what I got on this plain ubuntu:
carla@carla-desktop:~$ ffmpeg -version
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896
carla@carla-desktop:~$ 

I have Hardy Heron installed.

I will transfer over to my other hard drive and install the other ffmpeg there because I think I have done this before and I wasn't able to use skype for some reason. Hard to remember why and no one could tell me why so I had to format and reinstall ubuntu.

Now I am on my ubuntustudio drive and this is what I got:
poppinlockin@studio:~$ ffmpeg -version
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896
poppinlockin@studio:~$ 

What is the line I should add in repositories for medibuntu? It has been ages since I have added it to the repositories.

---

### Post by rapattack1 on 2008-10-05
Ok I worked out how to do it on my ubuntustudio drive. It worked well with help from an medibuntu site!
Now I just want to know how to save the contact list or addressbook onto my hard drive. I haven't found out which app does that yet.

---

### Post by Brigrat on 2009-01-07
Somebody help this poor linux dummy!!!!  I am making another stab and joining the linux family full time and one last hurdle is to get bluetooth pan running on my stink pad.  In windows I use the BlueSoleil software and really like it, however it does not have a good package for ubuntu.  I saw several posts for BlueMan, downloaded the software but hit the wall trying to get it to install.  can anyone give me the idiots directions to install this into 8.1????   :(

---

### Post by fragos on 2009-01-07
The available version was built for 8.04. I haven't seen a deb for 8.10. The one for 8.04 may call for older dependancies than 8.10 has.

---

### Post by eeeenet on 2009-01-07
It seems there is already a BlueSoleil version for Ubuntu 8.04 on bluesoleil's website

---

### Post by Brigrat on 2009-01-08
yes bluesoleil has a free download for ubuntu, but it is limited to a 5M download, and comes in a TAR package which i was having trouble installing.  Still a newbie to the linux sftware installs.  If someone could make installing all the different packages easier I would leave windows completly

---

### Post by Brigrat on 2009-01-11
OK I found blueman and got the install to take but that is about it.  The laptop sees the phone, but I can not browse the files or get it to do a GPRS connect or like in the BleSoleil software do a Blue Tooth Personal Area Network connection to go on the internet.  Any advice or suggestions?????

---

### Post by fragos on 2009-01-11
Check out bitpim and see if it supports your phone. A number of different protocols are used with bluetooth, each relating to a specific feature. Not all bluetooth devices support a full set of the protocols. It's even posible that you cellular carrier has chosen to disable or limit protocols the phone manufacturer included.

---

