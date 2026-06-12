---
title: "Error After Compiling Kernel"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by piperdown10 on 2009-09-10
Recently I compiled my own kernel (2.6.30.5) and have been receiving an error in Terminal when running commands, especially apt-get. The error is as follows:
```
Errors were encountered while processing:
 linux-image-2.6.30.5-mk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Did the kernel not compile correctly? Have I gone to the bleeding edge by compiling such a new kernel? Is this going to effect my system?

Thanks all. :)

---

### Post by piperdown10 on 2009-09-17
So I figured out my error. When compiling the kernel, I was following directions from [this thread]("http://ubuntuforums.org/showthread.php?t=311158"). The command to compile the thread was broken up into two lines and if one copy/pastes the command, there's an enter between the first and second line causing the command to execute before the entire command is entered. When I typed it by hand, the error resolved.

---

