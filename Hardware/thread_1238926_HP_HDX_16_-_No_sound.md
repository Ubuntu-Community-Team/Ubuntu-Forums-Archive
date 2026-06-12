---
title: "HP HDX 16 - No sound"
date: 2009-08-12
forum: Hardware
---

### Post by alxxlc on 2009-08-12
I have been searching for hours now on how to fix Ubuntu's sound and I just cannot do it. I just got an HP HDX 16-1160US and I have installed Wubi on it. Everything works perfectly on it (except maybe the fingerprint scanner but I haven't tried it out and i don't even care) but the sound.
The sound works great in Vista but the only sound I am getting in Ubuntu is a crackling sound when I turn off my computer.

I am tired from trying to figure this out so I am going to just tell you what I have tried already and have failed:
- Yes, my volume is up all the way and it is not muted.
- I have tried[COLOR=Blue] _[this]("https://answers.launchpad.net/ubuntu/+question/74675")_[/COLOR] "solution" and all it did was crash my computer when I restarted it.
- _[COLOR=Blue][This]("http://ubuntuforums.org/showpost.php?p=6513689&postcount=9")[/COLOR]_ = failed.
- and there were a few other things that I have tried but I can't find where they were.

I cannot find specs for my computer that include the sound card but it is an HP HDX 16-1160US and[COLOR=Blue] _[here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834147923")_[/COLOR] is the Newegg page for it.
Please help me with this as much as you can. I am not very good with Ubuntu yet so I can't do very many advanced things on it so if you can, make it as simple as you can.

---

### Post by hovrashko on 2009-08-22
hello!
 yeah my sound disappeared 3 times since i have Ubuntu 9.04 (i386), 1st time after I have installed Ubuntu on HDD(dual boot), so followed advise about editing my alsa-mixer.conf helped, but I couldn't use my internal microphone( doesn't work), after I've found the way to play all on-line videos( i had to uninstall Mozilla and flash, and install them back) i lost my sound again, and after i did "The Hard Way" of [http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525) I got my sound again back, but same problem internal microphone doesn't response (only in linux). 
 so try to play with your system files how does it say in that link, who knows you might get lucky.
 "sodo nautilus" - will help you to get full access to system folder.
=)
 if anyone knows how i can get to work my internal microphone, I'd be happy to read that

HP HDX16

---

### Post by kamg on 2009-08-24
i have read this in another forum and it did work on my hdx 16

"Some things I also did was add


options snd-hda-intel model=hp-m4

to /etc/modprobe.d/alsa-base.conf

and then restart ALSA with
$ sudo alsa force-reload
$ sudo /etc/init.d/alsa-utils restart"
or you can also restar your entire system

---

### Post by peppersteak on 2009-08-24
i added **options snd-hda-intel model=hp-m4** to [B]/etc/modprobe.d/alsa-base.conf

[/B]This worked for me on my HP HDX 1380ED.

---

### Post by alxxlc on 2009-08-24
Thank you so much. "options snd-hda-intel model=hp-m4" worked perfectly. I wish it was that simple the first time I was trying to fix it.

I still haven't restarted my computer since I got the sound working so I don't know if it is going to crash like it did before. I doubt it will though.

---

### Post by spazznie on 2009-08-29
I tried adding "options snd-hda-intel model=hp-m4" 
After I forced reload, this is what I got: 

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/annie/.gvfs
      Output information may be incomplete.
Terminating processes: 12355 12363lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/annie/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/annie/.gvfs
      Output information may be incomplete.
.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.

I got about 20 repeats of those last 2 WARNINGs, but I cut them out to spare you guys. 
My sound still doesn't work =(

---

