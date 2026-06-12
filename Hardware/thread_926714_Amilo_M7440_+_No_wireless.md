---
title: "Amilo M7440 + No wireless"
date: 2008-09-22
forum: Hardware
---

### Post by tinhat42 on 2008-09-22
Total Neby to Ubuntu)
I've bitten the bullet and loaded Ubuntu 8.04 onto my laptop (FS Amilo M7440)
Mostly it all works except that I cannot turn the wireless on.
The switch that I normally use with windows is inoperable and although I've checked the bios and wireless is enabled I just cannot get any link.
Also I note that the wirelss network information (I've studiously copied it from the window section) is still OK
Although the drop downs will not allow a search for networks and the help file instructs.
Please note I did have a problem with logging on as the 'set logon screen just flashed on then off and I had to go in via the 'dos' prompt.

---

### Post by hunmatt on 2008-10-29
the solution is here: [http://fsam7440.sourceforge.net](http://fsam7440.sourceforge.net)
download, extract, make, make install

it worked for me on previous ubuntu. now I installed gOS and it wont work :(
could anybody help please?

I get this error message when I'd like to compile the module:
[I]
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/matt/fsam7440-0.4 modules
/usr/src/linux-headers-2.6.24-19-generic/scripts/gcc-version.sh: line 22: gcc: command not found
/usr/src/linux-headers-2.6.24-19-generic/scripts/gcc-version.sh: line 23: gcc: command not found
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/matt/fsam7440-0.4/fsam7440.o
/bin/sh: gcc: not found
make[2]: *** [/home/matt/fsam7440-0.4/fsam7440.o] Error 127
make[1]: *** [_module_/home/matt/fsam7440-0.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
[/I]

can it be because I dont have a swap partition? 
although there is 1Gb ram...

please help!
Thanks!
Matt

---

### Post by The2DQuartet on 2008-11-15
> gcc: command not found

You need to install GCC, which I believe may stand for Gnome C Compiler. It is included with Ubuntu Hardy & Intrepid, not sure about previous releases although it looks like gOS does not include it.

It should be very simple to fix, although you will of course need a network connection. Just run the following command:

```
sudo apt-get install gcc
```

I hope this helps!

---

