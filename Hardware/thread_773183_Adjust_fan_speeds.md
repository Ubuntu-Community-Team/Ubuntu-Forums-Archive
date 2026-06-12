---
title: "Adjust fan speeds?"
date: 2008-04-28
forum: Hardware
---

### Post by oni5115 on 2008-04-28
A few days ago I was doing a bunch of stuff and I started having some weird issues.  So I decided to reboot and see if it would fix it.  After I rebooted, I noticed my conky display and my processor was a good 68C, and when I resumed doing things it went up to 70C before my fan boosted into overdrive and cooled it back down to 55C...

I was wondering if there is a way to set the fan threshold somehow so that it would kick into high speed at 60C instead of 70C.  I checked my BIOS to see if it was a setting in there, but have found nothing.

As a side note, even though this is a Laptop, I shouldn't be suffering from the Hardy issue with Pentium M processors, as I am still running 7.10 at the moment. (Apparently, Hardy doesn't support CPU throttling on Pentium M's atm.)  I have seen my CPU bounce between 800 MHZ and 2.0 GHz, so I doubt that is the issue.  Regardless, I'd still like to make sure my fan goes into high speed at 60 instead of 70.

---

### Post by Whiffle on 2008-04-28
what kind of laptop?

---

### Post by oni5115 on 2008-04-28
Dell XPS m170

---

### Post by olejorgen on 2008-04-28
My toshiba have NO way of controlling the fan. I tried dozens of programs in windows, and all the tosh* packages in ubuntu. Really lame.. the temp is reported as 35 celcius, and the fan is going at full speed.. Last time I buy toshiba.

---

### Post by Whiffle on 2008-04-29
I think you should be able to do it with the i8k kernel module, and the i8k-utils ( [http://packages.ubuntu.com/hardy/i8kutils](http://packages.ubuntu.com/hardy/i8kutils) ).  

[http://www.diefer.de/i8kfan/](http://www.diefer.de/i8kfan/)

---

### Post by oni5115 on 2008-05-03
Not really sure what to do with 18kutils (the i8kfans utility is now outdated I guess).

[http://people.debian.org/~dz/i8k/00-README](http://people.debian.org/~dz/i8k/00-README)

I installed the utils from Ubuntu's repositories, but it doesn't seem to work properly yet.  I tried running "cat /proc/i8k" as mentioned in the readme, but get "cat: /proc/i8k: No such file or directory" as a response.  Same goes for "i8kctl", which gives "can't open /proc/i8k: No such file or directory"

The older i8kfansGUI says that it works for XPS m170's.  The BIOS revision of mine is A05, which according to the newer readme seems to be functional in other models displayed with that revision number (Inspiron 2650, Latitude D600).

Since I technically have an XPS, does it simply not recognize it as an Inspiron model, and so it does not function?
> On loading the module checks for the presence of an Dell Inspiron or Latitude laptop and refuses to load if running on an unknown system. You can however force loading of the driver, for testing it on unknown hardware, by passing the "force=1" option to insmod:

    insmod i8k.o force=1

Should I try running that and see what happens?

---

