---
title: "Logitech Mediaplay Cordless Mouse"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by SirTode on 2006-03-05
Hey folks. I'm running 5.1 on a small Shuttle PC, with intention of using it as a media player with the tv & stereo. I'm having a few problems, but one at a time... the first is that my Logitech Mediaplay mouse (basically a usb wireless mouse with some extra media player buttons) won't detect and work at all. 

All I've done is plug it in and move it, so if there's more to it than that, let me know. My microsoft usb mouse works fine, but I need the wireless or it's no good for the living room, and thus it's back to the waiting spider-like arms of microsoft... sigh.

But I'm sure that someone here can help. :>

---

### Post by SirTode on 2006-03-05
Ok, apologies for my ineptitude - I found a bunch of post about this very mouse. I thought I had searched for it, I dunno...

Anyways, I tried the instructions here, which seemed like the best bet...

[http://ubuntuforums.org/showpost.php?p=560528&postcount=140](http://ubuntuforums.org/showpost.php?p=560528&postcount=140)

And I got as far as running make, which I didn't have installed, so I ran

apt-get install make

And then ran make again, and got this...

make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/sirtode/lmpcm_usb-0.5.3 modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

What am I missing, and what do I need to do here? Thanks folks...

---

### Post by vargasman on 2006-12-23
Sorry for bring up and old post but I'm having the same problem with the make command. Does anyone know a solution for this problem?

---

### Post by L14UX_1NS1D3 on 2006-12-23
hello there! to answer vargasman just type:

sudo apt-get install build-essentials 

that should fix your problem ;-)

---

### Post by Verplrke on 2007-04-07
I have the same problem:

Specs:
[LIST]
[*]Kubuntu 6.10 on a Toshiba Satellite A60
    [*]Pentium 4, 3Ghz
    [*]512 MB Ram
    [*]Ati radeon Mobility 7000 IGP
[*]Logitech MediaPlay Cordless Mouse
[/LIST]

```
root@Maarten-SatA60:/home/maarten/Desktop/lmpcm_usb-0.5.5# make
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/maarten/Desktop/lmpcm_usb-0.5.5 modules
make: *** /lib/modules/2.6.17-11-386/build: No such file or directory.  Gestopt.
make: *** [default] Fout 2
root@Maarten-SatA60:/home/maarten/Desktop/lmpcm_usb-0.5.5#   
```

This wouldn't work:
```
sudo apt-get install build-essentials
```

So I looked a bit into the packet manager and then found and ran this
```
sudo apt-get install build-essential
```

The installation of build-essential was successful, but the make command still gave me the same "No such file or directory."-error

---

### Post by ZeroXtreme on 2007-04-30
Hi, would someone be kind enough to post the lmpcm_usb tarball please? The source for downloading is no longer working.

Thanks.

---

