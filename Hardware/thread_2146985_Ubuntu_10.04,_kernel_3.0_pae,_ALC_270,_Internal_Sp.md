---
title: "Ubuntu 10.04, kernel 3.0 pae, ALC 270, Internal Speakers OK, No Headphone sound"
date: 2013-05-20
forum: Hardware
---

### Post by lebiathan on 2013-05-20
I have a new **Asus K55a laptop**, with a **3rd gen i5**. As you can see from the attachments, my sound card codec is ALC270.

I've clean installed **Ubuntu 10.04**, and after updating / upgrading the system, I installed the oneiric backports image and headers

```

sudo apt-get install linux-image-generic-lts-backport-oneiric
sudo apt-get install linux-headers-generic-lts-backport-oneiric

```

The reason for installing the oneiric backports, are that I had no sound otherwise (at all), and the graphics were not as they should be (I was able to scroll horizontally to see the entire desktop).

After installing the backports, I reboot the system, and have sound from **both** the internal speakers and through the headphones (jack on the side). Up to this point, the only changes have been to update / upgrage, and install the oneiric backports.

After the next reboot I did, I only have sound from the internal speakers, but not from the headphones. When music is playing, if I unplug  the headphones, the sound comes clearly from the internal speakers. When reconnecting the headphones, no sound comes out from them.

Searching for similar problems, I have followed the guide(s) saying to tamper with the */etc/modprobe.d/alsa-base.conf* file, which I have done. I've tried out a number of alternatives, suggested from [here]("http://git.alsa-project.org/?p=alsa-kernel.git;a=blob_plain;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD"), [here]("https://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt"), and my local */usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz* file. Note that the **ACL270** appears only in the first link.

Just to be clear, I've added the following line at the end of the */etc/modprobe.d/alsa-base.conf*:

```

options snd-intel-hda model=XXXX

```

substituting *XXXX* with options, including: asus, asus-mode1, asus-mode2, ..., asus-mode8, basic, auto, laptop, laptop-amic, laptop-dmic, inv-dmic, 3stack, ecs, m51va, h13, g50v, eeepc-ep20, asus-dig, asus-dig2, F1734 . (*note: I may be forgetting some at the moment*). After updating the options, I always **reboot**ed the system, and checked the sound from the headphone and the speakers. **At all times**, the sound was coming out fine from the speakers, but I could not hear anything from the headphones.

Through alsamixer, I verified each time that the headphones sound was not muted (in fact it was always maxed). Sound preferences were as follows:

**Hardware Profile**: "Analog Stereo Duplex"
**Output Connector**: "Analog Speakers"

I should also note that yesterday, I also tried the driver from Realtek (the steps can be found [here]("http://ubuntuforums.org/showthread.php?t=1473191&highlight=alc270")), however, I was constantly facing a "No sound card" issue, whenever I did that step, even though I followed the suggestions of purging alsa and pulseaudio and reinstalling (suggested [here]("http://ubuntuforums.org/showthread.php?t=1316634")). Which is why I did a clean install today, and I thought I should seek some advice first, before having a go with realtek driver again.

Output of the alsa-info script can be seen here: [http://www.alsa-project.org/db/?f=e1fb91d22ae93637a49e7e329f13825786ab5bca](http://www.alsa-project.org/db/?f=e1fb91d22ae93637a49e7e329f13825786ab5bca) (also attached)

Let me know if you need any more information. Thanks everyone in advance!

Cheers!
George



**Solution**: As indicated by sanderj, installing the 3.8 kernels did the trick. Instructions on installing a 3.8 kernel can be found in various locations on the web, including [here]("http://askubuntu.com/questions/253546/how-to-update-to-kernel-3-8-rc7-ubuntu-12-10"), [here]("http://linuxg.net/install-linux-kernel-3-8-6-on-ubuntu-debian-and-linux-mint-operating-systems/"), and other places.

Credits go to sanderj. Thnx mate! :)

---

### Post by sanderj on 2013-05-20
Do you know Ubuntu 10.04 Desktop is not supported anymore?

And why run such old software on a new laptop?

---

### Post by lebiathan on 2013-05-20
> **sanderj said:**
> Do you know Ubuntu 10.04 Desktop is not supported anymore?

Yes, I am very well aware of this fact.

> **sanderj said:**
> And why run such old software on a new laptop?

