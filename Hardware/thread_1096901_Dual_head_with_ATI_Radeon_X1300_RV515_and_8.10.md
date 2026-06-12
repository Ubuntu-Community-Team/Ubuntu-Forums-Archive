---
title: "Dual head with ATI Radeon X1300 RV515 and 8.10"
date: 2009-03-15
forum: Hardware
---

### Post by billmania on 2009-03-15
Can anyone confirm that it is possible, with Intrepid Ibex 8.10 on a 64 bit Athlon Asus motherboard, to drive two analog monitors simultaneously and independently, with one ATI Radeon X1300 RV515 PCI Express 16 video interface? If you're doing that, would you mind posting the xorg.conf file and describing the specific version of the fglrx or radeon driver which you are using?

---

### Post by Neo_The_User on 2009-03-16
First install the drivers using the guide located on Page 2 of this thread.

[http://ubuntuforums.org/showthread.php?t=1091804&page=2](http://ubuntuforums.org/showthread.php?t=1091804&page=2)

To use dual monitors, open up a terminal and type in the following command and read up.

```

man aticonfig

```

Mix and match all the different variants of commands to do what you want followed by sudo. In example:

```

sudo aticonfig --crossfire --initial --dualhead --left-of-display 1 -f

```

Or something like that.

---

