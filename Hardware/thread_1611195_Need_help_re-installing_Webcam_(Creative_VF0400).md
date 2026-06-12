---
title: "Need help re-installing Webcam (Creative VF0400)"
date: 2010-11-01
forum: Hardware
---

### Post by shoryuken on 2010-11-01
Hi folks,

I use to have this webcam working in the past but all of a sudden it has stopped working. I've tried the instructions in [http://ubuntuforums.org/showthread.php?t=660463]("http://ubuntuforums.org/showthread.php?t=660463") as well as all other instructions I've found through google search.

I am currently running Ubuntu 10.10 on a Sony VGN-N365E. This laptop does not have an internal mic or webcam.

I've downloaded Ov51xJpegHackedSource (ov51x-jpeg-1.5.9.tar.gz) from [http://www.rastageeks.org/](http://www.rastageeks.org/) and once I try to compile the driver I get the following output:

```
make -C /lib/modules/2.6.35-22-generic/build M=/home/arash/ov51x-jpeg-1.5.9 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/arash/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o
/home/arash/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:87: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/home/arash/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o] Error 1
make[1]: *** [_module_/home/arash/ov51x-jpeg-1.5.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] Error 2

```


Here is the output from /var/cache/modass/ov51x-jpeg-source.buildlog.2.6.32-24-generic.1282519934

```

/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/ov51x-jpeg'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.32-24-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.mod$
    sed -e 's/##KVERS##/2.6.32-24-generic/g ;s/#KVERS#/2.6.32-24-generic/g ; s/$
  done
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp build-stamp
dh_clean
dh_clean: Compatibility levels before 5 are deprecated.
/usr/bin/make -w -f debian/rules clean
make[2]: Entering directory `/usr/src/modules/ov51x-jpeg'
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp build-stamp
dh_clean
dh_clean: Compatibility levels before 5 are deprecated.
make[2]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make[1]: Nothing to be done for `kdist_config'.
dh_testroot
dh_clean -k
dh_clean: Compatibility levels before 5 are deprecated.
# Build the module
/usr/bin/make KERNEL_DIR=/usr/src/linux KDIR=/usr/src/linux KVERS=2.6.32-24-gen$
make[2]: Entering directory `/usr/src/modules/ov51x-jpeg'
/usr/bin/make -C /usr/src/linux M=/usr/src/modules/ov51x-jpeg modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.o
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function &#8216;create_proc_ov511_c$
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:677: error: implicit declaration $
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:681: error: &#8216;struct proc_dir_entr$
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:689: error: &#8216;struct proc_dir_entr$
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:700: error: &#8216;struct proc_dir_entr$
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:712: error: &#8216;struct proc_dir_entr$
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function &#8216;proc_ov511_create&#8217;:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:766: error: &#8216;struct proc_dir_entr$
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function &#8216;ov51x_clear_snapsho$
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:1691: error: implicit declaration$
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function &#8216;ov51x_v4l1_ioctl&#8217;:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing argument 1$
include/media/v4l2-ioctl.h:298: note: expected &#8216;struct file *&#8217; but argument is $
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing argument 2$
include/media/v4l2-ioctl.h:298: note: expected &#8216;unsigned int&#8217; but argument is o$
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing argument 4$
include/media/v4l2-ioctl.h:298: note: expected &#8216;v4l2_kioctl&#8217; but argument is of$
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: error: too many arguments t$
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: At top level:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6651: warning: initialization fro$
make[4]: *** [/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.o] Error 1
make[3]: *** [_module_/usr/src/modules/ov51x-jpeg] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make: *** [kdist_build] Error 2


```

I'm not very familiar with the internal working of linux and I'm not sure where to go from this point on. 

I would appreciate any help that can guide me in resolving this problem.

Here is the lsusb output:
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 041e:4061 Creative Technology, Ltd Live! Cam Notebook Pro [VF0400]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```



Somehow the webcam is being detected but the video is not working.

Currently the microphone is picking up sound but the sound is being altered. Whether I use the Sound Recorder application or I try to do voice chatting through gmail for example, the sound comes across as if it is being fast forwarded. 

Thanks in advance for any suggestions and guidance that you can provide.

Regards.

---

### Post by shoryuken on 2010-11-08
A little bump, I would greatly appreciate any help with this.

Cheers

---

### Post by IcarusR on 2010-11-09
Have you tried installing the 'Ov51xJpeg' (driver) package for your version of Ubuntu as documented on the site you linked ? 

Download .deb for your Ubuntu install from here...

[http://packages.ubuntu.com/search?keywords=ov51x-jpeg-source]("http://packages.ubuntu.com/search?keywords=ov51x-jpeg-source")

---

### Post by shoryuken on 2010-11-09
> **IcarusR said:**
> Have you tried installing the 'Ov51xJpeg' (driver) package for your version of Ubuntu as documented on the site you linked ? 

Download .deb for your Ubuntu install from here...

[http://packages.ubuntu.com/search?keywords=ov51x-jpeg-source]("http://packages.ubuntu.com/search?keywords=ov51x-jpeg-source")

Hi,
and thank you for your reply. 
I have installed that package. That package seems to install properly but when that is installed the video part of the camera is not detected and the microphone on the camera which is detected records the sound in slow speed resulting in a fast play back (sounds like playing a recording in fast forward so high pitched) this even happens in live streaming of sounds for example using Gtalk.

Any test you can suggest that I can run after installing the package that could help in resolving this issue?

Thanks again

---

### Post by shoryuken on 2010-11-11
In case any one else has this same problem, I managed to solve it by completely re-installing Ubuntu. 
There should be an easier way to trouble shoot these issue.

The audio issue still remains. The microphone records sounds as if in fast playback, which tells me that the system is detecting/recording the audio at a slower than real time while playing it back at real time.

Someone else has also reported a similar issue but no solutions 
[http://ubuntuforums.org/showthread.php?t=1489981]("http://ubuntuforums.org/showthread.php?t=1489981")

---

