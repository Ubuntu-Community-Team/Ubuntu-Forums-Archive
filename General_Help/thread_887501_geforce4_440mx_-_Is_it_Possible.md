---
title: "geforce4 440mx - Is it Possible?"
date: 2008-08-12
forum: General Help
---

### Post by thebluestreak on 2008-08-12
I have an older geforce4 440mx card on hand and would like to run hardy and compiz (with effects; specifically wobbly windows).

Just looking for confirmation that this can actually work.

I have googled and ubuntu forumed this thing to death and don't seem to find a definative answer to this question.

I know I can get things going with XGL, but know that will not give me the effects that I want.

Just looking for confirmation that this will work, and some idea on the combination of packages to run to make it work.  Any helpful links greatly appreciated.

Thanks in advance,

Paul

---

### Post by ChimpofDOOM on 2008-08-12
I installed Ubuntu onto my parents machine a while back, which has a Geforce 4200Ti.. certainly had no problems!

So I guess it should work :)

---

### Post by thebluestreak on 2008-08-12
i appreciate the optimism ;) but looking for others with this specific card to help me avoid a little trial and error.

specifically, looking for someone that used this card that can tell me:

1) what version of nvidia driver was used
2) was it installed using envy, manually, or (k)ubuntu installer
3) any manual modify / deletes in xorg.conf
4) any nvidia utilities used to complete configuration

Paul

---

### Post by divague on 2008-08-12
I have a Geforce mx 4000, for what i've read in nvidia's web site they are similar.

I installed the driver that comes in the repos, System->Administration->Hardware Drivers. After the first reboot compiz was already activated but the resolution was low so i installed nvidia-settings using synaptic, then on a terminal:

$sudo nvidia-settings

i changed the resolution and pressed the "save to x configuration file" button.
After the second reboot windows didn't have borders so i modified my xorg.conf file like this:

$sudo nano /etc/X11/xorg.conf

and in the "Screen" section i added:

"AddARGBGLXVisuals"  "true"

there were two "screen" sections so i added that line in both.

And that's it, that got compiz running in my computer.

Hope it helps

---

### Post by thebluestreak on 2008-08-22
thanks for the replies.

i found it was pretty easy on hardy kubuntu:

*Installed nvidia drivers through system --> hardware drivers manager
*rebooted
*installed compiz through system --> desktop effects 
*sudo apt-get install compizconfig-settings-manager fusion-icon emerald nvidia-settings

and all works great.

thanks all.

paul

---

