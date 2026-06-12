---
title: "Lenovo s10-3s No Suspend or Hibernate"
date: 2010-09-05
forum: Hardware
---

### Post by swiftarrow on 2010-09-05
Hi friends!

I just got a new Lenovo s10 - 3s netbook and put Ubuntu on it.  It works really nice, with only one (rather large) problem:  The computer will not sleep or hibernate!  The only power options are On, or Off.

If I try to sleep, it will shut off the screen and hang, with CPU on, power LED on, etc.  Same story with Hibernate.  Waiting doesn't solve it.  Hard power down is required, and then power up.  Right now it's running EasyPeasy 1.6, which is just plain UNR 10.04 with a bit of a different interface.

I'm pretty sure that this can be solved by passing some kernel options at boot (I remember doing something like that for an old Inspiron), but I don't have any idea what the options would be.

Is there anyone with experience who can give me some pointers or tell me what to try?

Thanks!

---

### Post by m.izadi on 2010-11-28
With ubuntu 10.04, I had the same problem with suspend (hang), but a different problem with hibernate: after hibernation, the computer turned on again. In other words, instead of "hibernate+shut down" it performed "hibernate+restart"!
After upgrade to ubuntu 10.10 both of the problems solved. (But new problems arose!)

---

### Post by matt_symes on 2010-11-28
Hi

Open a termial and type

sudo pm-suspend

then enter your password. Nothing will be echoed to the screen. This is normal

Does it suspend or say file not found?

You might have to install it using

sudo apt-get install acpi-support

Kind regards

---

### Post by swiftarrow on 2010-11-29
Hey, Thanks for the replies!

The problem still persists, and I have more problems now:

Using Ubuntu 10.04, btw.

Hibernate shuts down and restarts.

Sleep turns off monitor, but system is still on full blast.

SOUND: after using voice chat (with both microphone and speakers active) for about 20 minutes, the speakers just shut off.  Mic is still working, but speakers are not.  Restart required to fix.  Sometimes happens within 5 minutes.

Also, plugging in headphones does not turn off the onboard speakers.

EDIT: acpi-support is installed, just checked.

I'd rather not upgrade to 10.10, want to stay with the LTS.  Is there a backported kernel?

Thanks again!

---

### Post by m.izadi on 2010-11-29
> **swiftarrow said:**
> 
Also, plugging in headphones does not turn off the onboard speakers.


In 10.04, for this problem I first added apt repository 'ppa:ubuntu-audio-dev/ppa' and updated and the problem was solved. But after a while it returned (may be due to some updates).

Now, I've inastalled hda-verb (may be from [http://www.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/](http://www.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/)) and use the following commands to turn on/off the speakers on demand:

To turn on:
```
hda-verb /dev/snd/hwC0D0 0x1f 0x701 0
```

To turn off:
```
hda-verb /dev/snd/hwC0D0 0x1f 0x701 1
```

> **swiftarrow said:**
> 
I'd rather not upgrade to 10.10, want to stay with the LTS.


Currently, I suggest you not to upgrade. On my S10-3s it has some problems which are really annoying, compared to your problems.

For example after every hibernate/suspend the wireless becomes disabled. And very often NetworkManager disappears from notification area and network gets disconnected and my only solution is to restart!

Or touchpad keys don't work. Just tapping works, which is little hard for right-clicking!

You may find this article interesting: [Linux on the Lenovo S10-3s: Scorecard (Rap Sheet?)]("http://www.zdnet.co.uk/blogs/jamies-mostly-linux-stuff-10006480/linux-on-the-lenovo-s10-3s-scorecard-rap-sheet-10021131/")

---

### Post by matt_symes on 2010-11-29
Hi

Have a look at this for your speaker/headphones issue. It may hold some clues.

[http://ubuntuforums.org/showthread.php?t=1366524&highlight=headphones+speakers](http://ubuntuforums.org/showthread.php?t=1366524&highlight=headphones+speakers)

What did you do to get hibernate to work?

> For example after every hibernate/suspend the wireless becomes disabled.  And very often NetworkManager disappears from notification area and  network gets disconnected and my only solution is to restart!

Have you tried something like (at the terminal)

/etc/init.d/networking restart

or
[FONT=monospace]
[/FONT]sudo ifdown wlan0 && sudo ifup wlan0

Kind regards

---

### Post by swiftarrow on 2010-11-30
Hey guys,

I have a confession: this isn't my computer... It's for my Mom.

So, unfortunately, hackish solutions like running commands to turn off the speakers is out of the question. :D

I haven't tried the Wi-Fi, and am also wondering how the built-in 3G modem will work with Linux (but don't have a sim card to test it on).