I really hope(d) to avoid such a discussion, so I'll try and keep it simple: 10.04 suits my needs fine. I don't like unity at all, and I see no reason to install all the additional stuff, only to uninstall gnome 3 and get back to a gnome 2.x like environment (which I've done for another machine).

Also note that, as far as I can tell, 10.04 is much more "lightweight" than 12.04 (as I perceive it during, for instance, apt-get update and apt-get install, as well as make / compiling, starting up applications etc. ). These are based on actual usage of the two OS on the same laptop (the Asus I talked about).

Finally, I should note that due to the above reasons, I tried out Xubuntu 12.04, to avoid the Unity interface. That OS, however, was by far the most unstable ubuntu installation I've experienced, with constant system freezes and screen locks (only hard reset worked then).



Returning back to the basic problem, I 'd also like to point out the following behavior. I installed the vlc player from the repositories, with
```
sudo apt-get install vlc
```
which also installed some additional, necessary libraries and dependencies. The interesting part is that **once installed**, and **before rebooting**, I got again sound from the headphones for just this time. After rebooting, the sound was once again audible only from the speakers, but not the headphones.

Thanks again everyone!

Cheers,
George

---

### Post by sanderj on 2013-05-21
If you live-boot Ubuntu 13.04 from CD/USB-stick, does the sound work well?

---

### Post by lebiathan on 2013-05-21
> **sanderj said:**
> If you live-boot Ubuntu 13.04 from CD/USB-stick, does the sound work well?

Hi sanderj, thanks for your interest!

I just tried out live Ubuntu 13.04 from USB and the sound seems to work fine, out of the box.

Another thing that might be of interest is that I see the following behavior: Anytime I choose to restart the computer, the sound will not work properly (experiencing the problem that I've mentioned). However, if I choose "shut down" and I start the laptop from hardware, the sound will come through the headphones just fine.

Hope that the above give some additional hints on what the problem might be.

Thanks!
George

---

### Post by sanderj on 2013-05-21
> **lebiathan said:**
> I just tried out live Ubuntu 13.04 from USB and the sound seems to work fine, out of the box.


Ah. That's good news. And it's bad news, as now you can't report a bug (on the supported 13.04).

In general, an old operating system on new hardware is not a great combination.

You could try to install a Linux 3.8 kernel on your Ubuntu 10.04, and see if that solves it.

I have no further suggestions.

---

### Post by lebiathan on 2013-05-22
> **sanderj said:**
> Ah. That's good news. And it's bad news, as now you can't report a bug (on the supported 13.04).

Oh well. There's no need to file a bug, when there isn't one ;)

> **sanderj said:**
> In general, an old operating system on new hardware is not a great combination.

I totally understand the caveats of such a combo, but I'd much rather stick with a version that is truly intuitive (for me at least). Anyway, as I said I don't want to get tangled in such a discussion (won't do much good to anyone).


> **sanderj said:**
> You could try to install a Linux 3.8 kernel on your Ubuntu 10.04, and see if that solves it.

I have no further suggestions.

Installing the 3.8 kernel did the trick. Touchpad sliding works fine as well now, but touchpad right click works as if I'm having a machine of the fruit company.. :S

Anyway, marking the problem as solved (and updating initial post with solution).

Thnx sanderj! Tell me where to send the beers (or coffee ;) ).

Cheers!
George

---

### Post by sanderj on 2013-05-22
You installed Linux 3.8 on Ubuntu 10.04 (and that solved the problem)? If so ... coooool! 

Maybe you can tell in a few lines how to do that? I think it would be useful for others.

---

### Post by lebiathan on 2013-05-22
> **sanderj said:**
> You installed Linux 3.8 on Ubuntu 10.04 (and that solved the problem)? If so ... coooool! 

Maybe you can tell in a few lines how to do that? I think it would be useful for others.

I have updated the first post with the solution, but posting it here, for efficiency and quick reference. Variation of [this guide]("http://linuxg.net/install-linux-kernel-3-8-6-on-ubuntu-debian-and-linux-mint-operating-systems/").

Open up a terminal. Download and install the linux kernels 3.8 as follows

```

mkdir kernel-3.8
cd kernel-3.8
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.6-raring/linux-headers-3.8.6-030806_3.8.6-030806.201304051406_all.deb
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.6-raring/linux-headers-3.8.6-030806-generic_3.8.6-030806.201304051406_i386.deb
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.6-raring/linux-image-3.8.6-030806-generic_3.8.6-030806.201304051406_i386.deb
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.6-raring/linux-image-extra-3.8.6-030806-generic_3.8.6-030806.201304051406_i386.deb
sudo dpkg -i *.deb
cd ..

```

Input your credentials when asked.

Shutdown the system completely (*Note*: If you just "Restart", it may seem that you are still having the problem. So, do a "Shut Down" to be sure).

Fire up your computer. Make sure that you now have the 3.8 kernel.
```

uname -r

```

should give **3.8.6-030806-generic** as output.

Sound from headphones and speakers will (*should*) come out nicely, *even after a restart*.

Note, there is a newer **3.8.13** version of the 3.8 kernel, available from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.13-raring/").

Once again, credit goes to sanderj for the suggested solution. ;)

Cheers!
George

---

### Post by sanderj on 2013-05-22
And no need to update GRUB? Or is that done by the "sudo dpkg -i *.deb" command?

---

### Post by lebiathan on 2013-05-22
> **sanderj said:**
> And no need to update GRUB? Or is that done by the "sudo dpkg -i *.deb" command?

Nope, I only did the installation step of the debs. Nothing more.

---

