---
title: "My Webcam is upside down in Asus N50Vc"
date: 2009-09-10
forum: Hardware
---

### Post by a.2mjed.a on 2009-09-10
Hi,

first of all, excuze me for my english

i have Asus N50Vc and my webcam is upside down :(

i found the slove here [https://wiki.ubuntu.com/LaptopTestingTeam/AsusN50Vc](https://wiki.ubuntu.com/LaptopTestingTeam/AsusN50Vc)

i download this file "libv4l-0.6.1-test.tar.gz" to Home folderand wrote this command in terminal "ls /lib64/libc.so.6" and get "[COLOR=DeepSkyBlue]/lib64/libc.so.6[COLOR=Black]" so it's work successful[/COLOR] :)
[COLOR=Black]so i [/COLOR][/COLOR]use the multilib instrucions.
[COLOR=DeepSkyBlue][COLOR=Black]then wrote this command "tar xvfz libv4l-0.6.1-test.tar.gz" and this is what i got
[/COLOR][/COLOR]```
libv4l-0.6.1/
libv4l-0.6.1/README.multi-threading
libv4l-0.6.1/TODO
libv4l-0.6.1/libv4l2/
libv4l-0.6.1/libv4l2/libv4l2-priv.h
libv4l-0.6.1/libv4l2/v4l2convert.c
libv4l-0.6.1/libv4l2/log.c
libv4l-0.6.1/libv4l2/libv4l2.c
libv4l-0.6.1/libv4l2/Makefile
libv4l-0.6.1/libv4lconvert/
libv4l-0.6.1/libv4lconvert/crop.c
libv4l-0.6.1/libv4lconvert/libv4lconvert.c
libv4l-0.6.1/libv4lconvert/rgbyuv.c
libv4l-0.6.1/libv4lconvert/processing/
libv4l-0.6.1/libv4lconvert/processing/libv4lprocessing-priv.h
libv4l-0.6.1/libv4lconvert/processing/libv4lprocessing.c
libv4l-0.6.1/libv4lconvert/processing/gamma.c
libv4l-0.6.1/libv4lconvert/processing/autogain.c
libv4l-0.6.1/libv4lconvert/processing/libv4lprocessing.h
libv4l-0.6.1/libv4lconvert/processing/whitebalance.c
libv4l-0.6.1/libv4lconvert/mr97310a.c
libv4l-0.6.1/libv4lconvert/spca501.c
libv4l-0.6.1/libv4lconvert/sn9c20x.c
libv4l-0.6.1/libv4lconvert/control/
libv4l-0.6.1/libv4lconvert/control/libv4lcontrol-priv.h
libv4l-0.6.1/libv4lconvert/control/libv4lcontrol.h
libv4l-0.6.1/libv4lconvert/control/libv4lcontrol.c
libv4l-0.6.1/libv4lconvert/spca561-decompress.c
libv4l-0.6.1/libv4lconvert/bayer.c
libv4l-0.6.1/libv4lconvert/sn9c10x.c
libv4l-0.6.1/libv4lconvert/ov511-decomp.c
libv4l-0.6.1/libv4lconvert/libv4lconvert-priv.h
libv4l-0.6.1/libv4lconvert/hm12.c
libv4l-0.6.1/libv4lconvert/tinyjpeg.h
libv4l-0.6.1/libv4lconvert/tinyjpeg-internal.h
libv4l-0.6.1/libv4lconvert/sn9c2028-decomp.c
libv4l-0.6.1/libv4lconvert/helper.c
libv4l-0.6.1/libv4lconvert/tinyjpeg.c
libv4l-0.6.1/libv4lconvert/libv4lsyscall-priv.h
libv4l-0.6.1/libv4lconvert/flip.c
libv4l-0.6.1/libv4lconvert/pac207.c
libv4l-0.6.1/libv4lconvert/helper-funcs.h
libv4l-0.6.1/libv4lconvert/sq905c.c
libv4l-0.6.1/libv4lconvert/jidctflt.c
libv4l-0.6.1/libv4lconvert/ov518-decomp.c
libv4l-0.6.1/libv4lconvert/Makefile
libv4l-0.6.1/README
libv4l-0.6.1/include/
libv4l-0.6.1/include/libv4l2.h
libv4l-0.6.1/include/libv4l1.h
libv4l-0.6.1/include/libv4lconvert.h
libv4l-0.6.1/COPYING.LIB
libv4l-0.6.1/libv4l1/
libv4l-0.6.1/libv4l1/v4l1compat.c
libv4l-0.6.1/libv4l1/libv4l1-priv.h
libv4l-0.6.1/libv4l1/log.c
libv4l-0.6.1/libv4l1/libv4l1.c
libv4l-0.6.1/libv4l1/Makefile
libv4l-0.6.1/ChangeLog
libv4l-0.6.1/Makefile
```so it's work :)
and wrote this command "cd libv4l-0.6.1-test.tar.gz" and this it what i got "bash: cd: libv4l-0.6.1-test.tar.gz: Not a directory"
what i have to do now :confused:

please help me

---

### Post by pmaciver on 2009-10-13
> **a.2mjed.a said:**
> Hi,

first of all, excuze me for my english

i have Asus N50Vc and my webcam is upside down :(

i found the slove here [https://wiki.ubuntu.com/LaptopTestingTeam/AsusN50Vc](https://wiki.ubuntu.com/LaptopTestingTeam/AsusN50Vc)

i download this file "libv4l-0.6.1-test.tar.gz" to Home folderand wrote this command in terminal "ls /lib64/libc.so.6" and get "[COLOR=DeepSkyBlue]/lib64/libc.so.6[COLOR=Black]" so it's work successful[/COLOR] :)
[COLOR=Black]so i [/COLOR][/COLOR]use the multilib instrucions.
[COLOR=DeepSkyBlue][COLOR=Black]then wrote this command "tar xvfz libv4l-0.6.1-test.tar.gz" and this is what i got
[/COLOR][/COLOR]```
libv4l-0.6.1/
libv4l-0.6.1/README.multi-threading
libv4l-0.6.1/TODO
libv4l-0.6.1/libv4l2/
libv4l-0.6.1/libv4l2/libv4l2-priv.h
libv4l-0.6.1/libv4l2/v4l2convert.c
libv4l-0.6.1/libv4l2/log.c
libv4l-0.6.1/libv4l2/libv4l2.c
libv4l-0.6.1/libv4l2/Makefile
libv4l-0.6.1/libv4lconvert/
libv4l-0.6.1/libv4lconvert/crop.c
libv4l-0.6.1/libv4lconvert/libv4lconvert.c
libv4l-0.6.1/libv4lconvert/rgbyuv.c
libv4l-0.6.1/libv4lconvert/processing/
libv4l-0.6.1/libv4lconvert/processing/libv4lprocessing-priv.h
libv4l-0.6.1/libv4lconvert/processing/libv4lprocessing.c
libv4l-0.6.1/libv4lconvert/processing/gamma.c
libv4l-0.6.1/libv4lconvert/processing/autogain.c
libv4l-0.6.1/libv4lconvert/processing/libv4lprocessing.h
libv4l-0.6.1/libv4lconvert/processing/whitebalance.c
libv4l-0.6.1/libv4lconvert/mr97310a.c
libv4l-0.6.1/libv4lconvert/spca501.c
libv4l-0.6.1/libv4lconvert/sn9c20x.c
libv4l-0.6.1/libv4lconvert/control/
libv4l-0.6.1/libv4lconvert/control/libv4lcontrol-priv.h
libv4l-0.6.1/libv4lconvert/control/libv4lcontrol.h
libv4l-0.6.1/libv4lconvert/control/libv4lcontrol.c
libv4l-0.6.1/libv4lconvert/spca561-decompress.c
libv4l-0.6.1/libv4lconvert/bayer.c
libv4l-0.6.1/libv4lconvert/sn9c10x.c
libv4l-0.6.1/libv4lconvert/ov511-decomp.c
libv4l-0.6.1/libv4lconvert/libv4lconvert-priv.h
libv4l-0.6.1/libv4lconvert/hm12.c
libv4l-0.6.1/libv4lconvert/tinyjpeg.h
libv4l-0.6.1/libv4lconvert/tinyjpeg-internal.h
libv4l-0.6.1/libv4lconvert/sn9c2028-decomp.c
libv4l-0.6.1/libv4lconvert/helper.c
libv4l-0.6.1/libv4lconvert/tinyjpeg.c
libv4l-0.6.1/libv4lconvert/libv4lsyscall-priv.h
libv4l-0.6.1/libv4lconvert/flip.c
libv4l-0.6.1/libv4lconvert/pac207.c
libv4l-0.6.1/libv4lconvert/helper-funcs.h
libv4l-0.6.1/libv4lconvert/sq905c.c
libv4l-0.6.1/libv4lconvert/jidctflt.c
libv4l-0.6.1/libv4lconvert/ov518-decomp.c
libv4l-0.6.1/libv4lconvert/Makefile
libv4l-0.6.1/README
libv4l-0.6.1/include/
libv4l-0.6.1/include/libv4l2.h
libv4l-0.6.1/include/libv4l1.h
libv4l-0.6.1/include/libv4lconvert.h
libv4l-0.6.1/COPYING.LIB
libv4l-0.6.1/libv4l1/
libv4l-0.6.1/libv4l1/v4l1compat.c
libv4l-0.6.1/libv4l1/libv4l1-priv.h
libv4l-0.6.1/libv4l1/log.c
libv4l-0.6.1/libv4l1/libv4l1.c
libv4l-0.6.1/libv4l1/Makefile
libv4l-0.6.1/ChangeLog
libv4l-0.6.1/Makefile
```so it's work :)
and wrote this command "cd libv4l-0.6.1-test.tar.gz" and this it what i got "bash: cd: libv4l-0.6.1-test.tar.gz: Not a directory"
what i have to do now :confused:

please help me
You have tried to change into the tar archive instead of the directory that was created.

Just do a 

cd libv4l-0.6.1/

and you will be able to go from there.

---

### Post by a.2mjed.a on 2009-11-05
Thanx pmaciver for the solution and i'm sorry for the late replay

now i got Ubuntu 9.10 and the Webcam is upside-down
i did the solution but it doesn't work :(

what can i do know??

---

### Post by priegog on 2009-11-08
Seconded.
The solutions that worked on Jaunty don't apply to karmic anymore... 
Help?

---

### Post by PacShady on 2009-11-09
Hey guys, just started the horrible process of upgrading to Karmic a few days ago (still going, trying to work out as many bugs as I can to make my laptop usable again), and found this thread in my travels.

I didn't test the 0.6.1-test version of libv4l as mentioned in the wiki page, but I had a look through the server that file came from, and found a newer version here: [http://people.atrpms.net/~hdegoede/libv4l-0.6.2-test.tar.gz](http://people.atrpms.net/~hdegoede/libv4l-0.6.2-test.tar.gz)

Tested it out, seems to work on my system. Hope it works for you as well. Once I get most of the kinks out of this system I'll be updating the AsusN50Vc wiki page for Karmic, but at this stage it seems nearly as hard to get usable as Edgy was.

'Shady

---

