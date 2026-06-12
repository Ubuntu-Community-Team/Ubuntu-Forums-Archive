---
title: "Pulseaudio and laptop speakers"
date: 2009-05-02
forum: Hardware
---

### Post by karvec on 2009-05-02
I installed 9.04 and haven't had audio from my speakers since.  Was wondering if there was anyone whose had the same problem.  Speaker jack works fine, but its annoying to use all the time.

Audio:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Umm, not sure if there's any other specs I need to post, if there is let me know and I'll post them.

---

### Post by jords on 2009-05-02
I had a similar problem when i installed ubuntu a while ago, I have a ICH9 intel sound controller so might be a different solution though.

I fixed it by following some of the instructions on this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027) , not sure exactly which ones now or what was actually neseccary. I think that just adding the "options snd-hda-intel model=mobile" line to /etc/modprobe.d/alsa-base and /etc/modprobe.d/options  and rebooting was all that's needed.

However, neither of those files exist since i've upgraded to 9.04 but my sound is still working... not sure what's happened there :)

---

### Post by -kg- on 2009-05-02
> **jords said:**
> I had a similar problem when i installed ubuntu a while ago, I have a ICH9 intel sound controller so might be a different solution though.

I fixed it by following some of the instructions on this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027) , not sure exactly which ones now or what was actually neseccary. I think that just adding the "options snd-hda-intel model=mobile" line to /etc/modprobe.d/alsa-base and /etc/modprobe.d/options  and rebooting was all that's needed.

However, neither of those files exist since i've upgraded to 9.04 but my sound is still working... not sure what's happened there :)

I had a similar but opposite problem where the speakers would work, but the headphone jack didn't, and I had to add a line to my /etc/modprobe.d/alsa-base file.  Upon upgrade to Jaunty I, also, found that that file no longer existed.

But it does exist.  I navigated down into the directory and found that there is a suffix appended to it.  The file is now alsa-base[COLOR="Red"].conf[/COLOR].  I don't know why they tacked the ".conf" to the end of it, but it's there and accessible.  I added my line when I upgraded to Jaunty and my headphone jack immediately started working (after reboot, of course).

As far as the "options" file, if it is necessary to modify that file as well, then navigate down into the menu and see whether it might be there with such a suffix attached to it, as well.  If something like it is present, then open it with Gedit and see if it contains familiar commands and, if so, edit it as required.

---

### Post by karvec on 2009-05-03
Tried both those fixes and had no luck, also followed the howto on UbuntuWiki for alsa.

Not sure what else to do, headphones still work, speakers still do not.

I know I had trouble in windows with the sound card drivers as well, they were hard to hunt down.  *shrugs*

Any other suggestions?

---

