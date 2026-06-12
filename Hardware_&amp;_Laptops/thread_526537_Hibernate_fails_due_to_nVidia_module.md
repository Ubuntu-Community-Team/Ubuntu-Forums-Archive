---
title: "Hibernate fails due to nVidia module"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by George007 on 2007-08-15
Hello, I have a sony VGN-FE38GP. it has a NVIDIA 7600 GO graphic card.
when I try to go into hibernation, i get the following error:

```

sudo hibernate

Some modules failed to unload: nvidia
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

```

what should I do?

---

### Post by i60t on 2007-08-16
Currently i'm sorry for not posting an solution - BUT i have the same Problem and i'm very curious for an solution..

Best wishes
- i60t

---

### Post by i60t on 2007-08-16
sadly - the "--force" option ist not helping out here

[code]
$ sudo hibernate --force
Some modules failed to unload: nvidia
Some modules failed to unload: nvidia
/bin/echo: Schreibfehler: Cannot allocate memory
[code]

:confused:

---

### Post by EXCiD3 on 2007-08-16
I think i may possibly be able to help here. Here is some info from my HP dv9000 Howto which can be found here: [http://ubuntuforums.org/showthread.php?t=512059]("http://ubuntuforums.org/showthread.php?t=512059")

>     Suspend/Hibernate

        Supposedly adding "nosmp" as a boot option, disabling Sync To Vblank in Beryl, and if you edit the /etc/default/acpi-support and set POST_VIDEO=false, suspend and hibernate
        should work better. QUESTION: Is "nosmp" the option that makes this work? Anyone know?

    Suspend

        Works! Scary looking whitewashed screen on resume, but it works. Intel wireless sometimes stops working after suspend/hibernate.
        First suspend, wireless doesnt come back, every suspend after, wireless works.

    Hibernate

        Works! Same results as suspend. Unfortunately, after tweaking Feisty it is faster to shutdown and bootup than it is to hibernate. 

I don't know if it will work for your specific laptop, but it seemed to work on my HP dv9000 fairly well. Unfortunately I have not tested it too much since it is almost just as easy for me to shutdown/bootup in the time it takes to hibernate/resume. You may check out the other stuff on the thread as much of it pertains to many other laptops. I am also going to add a quickly little modification that cuts your bootup time in half tomorrow (i hope). Check it out.

---

