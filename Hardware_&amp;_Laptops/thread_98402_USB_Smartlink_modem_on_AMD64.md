---
title: "USB Smartlink modem on AMD64"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by dsd on 2005-12-03
I've been stuggling to get this modem to work, even though there are some instructions available.

After much searching I came up with these instructions,

[http://linmodems.technion.ac.il/archive-fourth/msg02594.html](http://linmodems.technion.ac.il/archive-fourth/msg02594.html)

I tried following these instructions, but to no avail. It seems (not sure) that I need a 32bit version of libasound, and maybe some other things.

The first error I get is,

```
modem_main.c:64:28: error: alsa/asoundlib.h: No such file or directory
```

Any advice? Please?

---

### Post by mlomker on 2005-12-03
To my knowledge there is no way to make a software modem work under 64-bit...there simply aren't any drivers available.  That's one of the reasons that I run 32-bit on my laptop.

---

### Post by dsd on 2005-12-04
According to the instructions that I posted a link to above, it should be possible. AMD64 can run 32 bit commands - is it not possible to compile the drivers for 32-bit on AMD64? The instructions are,
------------------------
1. Install alsa libs and drivers (both 64-bit and 32-bit versions from SuSE 9.1 64 bit DVD (alsa version 1.0.3-36))

2. Download slmodem-2.9.9-alsa.tar.gz and slmodem-2.9.9-alsa.patch from [http://linmodems.technion.ac.il/packages/](http://linmodems.technion.ac.il/packages/)

3. Apply the patch to the slmodem-2.9.9-alsa sources

4. Build the slmodemd for the 32-bit i386 architecture.    
A 32-bit verison is necessary, as the dsplibs.o object file supplied with slmodem (source not supplied) is compiled for 32-bit i386, so linking with 64-bit object files will fail. In order to build the 32-bit version, some changes are required to the slmodemd Makefile:  cd slmodem-2.9.9-alsa/modem , and edit the Makefile.
Add -m32 to the CFLAGS in the makefile (this will build a 32-bit rather than 64-bit executable). Add /usr/lib/libasound.so to the list of slmodemd dependencies (i.e. the 32 bit version of libasound.so). Comment out the line slmodemd: -lasound  (to prevent linking with the 64-bit version of libasound.so, in /usr/lib64)
Build slmodemd with make SUPPORT_ALSA=1

5. Load up the snd_intel8x0m module : modprobe snd_intel8x0m

6. Start slmodemd with slmodemd --country=YOUR_COUNTRY --alsa hw:1

7. Configure wvdial to use/dev/ttySL0 as modem, and also set Carrier Check= no

8. Start up wvdial
------------------------
I'm not sure what the ALSA support is for exactly, but just want to figure out if it is possible to do this, and what packages I would need to install. Is it possible to install 32-bit libraries onto my 64-bit system?

---

### Post by dsd on 2005-12-04
I getting the following error message when trying to compile,

```

gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -m32   -o modem.o -c modem.c
modem.c: In function ‘modem_reset’:
modem.c:1604: error: invalid storage class for function ‘sregs_init’
modem.c:1616: warning: implicit declaration of function ‘sregs_init’
modem.c: At top level:
modem.c:1630: error: static declaration of ‘sregs_init’ follows non-static declaration
modem.c:1616: error: previous implicit declaration of ‘sregs_init’ was here
make[1]: *** [modem.o] Error 1

```

The modem_reset function looks like this,

```

int modem_reset(struct modem *m)
{
        static int sregs_init(unsigned char sregs[]);
        MODEM_DBG("modem reset...\n");
        if(m->state != STATE_MODEM_IDLE)
                modem_hup(m,1);
        else if(m->started)
                modem_stop(m);
        else if(m->hook)
                modem_set_hook(m,MODEM_HOOK_ON);
        modem_set_state(m, STATE_MODEM_IDLE);
        m->command = 1;
        m->min_rate = MODEM_MIN_RATE;
        m->max_rate = MODEM_MAX_RATE;
        sregs_init(m->sregs);
        modem_homolog_init(m,m->homolog->id,NULL);
        modem_set_mode(m, MODEM_MODE_DATA);
        return 0;
}

```

Any suggestions as to what might need to be changed?

---

### Post by mlomker on 2005-12-04
[QUOTE=dsd]Is it possible to install 32-bit libraries onto my 64-bit system?[/QUOTE]

Interesting.  It sounds like it was pretty touchy about libraries on their system and 2.6.4 was a while ago.  I ran across [some 64-bit binaries]("http://www.xs4all.nl/~pjl/slmodemd/") for Fedora that I hadn't seen before.

I always assumed that it wouldn't work because intel snd module is 64-bit but your link suggests that they got it to interface with a 32-bit slmodemd anyway.

Have you looked into [setting up a chroot]("https://wiki.ubuntu.com/DebootstrapChroot")?  I didn't take things that far, but that'd be a way to be sure that it was linking to the proper libraries.

---

### Post by dsd on 2005-12-05
Is there anything that one can do with the Fedora binaries to convert them to .deb files? I saw them, just wasn't sure if I could make use of them.

The chroot options might work - I just need to figure out how it works, and what to setup.

---

### Post by mlomker on 2005-12-05
[QUOTE=dsd]Is there anything that one can do with the Fedora binaries to convert them to .deb files? I saw them, just wasn't sure if I could make use of them.
[/QUOTE]

**alien** will convert RPM's but it's unlikely to work since you're dealing with kernel modules and the paths are different on Ubuntu.

---

### Post by dsd on 2005-12-10
I asked a question on the linmodems discussion list, and was told to try the latest snapshot (22 sept) from [http://linmodems.technion.ac.il/packages/smartlink/snapshots/](http://linmodems.technion.ac.il/packages/smartlink/snapshots/)

I downloaded the suggested package with these results,

"make" with no changes. problems seem to occur when linking with the
following messages,
```

gcc -o slmodemd modem_main.o modem_cmdline.o modem.o modem_datafile.o
modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o
modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o
dsplibs.o sysdep_common.o
/usr/bin/ld: warning: i386 architecture of input file `dsplibs.o' is
incompatible with i386:x86-64 output
dsplibs.o: In function `ModulusEncoder::progress(unsigned char*,
unsigned int*)':
: undefined reference to `__moddi3'

```

If I modify the ./modem/Makefile and add -m32 to the CFAGS, then the
output is pretty much the same, except I get a warning for each of the
compiled files.

I tried adding -m32 to the linking command, so lines
```

slmodemd modem_test:
       $(CC) -o $@ $^

```
changed to
```

slmodemd modem_test:
       $(CC) -m32 -o $@ $^

```
with the following output messages,
```

gcc -m32 -o slmodemd modem_main.o modem_cmdline.o modem.o
modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o
modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o
dp_dummy.o dsplibs.o sysdep_common.o
/usr/bin/ld: skipping incompatible
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../libc.so when searching
for -lc
/usr/bin/ld: skipping incompatible
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../libc.a when searching for
-lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when
searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when
searching for -lc/usr/bin/ld: skipping incompatible /usr/lib/libc.so
when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc

```

So from this I'm guessing that I need the 32-bit libraries. How do I go about installing these libraries, or making the compiler link to them rather? I see that the lib32gcc1 package is installed on my system.

---

### Post by mlomker on 2005-12-10
[QUOTE=dsd]So from this I'm guessing that I need the 32-bit libraries. How do I go about installing these libraries, or making the compiler link to them rather? I see that the lib32gcc1 package is installed on my system.[/QUOTE]

I'd recommend starting a new thread in the developer forum with that question.

---

### Post by gazmon on 2006-12-28
> **dsd said:**
> 
...
The first error I get is,

```
modem_main.c:64:28: error: alsa/asoundlib.h: No such file or directory
```

...
To solve this you need install alsa headers:

```
sudo apt-get install libasound2-dev
```

---

