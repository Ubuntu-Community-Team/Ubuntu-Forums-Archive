---
title: "need help with sound on hp dv6000"
date: 2009-09-02
forum: Hardware
---

### Post by kcmccorm on 2009-09-02
I was having trouble getting my mic to work, so I saw this from another thread and tried it:

wget [ftp://ftp.alsa-project.org/pub/drive....16rc1.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2")
tar xvpjf alsa-driver-1.0.16rc1.tar.bz2
cd alsa-driver-1.0.16rc1
./configure --with-cards=hda-intel
make
sudo make install

but when I typed "sudo make install,"  this is the error message I got back:

make[1]: Entering directory `/home/katie/alsa-driver-1.0.16rc1/acore'
mkdir -p /lib/modules/2.6.28-15-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-timer.ko snd.ko /lib/modules/2.6.28-15-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/katie/alsa-driver-1.0.16rc1/acore'
make: *** [install-modules] Error 1



Now not only is my mic not working, my speakers aren't either! What is going on???

---

