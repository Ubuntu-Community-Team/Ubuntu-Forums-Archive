---
title: "config_hz_1000 in gutsy"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by asipi on 2007-10-28
Hi all,

I am an Enemy Territory player and have mouse lags often. I digged up the net if there is any info about my problem and found an idea.
It says set config_hz_1000=y and config_hz=1000 or 500.

My question is:
Does gutsy kernel has been compiled to use this options?
I am very unfamiliar with setting the kernel parameters and I am not brave enough to try it out.

I am using the "factory" gutsy kernel 2.6.22-14-generic

Thx for any help.

---

### Post by 444 on 2007-10-28
```

$ cat /boot/config-2.6.22-14-generic | grep CONFIG_HZ
# CONFIG_HZ_1000 is not set
# CONFIG_HZ_300 is not set
CONFIG_HZ=250
# CONFIG_HZ_100 is not set
CONFIG_HZ_250=y

```

As you can see it's set to 250.

---

### Post by asipi on 2007-10-29
Thx I also found the 250, my question was that is it ok to set:
```
config_hz_1000=y
config_hz=1000
```

Could my system boot with the above settings?

---

### Post by 5-HT on 2007-10-29
> **asipi said:**
> Thx I also found the 250, my question was that is it ok to set:
```
config_hz_1000=y
config_hz=1000
```Could my system boot with the above settings?
It's absolutely fine to set it. I wouldn't go any higher than 1000 Hz myself, but therere are options for that as well.
cheers,

---

### Post by 444 on 2007-10-29
Well it'll work fine, but it's not as simple as just changing the values in the file. You will have to completely recompile the kernel to change that setting.

---

### Post by asipi on 2007-10-29
so the "factory" kernel has been compiled with this option disabled?
omg, bad news
but if I recompile the kernel should I have to make new initrd too?

---

### Post by 444 on 2007-10-29
Yep :/

Here's an Ubuntu kernel howto:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

So you'd load up the .config file with all the Ubuntu settings, then you'd just change the config_hz (Processor Type...->Timer Frequency in menuconfig) setting.

The initrd is made as part of those instructions as well. And of course the kernel version (and thus filenames, like blah-2.6.22 vs blah-2.6.19) are different.

---

### Post by asipi on 2007-11-01
thx I try to do it, but never tried before...
will refer here about the results and success

---

### Post by asipi on 2007-11-01
kernel finished :) my first kernel compilation 
but the problem is still there, wasn't a solution for it
the starting up is a bit longer now with htis kernel anyway...

---

