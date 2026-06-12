---
title: "No sound with Tecra A8-S8514"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by wit_273 on 2007-07-03
I just got a Toshiba Tecra A8-S8514.  The first thing I did was install Ubuntu Feisty on it.  Everything works great accept the sound.  I get no sound from the speakers--but I do get sound from the headphone jack.  At first I thought that the problem may be bad speakers (unlikely but not impossible) so to be sure I restored WinXP and tested the speakers--worked without error.  Speakers are not the problem.  So next I reloaded Feisty and started Googling.  I found half a dozen different suggesting (most for Warty, Dapper, and Edgy).  Tried them anyway--no success.  I found [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG) which looked like the most reliable fix--it was for Feisty and Edgy.  Tried the suggestions--again no success.  I thought that maybe the other half dozen or so suggestions may have led to me messing something up.  Completely wiped and reloaded again-- this time only doing the suggestions from the above link.  Still no success.  So, if you are still reading you have probably long figured out that the point of this post is to ask if there are any other suggestions that someone has.  If you have a suggestion please let me know.  I would really like to have sound on this system without having to connect external speakers.  Thanks for any help.

---

### Post by wit_273 on 2007-07-07
Problem fixed thanks to wishie at #alsa in at irc.freenode.net.
Solution:

Download the alsa-info script from [http://bulletproof.servebeer.com/alsa/index.php?task=scripts](http://bulletproof.servebeer.com/alsa/index.php?task=scripts) and run the script.
Goto the download directoy and run
$ chmod +x alsa-info.sh
$ ./alsa-info.sh --no-upload
By default the script uploads the data to [http://pastebin.ca/](http://pastebin.ca/) the --no-upload will save the output to your /tmp directory. If you need someone else to see the data it may be useful to not use the --no-upload option and send them a link to the pastebin.ca site.

In the output look for the Codec section for the proper codec (which in this case is Realtek ALC262)

Then go to [http://www.wishie.net/alsa/configs/hda_intel_models](http://www.wishie.net/alsa/configs/hda_intel_models) and find the proper codec for possible modules.

Close any sound apps including gnome mixer applet
Run
$ sudo rmmod snd-hda-intel
$ sudo modprobe snd-hda-intel model=basic (in my case-- you may have to try different modules)

After each module the sound may be muted. Run alsamixer to unmute and increase volume.

Once you find the module that woks add the following to the end of /etc/modprobe.d/alsa-base
options snd-hda-intel model=(module that worked)

Then run the following so that it works after reboot.
$ update-modules


Hope this helps someone.

---

### Post by u-blunt-2 on 2007-07-19
Im going to try this with my tecra s4. Busted my balls with this on fiesty 64 in the past. Hope it works. 
Any idea if alsa and ubuntu will make some automatic update, be it in the next version or now ?
Now if I can only get the fingerprint reader to work...

---

### Post by u-blunt-2 on 2007-07-19
BTW, your link is dead

---

### Post by wit_273 on 2007-07-21
I see the links are dead.  If you have not already done this you might want to join #alsa at irc.freenode.net and see if someone has other links that are live.  I will look and see if I can find the info somewhere else and post it here if I do.

I do not know if alsa plans on adding this to future releases or not.  Recalling my chat with wishie he seemed to be a developer and was going to look into resolving this in the future--but I am not sure about that.

---

### Post by Tycoon12 on 2007-10-16
I found a wonderful fix.  It even works on Feisty.

All it takes is the editing of one file and adding a single line at the bottom.

File:
```
sudo gedit /etc/modprobe.d/alsa-base
```

Add this at the very bottom:
```
options snd-hda-intel enable=1 index=0 model=basic
```

---

### Post by PandaChan on 2007-11-17
> **Tycoon12 said:**
> I found a wonderful fix.  It even works on Feisty.

All it takes is the editing of one file and adding a single line at the bottom.

File:
```
sudo gedit /etc/modprobe.d/alsa-base
```

Add this at the very bottom:
```
options snd-hda-intel enable=1 index=0 model=basic
```

Ok, Ok, this one works great... BUT it only work on the start up at the moment of hearing the African drums, but either banshee or totem works .. any help about this?

---

### Post by Tycoon12 on 2007-12-14
> **PandaChan said:**
> Ok, Ok, this one works great... BUT it only work on the start up at the moment of hearing the African drums, but either banshee or totem works .. any help about this?That's odd.  Do other programs have sound, or is just the drums that you can hear?

---

### Post by aussie.ian on 2007-12-15
> **PandaChan said:**
> Ok, Ok, this one works great... BUT it only work on the start up at the moment of hearing the African drums, but either banshee or totem works .. any help about this?

I use both Suse 10.3 and Ubuntu Gutsy on a Toshiba A200 and after much hair pulling and silent browsing upgraded to alsa-1.0.15 sound now works no problem with: options snd-hda-intel enable=1 index=0 model=basic added to  /etc/modprobe.d/alsa-base.

alsa-1.0.15 has a fix for some of the newer intel based cards.

Hope this helps............

---

