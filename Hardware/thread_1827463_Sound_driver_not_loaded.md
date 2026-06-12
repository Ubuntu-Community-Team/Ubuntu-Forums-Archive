---
title: "Sound driver not loaded?"
date: 2011-08-18
forum: Hardware
---

### Post by LunarSandwich on 2011-08-18
I did some searching and found some drivers that were meant to install by default for my sound card but for some reason didn't...

but for the life of me I can't seem to get them to install, I'm new to linux so the terminal is quiet a hassle atm

Is there a way to get someone to remote connect like windows to my linux to fix the problem? It'd probably only take a few mins and probably half of you guys could do it but the linux snippet codes for the terminal that the site provided I just couldn't tweak to get it to work for myself

and maybe while they're there they can teach me how to get the jiggly windows when you drag them :O

I'm stuck with Windows 'till I can get those sound drivers working

---

### Post by fdrake on 2011-08-18
remote connect from a stranger is something not advisable . However just open the terminal and we will guide you. Copy & paste this
```

lspci | grep Audio

```

and post here the output so we know what kind of audiocard u have.

---

### Post by LunarSandwich on 2011-08-18
> **fdrake said:**
> remote connect from a stranger is something not advisable . However just open the terminal and we will guide you. Copy & paste this
```

lspci | grep Audio

```and post here the output so we know what kind of audiocard u have.
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]

Edit: OK

Apparently I do have audio.... just not with my good headset (usb)

I only have a pair of 5$ audio jack headphones and would like to use my USB headset which was 40$ so I don't wanna not use them lol


edit2:

**[*Logitech* ClearChat *Comfort USB*]("http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=USB+logitech+comfort+headsets&oe=utf-8&um=1&ie=UTF-8&tbm=shop&cid=3844041679359977382&sa=X&ei=ZaFMTsuKC8i70AG0iYysBw&ved=0CC4Q8wIwAA")**


is what I got

---

### Post by fdrake on 2011-08-18
> **LunarSandwich said:**
> 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]

Edit: OK

Apparently I do have audio.... just not with my good headset (usb)

I only have a pair of 5$ audio jack headphones and would like to use my USB headset which was 40$ so I don't wanna not use them lol

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install alsa alsa-base
sudo cat /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=laptop
[press enter]
[press Ctrl+c]

```
reboot and try.

---

### Post by LunarSandwich on 2011-08-18
> **fdrake said:**
> ```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install alsa alsa-base
sudo cat /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=laptop
[press enter]
[press Ctrl+c]

```reboot and try.

no luck :(

edit:
omg I'm awesome.

Fixed it by going to System->Preferences->Sound

Went to output tab

and then selected my headset XD

---

### Post by fdrake on 2011-08-18
> **LunarSandwich said:**
> no luck :(

edit:
omg I'm awesome.

Fixed it by going to System->Preferences->Sound

Went to output tab

and then selected my headset XD

:confused::P  ok. don't forget to mark the thread as solved.

---

