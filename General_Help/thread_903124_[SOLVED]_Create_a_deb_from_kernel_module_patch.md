---
title: "[SOLVED] Create a deb from kernel module patch?"
date: 2008-08-28
forum: General Help
---

### Post by dmizer on 2008-08-28
I have a kernel module patch that patches existing kernel modules (cdc-acm and acm-FOMA).  I finally learned how to patch the module, and compile it into a custom kernel by following these very detailed and helpful directions: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

However, the process took about 8 hours to complete on my under powered laptop. I'd like to avoid having to do this every time a new kernel comes out.

I know that there is a way to patch a module, compile the module as an installable deb package and install it into the existing (generic) kernel image, but despite extensive searching I have been unable to find a solution with a reasonable amount of explanation.

Patch is located here: [http://sourceforge.jp/projects/pepolinux/downloads/28145/acm-FOMA.v0.25.06.tar.gz](http://sourceforge.jp/projects/pepolinux/downloads/28145/acm-FOMA.v0.25.06.tar.gz)

Ask me about networking and servers and I can talk all day long, but this stuff is all new to me.

Thanks.

---

### Post by sdennie on 2008-08-28
You could have a look at module-assistant:

```

sudo apt-get install module-assistant
man m-a

```

That may not do exactly what you want but, if you can't find a way to do it, if I remember right, I believe that kernel building HOWTO leaves out two very important compilation options.  Specifically, if you prepend:

```

INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 fakeroot make-kpkg ...

```

The INSTALL_MOD_STRIP not only drastically reduces compilation time (well, packaging time) but makes the installed kernel much, much smaller.  The CONCURRENCY_LEVEL is like "make -j" and you can generally set it to "number of cores +1".

---

### Post by dmizer on 2008-08-28
> **vor said:**
> You could have a look at module-assistant:

```

sudo apt-get install module-assistant
man m-a

```

That may not do exactly what you want but, if you can't find a way to do it, if I remember right, I believe that kernel building HOWTO leaves out two very important compilation options.  Specifically, if you prepend:

```

INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 fakeroot make-kpkg ...

```

The INSTALL_MOD_STRIP not only drastically reduces compilation time (well, packaging time) but makes the installed kernel much, much smaller.  The CONCURRENCY_LEVEL is like "make -j" and you can generally set it to "number of cores +1".

I noticed that the resulting kernel seemed quite large.  I also noticed that there seem to be a couple of missing modules, one for sound and one for wireless.  Seems to be tolerably functional otherwise though. Not huge problems but given the overall experience, I'd rather do something a bit less invasive.

I'll take a look at module-assistant and see what I can do with that.  Man pages are good if you have a basic understanding of what needs to be done and how, but it's indescribably helpful going into a project like this to have a platform or template of some kind from which to base your own project.  That's what I'm really looking to get my hands on.

Edit:
Vor sent me this link: [http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402) over IRC. This is what ultimately solved my problem. Doesn't give me a deb, but it did teach me how to compile kernel modules individually so I can copy them to the current kernel.

Needs:
```
sudo depmod -a
```
to activate the new copied modules.

Thanks vor.

---

