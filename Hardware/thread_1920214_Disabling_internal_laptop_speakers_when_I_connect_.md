---
title: "Disabling internal laptop speakers when I connect the headphone jack"
date: 2012-02-04
forum: Hardware
---

### Post by akhil520c on 2012-02-04
Hi all,

I have a Toshiba C665-P5010 laptop, and I'm running Ubuntu 10.04 LTS. When I connect the headphones, the internal speakers were not getting muted, and I was getting output from both the speakers and the headphones. I tried the steps outlined here:

[http://playingwithsid.blogspot.in/2010/06/headphone-jack-sense-problem-in-ubuntu.html](http://playingwithsid.blogspot.in/2010/06/headphone-jack-sense-problem-in-ubuntu.html)

But the issue remained.

I tried the steps here:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html) 
(section "Mute speakers when headphones are used")

Now, it appears my soundcard is completely disabled (When I click on the speaker icon and go to "Sound Preferences", there is no device in the "Hardware" tab, and on the "Output" tab, there is only one entry "Dummy Output").

How can I reverse this process, and get my original issue solved? :confused:

Thanks,
akhil520c

---

### Post by Toz on 2012-02-08
> **akhil520c said:**
> 
How can I reverse this process, and get my original issue solved? :confused:

Thanks,
akhil520c

If all you did was follow the procedure in that link, then you should be able to just edit the /etc/modprobe.d/alsa-base.conf file, remove the entry you added, and reboot.

You might also want to try this entry in that file instead:
```
options snd-hda-intel model=ideapad
```

Reference link: [http://www.linlap.com/wiki/toshiba+satellite+c655d]("http://www.linlap.com/wiki/toshiba+satellite+c655d")

EDIT: If still no luck, try running the following command from a terminal window:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```
...choose the upload option and post back the link provided.

---

### Post by akhil520c on 2012-10-21
Hi Toz

Sorry for the very delayed reply, but here is the link to my alsa information. 

[http://www.alsa-project.org/db/?f=827189a493952c9059db4fdf0183493d76c803e6](http://www.alsa-project.org/db/?f=827189a493952c9059db4fdf0183493d76c803e6)

The headphone jack sense works on windows (for your information). Thanks in advance.

-akhil520c

---

