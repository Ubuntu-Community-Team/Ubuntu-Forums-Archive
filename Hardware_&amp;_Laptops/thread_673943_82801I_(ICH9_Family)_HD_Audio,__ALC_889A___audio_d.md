---
title: "82801I (ICH9 Family) HD Audio,  ALC 889A   audio drivers"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by Larion on 2008-01-21
Hi , this is my first post. Usually i used to solve my problems from the old threads but i couldn't solve this.

I am using the hardware which is the name of my topic. 
Everything was working fine , but i couldn't use 5.1 with my sound system. So i wanted to download and install the HD audio drivers which can be found here 
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

i've read the readme file and it says 
Linux Source Code for ALC audio codec
Support Codec list:
====HD Audio codec ====
ALC889A

there my sound card . First i tried to install it ./install but it did not work, then i tried installing manually.  Reading the readme file
```
The source code copy from www.alsa-project.org.      ver:3.3-4
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC268
ALC660
ALC660VD
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A

Installation:
This Source Code is from www.alsa-project.org.
For driver installation, please follow below steps. 

Automatic install:
execute

  ./install

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure
	c. make
	d. make install
	e. ./snddevices

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel
           --- ATI chipset -----
	       snd-atiixp

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.2.14 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the www.alsa-project.org, then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package. 
```

I can't make it work again. When i try running alsamixergui , i get an error
" alsamixer: function snd_ctl_open failed for default: No such device"

the default gnome mixed which can be seen on top right by deault can't run either
"No volume control GStreamer plugins and/or devices found."


I have been using ubuntu for some time , i'm not a completely new user but i haven'T had any problems with sound devices like ALSA and OSS so i don't know what outputs i should paste here. 

I need some help , i don't know where to look. 

Thanks

---

### Post by flosoft on 2008-02-03
I have exactly the same problem. Any help would be appreciated.

---

### Post by V8snail on 2008-02-05
Thanks to you, Larion my system sound is working!:):):)

To use the ./install you must have access to the script file that is inside the file that you download from Realtek (realtek-linux-audiopack-4.07b.tar.bz2). To do this you should unpack this file to a new folder.
Then enter in this new folder and go inside the folder named "realtek-linux-audiopack-4.07b". Now you will see a script file named "install".
Open one terminal inside this folder.
Then you must be root to run this script. 
Inside the terminal window that you open run the "su" command and use your root password.
Now you could use the ./install command!!!
Don't worry. This is a very long script that do a lot of things. When you think that your HD is being formatted or your system will be crashed by this crazy script...there will be a light at the end of the tunnel!
The script will prompt you to use the Alsa Configurator (alsaconf).
Select your sound card driver and follow the configuration steps until the end. When it finishes your sound card will be configured and WORKING.:)

:guitar:

Good Look!

:lolflag:

V8snail

---

### Post by dmatej on 2008-04-04
Mine is not working :(

[http://ubuntuforums.org/showthread.php?p=4653220](http://ubuntuforums.org/showthread.php?p=4653220)

---

