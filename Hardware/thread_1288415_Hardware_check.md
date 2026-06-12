---
title: "Hardware check ?"
date: 2009-10-11
forum: Hardware
---

### Post by eric489 on 2009-10-11
Hi all ! :)

I'm new on ubuntu 9.04 and as a starter I'd like to know how one does to check the current system hardware configuration 

(what type of ram, cpu, gpu, mb and such ...) 

Do I need to install a third-party software to do the check up ? or has 9.04 an inbuilt feature ?

Thanks in advance !

---

### Post by khughitt on 2009-10-11
Hi eric,

There are a few quick ways you can find out information about your system:

1. Run "gnome-system-monitor" and look at the "system" tab. This will list information about your memory, and CPU(s).

2. Using the command-line:

```

more /proc/cpuinfo

```

and

```
free -m
```

3. hwinfo

Install:
```
sudo apt-get install hwinfo
```

To use you can simply run the command from the command line and get a huge amount of information. To limit the information, specify the component which you want to learn more about, e.g:

```
hwinfo --gfxcard
```

You can get a list of the different components that you can lookup using "hwinfo --help".

Goodluck!

---

### Post by antonkedrov on 2009-10-11
also you can use lspci command to see your devices

---

### Post by diesch on 2009-10-11
hardinfo (not installed by default, but you can install it via Synaptic) is a nice GUI tool

---

### Post by khughitt on 2009-10-11
> **diesch said:**
> hardinfo (not installed by default, but you can install it via Synaptic) is a nice GUI tool

Very cool. I've been looking for something like that for a long time. Thanks for sharing :)

---

### Post by technosysind on 2011-09-19
install sysinfo from Ubuntu Software Center

---

