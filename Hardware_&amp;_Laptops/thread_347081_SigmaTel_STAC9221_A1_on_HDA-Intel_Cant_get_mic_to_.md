---
title: "SigmaTel STAC9221 A1 on HDA-Intel Cant get mic to work"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by chronusdark on 2007-01-26
i have a dell xps m1210 with SigmaTel STAC9221 A1 audio card and i cannot get external mic port to work (i dont have the internal mic option)

Someone please help me i have looked everywhere and its driving me crazy

---

### Post by eggdeng on 2007-01-29
Sorry to share bad news but I've been following snd_hda_intel threads for a while and as far as I can see, nobody has managed to get microphones working - most are grateful just to have sound. If you make any progress on this, I'd appreciate a PM.

---

### Post by chronusdark on 2007-01-29
thanks same to you

---

### Post by eggdeng on 2007-01-30
Some of these guys seem to have got a working mic on a Dell Inspiron.
[http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200](http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200)
The fix is to add
```
options snd-hda-intel model=ref
```
to
/etc/modprobe.d/alsa-base
Reboot for changes to take effect.

---

### Post by morgengenuss on 2007-02-14
@eggdeng: ok, i've been reading through quite a few sigmatel-intel hda mic related threads and what you wrote seems to be the solution for quite many. my problem is that i simply don't have this file /etc/modprobe.d/alsa-base - i compiled alsa 1.0.14rc2, still not there. did i miss something?

---

### Post by eggdeng on 2007-02-14
Have you got a file called /etc/modprobe.d/options. I've seen a few threads where people added the required line to this file.

---

### Post by chronusdark on 2007-02-20
doesnt help me....i think the problem is the jack is both a line in and mic

On Windows when i plug a mic in, it asks if the device is a mic or line level device

is there a way to pick in linux?

---

### Post by dtruesdale on 2007-02-21
Appears to be an Alsa issue there are several bug reports on the had-intel Sigmatel 92XX series. The developer handling it has it in high priority but i have not found a status on it yet. It would be nice to standardize sound in linux so we can use apps with a standard. That way everything could co-exist.

---

### Post by eggdeng on 2007-02-25
Finally got that mic to work following this thread.

