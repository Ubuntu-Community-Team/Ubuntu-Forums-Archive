---
title: "ATI Guide for 5770.... terrible performance"
date: 2010-06-21
forum: Hardware
---

### Post by phr0ze on 2010-06-21
Hi all, 
I got a new HD 5770, that I would love to keep but I have terrible performance.

is there a 10.04 install guide for doing ATI the right way?

I've tried google.

Second, how do I strip out the drivers I d/l from the ATI site and kinda start again without reinstalling?

Thanks,
John

---

### Post by Yellow Pasque on 2010-06-21
Run the uninstaller and purge all of the fglrx packages Ubuntu installed (if any): [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)
Then try "manually installing the drivers" again. Please let us/me know how it works since I just wrote that guide (actually, I adapted it from the Jaunty guide because I'm laz..err, energy-efficient ;) ).

---

### Post by phr0ze on 2010-06-22
I did the removal guide, but then the restricted hardware screen would not offer the restricted driver. I think there was a missing helper package.

However, instead of installing manually, I used this PPA ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)) which is kept fairly up to date. (latest 10.6 driver but much better performance.)

My computer is now usable enough to keep the video card.

---

### Post by Yellow Pasque on 2010-06-22
> I did the removal guide, but then the restricted hardware screen would not offer the restricted driver. I think there was a missing helper package.
Ah. That's because the command removes fglrx-modaliases package. Thank you for finding that.

---

### Post by phr0ze on 2010-06-22
No problem. Perhaps offer up the PPA as an installation alternative in your guide?

---

### Post by Yellow Pasque on 2010-06-22
> **phr0ze said:**
> No problem. Perhaps offer up the PPA as an installation alternative in your guide?
Done, and fixed the removal procedure. Thanks again.

---

