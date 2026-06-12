---
title: "Only one native program can have audio at a time?"
date: 2009-03-07
forum: Hardware
---

### Post by beastrace91 on 2009-03-07
Is there a way I can make it so I can have audio coming from multiple native programs at the same time? Most times I like to leave fire fox playing music from pandora while I game... but for some reason when I am running any native game the sound does not work while firefox is open and playing sound... how ever all of my windows games I run through Wine and/or Cedega work with the sound at the same time just fine... is there a way to make my native Linux games do this as well?

~Jeff

---

### Post by bazzer on 2009-03-13
Sounds to me like you want ALSA to control your outputs.

---

### Post by yusuo85 on 2009-03-13
i had exactly the same problem, bit of searching and it was easy to solve, share tha love i say so here you go
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by alexroat on 2009-03-14
Hello,
this is a pulse audio configuration problem.

To fix it simply install asoundconf-gtk
```

sudo apt-get install asoundconf-gtk
```

Then launch as current user 

```
asoundconf-gtk
```

Choose Pulseaudio from the list and then press quit.

Reboot your machine and you'll be able to run a video on youtube and listen some music with Totem at the same time.

Cheers.

Alessandro

---

### Post by wastedfluid on 2009-04-13
> **alexroat said:**
> Hello,
this is a pulse audio configuration problem.

To fix it simply install asoundconf-gtk
```

sudo apt-get install asoundconf-gtk
```

Then launch as current user 

```
asoundconf-gtk
```

Choose Pulseaudio from the list and then press quit.

Reboot your machine and you'll be able to run a video on youtube and listen some music with Totem at the same time.

Cheers.

Alessandro

Hello,

Unfortunately, this did not work for me.  Sorry to "revive" an old thread,

but the first application to use sound on my jaunty system.. is the only one that can.  The only work around I'ev found is 'alsa force-reload' - and then whatever the fisrt program to play sound is.. will be the only one, until you re-load.

I've ran the asound app, and chose 'pulseaudio' - but it did not help.

Any other ideas?

---

