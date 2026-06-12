---
title: "How to install my graphic drivers?"
date: 2009-04-05
forum: Hardware
---

### Post by soomro on 2009-04-05
well i have Intel graphic accelerator (forgot the name at the moment)
but how do i install them to my linux?

i searched here
system>administration>hardware drivers
but it did not show my any drivers

so now where i can get them?

---

### Post by cariboo on 2009-04-05
Depending on what version you are using, for Intrepid and better, the driver is built into the kernel and automagically gets loaded on startup.

Jim

---

### Post by soomro on 2009-04-05
> **cariboo907 said:**
> Depending on what version you are using, for Intrepid and better, the driver is built into the kernel and automagically gets loaded on startup.

Jim

Yes i have intrepid ibex.

but it still doesn't load?

---

### Post by starcannon on 2009-04-05
Please post in a codebox, the output of 
```
sudo lshw -C display
```
and the output of
```
glxinfo | grep direct
```

---

### Post by soomro on 2009-04-05
here
```

tassaduq@Lost-in-dreams:~$ sudo lshw -C display
[sudo] password for tassaduq: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
tassaduq@Lost-in-dreams:~$ 
```

and here

```
tassaduq@Lost-in-dreams:~$ glxinfo | grep direct
direct rendering: Yes
```

---

### Post by soomro on 2009-04-07
bump!

---

### Post by dolton on 2009-04-07
Hi,
In every system it has their own requirement of installing of graphic drivers.

---

### Post by mhgsys on 2009-04-07
Are you trying to enable compiz or something?
according to cariboo907 the driver is included, and google gets me lots of hits that there's no 3d 
f.e:
[http://ubuntuforums.org/showthread.php?t=1100761&highlight=Intel(R)+82945G](http://ubuntuforums.org/showthread.php?t=1100761&highlight=Intel(R)+82945G)

you could check Section "Device" in xorg.conf if there's a intel driver loaded.

```

sudo nano /etc/X11/xorg.conf

```

---

### Post by soomro on 2009-04-07
> **mhgsys said:**
> Are you trying to enable compiz or something?
according to cariboo907 the driver is included, and google gets me lots of hits that there's no 3d 
f.e:
[http://ubuntuforums.org/showthread.php?t=1100761&highlight=Intel(R)+82945G](http://ubuntuforums.org/showthread.php?t=1100761&highlight=Intel(R)+82945G)

you could check Section "Device" in xorg.conf if there's a intel driver loaded.

```

sudo nano /etc/X11/xorg.conf

```

no the compiz is already enabled and i can't find it in device manger. XD
what is that command for XD

---

### Post by mhgsys on 2009-04-07
Maybe I'm mistaken but your booting ubuntu 8.10 right?

Then why do you get: sorry try again
 when you put in 
```

sudo nano /etc/X11/xorg.conf

```
???

Doesn't it prompt for a password?

What happens if you put in 
```

sudo gedit /etc/X11/xorg.conf

```

Edit: I saw you edited your response, which make mine now useless I guess;
Anyway, the command is for viewing and editing the xorg.conf file.
nano is a editor, like vi(m), or gedit.

---

### Post by starcannon on 2009-04-07
Sorry, got busy; but checking back in, I see that Direct Rendering is reporting as enabled, and lshw shows that you have an Intel 82945G/GZ GPU; so, you should not need to install any additional drivers/modules to your system. Perhaps if we knew what your trying to achieve we could be of better assistance?

GL let us know how your getting along.

---

### Post by Psychopump on 2009-04-08
I have the same chipset with the same results.
On windows I could get higher resolutions than 10280x800, but now I am limited to this.
MAybe this is the same issue?
Any ideas?

---

### Post by mhgsys on 2009-04-11
> **Psychopump said:**
> I have the same chipset with the same results.
On windows I could get higher resolutions than 10280x800, but now I am limited to this.
MAybe this is the same issue?
Any ideas?

could you post your /etc/X11/xorg.conf?
```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by soomro on 2009-04-12
well sorry for late reply but when i am enabling certain effects in compiz like the zoom effect so when i click the effect my screen goes black on some areas like wallpaper and every thing except the buttons in my pannels and when i mouse over them they get black as well. so i thought it might be because of that?

---

