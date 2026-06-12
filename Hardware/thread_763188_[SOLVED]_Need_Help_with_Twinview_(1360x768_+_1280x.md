---
title: "[SOLVED] Need Help with Twinview (1360x768 + 1280x1024)"
date: 2008-04-22
forum: Hardware
---

### Post by Nexano on 2008-04-22
Hi, I'm using an Nvidia GeForce 7800 Video Card, I currently use my HDTV @ 1360x768 as my monitor.

What I want to do is use my regular computer screen @ 1280x1024 along with the HDTV so that I can for example have IRC on one screen and do something productive on the other:)

I've read through these forums over and over again trying to find a solution.

If anyone at all has this setup working, or has any clue at all on what to do, please answer :(

Link to xorg.conf: [http://pastebin.com/m1f774449](http://pastebin.com/m1f774449)

EDIT: Standard nvidia settings and simple "add Twinview blah blah" doesnt work. My xorg.conf is modified following a guide.

---

### Post by Limpan on 2008-04-23
I assume you have the nVidia drivers enabled.

Then you'll need to install the package nvidia-settings. Either you use Synaptic and search for it or you can run
```

sudo apt-get install nvidia-settings

```
in a terminal.

Then you run
```

sudo nvidia-settings

```
in a terminal and you can then activate your second monitor and change the usual settings.

---

### Post by Nexano on 2008-04-23
> **Limpan said:**
> I assume you have the nVidia drivers enabled.

Then you'll need to install the package nvidia-settings. Either you use Synaptic and search for it or you can run
```

sudo apt-get install nvidia-settings

```
in a terminal.

Then you run
```

sudo nvidia-settings

```
in a terminal and you can then activate your second monitor and change the usual settings.

No I cant, it refuses to let the second monitor use any resolution higher then 640x480.

---

### Post by Limpan on 2008-04-23
I've looked through my own configuration and it works for me but then I have two monitors of the same make and model.

Hopefully someone else on the forums will be able to help but I'm afrain I can not. Sorry.

---

### Post by Nexano on 2008-05-29
Problem Solved. DVI + VGA is a no go. So switched over to VGA + VGA and did some xorg editing. (Some, being an understatement.)

---

