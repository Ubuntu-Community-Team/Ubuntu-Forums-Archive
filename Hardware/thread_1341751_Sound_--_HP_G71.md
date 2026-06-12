---
title: "Sound -- HP G71"
date: 2009-11-30
forum: Hardware
---

### Post by mschap on 2009-11-30
Did a search and came up empty.  I have checked the settings - nothing is muted - so I will get that out of the way to begin with.
In addition did the medibuntu install etc. Again, no luck.

I have just acquired HP G71 (G71-343US) and have no sound.  Any suggestions would be deeply appreciated.

In advance thank-you

---

### Post by tarun on 2009-12-03
I am having the same issue with the same model. When I plug in my headphones it works. Without the headphones, it doesn't play anything.

---

### Post by tarun on 2009-12-03
This is SOLVED. Follow the instructions [on this page.]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/91675")

---

### Post by erfahren on 2009-12-04
> **tarun said:**
> This is SOLVED. Follow the instructions [on this page.]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/91675")
sweet! thanks for the link [COLOR="Blue"]Tarun[/COLOR] - it did the trick for me 

I'm pretty happy with my G71 - it's pretty nice I think


[COLOR="Blue"][SIZE="3"]mschap[/SIZE][/COLOR] - if that solution worked for you pls mark this thread as "Solved" by going to the "Thread Tools" above your first post


To make this easy for anyone with same issue, this is what you do
backup the alsa-base.conf file first if you want
```

sudo cp /etc/modprobe.d/alsa-base.conf /etc/modprobe.d/alsa-base.conf_back

```
open it in Gedit to edit it (use "gksu" since Gedit is a GUI app)
```

gksu gedit /etc/modprobe.d/alsa-base.conf

```
add the following to the bottom of the file then save and restart
```

# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

```

---

### Post by eliaspoveda on 2009-12-04
Thanks!!!

It worked!! The only isuue I find is that Spotify (Wine) can't play any song, it says "There's a problem with the sound card" :(

Any solution?

Thanks again.

EDIT: My microphone is still not recording. :(

---

### Post by Madmoose on 2010-05-07
Hello, 

This worked for me. I found this after I placed a post, so I guess I'll close it. 

Thanks guys!

---

