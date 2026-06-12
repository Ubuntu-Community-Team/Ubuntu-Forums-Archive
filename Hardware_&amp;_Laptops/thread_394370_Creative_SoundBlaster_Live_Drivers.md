---
title: "Creative SoundBlaster Live Drivers?"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by forevereating on 2007-03-26
As a new linux user I am getting along quite well, everything is thought out very well in ubuntu. That is until I ran into installing drivers for my soundcard. The repositories doesn't seem to have suitable drivers for me... or am I looking at the wrong place? I suspect I am but really have no idea where to look even after searching for them. Really would appreciate any help. 
p.s. my widescreen is giving me a headache since the resolutions are not widescreen friendly. I've downloaded the 915resolution for my 845g intel graphics but have not idea how to set it up. I got to the configuration place but it doesn't seem to have the correct drivers for my graphics.

---

### Post by will_in_wi on 2007-03-26
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1)

This should be the link to the linux drivers for your sound card.

---

### Post by forevereating on 2007-03-26
Would I be considered a debian user? And all I do is just copy and paste those lines of code?
Edit: sorry, seems like I have to do more then just copy and paste, where is this "update-modules"?

---

### Post by forevereating on 2007-03-27
Any other SoundBlaster Live users out there? Currently I am lucky and am able to hear sound and listen to music but only in stereo while the card is a 5.1 channel card. I would love to maximize my sound experience on Ubuntu.

---

### Post by BLTicklemonster on 2007-04-15
I never had any problems in alsamixer showing both sigmatel and soundblaster, but now, in feisty, I only show sigmatel, and I get an error when I run alsamixer.

Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Master": `,' is an invalid character in key/directory names

tons of variations of that error.

---

### Post by BLTicklemonster on 2007-04-15
> **will_in_wi said:**
> [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1)

This should be the link to the linux drivers for your sound card.

wow, that makes more errors than anything I've ever seen. and the cp /downloads/alsa-* wants more info than just the file name.

---

### Post by sweBers on 2008-03-08
> **forevereating said:**
> Any other SoundBlaster Live users out there? Currently I am lucky and am able to hear sound and listen to music but only in stereo while the card is a 5.1 channel card. I would love to maximize my sound experience on Ubuntu.

This is where I was a few days ago, so I decided to download and install the new drivers.

Unfortunately I had forgotten that I had installed my Sound Blaster Live Value and disabled my AC '97 (easy to do, I haven't opened the case in quite some time)

I downloaded the realtek drivers from here 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false)

and proceeded to remove the drivers installed by Ubuntu from the install.

Once I realized my mistake, I downloaded alsa-driver-1.0.16 from [www.alsa-project.org/](www.alsa-project.org/) 

I have been following these 

[http://www.euronet.nl/~mailme/index4.html#Instructions](http://www.euronet.nl/~mailme/index4.html#Instructions)

instructions which indicate that my sound drivers should have installed the modules in 

/lib/modules/2.6.22-14-generic/kernel/drivers 

with a subdirectory of sound instead of where my make install put them which is

/lib/modules/2.6.22-14-generic/kernel/sound


My question is whether I should just cut the entire sound directory from the kernel directory and put it in the drivers directory, or if there would be different options to run in the make process to tell the installation program where to put the newly made drivers?

Some of the documentation I have read has indicated that I need to recompile the entire kernel to get my sound working,

[http://infogroep.be/Main/SoundBlasterLive](http://infogroep.be/Main/SoundBlasterLive)

while the euronet instructions seem to indicate that all I do is run the make then the make install.

The next step is telling me that I need to edit /etc/conf.modules, however that particular path or filename doesn't seem to exist on this  machine.  I would be willing to bet that the config file is under a different name, 

-Edit-
  In Ubuntu /etc/conf.modules seems to be replaced by /etc/modules.  Correct me if I'm wrong here!

Any help would be appreciated!

---

### Post by sweBers on 2008-03-17
Well, I was able to reload my drivers, but it was an awfully painful process of having to remove the entire alsa architecture and gdm and then reinstall all of it

I followed this process here.  

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

If anyone is able to produce a technical explanation of what I actually did to cause this (other than the obvious, well you removed your sound drivers) and possibly an easier explanation I would like to know.

---

### Post by devanson on 2008-04-04
> **forevereating said:**
> Any other SoundBlaster Live users out there? Currently I am lucky and am able to hear sound and listen to music but only in stereo while the card is a 5.1 channel card. I would love to maximize my sound experience on Ubuntu.

here too friend.. I am also experiencing the same problem. I have creative soundblaster live - 24-bit. when I play mp3 in Totem Movie Player, only two FRONT speaker are working..  Again I changed something in Sound Preference (just enable all the option. :-) ) and now only two rear speaker are working.. Great Confusion:confused:

---

### Post by stevecartermo on 2008-06-23
I have the same problem .. namely a SOUNDBLASTER 5.1 sound card .. and a desire to hear some 5.1 sound. I am using Mythbuntu 8.04

speaker-test -Dplug:surround51 -c6 -twav

this TEST confirms I am only getting sound out of the front two speakers. I believe my speakers are plugged into the correct ports on the SOUNDBLASTER card.

I have YELLOW GREEN AND BLACK LEADS coming from my LOGITECH 5.1 speaker system

I have the yellow lead from speakers plugged into the blue jack on the card
I have the green speaker jack plugged into the green soundcard plug
and the black speaker plug connected to the black plug on the soundblaster 

Anyone using this configuration or any thoughts

Thanks

---

