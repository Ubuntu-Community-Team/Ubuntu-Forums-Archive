---
title: "Nvidia Drivers?"
date: 2008-05-24
forum: Hardware
---

### Post by tckrockz on 2008-05-24
when i installed Ubuntu 8.04 when it was released i got the main pain in my head which was the VGA Drivers the screen resolution problem...so many people gave solutions and sadly none of them worked so i came back to windows again :( i m gonna give another try today i just want to know can u suggest me a solution for the driver problem ? plz...

---

### Post by atomkarinca on 2008-05-24
I had the resolution problem, too. When I installed 8.04 I let Hardware Drivers install the drivers for me. Under /usr/share/applications there is an application called "Screens and Graphics", I selected my Monitor from the list and restarted. After that I was able to select my native list from Nvidia Settings. I started it with sudo

```
gksudo nvidia-settings
```

selected my native resolution and frequency and hit "Save to X Configuration File", after I restarted everything was OK.

---

### Post by sdennie on 2008-05-24
You may also want to check out envy if you are having problems.  It's been known to sort out many problems:

```

sudo apt-get install envyng-gtk

```

If you managed to get your gui up but not configured correctly, run:

```

envyng-gtk

```

If you can only managed to get to the terminal, try:

```

envyng

```

---

### Post by tckrockz on 2008-05-24
> **atomkarinca said:**
> I had the resolution problem, too. When I installed 8.04 I let Hardware Drivers install the drivers for me. Under /usr/share/applications there is an application called "Screens and Graphics", I selected my Monitor from the list and restarted. After that I was able to select my native list from Nvidia Settings. I started it with sudo

```
gksudo nvidia-settings
```

selected my native resolution and frequency and hit "Save to X Configuration File", after I restarted everything was OK.

thanks alot bro...i tried ur method n its working like a charm...cheers....thankss..:guitar::guitar::guitar:

---

### Post by tckrockz on 2008-05-24
> **vor said:**
> You may also want to check out envy if you are having problems.  It's been known to sort out many problems:

```

sudo apt-get install envyng-gtk

```

If you managed to get your gui up but not configured correctly, run:

```

envyng-gtk

```

If you can only managed to get to the terminal, try:

```

envyng

```
i tired envy last time n it dint give any good results but i tired the post above and its working like a charm thanks anyways :D

---

### Post by atomkarinca on 2008-05-24
> **tckrockz said:**
> thanks alot bro...i tried ur method n its working like a charm...cheers....thankss..:guitar::guitar::guitar:

No problem mate.

---

