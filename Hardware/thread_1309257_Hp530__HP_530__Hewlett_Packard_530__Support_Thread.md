---
title: "Hp530 | HP 530 | Hewlett Packard 530 | Support Thread #2"
date: 2009-11-01
forum: Hardware
---

### Post by quodlibet on 2009-11-01
Hi everyone!

There used to be a support thread for HP 530 here:[ http://ubuntuforums.org/showthread.php?t=502833]("http://ubuntuforums.org/showthread.php?t=502833")

But as it's been moved into the archive, I thought we'd start again. (Unless I'm the only one still using this laptop ;))

I performed a clean installation of Karmic yesterday and almost everything seems to work out of the box: sound (including correct detection of headphone jack), compositing, WiFi.

There is only one problem so far and I haven't found a solution: when there is no sound playing there is a clicking that occurs intermittently. To my ears it sounds like the clicking you get when turning speakers off or on, but perhaps I'm imaging this. This clicking is audible regardless of whether headphones are plugged in, but it does not occur during playback, nor if the sound is muted.

I still haven't tested the microphone and the standby/hibernation modes.

Please post your own issues, solutions, and so on.

---

### Post by gitane79 on 2009-11-04
I can confirm the issue for my Hewlett Packard 530 laptop. The speakers click when there's no sound playing. I think it has something to do with the headphones plug or sound drivers.

I've tried with/without pulseaudio and reinstalled from scratch twice. I also installed alsa-firmware (non-free) but to no avail.

Did you already find a solution? It's really annoying, this clicking.

---

### Post by quodlibet on 2009-11-06
I have found a solution! Internet radio. ;) And if I am not listening to music, I simply start playing a nice long film in totem, minimize it, and turn my speakers off.

As you can tell, I'm still stumped about this. And to be perfectly frank, I was hoping someone else would come up with something, as I don't feel particularly safe fiddling with my only computer. (I'm not that techie either.)

If I find the time over the weekend I'll try a few things from the old thread (there was something about adding a module to fix the microphone jack, if I recall) in hope of magic.

Let me add this: muting sound (without any playback) does not turn the clicking off as I stated earlier but it does, I think, make it more quiet.

And this: I propose we wait (a week or so) to see if any other HP530'ers come up with anything and then starting a new thread: "HP 530 LAPTOP - MAKE THE F******G CLICKING SOUND STOP!"

---

### Post by ruinen on 2009-11-06
I have the same sound problem (had it with RC and Beta as well). Definitely sounds like it is powering off the speak and creating a click.

---

### Post by quodlibet on 2009-11-07
Our clicking problem is a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201)

And the solution is:

> **P4man said:**
> 

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```If the last line looks like this:
```

# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```comment the last line out:

```
# Power down HDA controllers after 10 idle seconds
# options snd-hda-intel power_save=10 power_save_controller=N

```save, reboot, cross fingers.

Reportedly, "snd-hda-intel power_save=0" also works, but I haven't tried it.

---

### Post by gitane79 on 2009-11-10
It appears different laptop brands are concerned as many have the same chipset in their soundcards. I have followed the instructions on [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html) which **solved the issue** for me!


[LIST=1]
[*]```
sudo apt-get update && sudo apt-get install linux-backports-modules-alsa-karmic-generic linux-backports-modules-karmic-generic-pae
```
[*]```
sudo gedit /etc/modprobe.d/alsa-base.conf
```... and comment (add a "#" in front of) the line ```
options snd-hda-intel power_save=10 power_save_controller=N
```
[/LIST]
By the way, nice job on pulseaudio this time. It seems that the issues are dealt with in karmic, I can even use my analogue microphone with Skype while running pulseaudio! In former releases, I had to uninstall pulseaudio and use alsa instead.

---

### Post by Nico666 on 2009-12-29
First of all, sorry about use your thread to post a non-totally related questions, but I tough that it is similar enough to start a new thread.

I'm update my HP 530 from Jaunty to Karmic, and I solve the sound problem as is described here. But I also noticed a very bad graphic performance in comparison with Jaunty. I have been trying different things, but nothing works.

It would be very helpful if HP530 users with Karmic and normal graphic performance could post their /etc/X11/xorg.conf files, and other relevant information (e.g Whether driver package is xserver-xorg-video-intel or any other, composition (compiz-fusion, or other), or if they had similar problems and how they solve it).

I can't post my xorg.conf yet, because I'm working in other computer, but If that could help to solve my problem I will post it as soon as I can.

Thanks,

---

