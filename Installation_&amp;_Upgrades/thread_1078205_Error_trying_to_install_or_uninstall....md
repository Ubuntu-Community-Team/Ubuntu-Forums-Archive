---
title: "Error trying to install or uninstall..."
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by Hagar55 on 2009-02-23
I tried installig the "cheese' aplication and got this error message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I tried uninstalling Clam and got the same message.
Does anyone know what's wrong and how to fix it ?

---

### Post by frost151n on 2009-02-23
> **Hagar55 said:**
> you must manually run 'dpkg --configure -a' to correct the problem.

Means open a terminal and type

```
sudo dpkg --configure -a

```

---

### Post by RVA Dennis on 2009-02-23
I had a similar problem a bit earlier in the day and ran the above command,
the result is below:

dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 6 package `libaudio2':
 EOF after field name `Ma'

What is my next step to resolve the problem, please?

---

### Post by frost151n on 2009-02-23
umm... no idea. Best wait for someone more knowledgeable than me.

In the mean while, open the file and check what line 6 says.

```
sudo gedit /var/lib/dpkg/updates/0000
```

Also, do some research on what 'EOF' means

p.s. It's considered rude to hijack another's thread. You should make your own!

---

### Post by snova on 2009-02-23
> **RVA Dennis said:**
> I had a similar problem a bit earlier in the day and ran the above command,
the result is below:

dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 6 package `libaudio2':
 EOF after field name `Ma'

What is my next step to resolve the problem, please?

Found an old thread: [http://ubuntuforums.org/showthread.php?t=385886](http://ubuntuforums.org/showthread.php?t=385886)

```
cd /var/lib/dpkg
sudo cp updates updates.bak
sudo dpkg --configure -a
```

Try it and see...

---

### Post by Hagar55 on 2009-02-24
tried the suggestion and got this :
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

---

### Post by Hagar55 on 2009-02-25
anyone out there know what to do, I cannot open synaptic as well...
I get the same original error

---

### Post by Hagar55 on 2009-02-25
I tried uninstalling a package and got the same error, I did however look in the detial menu as ubuntu tried to uninstall and got the following line before the proces died:
 cannot configure libxinel-bin
cannot configure status (awaiting triggers)

This is a little urgent since I cannot install/uninstall anything now,
is this fixable or should I just dump the install and start all over fresh ?? (wich would be very difficult for me since I'm not yet well versed in linux....

---

### Post by oldos2er on 2009-02-25
> **Hagar55 said:**
> tried the suggestion and got this :
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

 See [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/46530](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/46530) , apparently this is a known bug. Read the posts toward the bottom of the page for some possible solutions.

---

### Post by Hagar55 on 2009-02-26
Ok I'm not that good in linux yet so I tried the next thing:
After entering this command :
sudo dpkg -l | grep iU I got the following reply :

iU  libxine1                                   1.1.15-0ubuntu3.1                                    the xine video/media player library, meta-pa
iU  libxine1-console                           1.1.15-0ubuntu3.1                                    libaa/libcaca/framebuffer/directfb related p
iU  libxine1-ffmpeg                            1.1.15-0ubuntu3.1                                    MPEG-related plugins for libxine1
iU  libxine1-misc-plugins                      1.1.15-0ubuntu3.1                                    Input, audio output and post plugins for lib
iU  libxine1-plugins                           1.1.15-0ubuntu3.1                                    the xine video/media player library, meta pa
iU  libxine1-x                                 1.1.15-0ubuntu3.1                                    X desktop video output plugins for libxine1

Now I do not know if that is the damaged package with me, if it is how do I remove and and once I did that how do reinstall it (I probably need it...)

---

### Post by Hagar55 on 2009-02-27
Anyone ?

---

### Post by Hagar55 on 2009-02-28
I looked at the various posts about the problem again and tried updating the system like one person did.
First there where no updates, when I asked to check the packages it said I needed 156 updates ??
In the detail I saw it replaced a version of dpkg as well. I can now startup synaptic again so I'm hoping everything is working again.

---

### Post by paks.dreamer on 2009-07-09
I don't know if this helps, especially on such a late reply, but I noticed when I ran **sudo apt-get remove example-content** today it said that a whole string of "libxine" - type entries were made invalid and could now be removed with a certain autoremove code (which I can't remember, but could only be done through root).

Did you by any chance remove the example content and/or the ubuntu examples folder?  It could explain why those files are missing if it has "updated" itself at the next check by removing those "redundant" libxine entries for you, mistakenly of course, as you seem to need them?  Or maybe something similar is going on.

I wonder if reinstalling the example-content would fix this, though that's not the ideal fix imo.  Could you apt-get the missing files?  I dunno how this works completely, I'm still fresh on this OS.
--
nm, it seems your update fixed it?

---

