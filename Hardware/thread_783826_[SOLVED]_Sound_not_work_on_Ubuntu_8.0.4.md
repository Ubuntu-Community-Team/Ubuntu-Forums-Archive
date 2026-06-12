---
title: "[SOLVED] Sound not work on Ubuntu 8.0.4"
date: 2008-05-06
forum: Hardware
---

### Post by ngduonglam on 2008-05-06
Hi all,

I have just installed Ubuntu 8.0.4 on my Lenovo 3000 n200 laptop with Windows Vista installed to run dual OS.

Every is ok except that the sound is not work although I tried to configure the sound as some of you guys show in this forum.

Could any of you show me how to solve this? I really need sound. Thanks.

---

### Post by manish779 on 2008-05-06
I had the same problem with the Acer Aspire 5583 I have.

Have you tried configuring the sound using ALSA?

Right click on the Sound.

Select "Open Volume Control"

In File menu select the "Change Device".. Please tell what are the things you see.

If you can see "HDA Intel". Select it.

Now go to Edit menu and choose "Preferences".

Select "PCM". Close.

Now there should be PCM in your Volume Control. Make the sound adjustments for Master and PCM to FULL.

Run any sound file on your machine. Do you here the sound?

---

### Post by Nxx on 2008-05-06
I have no "HDA Intel", no device at all.

---

### Post by ngduonglam on 2008-05-06
> **manish779 said:**
> I had the same problem with the Acer Aspire 5583 I have.

Have you tried configuring the sound using ALSA?

Right click on the Sound.

Select "Open Volume Control"

In File menu select the "Change Device".. Please tell what are the things you see.

If you can see "HDA Intel". Select it.

Now go to Edit menu and choose "Preferences".

Select "PCM". Close.

Now there should be PCM in your Volume Control. Make the sound adjustments for Master and PCM to FULL.

Run any sound file on your machine. Do you here the sound?

I tried as your suggestion, choose HDA Intel, then select PCM. However, no sound at all although after restart.

Any other suggestions? Thanks.

---

### Post by ngduonglam on 2008-05-15
I tried to re-install ubuntu, then add the following line to /etc/modprobe.d/alsa-base file

options snd-hda-intel model=lenovo

Then restart, and it works now :)

---

### Post by kempy on 2008-05-28
> **manish779 said:**
> I had the same problem with the Acer Aspire 5583 I have.

Have you tried configuring the sound using ALSA?

Right click on the Sound.

Select "Open Volume Control"

In File menu select the "Change Device".. Please tell what are the things you see.

If you can see "HDA Intel". Select it.

Now go to Edit menu and choose "Preferences".

Select "PCM". Close.

Now there should be PCM in your Volume Control. Make the sound adjustments for Master and PCM to FULL.

Run any sound file on your machine. Do you here the sound?


Thanks, mannish, this helped me out a bunch.  Except, instead of PCM, I needed to check off "Surround".  Once I had "Surround" in my volume control, I un-muted it and now I finally have sound.  My laptop is an Acer Aspire 5920.

I probably wouldn't have had to look for a solution in the forums if I had remembered that I removed the volume control from the panel right after I installed Ubuntu...

Thanks again.

---

### Post by phx129 on 2008-06-09
> **ngduonglam said:**
> I tried to re-install ubuntu, then add the following line to /etc/modprobe.d/alsa-base file

options snd-hda-intel model=lenovo

Then restart, and it works now :)

I have the exact lineup as you, worked just fine.
For the noobs, its "sudo gedit /etc/modprobe.d/alsa-base ."
Thanks!

---

