---
title: "No Audio on Acer Aspire 3680"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by kc0zbv on 2007-07-25
I am going crazy with this! I have everything on my Acer Aspire 3680 working but the sound! I have gone through the other threads and have followed advice and have gotten nothing.  My sound is still not there.

I have unmuted the surround which seems to have worked on other machines, and I have added patches, etc as suggested by others.

Is there *any* other way I can get sound?  I am new to Linux so please talk in kindergarten, step by step talk so I can get it.

Thanks!

---

### Post by qhobbes on 2007-08-06
Goto System / Preferences / Sound, everything should be Auto, Sound cap. should be ALSA, Device should be HDA Intel (Alsa mixer), select Surround, hold down the Fn key and press F8 (it needs to be unmuted)

I installed Ubuntu with Wubi

---

### Post by darrenrxm on 2007-08-07
I have the same laptop and sound worked for me right out of the box. But I did install linux mint cassandra. And yes the headphones do work but you have to change one of the settings in the volume control panel.

---

### Post by Sparkfist on 2007-09-12
I was able to get audio to work, but even with the volume all the way up I have to put my ear to the speaker to hear anything. Is there anyway to fix this?

---

### Post by MissShona on 2008-02-09
I have an Acer 3680-2762 running Feisty (Kubuntu version).  I was able to fix this problem by:

Going to the root shell and entering
> vi /etc/modprobe.d/alsa-base

Then adding

> options snd-hda-intel model=auto

at the bottom of the file.  Save your changes, rebooted...and my sound worked!  :)

---

### Post by ljonesj on 2008-02-09
i had to do that with 7.04 to get mine working with gutsy it worked out of the box

---

### Post by missiledave on 2008-02-24
> **kc0zbv said:**
> I am going crazy with this! I have everything on my Acer Aspire 3680 working but the sound! I have gone through the other threads and have followed advice and have gotten nothing.  My sound is still not there.

I have unmuted the surround which seems to have worked on other machines, and I have added patches, etc as suggested by others.

Is there *any* other way I can get sound?  I am new to Linux so please talk in kindergarten, step by step talk so I can get it.

Thanks!

hey duder i have the same notebook and had the same problem until five hours ago. it took some digging but i found this little gem. plug this into a terminal and see what happens.  fixed the whole deal for me in about five seconds.

```

sudo apt-get install linux-backports-modules-generic
```


it just rolls back some audio modules.  good luck, lemme know if it works.

---

