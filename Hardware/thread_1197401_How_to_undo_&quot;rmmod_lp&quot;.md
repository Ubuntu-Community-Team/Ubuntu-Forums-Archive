---
title: "How to undo &quot;rmmod lp&quot;?"
date: 2009-06-26
forum: Hardware
---

### Post by ario on 2009-06-26
Hi
I accidentally ran the command:
```

sudo rmmod lp

```
so the lp kernel module removed from my kernel.
Are there Anyone knows how to undo that?
Thanks for your attention guys.

---

### Post by keplerspeed on 2009-06-26
EDIT: See sisco's post. Please use modprobe in this case.

Well:

```

sudo insmod lp

```

To load the module into the kernel.

---

### Post by sisco311 on 2009-06-26
```
sudo modprobe lp
```
or reboot the computer.

---

### Post by ario on 2009-06-26
Thanks a lot sisco. I tried that. But it showed me this:
```
insmod: can't read 'lp': No such file or directory

```
So where "lp" must be? I think I must first "cd" to the directory of my kernel modules and then install one of them. If so, Where lp and other kernel modules are?
Thanks for you attention again:)

---

### Post by sisco311 on 2009-06-26
just use the modprobe command instead of insmod.

---

### Post by keplerspeed on 2009-06-26
```

insmod *filename*

```

Is used to add a module independently (for example one that doesnt load on boot), and you muse edit /etc/modules to load a newly added module on boot . Modprobe is the best option for this case, as modprobe will reload the removed lp module. IF you look at /etc/modules, it contains lp.

---

### Post by ario on 2009-06-28
Thanks guys.
I used "modprobe lp" as you said, But it returns nothing to me. Is it ok?
I seen "/etc/modules" file. It contains "lp", So it seems that my ubuntu still loads "lp" at boot time.
So I think the main problem is **SOLVED**.:D 
---------------------
No its not solved yet!

---

### Post by ario on 2009-07-10
Hi guys.
I tried all you said. my /etc/modules contains "lp" in it. but I cant see any file like "lp" or "parport0" in my /dev directory.
The parallel port completely removed from my ubuntu and I don't now how to bring it back.
Please help me.
Thanks for your attention.

---

### Post by ario on 2010-10-02
No matter what I do, Linux will not recognize my Printer port. I can not see any partport0 or lp file in /dev directory.
Any help?

---

### Post by ario on 2010-11-09
Bump!

---

### Post by Yellow Pasque on 2010-11-09
Is your parallel port enabled in the BIOS?

---

### Post by ario on 2010-11-10
> **Temüjin said:**
> Is your parallel port enabled in the BIOS?

Yes. I must add that I need Parallel port for programming micro-controller chips. Right now I use to reboot to windows, start codevision software, and program my chip, and the parallel port works well there:( Which is annoying!
Any Idea?

---

### Post by ario on 2010-11-16
BUMP!
-----------------------
Ubuntu 10.04 32bit parallel port isn't detected! :(

---

### Post by ario on 2010-11-23
Any Idea?

---

### Post by Yellow Pasque on 2010-11-23
Does *lspci -vv* see the parallel port?

---

