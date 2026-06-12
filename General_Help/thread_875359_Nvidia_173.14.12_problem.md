---
title: "Nvidia 173.14.12 problem"
date: 2008-07-30
forum: General Help
---

### Post by shamusl on 2008-07-30
A new nvidia driver was released today, so I downloaded it, stopped xserver and ran:
```

sudo sh /home/shamus/Desktop/NVIDIA-Linux-x86-173-14-12.run

```

After that it returns the error:
```

ERROR: You do not appear to have libc header file installed on your system. Please install your distributions libc development package.

```

Does anyone know where to get this package?
(apt-get install libc doesn't work)

---

### Post by hardyn on 2008-07-30
apt-get install build-essentials

you might need the kernel source too.


before you go an do all that work, is there a feature that that release you need?

---

### Post by kuja on 2008-07-30
You'll also need to ```
sudo apt-get install linux-headers-`uname -r`
```

and edit the /etc/default/linu<TAB> and add "nv" to the disabled line at the bottom of the file.

---

### Post by shamusl on 2008-07-30
> **hardyn said:**
> apt-get install build-essentials

you might need the kernel source too.


before you go an do all that work, is there a feature that that release you need?

I have an 8800gt, and in the release notes it says that it clears up some bugs with my card. Why is there something wrong with updating merely for the sake of being up to date?

EDIT:
This is what I get when I try to install build-essentials
```


shamus@shamus-desktop:~$ sudo apt-get install build-essentials
[sudo] password for shamus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials

```

---

### Post by shamusl on 2008-07-30
Bump for GREAT justice.

---

### Post by drs305 on 2008-07-30
```
sudo apt-get install build-essential
```

No S.

---

### Post by kuja on 2008-07-31
In other news, I'm surprised nobody mentioned that you could just grab it with envyng ...

```

sudo apt-get install envyng
sudo envyng -t

```

---

### Post by cfvh600 on 2008-08-27
Hi people sorry to be a pain but I get the following error message when trying to get the libc header files:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

Please help!

---

### Post by cfvh600 on 2008-08-27
Update: I think I've fixed it. I've reloaded the package list in Synaptic cause everything was marked as being installed. After that I could install the libc header files in Synaptic. Yay!

---

### Post by cfvh600 on 2008-08-27
Update: I think I've fixed it. I've reloaded the package list in Synaptic cause everything was marked as being installed. After that I could install the libc header files in Synaptic. Yay!

---