[http://ubuntuforums.org/showthread.php?p=2210477#post2210477](http://ubuntuforums.org/showthread.php?p=2210477#post2210477)

---

### Post by treesurf on 2007-02-25
> **eggdeng said:**
> Finally got that mic to work following this thread.

[http://ubuntuforums.org/showthread.php?p=2210477#post2210477](http://ubuntuforums.org/showthread.php?p=2210477#post2210477)

Thanks for the tip, but unfortunately that did not work for me.

---

### Post by dimeotane on 2007-03-08
same here... for now this means no VOIP... this is a big fault with linux on this otherwise great laptop.  Please PM me if you get this to work!

I tried adding the extra line to alsa-base and it did give me some extra options, and I can get a background hiss... but thats all: 
 
~$ gksudo gedit  /etc/modprobe.d/alsa-base

options snd-hda-intel model=ref

:confused: :confused: :confused: :confused: :confused: 

*i have a dell xps m1210 with SigmaTel STAC9221 A1 audio card and i cannot get external mic port to work (i dont have the internal mic option)*

---

### Post by dtruesdale on 2007-03-09
Ok I got it fixed and working, tested even with multi programs. The source of the rc3 released on the 6th on Alsa's site has us working with microphone. Install it through the directions on the Alsa site for the intel ICH7. when you complete that backup the .asoundrc from your home directory if all programs give you no sound hardware issues. By backing up, simply rename the .asoundrc to .asoundrc-backup. It's working I also made a custon .asoundrc file for duplexing sound for voip and gaming. I am happy.

---

### Post by dimeotane on 2007-03-10
Glad to hear someone got it working!
But can we retrace your steps in more detail  :confused:  
so the rest of us can get it working. :confused: 
I've gone as far as I can but still just background noise and no microphone recording. 

I assume you  mean this page:  [here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel")
when you say "Install it through the directions on the Alsa site for the intel ICH7"



Heres what I've done so far:

1) download the latest driver
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2
```

2)decompress it
```
tar xvjf alsa-driver-1.0.14rc3.tar.bz2
```

3)change to the directory and become superuser
```
cd alsa-driver-1.0.14rc3
```
```
su 
```

4) install the new driver
```
  ./configure --with-cards=hda-intel --with-sequencer=yes;make;make install

```

5) download and untar the library and utilities
```
cd ..
```
```
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14rc3.tar.bz2
```
```
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14rc2.tar.bz2
```
```
tar xvjf alsa-lib-1.0.14rc3.tar.bz2
```
```
tar xvjf alsa-utils-1.0.14rc2.tar.bz2
```

6) change to the lib directory and install
```
cd alsa-lib-1.0.14rc3
```
```
 ./configure;make;make install
```
```
cd ..
```

7) change to the utils directory and install
```
cd alsa-utils-1.0.14rc2
```
```
./configure;make;make install
```

8 ) insert the modules into the kernel
 ```

modprobe snd-hda-intel;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss
```

9) adjust your soundcards volume levels + unmute
```
alsamixer
```



under the section for :"Setting up modprobe and kmod support"
I have no  /etc/conf.modules or /etc/modules.conf   what did you do for that part?


You say to backup the .asoundrc file, but there's nothing there.  The guide says to edit it 
```
gedit .asoundrc
```
and to paste the following and save it:
```

  pcm.hda-intel {
           type hw
           card 0
        }

        ctl.hda-intel {
           type hw
           card 0
        }
 
```

---

### Post by dtruesdale on 2007-03-10
ok that was it the only other thing i did was delete ~/.asoundrc ran teamspeak then created my ~/.asoundrc file so i could use it with multi apps at once. This is on a Dell E1705 (9400 version Core 2 Duo).

---

### Post by treesurf on 2007-03-10
Thanks for the detailed directions dimeotane.  That's very useful for newbies like me.  Should I assume that this might also work for the SigmaTel STAC9250?

---

### Post by dtruesdale on 2007-03-11
According to Alsa for this release candidate it should fix it for hda-intel using sigmatel  stac-xxxx.

---

### Post by treesurf on 2007-03-12
I should start off by saying that I don't really understand the installing/configuring process in linux yet as I have just recently started using Ubuntu.  That being said I tried following dimeotanes directions for installing the alsa 1.0.14rc3 and ran into problems pretty quickly.  The first ./configure command seemed to go alright until  the end which gave the following errors.  

```
ALSA modules were successfully compiled.

if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/leon/alsa-driver-1.0.14rc3/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
rm: cannot remove `/usr/include/sound/ac97_codec.h': Permission denied
rm: cannot remove `/usr/include/sound/ad1816a.h': Permission denied
rm: cannot remove `/usr/include/sound/ad1848.h': Permission denied
rm: cannot remove `/usr/include/sound/ainstr_fm.h': Permission denied
rm: cannot remove `/usr/include/sound/ainstr_gf1.h': Permission denied
rm: cannot remove `/usr/include/sound/ainstr_iw.h': Permission denied
rm: cannot remove `/usr/include/sound/ainstr_simple.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4114.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4117.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4531_codec.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4xxx-adda.h': Permission denied
rm: cannot remove `/usr/include/sound/asequencer.h': Permission denied
rm: cannot remove `/usr/include/sound/asound.h': Permission denied
rm: cannot remove `/usr/include/sound/asound_fm.h': Permission denied
rm: cannot remove `/usr/include/sound/asoundef.h': Permission denied
rm: cannot remove `/usr/include/sound/control.h': Permission denied
rm: cannot remove `/usr/include/sound/core.h': Permission denied
rm: cannot remove `/usr/include/sound/cs4231.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx_dsp_scb_types.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx_dsp_spos.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx_dsp_task_types.h': Permission denied
rm: cannot remove `/usr/include/sound/cs8403.h': Permission denied
rm: cannot remove `/usr/include/sound/cs8427.h': Permission denied
rm: cannot remove `/usr/include/sound/driver.h': Permission denied
rm: cannot remove `/usr/include/sound/emu10k1.h': Permission denied
rm: cannot remove `/usr/include/sound/emu10k1_synth.h': Permission denied
rm: cannot remove `/usr/include/sound/emu8000.h': Permission denied
rm: cannot remove `/usr/include/sound/emu8000_reg.h': Permission denied
rm: cannot remove `/usr/include/sound/emux_legacy.h': Permission denied
rm: cannot remove `/usr/include/sound/emux_synth.h': Permission denied
rm: cannot remove `/usr/include/sound/es1688.h': Permission denied
rm: cannot remove `/usr/include/sound/gus.h': Permission denied
rm: cannot remove `/usr/include/sound/hdsp.h': Permission denied
rm: cannot remove `/usr/include/sound/hdspm.h': Permission denied
rm: cannot remove `/usr/include/sound/hwdep.h': Permission denied
rm: cannot remove `/usr/include/sound/i2c.h': Permission denied
rm: cannot remove `/usr/include/sound/info.h': Permission denied
rm: cannot remove `/usr/include/sound/initval.h': Permission denied
rm: cannot remove `/usr/include/sound/memalloc.h': Permission denied
rm: cannot remove `/usr/include/sound/minors.h': Permission denied
rm: cannot remove `/usr/include/sound/mixer_oss.h': Permission denied
rm: cannot remove `/usr/include/sound/mpu401.h': Permission denied
rm: cannot remove `/usr/include/sound/opl3.h': Permission denied
rm: cannot remove `/usr/include/sound/opl4.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm-indirect.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm_oss.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm_params.h': Permission denied
rm: cannot remove `/usr/include/sound/pt2258.h': Permission denied
rm: cannot remove `/usr/include/sound/rawmidi.h': Permission denied
rm: cannot remove `/usr/include/sound/sb.h': Permission denied
rm: cannot remove `/usr/include/sound/sb16_csp.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_device.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_instr.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_kernel.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_midi_emul.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_midi_event.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_oss.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_oss_legacy.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_virmidi.h': Permission denied
rm: cannot remove `/usr/include/sound/sfnt_info.h': Permission denied
rm: cannot remove `/usr/include/sound/snd_wavefront.h': Permission denied
rm: cannot remove `/usr/include/sound/soc-dapm.h': Permission denied
rm: cannot remove `/usr/include/sound/soc.h': Permission denied
rm: cannot remove `/usr/include/sound/soundfont.h': Permission denied
rm: cannot remove `/usr/include/sound/sscape_ioctl.h': Permission denied
rm: cannot remove `/usr/include/sound/tea575x-tuner.h': Permission denied
rm: cannot remove `/usr/include/sound/tea6330t.h': Permission denied
rm: cannot remove `/usr/include/sound/timer.h': Permission denied
rm: cannot remove `/usr/include/sound/tlv.h': Permission denied
rm: cannot remove `/usr/include/sound/trident.h': Permission denied
rm: cannot remove `/usr/include/sound/uda1341.h': Permission denied
rm: cannot remove `/usr/include/sound/util_mem.h': Permission denied
rm: cannot remove `/usr/include/sound/version.h': Permission denied
rm: cannot remove `/usr/include/sound/vx_core.h': Permission denied
rm: cannot remove `/usr/include/sound/wavefront.h': Permission denied
rm: cannot remove `/usr/include/sound/wavefront_fx.h': Permission denied
rm: cannot remove `/usr/include/sound/ymfpci.h': Permission denied
install: cannot change owner and/or group of `/usr/include/sound': Operation not permitted
install: cannot remove `/usr/include/sound/ac97_codec.h': Permission denied
install: cannot remove `/usr/include/sound/ad1816a.h': Permission denied
install: cannot remove `/usr/include/sound/ad1848.h': Permission denied
install: cannot remove `/usr/include/sound/ainstr_fm.h': Permission denied
install: cannot remove `/usr/include/sound/ainstr_gf1.h': Permission denied
install: cannot remove `/usr/include/sound/ainstr_iw.h': Permission denied
install: cannot remove `/usr/include/sound/ainstr_simple.h': Permission denied
install: cannot remove `/usr/include/sound/ak4114.h': Permission denied
install: cannot remove `/usr/include/sound/ak4117.h': Permission denied
install: cannot remove `/usr/include/sound/ak4531_codec.h': Permission denied
install: cannot remove `/usr/include/sound/ak4xxx-adda.h': Permission denied
install: cannot remove `/usr/include/sound/asequencer.h': Permission denied
install: cannot remove `/usr/include/sound/asound.h': Permission denied
install: cannot remove `/usr/include/sound/asound_fm.h': Permission denied
install: cannot remove `/usr/include/sound/asoundef.h': Permission denied
install: cannot remove `/usr/include/sound/control.h': Permission denied
install: cannot remove `/usr/include/sound/core.h': Permission denied
install: cannot remove `/usr/include/sound/cs4231.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx_dsp_scb_types.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx_dsp_spos.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx_dsp_task_types.h': Permission denied
install: cannot remove `/usr/include/sound/cs8403.h': Permission denied
install: cannot remove `/usr/include/sound/cs8427.h': Permission denied
install: cannot remove `/usr/include/sound/driver.h': Permission denied
install: cannot remove `/usr/include/sound/emu10k1.h': Permission denied
install: cannot remove `/usr/include/sound/emu10k1_synth.h': Permission denied
install: cannot remove `/usr/include/sound/emu8000.h': Permission denied
install: cannot remove `/usr/include/sound/emu8000_reg.h': Permission denied
install: cannot remove `/usr/include/sound/emux_legacy.h': Permission denied
install: cannot remove `/usr/include/sound/emux_synth.h': Permission denied
install: cannot remove `/usr/include/sound/es1688.h': Permission denied
install: cannot remove `/usr/include/sound/gus.h': Permission denied
install: cannot remove `/usr/include/sound/hdsp.h': Permission denied
install: cannot remove `/usr/include/sound/hdspm.h': Permission denied
install: cannot remove `/usr/include/sound/hwdep.h': Permission denied
install: cannot remove `/usr/include/sound/i2c.h': Permission denied
install: cannot remove `/usr/include/sound/info.h': Permission denied
install: cannot remove `/usr/include/sound/initval.h': Permission denied
install: cannot remove `/usr/include/sound/memalloc.h': Permission denied
install: cannot remove `/usr/include/sound/minors.h': Permission denied
install: cannot remove `/usr/include/sound/mixer_oss.h': Permission denied
install: cannot remove `/usr/include/sound/mpu401.h': Permission denied
install: cannot remove `/usr/include/sound/opl3.h': Permission denied
install: cannot remove `/usr/include/sound/opl4.h': Permission denied
install: cannot remove `/usr/include/sound/pcm-indirect.h': Permission denied
install: cannot remove `/usr/include/sound/pcm.h': Permission denied
install: cannot remove `/usr/include/sound/pcm_oss.h': Permission denied
install: cannot remove `/usr/include/sound/pcm_params.h': Permission denied
install: cannot remove `/usr/include/sound/pt2258.h': Permission denied
install: cannot remove `/usr/include/sound/rawmidi.h': Permission denied
install: cannot remove `/usr/include/sound/sb.h': Permission denied
install: cannot remove `/usr/include/sound/sb16_csp.h': Permission denied
install: cannot remove `/usr/include/sound/seq_device.h': Permission denied
install: cannot remove `/usr/include/sound/seq_instr.h': Permission denied
install: cannot remove `/usr/include/sound/seq_kernel.h': Permission denied
install: cannot remove `/usr/include/sound/seq_midi_emul.h': Permission denied
install: cannot remove `/usr/include/sound/seq_midi_event.h': Permission denied
install: cannot remove `/usr/include/sound/seq_oss.h': Permission denied
install: cannot remove `/usr/include/sound/seq_oss_legacy.h': Permission denied
install: cannot remove `/usr/include/sound/seq_virmidi.h': Permission denied
install: cannot remove `/usr/include/sound/sfnt_info.h': Permission denied
install: cannot remove `/usr/include/sound/snd_wavefront.h': Permission denied
install: cannot remove `/usr/include/sound/soc-dapm.h': Permission denied
install: cannot remove `/usr/include/sound/soc.h': Permission denied
install: cannot remove `/usr/include/sound/soundfont.h': Permission denied
install: cannot remove `/usr/include/sound/sscape_ioctl.h': Permission denied
install: cannot remove `/usr/include/sound/tea575x-tuner.h': Permission denied
install: cannot remove `/usr/include/sound/tea6330t.h': Permission denied
install: cannot remove `/usr/include/sound/timer.h': Permission denied
install: cannot remove `/usr/include/sound/tlv.h': Permission denied
install: cannot remove `/usr/include/sound/trident.h': Permission denied
install: cannot remove `/usr/include/sound/uda1341.h': Permission denied
install: cannot remove `/usr/include/sound/util_mem.h': Permission denied
install: cannot remove `/usr/include/sound/version.h': Permission denied
install: cannot remove `/usr/include/sound/vx_core.h': Permission denied
install: cannot remove `/usr/include/sound/wavefront.h': Permission denied
install: cannot remove `/usr/include/sound/wavefront_fx.h': Permission denied
install: cannot remove `/usr/include/sound/ymfpci.h': Permission denied
make: *** [install-headers] Error 1

```


So I continued anyways.    The next " ./configure;make;make install" had these errors tacked on the end of the output 

```
Making all in control
make[2]: Entering directory `/home/leon/alsa-lib-1.0.14rc3/src/control'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT cards.lo -MD -MP -MF ".deps/cards.Tpo" -c -o cards.lo cards.c; \
        then mv -f ".deps/cards.Tpo" ".deps/cards.Plo"; else rm -f ".deps/cards.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT cards.lo -MD -MP -MF .deps/cards.Tpo -c cards.c  -fPIC -DPIC -o .libs/cards.o
cards.c:191: fatal error: opening dependency file .deps/cards.Tpo: Permission denied
compilation terminated.
make[2]: *** [cards.lo] Error 1
make[2]: Leaving directory `/home/leon/alsa-lib-1.0.14rc3/src/control'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/leon/alsa-lib-1.0.14rc3/src'
make: *** [all-recursive] Error 1
Making install in doc
make[1]: Entering directory `/home/leon/alsa-lib-1.0.14rc3/doc'
Making install in pictures
make[2]: Entering directory `/home/leon/alsa-lib-1.0.14rc3/doc/pictures'
make[3]: Entering directory `/home/leon/alsa-lib-1.0.14rc3/doc/pictures'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/leon/alsa-lib-1.0.14rc3/doc/pictures'
make[2]: Leaving directory `/home/leon/alsa-lib-1.0.14rc3/doc/pictures'
make[2]: Entering directory `/home/leon/alsa-lib-1.0.14rc3/doc'
make[3]: Entering directory `/home/leon/alsa-lib-1.0.14rc3/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/leon/alsa-lib-1.0.14rc3/doc'
make[2]: Leaving directory `/home/leon/alsa-lib-1.0.14rc3/doc'
make[1]: Leaving directory `/home/leon/alsa-lib-1.0.14rc3/doc'
Making install in include
make[1]: Entering directory `/home/leon/alsa-lib-1.0.14rc3/include'
Making install in sound
make[2]: Entering directory `/home/leon/alsa-lib-1.0.14rc3/include/sound'
make[3]: Entering directory `/home/leon/alsa-lib-1.0.14rc3/include/sound'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/include/alsa/sound" || mkdir -p -- "/usr/include/alsa/sound"
 /usr/bin/install -c -m 644 'ainstr_fm.h' '/usr/include/alsa/sound/ainstr_fm.h'
/usr/bin/install: cannot remove `/usr/include/alsa/sound/ainstr_fm.h': Permission denied
 /usr/bin/install -c -m 644 'ainstr_gf1.h' '/usr/include/alsa/sound/ainstr_gf1.h'
/usr/bin/install: cannot remove `/usr/include/alsa/sound/ainstr_gf1.h': Permission denied
 /usr/bin/install -c -m 644 'ainstr_simple.h' '/usr/include/alsa/sound/ainstr_simple.h'
/usr/bin/install: cannot remove `/usr/include/alsa/sound/ainstr_simple.h': Permission denied
 /usr/bin/install -c -m 644 'ainstr_iw.h' '/usr/include/alsa/sound/ainstr_iw.h'
/usr/bin/install: cannot remove `/usr/include/alsa/sound/ainstr_iw.h': Permission denied
 /usr/bin/install -c -m 644 'asound_fm.h' '/usr/include/alsa/sound/asound_fm.h'
/usr/bin/install: cannot remove `/usr/include/alsa/sound/asound_fm.h': Permission denied
 /usr/bin/install -c -m 644 'hdsp.h' '/usr/include/alsa/sound/hdsp.h'
/usr/bin/install: cannot remove `/usr/include/alsa/sound/hdsp.h': Permission denied
 /usr/bin/install -c -m 644 'sb16_csp.h' '/usr/include/alsa/sound/sb16_csp.h'
/usr/bin/install: cannot remove `/usr/include/alsa/sound/sb16_csp.h': Permission denied
 /usr/bin/install -c -m 644 'sscape_ioctl.h' '/usr/include/alsa/sound/sscape_ioctl.h'
/usr/bin/install: cannot remove `/usr/include/alsa/sound/sscape_ioctl.h': Permission denied
 /usr/bin/install -c -m 644 'emu10k1.h' '/usr/include/alsa/sound/emu10k1.h'
/usr/bin/install: cannot remove `/usr/include/alsa/sound/emu10k1.h': Permission denied
 /usr/bin/install -c -m 644 'type_compat.h' '/usr/include/alsa/sound/type_compat.h'
/usr/bin/install: cannot create regular file `/usr/include/alsa/sound/type_compat.h': Permission denied
make[3]: *** [install-alsasoundincludeHEADERS] Error 1
make[3]: Leaving directory `/home/leon/alsa-lib-1.0.14rc3/include/sound'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/leon/alsa-lib-1.0.14rc3/include/sound'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/leon/alsa-lib-1.0.14rc3/include'
make: *** [install-recursive] Error 1

```

Then it tells me that there is no directory for alsa 1.0.14rc2.  Finally modprobe gives me these errors:
```
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.17-11-generic/kernel/sound/acore/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.17-11-generic/kernel/sound/acore/seq/snd-seq-device.ko): Operation not permitted
FATAL: Error inserting snd_seq (/lib/modules/2.6.17-11-generic/kernel/sound/acore/seq/snd-seq.ko): Operation not permitted
WARNING: Error running install command for snd_seq
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.17-11-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko): Operation not permitted
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.17-11-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko): Operation not permitted
```

The good news is that sound output still seems to work so I haven't killed alsa completely!  Any advice on how I went wrong and what I should do to fix it would be greatly apprecieated.

Thanks!

---

### Post by dejitarob on 2007-03-13
> **eggdeng said:**
> Sorry to share bad news but I've been following snd_hda_intel threads for a while and as far as I can see, nobody has managed to get microphones working - most are grateful just to have sound. If you make any progress on this, I'd appreciate a PM.
My microphone works fine using the hda-intel module on an Asus Z70v laptop with an Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller. You may just need to change a few settings that are not intuitive. See [http://ubuntuforums.org/showthread.php?p=1720522&highlight=Z70V#post1720522](http://ubuntuforums.org/showthread.php?p=1720522&highlight=Z70V#post1720522)

> **treesurf said:**
> I should start off by saying that I don't really understand the installing/configuring process in linux yet as I have just recently started using Ubuntu.  That being said I tried following dimeotanes directions for installing the alsa 1.0.14rc3 and ran into problems pretty quickly.  The first ./configure command seemed to go alright until  the end which gave the following errors.  

[CODE]ALSA modules were successfully compiled.

if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/leon/alsa-driver-1.0.14rc3/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
rm: cannot remove `/usr/include/sound/ac97_codec.h': Permission denied
rm: cannot remove `/usr/include/sound/ad1816a.h': Permission denied
rm: cannot remove `/usr/include/sound/ad1848.h': Permission denied
[...]

Make sure you use 'sudo make install.' The sudo commands gives the install script administrative privileges. Without using this, you basically only have access to your /home/username directory for security reasons. I would recommend before trying to upgrade ALSA you try fiddling with a few settings to get your mic working. See the thread I posted above.

---

### Post by treesurf on 2007-03-14
dejitarob,

Thanks for the advice.  Unfortunately, I have tried just about everything posted on these forums about the Sigmatel STAC9xxx drivers without much luck (including the tips you included on that link).

I did use sudo for all the configure/install/make install/etc. commands while tryiing to install 14rc4.  I'm really not sure where I went wrong.  I'm going to give it another shot from the beginning this evening and see if I can get it working.

---

### Post by treesurf on 2007-03-15
Well, I think I was successful in installing 14rc3 this evening.  Unfortunately my mic still does not seem to work.  Audacity and sound recorder both crash whenever I try to record sound.

How do I check to make sure that I actually installed rc3?

---

### Post by morgengenuss on 2007-03-27
@ treesurf: if you run alsamixer you'll at least see the version number of the alsa-utils you installed.

it took me a long time to realize that alsamixers switch to show my capture channel was -V all (so the command would be "alsamixer -V all"). then i could unmute the capture channel and set it to record.

one more thing that gave me a headache was that i used "alsactl store" instead of "alsactl store 0" (where 0 is the only soundcard, in case you have more this just indicates that it's the n'th soundcard).

just mentioning because this might be of use for someone.

oh, and one more thing: although i can record sound, use skype or gizmo and whatever: the quality of the recordings is really poor. there is this annoying buzzing or droning in the background (getting more when i turn up capture mux) - any solution or workaround for that?

---

### Post by morgengenuss on 2007-03-28
update on my situation: i was wrong about the "0" with sudo alsactl store; that didn't make a difference, but for some reason my /etc/init.d/alsa-utils (the script that stores and restores mixer volumes at startup) was linked to /var/lib/alsa/asound.state instead of /etc/asound.state, so i resolved this by creating a symbolic link (of course i could have modified alsa-utils as well, but in case i want to upgrade one day...).

the issue with the noisy recording still isn't resolved...

---

### Post by luzdegas on 2007-10-14
I was able to solve this issue following this post

[http://mailman.alsa-project.org/pipermail/alsa-devel/2007-June/001414.html]("http://mailman.alsa-project.org/pipermail/alsa-devel/2007-June/001414.html")

---

