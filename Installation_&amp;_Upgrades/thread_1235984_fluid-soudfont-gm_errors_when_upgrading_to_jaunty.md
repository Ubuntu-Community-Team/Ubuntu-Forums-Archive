---
title: "fluid-soudfont-gm errors when upgrading to jaunty"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by dvlchd3 on 2009-08-09
During my upgrade from 8.10 to 9.04, I encountered several error messages about packages not upgrading.  The majority of which I was able to resolve later, however, one package is still not installing correctly.

fluid-soundfont-gm is a depencency of ubuntustudio-audio, however, I am unable to install the package.  Here is the message 'sudo apt-get -f install' gives me:

```
Unpacking fluid-soundfont-gm (from .../fluid-soundfont-gm_3.1-2_all.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/fluid-soundfont-gm_3.1-2_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/sounds/sf2/FluidR3_GM.sf2')
Errors were encountered while processing:
 /var/cache/apt/archives/fluid-soundfont-gm_3.1-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

dpkg.log:
```
2009-08-09 17:59:38 startup archives unpack
2009-08-09 17:59:57 upgrade fluid-soundfont-gm 3.1-1 3.1-2
2009-08-09 17:59:57 status half-configured fluid-soundfont-gm 3.1-1
2009-08-09 17:59:57 status unpacked fluid-soundfont-gm 3.1-1
2009-08-09 17:59:57 status half-installed fluid-soundfont-gm 3.1-1
2009-08-09 18:00:13 status unpacked fluid-soundfont-gm 3.1-1
2009-08-09 18:00:13 status installed fluid-soundfont-gm 3.1-1
2009-08-09 18:18:23 startup packages remove
2009-08-09 18:18:23 status installed ubuntustudio-audio 0.52
2009-08-09 18:18:23 remove ubuntustudio-audio 0.52 0.52
2009-08-09 18:18:23 status half-configured ubuntustudio-audio 0.52
2009-08-09 18:18:24 status half-installed ubuntustudio-audio 0.52
2009-08-09 18:18:24 status config-files ubuntustudio-audio 0.52
2009-08-09 18:18:24 status config-files ubuntustudio-audio 0.52
2009-08-09 18:18:24 status config-files ubuntustudio-audio 0.52
2009-08-09 18:18:24 status not-installed ubuntustudio-audio <none>
2009-08-09 18:18:24 status installed fluid-soundfont-gs 3.1-2
2009-08-09 18:18:24 remove fluid-soundfont-gs 3.1-2 3.1-2
2009-08-09 18:18:24 status half-configured fluid-soundfont-gs 3.1-2
2009-08-09 18:18:24 status half-installed fluid-soundfont-gs 3.1-2
2009-08-09 18:18:24 status config-files fluid-soundfont-gs 3.1-2
2009-08-09 18:18:24 status config-files fluid-soundfont-gs 3.1-2
2009-08-09 18:18:25 startup packages purge
2009-08-09 18:18:25 status installed fluid-soundfont-gm 3.1-1
2009-08-09 18:18:25 remove fluid-soundfont-gm 3.1-1 3.1-2
2009-08-09 18:18:25 status half-configured fluid-soundfont-gm 3.1-1
2009-08-09 18:18:25 status half-installed fluid-soundfont-gm 3.1-1
2009-08-09 18:18:25 status config-files fluid-soundfont-gm 3.1-1
2009-08-09 18:18:25 status config-files fluid-soundfont-gm 3.1-1
2009-08-09 18:18:25 status config-files fluid-soundfont-gm 3.1-1
2009-08-09 18:18:25 status not-installed fluid-soundfont-gm <none>
2009-08-09 18:21:50 startup archives unpack
2009-08-09 18:21:50 install fluid-soundfont-gm <none> 3.1-2
2009-08-09 18:21:50 status half-installed fluid-soundfont-gm 3.1-2
2009-08-09 18:22:04 status not-installed fluid-soundfont-gm <none>
2009-08-09 18:22:04 install fluid-soundfont-gs 3.1-2 3.1-2
2009-08-09 18:22:04 status half-installed fluid-soundfont-gs 3.1-2
2009-08-09 18:22:05 status unpacked fluid-soundfont-gs 3.1-2
2009-08-09 18:22:05 status unpacked fluid-soundfont-gs 3.1-2
2009-08-09 18:22:05 install ubuntustudio-audio <none> 0.52
2009-08-09 18:22:05 status half-installed ubuntustudio-audio 0.52
2009-08-09 18:22:05 status unpacked ubuntustudio-audio 0.52
2009-08-09 18:22:05 status unpacked ubuntustudio-audio 0.52
2009-08-09 18:22:06 startup packages configure
2009-08-09 19:15:13 startup archives unpack
2009-08-09 19:15:14 startup packages configure
2009-08-09 19:18:53 startup archives unpack
2009-08-09 19:18:54 install fluid-soundfont-gm <none> 3.1-2
2009-08-09 19:18:54 status half-installed fluid-soundfont-gm 3.1-2
2009-08-09 19:19:07 status not-installed fluid-soundfont-gm <none>
```

kern.log:
```
Aug  9 19:14:40 BRICKMAN kernel: [ 5326.508401] synaptic[20928]: segfault at 568 ip b7fa53af sp bf8676f4 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[b7f71000+bf000]
Aug  9 19:15:13 BRICKMAN kernel: [ 5359.373074] dpkg[20963]: segfault at 0 ip 08053103 sp bfc996e0 error 4 in dpkg[8048000+5a000]
Aug  9 19:15:14 BRICKMAN kernel: [ 5360.130040] dpkg[20973]: segfault at 2d726582 ip 08060f92 sp bffb29b0 error 4 in dpkg[8048000+5a000]
```

Not sure if any other logs are applicable.  I have seen several bug reports on this, however, no activity, I was hoping someone else may have run into this issue and have some sort of resolution.

---

### Post by Partyboi2 on 2009-08-09
Hi, try clearing the cache and installing it again
```
sudo apt-get clean
```
```
sudo apt-get update && sudo apt-get install fluid-soundfont-gm
```

---

### Post by dvlchd3 on 2009-08-10
I actually already tried that.  I guess I should've specified, in more detail, what I have attempted to do to fix this issue.

I have done an autoclean and an autoremove.  Then attempted to install the package again.

I have gone into synaptics, and done a "complete removal" and re-install through synaptics.

I'm not sure why I keep downloading what appears to be a corrupt deb file.  Now that I ponder a bit more on this, perhaps this is an issue to go to bug reporting.  Please let me know if anyone has any other suggestions though.

---

