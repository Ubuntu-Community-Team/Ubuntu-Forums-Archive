---
title: "How do i can Turn ON or OFF or Restart dev ?"
date: 2008-12-12
forum: Hardware
---

### Post by Vahids on 2008-12-12
How do i can Turn ON or OFF or Restart a dev ?
for example /dev/dvb/0net ;)

i want to restart a PCI card?! how do i can do it,:KS

---

### Post by sdennie on 2008-12-12
Usually you can do this by removing the kernel module that controls the card.  You may be able to figure out the module name using:

```

sudo lshw

```

Then, to remove it, try:

```

sudo modprobe -r name_of_module

```

---

### Post by Vahids on 2008-12-12
> **vor said:**
> Usually you can do this by removing the kernel module that controls the card.  You may be able to figure out the module name using:

```

sudo lshw

```

Then, to remove it, try:

```

sudo modprobe -r name_of_module

```
Error:
> 
sudo modprobe -r b2c2_flexcop
FATAL: Module b2c2_flexcop is in use.

---

### Post by sdennie on 2008-12-12
> 
Error:

```

sudo modprobe -r b2c2_flexcop
FATAL: Module b2c2_flexcop is in use. 

```


If any program or other kernel module is currently using the module you want to remove, you'll get that error.  A good example of this is if you have the volume applet sitting on your gnome panel, it's impossible to remove your sound drivers because the applet has them "open".  There may be a way to determine what applications are using a particular driver but, I don't know of it.  To determine if other drivers are using the thing you want to remove, try:

```

lsmod | grep thing_you_want_to_remove

```

---

### Post by Vahids on 2008-12-12
> **vor said:**
> If any program or other kernel module is currently using the module you want to remove, you'll get that error.  A good example of this is if you have the volume applet sitting on your gnome panel, it's impossible to remove your sound drivers because the applet has them "open".  There may be a way to determine what applications are using a particular driver but, I don't know of it.  To determine if other drivers are using the thing you want to remove, try:

```

lsmod | grep thing_you_want_to_remove

```
Thanks alot..... WORKED ;)
and now, how do i can start that module again???

---

### Post by Vahids on 2008-12-12
> **vor said:**
> If any program or other kernel module is currently using the module you want to remove, you'll get that error.  A good example of this is if you have the volume applet sitting on your gnome panel, it's impossible to remove your sound drivers because the applet has them "open".  There may be a way to determine what applications are using a particular driver but, I don't know of it.  To determine if other drivers are using the thing you want to remove, try:

```

lsmod | grep thing_you_want_to_remove

``` 
Thanks alot..... WORKED ;) 
and now, how do i can start that module again???


---------------------
EDIT:
---------------------
Thanks i understand it, i must to use 
> sudo modprobe
without -r

:guitar:

---

