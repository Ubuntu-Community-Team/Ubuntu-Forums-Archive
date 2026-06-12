---
title: "Linux Swap for Suspend"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by Kingsley on 2007-06-09
I recently bought a laptop and installed Ubuntu. When I want to save power, I'm unable to suspend. It gives me an error message about insufficient swap space. 

Right now I have 2gb of RAM and around 256mb swap. What should I increase the swap  size to?

---

### Post by PhatStreet on 2007-06-09
Generally the rule is 2x your RAM, but I dunno if you have 2 GBs... I guess you could do 4 GBs anyways, just to be safe.

---

### Post by Kingsley on 2007-06-09
Alright, I may format and try that method.

---

### Post by Chevhq on 2007-06-10
When you save to Hibernate, you need enough space to cover the entire ram installed plust about 20% for the file information etc

If you ahve a windows partition, then you can check the diskspace necessay by using explorer
cheers Chris T

---

### Post by 444 on 2007-06-10
2x ram rule is outdated.

Try 1gb. Of course if you end up using more than 1gb memory one day then it'll fail. But that will *always* be a possibility, no matter how much swap you have, although the more swap the less likely it is.

---

### Post by neptho on 2007-06-10
> **444 said:**
> 2x ram rule is outdated.

It's true that most of the kernel RAM is used for buffers these days. but why would you cut yourself short in the off chance you left FireFox running too long, or liked to use Emacs.  ;)

---

### Post by 444 on 2007-06-10
> **neptho said:**
> It's true that most of the kernel RAM is used for buffers these days. but why would you cut yourself short in the off chance you left FireFox running too long, or liked to use Emacs.  ;)

More swap = more space for firefox to take up. So firefox can theoretically gulp down 6gb (2gb ram + 4gb swap), making hibernate fail. Then you end up in an inifinite loop of adding more swap :P.

---

