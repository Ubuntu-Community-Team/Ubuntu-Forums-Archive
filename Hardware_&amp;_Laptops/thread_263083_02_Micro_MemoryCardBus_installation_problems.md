---
title: "02 Micro MemoryCardBus installation problems"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by CELI-Nux on 2006-09-22
Hi there,

I've downloaded the above mentioned driver from [http://www.musclecard.com](http://www.musclecard.com).  I then proceeded with the pre-requisite installation of pcsclite-<latest_version> from [http://pcsclite.alioth.debian.org](http://pcsclite.alioth.debian.org) (which, by the way, needed another pre-requisite from Synaptic which wasn't mentioned - "libusb-dev").

Unfortunately, somewhere down the ./configure-release shell script is a line looking for:

- if test -d /lib/modules/$act_kern/build/include (where $act_kern is a variable declared as act_kern='uname-r' at the beginning of the script)

As you have guessed the /lib/modules/2.6.15-27-386 doesn't contain any '/build/include' sub-directory.

Hence, my question is: How/where do I get the necessary files? Is there a Synaptic package I'm missing and if so, which one? Would a symbolic link do the trick? If so, what would be the appropriate syntax? Hellllllllp!


Regards

(P.S.: I do have the necessary packages to normally compile, make and make install).

---

### Post by CELI-Nux on 2006-09-24
There was an error in my last post.  Note muscle.com but [www.musclecard.com](www.musclecard.com)

Regards

---

### Post by gdoutch on 2007-10-26
Did you ever get a fix for this? if so, how?

---

