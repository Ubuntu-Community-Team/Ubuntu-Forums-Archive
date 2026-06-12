---
title: "dell inspiron 2200 fan problems"
date: 2011-06-14
forum: Hardware
---

### Post by pmancini100 on 2011-06-14
hello everyone,

this is my first post on the ubuntu forums.  i have recently begun converting my old laptop over to ubuntu, and it has been pretty smooth up to this point.  my computer has been overheating, so i looked for other threads here that would help.  i found a couple of threads concerning my dell inspiron 2200, but it seems they were dealing with earlier forms of ubuntu.  i decided to download the gkrellm 2.x program so i can install the dell i8k plugin, and have full control of the fans.  however, when i get to the compiling part of the process, i am somewhat lost.  i cant seem to install the plugin so i can select it from the gkrellm menu.  i dont know what a kernel is.  please help me.  i am scared.

---

### Post by pmancini100 on 2011-06-20
<cough>

bump.

<cough>

anyway, i found out how to manually control the fans in the terminal.  i feel like this is a temporary fix.  still lost on the gkrellm compiling process, would really appreciate some help on this one.  did i mention how much i love you guys?

---

### Post by faceonline on 2011-06-20
hey, 

Could be something to do with Linux booting up without explicitly setting your ACPI config... or something like that.

Before doing stuff with gkrellm, try doing 

```
sudo gedit /etc/default/grub
```

Assuming you're usung 10.04 or later

find the line which says:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and change it to 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
```

Seemed to sort out fan issues for me... 

If it doesn't, then you can do something like installing lm-sensors and some other voodoo that I don't really understand.

Hope this helps!

---

### Post by pmancini100 on 2011-06-21
thanks for getting back to me!  i just did what you suggested.  how does it sort out fan issues?  can i control them now?  set temperatures and whatnot?

---

### Post by faceonline on 2011-06-22
Hey, it doesn't let you control the fans per-se, only allows your BIOS to utilise ACPI. Apparently some BIOSes want to know if they're running under Windows or not. This tells them that they're running under Linux.

I think :)

[See here for more info]("http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do")

EDIT:

I haven't quite answered your question. Setting the proper ACPI configuration means that Linux will actively (or passively) regulate your CPU fan speed, so when your CPU gets to about 60 degrees C, the fans should kick in until it gets to a more dignified temperature

---

### Post by pmancini100 on 2011-06-22
i'll see if it works out, thanks for the help man

---

### Post by mikeleonard on 2011-06-23
Same Problem I also faced with My Dell  Laptop .It make a lot of noise .You have to Submit your Laptop to Dell Services Center . it is Because of Dust.

---

### Post by pmancini100 on 2011-06-30
so my bios seems to work now, and my fans magically turn on by themselves!  however, the computer is still pretty hot.  any idea of what i should do?

---

