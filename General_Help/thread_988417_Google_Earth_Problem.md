---
title: "Google Earth Problem"
date: 2008-11-20
forum: General Help
---

### Post by G-Dub on 2008-11-20
I successfully installed google earth. I downloaded the .bin file of their website, made the file executable, and ran it through the terminal. I booted up google earth, no earth appears. All i can see is outerspace. I cannot go anywhere. Anybody have a clue what might be happening?

---

### Post by pennacook on 2008-11-20
Is the planet button on? Untoggle that and you should see Earth.

---

### Post by G-Dub on 2008-11-20
All the buttons are grayed out, here is a screen

---

### Post by scouser73 on 2008-11-20
What I'd suggest is that you delete the current version of Google Earth and install Ubuntu Tweak; [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/") as it should install version 4.2. I had previously installed version 4.3 independently of Ubuntu Tweak and found that the Earth was missing.

---

### Post by fatphilthethird on 2008-11-21
It's a problem with the permissions I think. Does the earth appear if you run:

```
gksudo googleearth
```

If so, you need to amend the permssions on a configuration file. See here

[http://ubuntuforums.org/showthread.php?t=822138](http://ubuntuforums.org/showthread.php?t=822138)

Fat

---

### Post by G-Dub on 2008-11-21
> **fatphilthethird said:**
> It's a problem with the permissions I think. Does the earth appear if you run:

```
gksudo googleearth
```

If so, you need to amend the permssions on a configuration file. See here

[http://ubuntuforums.org/showthread.php?t=822138](http://ubuntuforums.org/showthread.php?t=822138)

Fat

Woo Hoo! That worked! Thanks!

---

### Post by SocratesTNR on 2008-11-23
WooHoo Too!

This is better than having a geek on retainer...

Thanks guys (and girlz...)

---

### Post by Wharf Rat on 2008-11-23
Fat,
Thanks!  It fixed my problem too.

---

### Post by philinux on 2008-11-23
For anyone else reading this, google earth is available, from Medibuntu, as an easy to install .deb package within synaptic.

Click the medibuntu link below to enable their repositories.

---

### Post by mynydd on 2008-11-24
> **philinux said:**
> For anyone else reading this, google earth is available, from Medibuntu, as an easy to install .deb package within synaptic.

Click the medibuntu link below to enable their repositories.

I just clicked on your medibuntu link and synaptic won't run. I just get...


[COLOR="DarkOrange"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR]

Could someone help me fix the error?

OK it is fixed now.
All I needed to do was open a terminal and type 'dpkg --configure -a'.............doh!!!!!

---

