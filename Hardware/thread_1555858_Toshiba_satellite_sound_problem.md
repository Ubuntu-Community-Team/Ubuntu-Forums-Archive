---
title: "Toshiba satellite sound problem"
date: 2010-08-18
forum: Hardware
---

### Post by FattyOwl on 2010-08-18
I've just installed ubuntu for the first time, and everything seems to be working great except for my sound. The sound card gets recognized and nothing is muted; but I still can't hear anything.

After searching this forum and others for a while I still haven't found a solution. The terminal told me to post the following link:

[http://www.alsa-project.org/db/?f=cc67a04a5bcb08f5395c1cd2019ca79b251ab860](http://www.alsa-project.org/db/?f=cc67a04a5bcb08f5395c1cd2019ca79b251ab860)

Currently I'm stuck, I've tried multiple options and even reinstalled ubuntu with no luck. I can't find my sound card in BIOS, but I did have sound in Windows Vista.

I'm a complete linux-noob, so any help would be appreciated!

Thanks

---

### Post by FattyOwl on 2010-08-18
Crossposted this in the multimedia forum, it seems to fit that category more than this one. Sorry for the hassle!

---

### Post by bogustrumper on 2010-08-18
Looks like you have the snd_hda_intel card.  I have one of those too, and for whatever reason it gives me trouble in ubuntu.

Try editing your /etc/modprobe.d/alsa-base.conf file (this is a text file that you'll have to use root privelages to read; if you're not sure how to edit files like this, an easy way is to open a terminal and use the command "sudo nano /etc/modprobe.d/alsa-base.conf").  At the very end, add a line like this:
```

options snd_hda_intel model=3stack

```
I threw up the 3stack model because that works for my system, but you might want to have a look at [http://alsa.opensrc.org/Hda](http://alsa.opensrc.org/Hda) to see if another model sounds more likely for your laptop.

After you save the file, you should restart, and if you pick the right model number sound should work.  

There are probably ways to try messing around with different models without restarting using the rmmod and modprobe commands, but I was getting errors trying that when I was casually messing around.  But if you'd like to give it a shot, what I would recommend is trying this, with absolutely nothing open (no browsers, etc):
```

sudo rmmod snd_hda_intel
sudo modprobe snd_hda_intel model=3stack

```
I used to be able to do this, but in more recent versions of Linux it hasn't worked.  Of course, I also know my model is 3stack, so... it's not necessary.

Anyway, good luck, and let us know if you make any progress.

---

### Post by Rodney9 on 2010-08-18
My Toshiba Satelite L500 has no sound problems.

Try This -

Thanks to LordRaiden

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Using alsamixer

* Type this into a shell
Code:

alsamixer

You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place.

* To navigate around:
o Left and Right Arrow Keys - Move left and right (if you move long enough in one direction you will get back to where you started - you will not fall off the screen )
o
Up and Down Arrow Keys - Increase and decrease volume respectively.
o
Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a green box underneath the volume slider. If the channel is muted, the box is grey.

Saving Sound Settings
Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do
Code:

sudo alsactl store 0

or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1. Many thanks to xpix for trying this out.-
______________

---

