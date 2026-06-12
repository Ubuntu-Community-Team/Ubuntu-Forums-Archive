---
title: "Sound on Toshiba C665"
date: 2013-05-10
forum: Hardware
---

### Post by peragrate2 on 2013-05-10
Hi everyone. I've used Ubuntu Lucid for the last three years without an issue, but unfortunately my laptop was stolen. I replaced it with a Toshiba C665, and no matter what I do the sound cuts out every time I try to watch any videos at all.

I've followed just about every procedure I can find, and I still can't fix it. (Please don't bring up alsamixer!)

aplay -l:
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
The internal sound is HDA-Intel-generic

....and...

cat /proc/asound/card0/codec* | grep Codec
gives Conexant cx20585

So far I have reinstalled Ubuntu 10.04, 12.04, and 13.

I have absolutely no idea on Earth WTF is wrong with my sound. Everything was fine for the first three weeks after getting this laptop and installing Ubuntu 10.04 (my favorite), but now I SERIOUSLY do not know what to do.

When I run "sudo alsa force-reload", I get this:

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/marc/.gvfs
      Output information may be incomplete.
Terminating processes: 1633lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/marc/.gvfs
      Output information may be incomplete.
 2048lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/marc/.gvfs
      Output information may be incomplete.
 2087lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/marc/.gvfs
      Output information may be incomplete.
 2139lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/marc/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 2161lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/marc/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 2190(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/marc/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 2190(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

I also get a message from totem that says "pa_stream_writable_size() failed: Connection terminated".

When I type pulseaudio at the cli, I get:
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

I've installed VLC and everthing that comes with it, but no dice.

PLEASE! Someone help me with this before my head explodes!
:-)

Thanks in advance

---

### Post by gordintoronto on 2013-05-10
Ubuntu 10.04 desktop has expired, it is no longer supported.

If everything was fine for three weeks, and now it's not, there is probably a hardware problem.

How about lspci optput?

---

### Post by peragrate2 on 2013-05-11
I know  is 10.04 is obsolete, yet I like it's simplicity. Unity is very innovative, but there are many things I don't like about it. I also tend to use the same software as it is....and don't necessarily need all the new bells and whistles... You're probably about it being hardware. I think there's something wrong with ALSA talking to my hardware. Here's lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by gordintoronto on 2013-05-11
In my experience, sound problems are often solved in new versions of Linux, if they are software problems.

10.04 no longer gets security updates, and that could be a catastrophe.  If you can't stand Unity, try Xubuntu 12.04 or Linux Mint 13. Or try them both from LiveUSBs created using Unetbootin. and install the one you can live with.

But first, TWO full backups of your essential data. Don't forget your bookmarks and email. You're probably using Evolution, File/Back up Evolution Data."

---

### Post by peragrate2 on 2013-05-12
Thanks, Just movedd to mint 14. Sound worked for about 30 minutes then crashed again.:(

---

### Post by peragrate2 on 2013-05-13
update. I bought some headphones and the sound works fine through them, but not the external speakers. Is anyone out there?

---

