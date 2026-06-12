---
title: "Disabling Kernel Updates"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by beastrace91 on 2009-01-26
How can I go about disabling further Kernel updates? I just recently went through a headache of a process to recompile a custom kernel to get my ram working and I do not want to be doing this again any time soon.

Thanks,
~Jeff

---

### Post by beastrace91 on 2009-02-04
*bump* hello, anyone have any idea? I doubt I am the first one to compile a custom kernel who was looking to do this, it is annoying having to pick through the updates every day removing the kernel ones before I update the rest of my packages.

~Jeff

---

### Post by beastrace91 on 2009-02-17
Just popping it back up there again... no one seems to know... and google was less than helpful.

~Jeff

---

### Post by mltucker on 2009-02-17
I think what you're looking for is

```
sudo apt-get remove linux-generic linux-image-generic
```

> I was a little hesitant about giving this info out earlier, as this disconnects your eeepc from the mainstream ubuntu kernel development process. **It will keep the last generic kernel on your device** (useful for falling back incase there are problems with my eeepc version) but it should no longer force new generic kernels downstream.

from:

[http://forum.eeeuser.com/viewtopic.php?pid=300819](http://forum.eeeuser.com/viewtopic.php?pid=300819)

---

