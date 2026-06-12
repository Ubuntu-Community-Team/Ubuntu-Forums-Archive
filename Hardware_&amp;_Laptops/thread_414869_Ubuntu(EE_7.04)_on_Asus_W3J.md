---
title: "Ubuntu(EE 7.04) on Asus W3J"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by contro on 2007-04-20
This is going to try and be a guide on how to get everything working fully on a[COLOR="Blue"] [Asus W3J]("http://www.notebookreview.com/default.asp?newsID=2995&review=Asus+W3J")[/COLOR] so far I am starting by using this guide obtained from here:
 
Graphics: 
Got beryl to work on my Asus W3J 
First:
 I installed the restricted drivers via System>>Administration>>Restricted Drivers Manager
Then was prompted to restart computer.

I also enabled universe and multiverse repositories
enter this in the terminal:

sudo gedit /etc/apt/sources.list
you will need to find this group of text make it look like this by deleteing the "#" sign and the space it should look like this:
"
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted multiverse
"

then i proceeded to follow this guide exactly as it was shown

[http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+xgl+ati](http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+xgl+ati)

you can skip to configuring the xorg config file it may already be there 


Sound:Working on it.




I will try to update here as well. [COLOR="Blue"][post on getting everything working on my W3J]("http://forum.notebookreview.com/showthread.php?t=118390")[/COLOR]

---

### Post by contro on 2007-04-27
can't get sound working anyone have any possible solutions

---

### Post by starorbs on 2007-04-27
Hmm, I'm suprised that it's still not working on Ubuntu, I had that same problem almost 8 months ago. This is what I did to fix it. I haven't used version 7 of ubuntu yet so I don't know if the files are still in the same place.

Put "options snd-hda-intel position_fix=1 model=laptop-eapd" to "/etc/modprobe.d/alsa-base"

---

### Post by contro on 2007-05-02
unfortunately getting the sound to work on my laptop is the only thing holding me off from making the full switch to nix anyone please help.

btw star orbs tried that no dice...:(

---

### Post by contro on 2007-05-10
bump...anyone have any clues ..

---

### Post by contro on 2007-05-17
grrr this is so frustrating after getting beryl and almost everything else to work....the sound won't work help!!!!It worked before in previous versions does anyone have a solution...>???

---

### Post by ithildin on 2007-06-20
I am happy to say that my Asus W3J is now working fine with Feisty with Compiz, sound, touchpad and bluetooth! Beryl kept giving me white screens so I gave up on it. 

The sound problem was a tough one to crack but I got it to work by updating the alsa driver, utils and lib to 1.0.14rc4 and adding the "eapd" line to the alsa-base (already mentioned in this thread). Apparently there is a ACPI DSDL issue with some laptops that the bundled ALSA driver cannot sort out. The new RC4 works fine here. 

Sound now works fine in ALSA and OSS. Built-in mic input is fine - I've tested it using Skype (32-bit)installed with Automatix. 

I got myself into the mess that is PulseAudio while trying to get Flash to play audio on my W3J but I ended up uninstalling Pulse altogether and switching to using Swiftfox (32-bit, Automatix) instead.

I'll post more info on the other things that were not-so-obvious to fix. 
W3J users, there is still hope! ;)

---

### Post by contro on 2007-09-05
> **ithildin said:**
> I am happy to say that my Asus W3J is now working fine with Feisty with Compiz, sound, touchpad and bluetooth! Beryl kept giving me white screens so I gave up on it. 

The sound problem was a tough one to crack but I got it to work by updating the alsa driver, utils and lib to 1.0.14rc4 and adding the "eapd" line to the alsa-base (already mentioned in this thread). Apparently there is a ACPI DSDL issue with some laptops that the bundled ALSA driver cannot sort out. The new RC4 works fine here. 

Sound now works fine in ALSA and OSS. Built-in mic input is fine - I've tested it using Skype (32-bit)installed with Automatix. 

I got myself into the mess that is PulseAudio while trying to get Flash to play audio on my W3J but I ended up uninstalling Pulse altogether and switching to using Swiftfox (32-bit, Automatix) instead.

I'll post more info on the other things that were not-so-obvious to fix. 
W3J users, there is still hope! ;)

Share your Bluetooth solution please!

---

