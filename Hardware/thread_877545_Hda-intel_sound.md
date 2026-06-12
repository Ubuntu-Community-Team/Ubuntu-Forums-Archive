---
title: "Hda-intel sound"
date: 2008-08-01
forum: Hardware
---

### Post by RxRated on 2008-08-01
I have a hp dv 8000 laptop that I just upgraded to hardy. My sound worked perfect with feisty and gutsy, but now the card is not detected. I have reinstalled alsa and searched these forums for hours. The card is an hda-intel ICH 7family. When I try to insert the module into the kernel by typing sudo modprobe snd-hda-intel I get errors saying:

WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.24-19-generic/updates/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-19-generic/updates/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

When I click on the volume icon on the taskbar I get the following message:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.


I am completely lost at this point. Can anyone help?

---

### Post by jocko on 2008-08-01
hda-intel in hardy has been broken since late in the hardy development, and apparently it's not getting fixed... [This is getting silly]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192382")...

To fix it, try this:```
sudo apt-get install module-assistant
sudo module-assistant auto-install alsa
```It will automatically recompile alsa from source, which will fix the problem with the hda-intel module.
You'll have to repeat it when the kernel is updated, but it gets sound working properly...

---

### Post by treggmo on 2008-08-01
Hey RxRated,
I know nothing about your errors or reinstalling alsa but,
What does it say at System>Preferences>Sound? Mine specifies the device as HDA Intel(Alsa mixer).

Have you gone through this link?
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
It may solve your problem.

---

### Post by RxRated on 2008-08-01
Thanks for the replies!  I tried your solution jocko but no luck.  It doesn't seem to recognize my card.

---

### Post by geminiviper on 2008-08-01
I'm having trouble getting my sound to work.  I have NO sound whatsoever.  I have already installed all the plugins and all that to play MP3s and movies.  No luck so the obvious is out of the way.  So I have been following a tutorial I found here

[http://ubuntuforums.org/showthread.php?t=332472&highlight=snd_hda_intel](http://ubuntuforums.org/showthread.php?t=332472&highlight=snd_hda_intel)

But I am having this problem.  In this stage

Step 2)
wget [ftp://ftp.alsa-project.org/pub/drive....14rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/drive....14rc1.tar.bz2)
tar jxvf alsa-driver-1.0.14rc1.tar.bz2
cd alsa-driver-1.0.14rc1/
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel
sudo make
sudo make install

When I run the sudo make line it goes through everything and then ends with

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic`
scripts/Makefile.build:46: ***CFLAGS was changed in "/home/one/repository/alsa-driver1.0.14rc1/acore/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[2]: *** [/home/one/Repository/alsa-driver-1.0.14rc1/acore] Error 2
make[1]: *** [_module_/home/one/Repository/alsa-driver-1.0.14rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic`
make: *** [compile] Error 2

then it kicks me back to the command line.
If I try to continue to sudo make install I get this.

if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/one/Repository/alsa-driver-1.0.14rc1/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                 done \
         fi
find /lib/bodules/2.6.24-16-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
make[1]: Entering directory `/home/one/Repository/alsa-driver-1.0.14rc1/acore`
mkdir -p /lib/modules/2.6.24-16-generic/kernel/sound/acore
cp snd-page-alloc.ko snd-pcm.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.24-16-generic/kernel/sound/acore
cp cannot stat `snd-page-alloc.ko`: No such file or directory
cp cannot stat `snd-pcm.ko`: No such file or directory
cp cannot stat `snd-rtctimer.ko`: No such file or directory
cp cannot stat `snd-timer.ko`: No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/one/Repository/alsa-driver-1.0.14rc1/acore`
make: *** [install-modules] Error1

Then goes back to command line.

So how can I get my sound working?  I have a small limitation.  I cannot connect my laptop to the internet.  So I'm having to find each individual package and install them manually.  It's a pain but it's what I have.  

I also when through this...

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


Tried following this but had a hard time following it, and had a hard time actually coming up with the exact driver or where to get it...

[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

So I downloaded alsa-source_1.0.16-2ubuntu_all.deb and ran it and I still have no sound.  Any help would be greatly appreciated.

---

