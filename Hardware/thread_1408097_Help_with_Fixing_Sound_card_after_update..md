---
title: "Help with Fixing Sound card after update."
date: 2010-02-15
forum: Hardware
---

### Post by Lord-Koga on 2010-02-15
Ok so I'm not quite sure if this is the best place for my thread but since I'm having laptop problems I though i might start here. I recently updated my computer Using 9.10 and I updated on the 14th. Before the update my sound was working great. No problems, but afterwards  my sound is completly gone and under hardware when I click the sound option on the speaker icon I get nothing listed under hardware. I am using the HP DV2810 US notebook PC. With  this being listed as the audio device.

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
    Subsystem: Hewlett-Packard Company Device 30d6
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at fc480000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel




I will also list the updates from my synaptic history. Please help me fix my sound until its Fixed I'm having to use Win7 :(. And i only wanted that for the few games that one run well in wine.





Commit Log for Sun Feb 14 15:48:09 2010


Upgraded the following packages:
adobe-flashplugin (10.0.42.34-2karmic1) to 10.0.45.2-1karmic1
cups (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
cups-bsd (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
cups-client (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
cups-common (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
cups-ppdc (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
cupsddk (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
devicekit-power (011-1ubuntu1) to 011-1ubuntu2
foomatic-filters (4.0.3-0ubuntu2) to 4.0.3-0ubuntu2.1
fuse-utils (2.7.4-1.1ubuntu4.1) to 2.7.4-1.1ubuntu4.3
gnome-power-manager (2.28.1-0ubuntu1) to 2.28.1-0ubuntu1.3
gnome-screensaver (2.28.0-0ubuntu3.3) to 2.28.0-0ubuntu3.4
google-chrome-unstable (4.0.302.2-r36665) to 5.0.322.2-r38810
gtk2-engines-pixbuf (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libcups2 (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
libcupscgi1 (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
libcupsdriver1 (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
libcupsimage2 (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
libcupsmime1 (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
libcupsppdc1 (1.4.1-5ubuntu2.1) to 1.4.1-5ubuntu2.2
libdevkit-power-gobject1 (011-1ubuntu1) to 011-1ubuntu2
libfuse2 (2.7.4-1.1ubuntu4.1) to 2.7.4-1.1ubuntu4.3
libgail-common (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libgail18 (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libgtk2.0-0 (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libgtk2.0-bin (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libgtk2.0-common (2.18.3-1ubuntu2.1) to 2.18.3-1ubuntu2.2
libmysqlclient16 (5.1.37-1ubuntu5) to 5.1.37-1ubuntu5.1
libsmbclient (2:3.4.0-3ubuntu5.3) to 2:3.4.0-3ubuntu5.4
libwbclient0 (2:3.4.0-3ubuntu5.3) to 2:3.4.0-3ubuntu5.4
linux-generic (2.6.31.17.30) to 2.6.31.19.32
linux-headers-generic (2.6.31.17.30) to 2.6.31.19.32
linux-image-generic (2.6.31.17.30) to 2.6.31.19.32
linux-libc-dev (2.6.31-17.54) to 2.6.31-19.56
mysql-common (5.1.37-1ubuntu5) to 5.1.37-1ubuntu5.1
samba-common (2:3.4.0-3ubuntu5.3) to 2:3.4.0-3ubuntu5.4
samba-common-bin (2:3.4.0-3ubuntu5.3) to 2:3.4.0-3ubuntu5.4
smbclient (2:3.4.0-3ubuntu5.3) to 2:3.4.0-3ubuntu5.4
winbind (2:3.4.0-3ubuntu5.3) to 2:3.4.0-3ubuntu5.4

Installed the following packages:
linux-headers-2.6.31-19 (2.6.31-19.56)
linux-headers-2.6.31-19-generic (2.6.31-19.56)
linux-image-2.6.31-19-generic (2.6.31-19.56)

---

### Post by amsterdamharu on 2010-02-16
Does sound work when you boot with the previous kernel?

If so I suggest just using that one until a new kernel update comes along that fixes it.

---

### Post by Lord-Koga on 2010-02-16
No I tried. No sound what so ever. I think it did something ot my sound card. As it's no longer listed. When I do aplay -l in terminal i get the following: aplay: device_list:223: no soundcards found...

---

### Post by amsterdamharu on 2010-02-16
I have exactly the same value for my audio device on my desktop as you have on your notebook (nVidia Corporation MCP67 High Definition Audio (rev a1)).

I guess you need the same mods loaded as I do but I am running Hardy here.

Is the module loaded? Can you try the following commands and see what output you have?

```
user@desktop:~$ lsmod | grep snd_hda_intel
snd_hda_intel         346264  6 
snd_pcm                78724  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd                    56996  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
user@desktop:~$ modprobe --list *snd-hda-*
/lib/modules/2.6.24-27-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko

```You should not do anything to load these modules but if you have different output I am curious as to why it doesnt load.
Think you can manually load it using

```
modprobe snd-hda-intel
```

---

