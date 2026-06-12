---
title: "Sound problem"
date: 2005-11-03
forum: General Help
---

### Post by dJnEvS on 2005-11-03
I've got a wierd sound prob.
i do have sound,
only my movies doesnt play audio.
and my MP3's doesnt work
it runs, and maybe 1 or 2 sec later: Playlist finished..

how can i fix this prob? :confused:

---

### Post by tonysathre on 2005-11-03
do u have win32codecs

---

### Post by dJnEvS on 2005-11-04
dunno, where can i see/get it?

---

### Post by shinygerbil on 2005-11-04
What programs are you using?

---

### Post by dJnEvS on 2005-11-04
kaffeine
xmms
amaroK
noatun

---

### Post by Breaks on 2005-11-04
Have you tried using a different sound engine with amarok? and what sound engine are you currently using? you can check this by going into the preferences and then looking at the "engine" options.

---

### Post by dJnEvS on 2005-11-04
aRts Engine...

---

### Post by Breaks on 2005-11-04
Try using "xine" engine, as thats the one i found to work for me.

```

sudo apt-get install amarok-xine

```

Although you'll need to allow the extra repositories within synpatic to get that.

---

### Post by dJnEvS on 2005-11-04
cant find amarok-xine..

---

### Post by Breaks on 2005-11-04
Yeah because you most likely havent got the extra repositories allowed within synaptic that amarok-xine is located within. Im at college at the moment so i cant tell you how to do it until i get home (as they use windows here, urgh, and i dont know it off by heart). So unless someone else posts how to get that working before i get home, ill do it when i get back which should be in about 3 hours max :D.

---

### Post by dJnEvS on 2005-11-04
ok.. :)
i do remember that i have to put some lines in a file.. kinda urls where apt-get downloads from..
but i dont remember the file.. 8-)

---

### Post by shinygerbil on 2005-11-04
Ok, you need to edit the file: /etc/apt/sources.list

Make sure you're root when you do this, so open up Konsole and type something like:

```
kdesu kwrite /etc/apt/sources.list
```

You should find some lines with comments (shown by # or ## in front of them), that look like the following:

```
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
```

They may look different to this, my file has been changed beyond recognition ;) but basically, remove the comments from the ones with 'universe' or 'multiverse' or 'restricted'. Then do the following:

```
sudo apt-get update
```

and you should be able to see the packages :)

You can also do this through Adept, by opening it, going to Adept -> Manage Repositories and right-clicking on the greyed out lines and clicking Enable. And there's a similar option in Synaptic, and I presume, Kynaptic too. But you still have to update afterwards, however you do it.

Steve

---

### Post by dJnEvS on 2005-11-04
yea, thanks. i have installed xine now.
but if i want to play a mp3, it crashes :S
no error, nothing
it jus' turns off...

---

### Post by dJnEvS on 2005-11-04
bump

---

### Post by Diod on 2005-11-04
Go into xine options then change configuration experience level to advanced, then press apply and then click the Audio tab. Set audio driver to use to auto and press apply and ok

But i dont use xine as mp3 player. I use amarok. U should get it too. And once u have it goto amarok's options and:

then click the engine tab and select xine as sound engine

---

### Post by dJnEvS on 2005-11-04
now amarok crashes also.. :s

---

### Post by dJnEvS on 2005-11-04
dunno what i've done.
but my mp3 works :D

---

### Post by Breaks on 2005-11-04
Apologies i never got back to you sooner on this issue. But im glad its all sorted now :).

---

### Post by tonysathre on 2005-11-07
get XMMS for MP3's

---

