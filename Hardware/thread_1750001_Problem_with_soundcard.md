---
title: "Problem with soundcard"
date: 2011-05-05
forum: Hardware
---

### Post by asai on 2011-05-05
Hi

I have posted a problem in Desktop section, but no respons.
Maybe someone reading this section could help?

Read the post [here]("http://ubuntuforums.org/showthread.php?t=1731782")

---

### Post by asai on 2011-05-05
Here is my alsa info:
[http://www.alsa-project.org/db/?f=e0a066389598cf0e81fb42f8c281bdbf49c95a1d](http://www.alsa-project.org/db/?f=e0a066389598cf0e81fb42f8c281bdbf49c95a1d)
Anyone get any useful information out of this?

If I open sound preferences, it has no devices

If I try to open alsamixer, this error comes:
```
cannot open mixer: No such file or directory
```

If I open gnome-alsamixer, it is totally blank.

```
terje@terje-desktop:~$ sudo lshw -C multimedia
  *-multimedia UNCLAIMED  
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
       resources: memory:fe024000-fe027fff
  *-multimedia UNCLAIMED
       description: Audio device
       product: RV710/730
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:fdcfc000-fdcfffff
```

Any suggestions?

---

### Post by lidex on 2011-05-06
You'll need to click the alsa-upgrade link in my sig, read the first post carefully, then run the script. If that doesn't work, post an updated alsa-info here.

---

### Post by asai on 2011-05-07
That was the solution! Everything works like a charm now!
Thank you very much lidex!! =D>

---

### Post by lidex on 2011-05-08
Great, and just remember:
> Ubuntu upgrades/updates might overwrite your Alsa installation once in a while (e.g. Major upgrades, kernel-upgrades or ALSA-package upgrades).
You just need to rerun the upgrade-script using the -i option in this case (if you still have the compiled sources on the disk).


---

### Post by asai on 2011-05-09
Thanks for the tip.:)

---

### Post by ankarajasekar on 2011-05-09
> **asai said:**
> Thanks for the tip.:)

i have  installed 11.04 but  my headphone  mike is not working  as it worked in 10.10  so let me  help in this regard

---

### Post by asai on 2011-05-09
Open Gnome alsamixer: ALT-F2 > gnome-alsamixer
Or if you prefer terminal, open a terminal an type: alsamixer

Here you can adjust the level of all channels on your soundcard, including lines in.

EDIT: You need to have alsa-base and alsa-utils installed...

---

