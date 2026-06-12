---
title: "Homeline (RTL8180 Chipset) WLAN driver setup"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by encompass on 2005-12-20
I have the RTL8180 chipset in my wlan card... it worked fin with the Open source driver from [here/]("http://rtl8180-sa2400.sourceforge.net/") when I was using debian's latest.  But with ubuntu and the new kernel I can't use the card at all.  I tried getting the cvs of the new driver whic is supposed to work and couldn't figure it out.  I then tried emailing the created to no avail.  I have tried many times to use the ndiswrapper too, but can't seem to get that working either.  If someone could help me here.  I would much appreciate it.
Thanks for your time...
Any questions I can answer... so please email me or IM me.

---

### Post by Danila on 2005-12-20
I got my rtl8180 based PCMCIA card working by building the driver from the CVS sources. For compiling the driver you need gcc-3.4 so make sure to install it first if not done yet.
Get the sources with
```

cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/rtl8180-sa2400 login
 
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/rtl8180-sa2400 co -P rtl8180-sa2400-dev

```

and execute
```

cd rtl8180-sa2400-dev
make
sudo ./module_load

```

Now it should be possible to configure the card with the "network-manager" from the gnome system-menu.

The following lines I found on the German Ubuntu-WiKi sites, they should make the modules loading at the system start.
```

sudo mkdir /lib/modules/`uname -r`/kernel/drivers/net/wireless/rtl8180
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rtl8180/

```

For some reasons, my card is not beeing activated while booting the system, so I had to press Ctrl+C two times, when the card should be activated. But it is possible to activate the card with the "Network-Manager" without problems. Maybe someone can help to solve this problem...

---

### Post by encompass on 2005-12-20
cool, I couldn't get the cvs, I am not used to that stuff yet.
I jsut tried a different forum thred about a debian package and it looks like it is working now.  at least the light is blinking... so I think it is working.  I will be trying it as soon as I get to school that has wireless.
Thanks though, it helps to have people so willing to help.

I think I am going to make this as SOLVED!

---

### Post by mikaPELL on 2006-02-05
Hey guys, I tried to follow Danila's instructions, but it doesn't seem to work for me. When i run make after getting the files from the cvs, all I get is this:
```
make: *** No rule to make target `/lib/modules/2.6.12-10-386/build/.config'.  Stop.

```
Any ideas?

---

### Post by mikaPELL on 2006-02-06
Never mind, it seems that 14 hours of sleeping did the trick :P

---

