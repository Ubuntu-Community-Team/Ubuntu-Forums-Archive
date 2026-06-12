---
title: "No PCMCIA Support"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by WhiteStool on 2006-07-02
I have a Dell Latitude CPx running Xubuntu Dapper Drake 6.06. I have a card supported by ndiswrapper (all set to go) and a 3com 589E, with a module that I know is supported (the module is 3c589_cs).

I know that the pcmcia socket and these modules work for that both have worked under Slackware 10.2, and I am posting via my wireless card right now.

I already tryed

```
modprobe pcmcia
```

and another pcmcia module that I cannot remember the name of. I am desperate to get out of this hole Microsoft calls Windows.

---

### Post by guitard00d on 2006-07-05
For some reason, they failed to fully test the Xubuntu installer on laptops that still use PCMCIA and the installer removes the pcmcia-cs package (and breaks a few other things) during its "clean up" procedure. I still can't get PCMCIA working in Xubuntu after it's installed on the hard drive. I even added the Kubuntu Alternate Install CD to Synaptic's list of repositories (since that CD has all of the necessary packages in the correct version) and even after reinstalling pcmcia and pcmcia-cs, PCMCIA support still doesn't work.

Looks like Xubuntu desperately needs to release a fixed v6.07 since the thing is targeted to run on older systems that are too slow to run Gnome or KDE.

---

### Post by benblur4 on 2006-07-05
I agree. I have an old Vaio N505ve and it only has a pcmcia cdrom drive.  The Xubuntu boot cd only makes it to the boot screen and then freezes on some error about not accessing the cd drive. Thus, I can't install Xubuntu.#-o

---

### Post by guitard00d on 2006-07-06
This is just the way it looks to me, but...It appears that the Xubuntu people were more concerned with pushing this thing out the door so it would be in time with the other *ubuntu 6.06 releases, rather than refining things in Xubuntu and making it stable/reliable.

---

