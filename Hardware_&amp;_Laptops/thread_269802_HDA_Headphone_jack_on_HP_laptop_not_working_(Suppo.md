---
title: "HDA Headphone jack on HP laptop not working (Support in Alsa 1.0.13?): Alsa help?"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2006-10-02
I just bought an HP dv6000z laptop. I've got almost everything working. However, the front headphone jack on the laptop is not working, the system just ignores it.

This particular laptop uses the Intel/nVidia HDA driver. According to this page: [http://alsa-project.org/changes/v1-0-12--v1-0-13.txt](http://alsa-project.org/changes/v1-0-12--v1-0-13.txt) , the new version of ALSA has support for the jack.

Has anyone had experience installing ALSA from source, or does anyone know what I would need to install (because ALSA is broken up into several little packages)?

OR, could we get ALSA 1.0.13 added to Ubuntu? Now that would be nice. Furthermore, should I post a bug for this?

---

### Post by Charles Hand on 2006-10-04
I have intel ich7 on my Vaio laptop, and the version 1.0.13 doesn't fix the headphone problem.

---

### Post by Charles Hand on 2006-10-04
After following the procedure on the alsa-project.org site for hda-intel (not the procedure in the thread [http://www.ubuntuforums.org/showthread.php?t=265027](http://www.ubuntuforums.org/showthread.php?t=265027)
which is a subset of the alsa-project procedure)
and after rebooting a couple of times, I got the headphone to work.

After following the procedure, look at /proc/asound/version to see whether the 1.0.13 version is being installed.

---

### Post by Exclamation on 2006-10-04
A patch needs to be applied to alsa.
Heres the ubuntu bug ive filed:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/59715](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/59715)

If you really want to get ti working use the instructions here with alsa 1.0.12:
[http://xopen.dyndns.org/linux/v6024ea/](http://xopen.dyndns.org/linux/v6024ea/)

---

### Post by enigma_0Z on 2006-10-04
Yeah, I just got it fixed today, but what I did was a real hack. All I did was took the 1.0.13 source, and copied the hda_intel.c file from the 1.0.12 source into the newer version...

I'll try the patch (my method is still dodgy at best...).

What was wrong with the update, eg. what does that diff fix?

---

### Post by enigma_0Z on 2006-10-05
Applied the patch, the headphones work *sometimes* now. Sometimes when I boot up I get the extra controls, and everything is dandy, but other times it comes up with just the PCM and Master (no headphone) controls. Is there a kernel option that I am missing or something?

---

### Post by mock_turtle on 2006-11-08
i ve also applied the patch (to a hp dv6000) but now i cant get sound output from speaker :) this is a funny bug. anybody can help?

---

### Post by shankariyer on 2006-11-16
['enigma_0Z]("http://ubuntuforums.org/member.php?u=22439")', how were you able to install Edgy. It freezes up and doens't get me to the login screen. Any tweaks you had to make to get this going ?

Details would be greatly appreciated.

---

### Post by enigma_0Z on 2006-11-18
> **shankariyer said:**
> ['enigma_0Z]("http://ubuntuforums.org/member.php?u=22439")', how were you able to install Edgy. It freezes up and doens't get me to the login screen. Any tweaks you had to make to get this going ?

Details would be greatly appreciated.

-- let me hijack this thread --

Do you have a laptop? Some laptops do not like usplash.

Try getting rid of "quiet splash" on your "kernel" line of grub ("e" on the kernel to boot, arrow to the line beginning with kernel, "e", edit, ENTER, "b" to boot.)

Then  you would change your config in /boot/grub/menu.lst .

---

