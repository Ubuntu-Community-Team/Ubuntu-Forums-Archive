---
title: "How-to asus 5050 ATI SB450 HDA sound installsudo gedit"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by pauldude000 on 2007-04-26
I have had a heck of a time getting my sound up and working, but have finally completed the effort successfully.  

With the time I had, I estimate that many probably still do not have their sound working, so I will duplicate the process here for everyone. This information is a simple explanation/compendium of the info I gleaned, without the unnecessary junk which I had to wade through myself.

You will need ALSA, alsautils and gedit. Check your package manager (Adept Manager, or Synaptic) if these are installed, if not install them. 

(ALSA is the Advanced Linux Sound Architecture and Gedit is a sudo capable text editor)

**_STEP 1. Making ALSA config module _**

At the console pompt, type:

       ***sudo gedit***


You NEED sudo mode to save into the proper directory.  In the Text editor, cut/paste:


        # ALSA portion
        alias char-major-116 snd
        alias snd-card-0 snd-hda-intel
	# module options should go here

        # OSS/Free portion
        alias char-major-14 soundcore
        alias sound-slot-0 snd-card-0
	
	# card #1
	alias sound-service-0-0 snd-mixer-oss
	alias sound-service-0-1 snd-seq-oss
	alias sound-service-0-3 snd-pcm-oss
	alias sound-service-0-8 snd-seq-oss
	alias sound-service-0-12 snd-pcm-osst

save this file into the /etc/modutils/  directory as alsa.  Example /etc/modutils/alsa

At the console prompt type:

        ***update-modules***


***info from alsa website

**_STEP 2. Setting up your card  _**

At the console prompt type:

        ***alsamixer***


use arrow keys to navigate through all settings, making sure that all are enabled.

Next, look for the speaker symbol on your taskbar. 

1. Click to open.
2. Click on "led" to turn it on.
3. Click on "mixer" (if available. I use kde desktop, therefore have kmix)
4. Turn on all devices in software mixer

Viola! you should have sound!

An easy way to test is to run "Hardware Information" in your "Settings" category (Ubuntu hardware reporting tool. Sound test is first option.) 

Good Luck all!

pauldude000

---

