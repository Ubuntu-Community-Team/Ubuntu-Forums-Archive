---
title: "dpkg --configure -a"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by jtmedin on 2009-08-27
ran update manager & go 64m of updates
After loading all the files it hung about half way thru the instllation

Turned off power (no other way) & restarted.
Got a msg about installation failure & sugested: sudo dpkg --configure -a

That fails right away so what do i do now? TIA

---

### Post by LowSky on 2009-08-27
the command is actually

```
sudo dpkg -configure --a
```

you have your dashes mixed up.

---

### Post by jtmedin on 2009-08-27
> **LowSky said:**
> the command is actually

```
sudo dpkg -configure --a
```

you have your dashes mixed up.
sorry think i had the dashes correct. However, 'sudo dpkg -config --a' produces o option unknown :-(. Tried 'sudo dpkg -configure --a' produced the same :-(

---

### Post by ronparent on 2009-08-27
Are you all completely mixed up now? :)

The o response is posted when you use only one dash on configure.

The correct command is : **sudo dpkg --configure -a**

Considering the hard boot, it may not work.

---

### Post by jtmedin on 2009-08-27
> **ronparent said:**
> Are you all completely mixed up now? :)

The o response is posted when you use only one dash on configure.

The correct command is : **sudo dpkg --configure -a**

Considering the hard boot, it may not work.
Thats what i did first the changes in dashes was responding to sugestions.

---

### Post by jtmedin on 2009-08-27
Looks like a reinstall :(.

---

### Post by lisati on 2009-08-27
> **ronparent said:**
> 
The correct command is : ```
sudo dpkg --configure -a
```

+1
> **jtmedin said:**
> Thats what i did first the changes in dashes was responding to sugestions.
Do you remember the error message(s) & other information that popped up?

---

### Post by jtmedin on 2009-08-28
Yes the warning said something about Gnome configure immediately after the boot & when i started update mgr thats when it got the 'sudo dpkg --configure -a' or close to that.

---

### Post by sandy4linux on 2009-08-29
Since the update was interrupted,restart your system.

Press escape when grub loads. Enter in to Root shell..
type this command,

sudo dpkg --configure -a

if it doesn't fix your problem, instead of going to Root shell, enter DPKG and you need to have you  DSL Connected, so that it could download necessary broken files.

Regards

LINUX- The Revolutionary Human Chain

---

### Post by jtmedin on 2009-08-29
> **sandy4linux said:**
> Since the update was interrupted,restart your system.

Press escape when grub loads. Enter in to Root shell..
type this command,

sudo dpkg --configure -a

if it doesn't fix your problem, instead of going to Root shell, enter DPKG and you need to have you  DSL Connected, so that it could download necessary broken files.

Regards

LINUX- The Revolutionary Human Chain
need some help in getting into root shell. When grub begins to load i press esc & get the menu with 4 levels of ubuntu with their recoveries. now what do i do?

---

### Post by stlsaint on 2009-08-29
choose the recovery option mode for the kernel you are currently using and you will see all options from there.

---

### Post by sandy4linux on 2009-08-30
Enter recovery mode for latest kernal version..

You will get in to Recovery menu..

In order to get in to Root shell, enter the ROOT tab (6th Tab i guess)..
type the following command.

sudo dpkg --configure -a

Still you have issues then,

repeat the same procedure..

Instead of ROOT shell..Enter DPKG...

I hope this may fix the issues..

Regards

---

