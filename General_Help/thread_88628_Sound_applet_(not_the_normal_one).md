---
title: "Sound applet (not the normal one)"
date: 2005-11-10
forum: General Help
---

### Post by Haegin on 2005-11-10
Is it possible to get a sound applet that lets you - with a right click - select the current default device so i can easily switch to headphone output when listening at night? I have usb headphones so I can't just plug em in...
Also if one does exist can it alter the volume on the current device?

Finally, if it doesn't exist, how hard would it be to make one in python (I just got a book on it (dive into python) and want a project to learn with as I cant learn with hello world programs (trust me - i tried enough times)). Also what stuff (modules or whatever they are called) would I need to make one?

Thanks

---

### Post by Haegin on 2005-11-11
Any ideas? Anybody?

---

### Post by Haegin on 2005-11-14
#bump#

nothing? at all?

---

### Post by Haegin on 2005-11-16
Hmm, evidently nobody needs to switch soundcards often.. Oh well - I found that by running
```

$ set-default-soundcard <number of soundcard>

```
Now as I know my soundcard numbers (0 and 1, 1 being headphones) I just need to work out how to tell alsa to switch to that soundcard (reload the config i assume)

Does anybody have a clue how to do this?

---

### Post by GameGod on 2005-11-16
Hmmm... after you run that command, did you try:

```

sudo /etc/init.d/alsa reload
sudo /etc/init.d/alsa-utils restart

```

---

### Post by Haegin on 2005-11-16
Yeah - they didnt work :( (and force-reload just mucked up all the sound entirely)
If I change the default soundcard then go into gnome-sound-properties then the default is set as the one I specified when I ran the command but it still plays on the other card.


I'll have to keep fiddling it seems...

---

### Post by GameGod on 2005-11-16
I would just rmmod the driver for the soundcard you don't want to work... That should do the job...

GNOME with two soundcards is kinda lacking though, I know your pain... The multimedia volume control on my keyboard works great, but there's no way to configure which soundcard it uses (I wonder if it's in bugzilla)... the only way I can make it work is by unloading the driver for my non-used soundcard...

---

### Post by Haegin on 2005-11-16
Thing is: I want to be able to switch to and from headphones quickly. They are usb headphones so appear as a second sound card. Its annoying...
grrr

---

