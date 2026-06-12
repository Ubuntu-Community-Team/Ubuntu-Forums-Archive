---
title: "grub more colors during boot"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by aeltester on 2009-06-21
Hey guys,

back on openSUSE 10 and I think Mandriva 2007 as well, the [OK]s during boot were green and the [FAILED] were red.

Nowadays, when I put something like this:
kernel      /boot/vmlinuz-2.6.27-14-generic root=/dev/sda2 ro vga=798
into my menu.lst, all the text is just plain white.

How can I achieve the nice colors?

thanks
:P

---

### Post by drs305 on 2009-06-21
You can use StartUp-Manager to change the boot menu text color and background. There are links in my signature line to a thread and also the wiki on how to install SUM and explains all the options.

```

sudo apt-get install startupmanager
gksudo startupmanager #  or System, Administration, StartUp-Manager. Go to Appearance tab.

```

---

### Post by aeltester on 2009-06-21
thanks!

managed it by modifying lsb-base-logging.sh.

have a great day
:P

---

### Post by ajgreeny on 2009-06-21
Just out of interest, what were the edits you made?  I notice that the file you mention is not actually executable in my system, so wonder if all you did was enable execution of the file.

I'm just curious, and it is of little importance, but this is the way I've learned so much about linux and ubuntu in particular, just by asking questions.

---

### Post by raymondh on 2009-06-21
> **ajgreeny said:**
> I notice that the file you mention is not actually executable in my system, so wonder if all you did was enable execution of the file

me too ... I'm also curious.

---

