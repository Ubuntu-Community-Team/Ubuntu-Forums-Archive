---
title: "Nvidia API MisMatch Terror"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by ronniew on 2007-05-06
I have tried everything i can find in these forums about how to fix the nvidia kernel module api mismatch error and nothing works... It seems I am stuck with nvidia-glx-legacy

this is the xserver error I encounter when trying to use the correct nvidia-glx for my card

Error: API mismatch: the NVIDIA kernel module has the version 1.0-7184, but
this client has the version 1.0-9631.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.


It doesn matter what directions or suggestion I follow I always get the same error..

This is my card in my machine

 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)

Someone please help I am unable to find a solution anywhere on the forums or in irc for this crazy error

---

### Post by ronniew on 2007-05-06
OK here is the solution which worked for me

i went into the 

/lib/linux-restricted-modules

directory and deleted everything but the

2.6.20-15-generic  directory (i'm sure that directory name will change with kernel updates)

there where two files in there one relating to the nvidia legacy driver and one relating to the nvidia new driver  i deleted them both and 

happy happy joy joy

hope this helps

i was stump for days on this one

---

### Post by casperlingus on 2007-05-08
I found out that removing and then reinserting the nvidia module was sufficient to start X again

```
~$ startx      # API MISMATCH ERROR
~$ rmmod nvidia
~$ modprobe nvidia
~$ startx      # SUCCESS!
```

Noticing that was all I needed to do, I modified /etc/init.d/gdm and added those two lines at the beginning.  It works!

Of course, I modified /etc/init.d/gdm which is a pretty important system file.  Was this safe to do?  This is not the most elegant solution, I am aware.

Thoughts?

-Casper

P.S. - I found this post AFTER I fixed my system like this.  Perhaps my solution will be more stable...??

---

### Post by bagbiter on 2007-05-11
I have an API mismatch error.

here's my output:

```

rc  nvidia-glx                                 **1.0.9631**+2.6.20.5-15.20                NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-glx-new                             **1.0.9755**+2.6.20.5-15.20                NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files

```

what should I do?

---

### Post by casperlingus on 2007-05-15
You haven't given me enough information to tell what your problem is...

Does X not start?  Do you just have really poor graphics?  How do you think you ended up with a version mismatch like this?  Did you try installing the latest nvidia drivers without first uninstalling the old ones?  Where did you even get nvidia-glx-new?

If X doesn't start and you are sent to the terminal, have you tried rmmod/modprobe nvidia like I did?

Try purging your nvidia driver installs:

```

sudo apt-get remove nvidia-glx-new --purge
sudo apt-get install nvidia-glx
sudo apt-get remove nvidia-glx --purge
```

then reinstalling the nvidia drivers the way you did originally.

I can't help you much beyond that at this point.   Hope that helps.
-Casper

---

