---
title: "KVM PS/2 Problem"
date: 2009-04-05
forum: Hardware
---

### Post by dehyde on 2009-04-05
greetings..

I am using a belkin ps/2 KVM, between a windows system an an Ubuntu machine. Each time I switch back to Ubuntu my mouse goes crazy.

I haven't found any answer that works for that issue in the forums.

---

### Post by blackened on 2009-04-05
As you obviously know already, the problem is in your KVM preventing the OS from recognizing the hardware automatically.

The only solution I could imagine working would be to explicitly specify all of your hardware, including mouse and keyboard, in your xorg.conf so that it overrides the autorecognition system.

As a kick in the right direction, you might plug all the hardware straight into your Ubuntu machine, run it from a Live CD, then have a look at the xorg.conf generated during the live session for some pointers.

---

### Post by dehyde on 2009-04-05
What is the diffrence between running it from a Live CD or straight from the installed OS?

---

### Post by dehyde on 2009-04-05
ok I found this answer on the web, although I don't unerstand how to put it to practice...

[http://lkml.org/lkml/2005/11/9/47](http://lkml.org/lkml/2005/11/9/47)

any help would be appriciated

---

### Post by blackened on 2009-04-05
> **dehyde said:**
> ok I found this answer on the web, although I don't unerstand how to put it to practice...

[http://lkml.org/lkml/2005/11/9/47](http://lkml.org/lkml/2005/11/9/47)

any help would be appriciated

That looks like a proposed kernel module patch from more than 3 years ago. If it were going to be implemented, it probably would have by now, otherwise there may be problems with it.

I would first check out this solution, though it is old it is easily reversed if ineffective: [http://ubuntuforums.org/showpost.php?p=31721&postcount=2]("http://ubuntuforums.org/showpost.php?p=31721&postcount=2")

---

### Post by dehyde on 2009-04-05
It didn't do much.
It seems when i raise my optic mouse and put it back on my desk the pointer stops jumping around. I have to do this every time I switch back to Ubuntu..

---

