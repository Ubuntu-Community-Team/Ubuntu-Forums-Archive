---
title: "[SOLVED] Packages needed to compile a kernel"
date: 2008-08-04
forum: General Help
---

### Post by Jordanwb on 2008-08-04
I cam back from Gentoo, finding it to be very annoying, and not having good documentation for configuring apache, so I came back to Ubuntu. I installed lvm2, but lvm wasn't included in the kernel that was installed. So I want to compile my own kernel to include lvm and get rid of stuff I don't need. Beside the build-essential package(and it's dependancies), what else do I to compile a kernel?

[Solved]

build-essential and libncurses5-dev

---

### Post by kellemes on 2008-08-04
```
sudo apt-get install libncurses5 libncurses5-dev
```

[More info.]("https://help.ubuntu.com/community/Kernel/Compile")

---

### Post by Jordanwb on 2008-08-04
I removed 80% of the stuff that's included in the Ubuntu kernel, token ring for crying out loud! AppleTalk! Who uses this stuff? Is there someplace where I can get a more descriptive description of the stuff included in the kernel?

---

