---
title: "No sound after Mplayer install"
date: 2005-02-19
forum: Hardware &amp; Laptops
---

### Post by chrismc on 2005-02-19
Hi,

I Installed Ubuntu---mp3 worked with rhythm box. TV sound worked with xawtv with my tv card (old Hauppauge pci card). The soundcards listed in my gnome volume control were: Realtek ALC650 rev 3 [OSS Mixer] and VIA 8235 [Alsa Mixer].

Then I installed MPlayer from source and it worked--sound worked fine. When I rebooted I had no sound with MPlayer (/dev/dsp: not found even though it does exist). I also have no sound with rhythm box for mp3s. I now have 2 new entries in gnome volume control: bt87x [OSS Mixer] and Broketree Bt878 [Alsa Mixer]--these are for the tv card, but the tv worked fine before and they were not listed. These are in addition to the 2 I already had. the sound from the tv still works fine.

I have looked around and have no idea what happened. It seems that PCM sound no longer works. I think maybe that the sound module for the tv card is being loaded before the regular onboard sound card module. Any advice is greatly appreciated.

Thanks,

Chris

---

### Post by chrismc on 2005-02-19
I just noticed that you are not supposed to post in this forum. Sorry--can an admin move it to the right place?

---

### Post by jdong on 2005-02-19
That's fine... It happens. :)

It seems best under "hardware".

We've discussed the problem with tv tuners loading before sound cards before -- I'm sure a search will turn it up. Try:

tv tuner hotplug alsa

or some combination of that. It came up as a "bug" in a backport.

---

### Post by chrismc on 2005-02-20
Thanks a lot! I did your seach and came up with this thread that solved my problem:
[http://ubuntuforums.org/showthread.php?p=45436%23post45436](http://ubuntuforums.org/showthread.php?p=45436%23post45436) 

This is the text from that thread that had the solution:

> had the same problem.Onboard via sound card and a tv tuner.
this is how i fix it:
sudo gedit /etc/modprobe.d/aliases
here i added this:
alias snd-card-0 snd_via82xx
options snd_via82xx index=0

alias snd-card-1 snd_bt87x
options snd_bt87x index=1

P.S.The solution can be found via bugzila.ubuntu.com

Thanks again,

Chris

---

