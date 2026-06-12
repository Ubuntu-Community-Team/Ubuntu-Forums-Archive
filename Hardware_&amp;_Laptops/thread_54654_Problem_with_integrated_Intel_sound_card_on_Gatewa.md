---
title: "Problem with integrated Intel sound card on Gateway 3525 (UK model) laptop"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by drednik on 2005-08-05
Ok, I have just installed Ubuntu v5.04 on my Gateway 3525 laptop (it's a UK version of I think the M250 US Gateway notebook).

I don't have any sound coming from the laptop. I have checked the volume control, it is unmuted and appears to be detected through the volume mixer.

I am a complete and utter beginner with Ubuntu / Linux, so I may need some reasonaby detailed explanations, though I can open a terminal window.

The output of the lspci command is:

```
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Rioworks: Unknown device 203e
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>
```

I am not logged in as root, though the user I am logged in as appears to have audio permissions.

Any help would be greatly appreciated. Thank You.

---

### Post by varunus on 2005-08-05
Can you post the output of "lsmod | grep snd" in a terminal?

Also, what happens when you type "aplay /usr/share/sounds/login.wav" in a terminal?  Do you hear sound, or do you have to CTRL-C the program?

---

### Post by drednik on 2005-08-05
Thank you for your quick reply.

The output of lsmod | grep snd is:
```
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe r_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
``` 

and when I type in "aplay /usr/share/sounds/login.wav" no sound can be heard and I have to Ctrl-C to get back to the prompt

[B]Update: I have just gone through the sound configure instructions [here](http://www.ubuntuguide.org/#configuresoundproperly) but unfortunately this did not help either.

Any ideas or help would be greatly appreciated, I am trying very hard not to return to Windows![/B]

---

### Post by cnayak on 2005-08-05
I also have an i8x0 based soundcard, but it works fine with Ubuntu. However, in FC4 there were some issues. I downloaded the latest alsa drivers (+alsa-lib and alsa-utils) and following instructions given in [www.alsa-project.org](www.alsa-project.org), was able to fix this problem.

  Also try running alsamixer and unmute the External Amplifier.

---

### Post by drednik on 2005-08-05
When I type in "alsamixer" at the run command, nothing happens, so I am assuming that it isn't supported.

I looked at [www.alsa-project.org](www.alsa-project.org), and downloaded the alsa-lib and alsa-utils compressed files into a new directory ..usr/src/alsa.

Not sure what to do next now, as the notes on [this page](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=.&chip=440MX%2C+i810%2C+i810%2C+i810E%2C+i820%2C+i820&module=intel8x0#links) become a bit incomprehensible for me.

Please keep the suggestions coming!

---

### Post by drednik on 2005-08-06
Needle. Haystack.

Ok, I got this far:```
root@cowboy:/usr/src/alsa # cd alsa-driver-1.0.9b
root@cowboy:/usr/src/alsa/alsa-driver-1.0.9b # ./configure --with-cards=intel8x0  --with-sequencer=yes;make;make install
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9b'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9b'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9b/acore'
Makefile:6: /usr/src/alsa/alsa-driver-1.0.9b/Makefile.conf: No such file or dire ctory
make[1]: *** No rule to make target `/usr/src/alsa/alsa-driver-1.0.9b/Makefile.c onf'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9b/acore'
make: *** [install-modules] Error 1
root@cowboy:/usr/src/alsa/alsa-driver-1.0.9b #
``` 

And the error messages suggest it failed at the configuring stage.

I now feel justified to do this... ](*,) 

Any kind souls out there to help me?

---

### Post by drednik on 2005-08-06
Found alsamixer (through GNOME terminal - doh) and checked that the external amplifier was not muted, it wasn't.

The error message in the above list suggests that I didn't have an available compiler, so I downloaded one through apt-get install gcc.

This learning curve is STEEP!

---

### Post by drednik on 2005-08-06
After installing the C compiler, I got this:
```
root@cowboy:/usr/src/alsa/alsa-driver-1.0.9b # ./configure --with-cards=intel8x0 --with-sequencer=yes;make;make install
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.9b
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9b'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9b'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9b/acore'
Makefile:6: /usr/src/alsa/alsa-driver-1.0.9b/Makefile.conf: No such file or directory
make[1]: *** No rule to make target `/usr/src/alsa/alsa-driver-1.0.9b/Makefile.conf'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9b/acore'
make: *** [install-modules] Error 1
root@cowboy:/usr/src/alsa/alsa-driver-1.0.9b # ./configure --with-cards=intel8x0 --with-sequencer=yes;make;make install
``` 

Don't quite know what to make of this now!

---

### Post by varunus on 2005-08-06
Try doing the following in a terminal (I don't recommend installing the new ALSA, frankly.  Its a PAIN for newbies.):
```

killall esd
aplay /usr/share/sounds/login.wav
```

Does that work for you?  You followed the configure sound properly howto completely, including the Multimedia Systems Selector part?  What error does say, rhythmbox give you when you try to play sound?

If you keep having problems (I don't know why you would, since I have an intel8x0 card that worked out of the box) check all of the things in alsamixer.  You may want to wait for breezy, with its MUCH better sound support out of the box.

---

### Post by drednik on 2005-08-09
when i enter "aplay /usr/share/sounds/login.wav" it seems to be play something, but nothing is heard.

i've messed about with the permutations of the alsamixer but no avail.

i also had problems with the resolution of the screen and managed to break it so it was only text input which amused me greatly.

so sadly, i have had to rebuild my laptop with windows only, and can only now access ubuntu through the live CD.

rhythmbox can't play mp3 files (no decoders / plugins) and when i try to play a wav file it says it can't write to the resource.

at this stage i am going to wait for breezy and see how that copes, cheers for all your help though.

---

