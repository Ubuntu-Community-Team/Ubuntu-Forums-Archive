---
title: "getting Komodo 3.5b1 to work"
date: 2005-11-06
forum: General Help
---

### Post by tomane on 2005-11-06
Hi all.

I D/Led Komodo 3.5 beta1 from activestate and installed it in /opt/Komodo-3.5 (the dir was empty) using the install.sh script. Then, created a symlink to /opt/Komodo-3.5/bin/komodo in /usr/local/bin

After instalation, if I executed komodo from the "run program" box, nothing would happen, although the command was recognized.

Looking at the komodo executable in /opt/Komodo-3.5 revealed that it is a stub that then executes /opt/Komodo-3.5/lib/mozilla/komodo, which in turn executes komodo-bin, under the same directory.

So I tried to execute komodo-bin directly and got error messages regarding some libs that weren't found. These were: libmozjs.so , libnspr4.so , libxpcom_compat.so , libxpcom_core.so and (I'm not sure on this last one) libxpcom.so .
I linked these files to /usr/lib with ln-s. After this komodo-bin crashed with a segmentation fault, as soon as it was started. I have libjpeg and glibc2.1 installed, which seem to be the only required packages, according to activestate.

Here is komodo-bin output, if called with -v(erbose).
Nothing gets drawn on screen, what so ever, all the executable does is to write the lines below....
```
to@ze:/opt/Komodo-3.5/lib/mozilla$ ./komodo-bin -v
komodo: debug: Komodo startup options:
komodo: debug:  nFiles: 0
komodo: debug: mutex name: '/home/to/.komodo/3.5/host-ze/mutex.lock'
komodo: debug: acquired mutex: fd=3
komodo: debug: running lock name: '/home/to/.komodo/3.5/host-ze/running.lock'
komodo: debug: we are the man: fd=4
komodo: debug: commandments file name: '/home/to/.komodo/3.5/host-ze/commandments.fifo'
komodo: debug: first commandments file name: '/home/to/.komodo/3.5/host-ze/first-commandments.txt'
komodo: debug: saving startup environment...
komodo: debug: startup env name: '/home/to/.komodo/3.5/host-ze/startup-env.tmp'
komodo: debug: writing out startup environment
komodo: debug: setting up environment for XRE launch...
komodo: debug: setting XRE_PROFILE_PATH=/home/to/.komodo/3.5/host-ze/XRE
komodo: debug: setting _XRE_USERAPPDATADIR=/home/to/.komodo/3.5/host-ze/XRE
komodo: debug: setting KOMODO_HOSTNAME=ze
komodo: debug: setting _KOMODO_VERUSERDATADIR=/home/to/.komodo/3.5/
komodo: debug: setting _KOMODO_HOSTUSERDATADIR=/home/to/.komodo/3.5/host-ze/
komodo: debug: setting KOMODO_VERBOSE=1
komodo: debug: setting PYTHONHOME=/opt/Komodo-3.5/lib/mozilla/./../python
komodo: debug: startup argv for XRE:
komodo: debug:  argv[0] = './komodo-bin'
Segmentation fault

```
If anyone has a clue of what might be causing this, any help would be apreciated.

BTW, Komodo 3.1 runs, unfortunately it suffers from the problem with the most recent versions of pango, wich makes it completely useless.

--

---

### Post by alext on 2005-11-07
Same here, so you're not alone. Just migrated to Kubuntu from Win XP where I was using Komodo frequently. Hoped it'd work a treat here, but so far nothing but problems with it :( 

Any thoughts anyone? Anyone got it working?

---

### Post by alext on 2005-11-09
Don't know if this helps, but I had what looked an identical problem, but have found a rather easy solution...

As outlined here:
[http://bugs.activestate.com/show_bug.cgi?id=42166](http://bugs.activestate.com/show_bug.cgi?id=42166)

I had installed with sudo to put it somewhere accessible to multiple users (who knows why, there's only me uses this machine). I installed the license with my own account though, and started komodo with just komodo -v from the command line with the nothing / zilch / nada consequences outlined in this thread. 

BUT...running sudo komodo worked a charm, and then you can close down komodo and then run komodo as yourself from then on in! 

Sometimes complex problems have simple solutions! :)

---

### Post by tomane on 2005-11-17
Wow! It really did the trick!
Many thanks for the help.
I don't remember clearly under which privileges did I install komodo and the license. If memory doesn't fail I installed komodo with sudo to use is as a "normal" user and the license as the "normal" user. Maybe it has something to do with that. :confused: 

Anyway it's working, now!
Thanks!:\\:D/

---

