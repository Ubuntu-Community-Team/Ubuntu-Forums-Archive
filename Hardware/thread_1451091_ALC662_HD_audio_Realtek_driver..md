---
title: "ALC662 HD audio Realtek driver."
date: 2010-04-10
forum: Hardware
---

### Post by Koolvinstine on 2010-04-10
followed the directions as closely as I could, as I'm new to Ubuntu, yet I can't seem to get it to start playing sound =\
any help?
Supported Codecs: ```

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
ALC267
ALC268
ALC259
ALC269
ALC270
ALC272
ALC275
ALC660
ALC660VD
ALC661
ALC662
ALC663
ALC665
ALC670
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A
ALC892
```
Here are the directions:
```

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
	(soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure (--with-cards=hda-intel)<= for HDA options
	c. make
	d. make install
	e. alsaconf

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel

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
        Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.6 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.x and alsa-utils-1.0.x form the www.alsa-project.org, then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package. 
```

Completed Steps:
```

1
3 -alsaconfig, unknown command
4 -Not sure how well I did it, or if I did it right at all.. 
```As you can see these directions were completely halfassed and are in horrible english..

---

### Post by Koolvinstine on 2010-04-10
I know this has already been asked, just not specifically with my driver, and I need a bit more hands on help.

---

### Post by Koolvinstine on 2010-04-10
bump.

---

### Post by lidex on 2010-04-11
I'll need some info. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by Koolvinstine on 2010-04-11
> **lidex said:**
> I'll need some info. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

bash: utils_alsa-info.sh: No such file or directory

---

### Post by lidex on 2010-04-11
You saved it to a different directory. Either "cd" in terminal to the download directory or move file to your user folder and execute.

---

### Post by Koolvinstine on 2010-04-11
> **lidex said:**
> You saved it to a different directory. Either "cd" in terminal to the download directory or move file to your user folder and execute.

What am I moving to my user folder?

---

### Post by Koolvinstine on 2010-04-11
nvm, followed directions completely, didn't work..

EDIT: Can you start over and step by step tell me what to do? The instructions are very unclear...


When trying to play things, my speakers pop like they are about to make noise, then don't....

---

### Post by lidex on 2010-04-11
Try this. Open a terminal="applications>Accessories>Terminal"
Enter these commands:
```
cd /Downloads
sudo bash utils_alsa-info.sh
```
One line at a time. Enter your user password when prompted. Follow the prompts in the terminal and when it asks to save locally or upload, choose the upload option. It will provide a url. Post it here.

---

### Post by Koolvinstine on 2010-04-11
> **lidex said:**
> Try this. Open a terminal="applications>Accessories>Terminal"
Enter these commands:
```
cd /Downloads
sudo bash utils_alsa-info.sh
```
One line at a time. Enter your user password when prompted. Follow the prompts in the terminal and when it asks to save locally or upload, choose the upload option. It will provide a url. Post it here.

I changed the directory to the downloads directory, which isn't /downloads, then I entered that, couldn't find file. I have everything extracted, in their respective files, into my user file which happens to be /home/korvin
ex:
/home/korvin/alsa-driver-1.0.22
/home/korvin/alsa-lib-1.0.22
/home/korvin/alsa-plugins-1.0.22
etc.

I typed ```
cd
sudo bash utils_alsa-info.sh
```
[quote=terminal]bash: utils_alsa-info.sh: No such file or directory[/quote]

---

### Post by lidex on 2010-04-11
I was asking you to download the alsa-info script. Looks like you got the wrong link - those files are for an alsa upgrade and you need to go to that page and follow the directions there if you are indeed trying to upgrade.

---

### Post by Koolvinstine on 2010-04-11
> **lidex said:**
> I was asking you to download the alsa-info script. Looks like you got the wrong link - those files are for an alsa upgrade and you need to go to that page and follow the directions there if you are indeed trying to upgrade.

Those are the drivers that were provided to me from [realtek](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false), the creators of my sound card.

---

