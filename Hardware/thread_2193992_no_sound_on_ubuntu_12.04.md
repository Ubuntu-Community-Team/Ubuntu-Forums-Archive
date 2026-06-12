---
title: "no sound on ubuntu 12.04"
date: 2013-12-15
forum: Hardware
---

### Post by Ferry_Boja_Sabara on 2013-12-15
before I'm sorry my bad english .. 


i have a pc and i install ubuntu, but no sound after instal ubuntu? 
please help me ..

---

### Post by Yellow Pasque on 2013-12-15
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Ferry_Boja_Sabara on 2013-12-15
[COLOR=#000000]before I'm sorry my bad english .. [/COLOR]


[COLOR=#000000]i have a pc and i install ubuntu, but no sound after instal ubuntu? [/COLOR]
[COLOR=#000000]please help me ..[/COLOR]

---

### Post by onerose on 2013-12-15
Run alsamixer through your terminal (type alsamixer, Enter)...
Check if anything is muted (it will have MM on the bottom and it needs to be 00, toggle it using M on your keyboard).
Make sure your output devices are set on high volume (use arrows). Esc to exit.

---

### Post by leeper69 on 2013-12-15
Hi ferry_boja_sabara can you tell me what soundcard you have? what flaver of ubuntu are you using xfce,gnome,kde,unity?

---

### Post by Ferry_Boja_Sabara on 2013-12-15
> **leeper69 said:**
> Hi ferry_boja_sabara can you tell me what soundcard you have? what flaver of ubuntu are you using xfce,gnome,kde,unity?
i dont know..
how to check it?

---

### Post by Ferry_Boja_Sabara on 2013-12-15
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

```
jalanbuntu@jalanbuntu-Aspire-E1-471G:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh--2013-12-16 07:04:22--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org (www.alsa-project.org)... 77.48.224.243
Connecting to www.alsa-project.org (www.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh [following]
--2013-12-16 07:04:43--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh
Resolving git.alsa-project.org (git.alsa-project.org)... failed: Name or service not known.
wget: unable to resolve host address `git.alsa-project.org'



```

---

### Post by leeper69 on 2013-12-16
hi ferry_boja_sabara can you tell me the desktop you are using?
ubuntu uses pulseaudio as its sound server and in the menu look for pulseaudio volume control your sound card will be listed there.
you can dowload the gnome alsa mixer with ubuntu software center to fine tune your sound card alsa is already loaded.

---

### Post by Ferry_Boja_Sabara on 2013-12-16
> **leeper69 said:**
> hi ferry_boja_sabara can you tell me the desktop you are using?
ubuntu uses pulseaudio as its sound server and in the menu look for pulseaudio volume control your sound card will be listed there.
you can dowload the gnome alsa mixer with ubuntu software center to fine tune your sound card alsa is already loaded.
i use alsamixer.. my desktop basic from ubuntu

this internal sound
[IMG]http://imageshack.com/a/img826/9379/k419.png[/IMG]

and this usb sound
[IMG]http://imageshack.com/a/img703/5248/vj8f.png[/IMG]

but still problem, no sound

---

### Post by howefield on 2013-12-16
Threads merged.

---

### Post by leeper69 on 2013-12-16
try gnome alsa mixer you may find channels muted or turned down it is worth a try.
it will look much differet than the alsa gui you are using.
to download it you can use ubuntu software center or type the following comands in terminal
sudo apt-get update       then hit enter ( this will update your registries )
sudo apt-get install gnome-alsamixer    then hit enter ( this will download and install gnome-alsamixer )
you are running unity desktop.
hope this helps

---

