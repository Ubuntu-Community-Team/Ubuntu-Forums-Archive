---
title: "Acer Aspire 6920g issues NEWBIE"
date: 2009-09-13
forum: Hardware
---

### Post by N1k0n on 2009-09-13
Hi All
Complete newbie to linux, (had enough of windows!!) 
I have been using ubuntu for a few days after trying the 'live cd' and decided to install a dual boot along side vista (for now)....

I currently have no sound (which worked okay in ububntu before i installed it...)and have trawled the forums for solutions but nothing seems to work, mainly, due to my non technical knowledge of linux!.. :confused:

Firstly I need to download a script file to my 'home' directory to update alsa.... (Is this correct?) when I download the file it goes straight to my desktop!, I've changed the setting in firefox to ask me where to save file, which I've selected as '/home' but the download does not start!... it will save to the desktop with no probs...

so... how do I save to the home directory?
and how do I run the script once I have it?

there are also some other issues, but will return once I get this sorted. :(

I've seen other posts relating to this, but to be quite honest it sounds mostly klingon to me!!

any help will be appreciated!

---

### Post by dream_coder on 2009-09-13
Your home directory will be /home/yourusername/ anyways 

you need to do this:
 

in a terminal type "sudo gedit /etc/modprobe.d/alsa-base.conf"

add this (if it isnt there to the end of the file " options snd-hda-intel model=auto" then reboot

after reboot you have download in your Home directory the following file

[ftp://ftp.suse.com/pub/people/tiwai/...erb-0.3.tar.gz](ftp://ftp.suse.com/pub/people/tiwai/...erb-0.3.tar.gz) 

Go to your Home directory, right click and extract the file hdaverb file

Now change into the hda-verb-0.3 by typing this in the terminal

cd hda-verb

compile with " make "

Copy it to this direcotry /usr/local/bin type " sudo cp hda-verb /usr/local/bin "

Edit /etc/rc.local by typing " gksudo gedit /etc/rc.local "

This will bring up your text editor add this line before the
"exit line"

" /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2 "

reboot.

you could also compile and install the latest alsa from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) this isnt neccesary but there are some guides kicking about on how to do this if you feel you must

Welcome to Ubuntu! ;)

---

### Post by N1k0n on 2009-09-13
Thanks for the reply Dream coder,
All I did was reboot and the sound came on, (even though I've done that numerous times before :confused: )
Very 'tinny' though... need to get some bass on now!!!
(I've seen a post somewhere for that) 

Thanks for the help and welcome....

I'll no doubt be back soon!!!! :)

---

### Post by N1k0n on 2009-09-13
Trying to get the bass working has thrown up some problems!

I'm following the instructions for making the bass work from here
[http://ubuntuforums.org/showthread.php?t=1013750&highlight=acer+6920g+bass](http://ubuntuforums.org/showthread.php?t=1013750&highlight=acer+6920g+bass)

After sudo reboot I enter 'tar -xvmf hda-verb-0.3.tar.gz' in the terminal and get the message  'cannot open: no such file or directory'

I've obviously missed something somewhere!
!s it possible to start from the top again even though some files were dl'd earlier in the instructions?

Thanks in advance

---

### Post by dream_coder on 2009-09-14
Just right click on the hda verb and click extract here, yeah the hda verb will get your sub working, would suggest still doing the steps I give you for better quailty.

You probably werent in the directory with hda verb in, you can check by typing ls to list the files in your current directory anyway I would just suggest following my guide above any probs let me know.

That guide says you need to install new alsa which you DONT works fine without upgrading alsa and besides there is a newer version of alsa available that post is outdated.

Also after you have followed my steps, you find you dont have sound working change the model=auto to acer-aspire but I found the auto option works better.

One last thing remember to reboot after changes, to get sound.

Regards

---