> In 10.04, for this problem I first added apt repository 'ppa:ubuntu-audio-dev/ppa' and updated and the problem was solved. But after a while it returned (may be due to some updates).

Since that's the development ppa, I don't want to use it either.  Mom must have a consistently improving experience, no today-it-works stuff :)

I'll take a look at the sound solutions in that forum link, thanks for that!  Hope something will turn up.

---

### Post by m.izadi on 2010-11-30
> **matt_symes said:**
> 
Have a look at this for your speaker/headphones issue. It may hold some clues.

[http://ubuntuforums.org/showthread.php?t=1366524&highlight=headphones+speakers](http://ubuntuforums.org/showthread.php?t=1366524&highlight=headphones+speakers)


According to the link, I added the following to [FONT=monospace]/etc/modprobe.d/alsa-base.conf[/FONT]:
```
options snd-hda-intel model=auto
```

Now everything works fine. (I have also removed the PPA and downgraded the packages to the stable version.)

But, the '[FONT=monospace]hda-verb[/FONT]' method has one advantage: Both speaker and headphone could play at the same time, which is useful in some occasions! It would be nice if volume of speaker and headphone could be managed separately.

Reminder: my Ubuntu is 10.10.

---

### Post by m.izadi on 2010-12-01
> **matt_symes said:**
> 
Have you tried something like (at the terminal)

/etc/init.d/networking restart

or
[FONT=monospace]
[/FONT]sudo ifdown wlan0 && sudo ifup wlan0


Yes. None of them worked! (I used [FONT=monospace]eth1[/FONT] instead of [FONT=monospace]wlan0[/FONT]. My wireless is known as [FONT=monospace]eth1[/FONT])

---

### Post by jessielikesmath on 2010-12-02
Same netbook, same version of UNR, similar problem.

It just started over the last weekend for me. I used to occasionally have the problem where I would shut the lid and the machine wouldn't stop (I usually wouldn't notice until I pulled it out of my bag later and the battery was dead). Over the weekend I found that when I shut the lid the computer completely shuts off. When I turn it back on I have to enable networking, something I've never had to do upon turning on my computer before.

I'm a complete noob to linux and have practically no idea what I'm doing. Before this all my problems were pretty simple to fix.

Any ideas?

---

### Post by m.izadi on 2010-12-05
> **m.izadi said:**
> 
And very often NetworkManager disappears from notification area and network gets disconnected and my only solution is to restart!


It seems that the NetworkManager crashes! Running [FONT=monospace]nm-applet[/FONT] solves this problem.

Moreover, after an update (including kernel update to 2.6.35-23) I have two new problems:
[LIST=1]
[*]Ubuntu does not recognize my Ethernet device at all. No more wired connection!
[*]Resume from hibernate hangs Ubuntu, which is essentially equivalent to no hibernate!
[/LIST]

Ubuntu is going to disappoint me!

---

### Post by byronpdx on 2011-01-24
I too have this issue. I installed 10.4 netbook and everything worked well. But about 2 weeks ago the suspend started to fail. It looked like it suspended but it turned the computer off instead of just suspending it. The suspend log looks normal as far as I can tell but it shuts the power off instead of turning the power light into a blinking light. This is a major problem for a netbook, and is something that used to work just fine.

I tried hibernate but it would go through all the work and then immediately restart. Not much use and it ran down the battery when I didn't notice it at first.

I tried a number of different solutions but nothing worked so I upgrade to 10.10. Don't like the new interface as well as the old one, but it did not solve the problem of suspend and hibernate.

Again, suspend turns the computer off instead of "suspending" forcing a restart when you power back up.

Hibernate does a suspend to disk, then an immediate restart.

I am ready to go back to Windows just to get this functionality back even though I hate almost everything about windows. Please, will someone find a solution! This has to be software as it used to work just fine! I can't seem to find what was changed that caused this to happen.

---

### Post by tjmachado on 2011-04-29
just upgraded to v11, same issue :(

---

