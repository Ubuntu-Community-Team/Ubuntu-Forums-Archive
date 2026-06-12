---
title: "Any opionions / ideas AMD64 Dual Core SLOW"
date: 2009-04-22
forum: Hardware
---

### Post by niehaoma on 2009-04-22
I apologize if this has been hashed out already. I am returning to Linux after years away, and I just loaded Ubuntu  64 bit, and then 32 bit onto my:

Dell Laptop Inspiron 1721
AMD64 Dual Core Proc 2.3 GHz
4GB of RAM
160GB SCSI HDe

It just seems perplexing to me how SLOW it runs. In slow, I mean screen refresh, app startup, Firefox, generally everything. I am reading and reading through forums, but I wanted to try and find out if other people are experiencing this in general, is this just Ubuntu 8.10, or is it tied to the AMD 64 architecture? Thanks in advance.

---

### Post by Sam Lars on 2009-04-24
Screen refresh and some other things would be more affected by your graphics card... do you know what kind you have?
The output of
```
lspci | grep VGA
```
in a terminal should tell you.

---

### Post by niehaoma on 2009-04-26
I have an ATI card: (ATI Technologies Inc RS690M ) I am using the fglrx driver, but I also tried the Ubuntu driver. Is this card / ATI driver just not well supported?

I know i recently was going to attempt to load 9.04, and it stated that the fglrx driver isnt supported at all.

---

