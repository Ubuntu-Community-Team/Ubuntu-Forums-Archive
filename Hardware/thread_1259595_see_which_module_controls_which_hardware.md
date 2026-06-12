---
title: "see which module controls which hardware"
date: 2009-09-06
forum: Hardware
---

### Post by pythonscript on 2009-09-06
Is there a way to see which module(s) controls a certain piece of hardware? I'm trying to minimize my laptop, and I'd like to know what controls what. I'd like to only load the modules I need when I need them. Any ideas? For example, if I search for "webcam" it'll turn up all the modules that control my webcam. I'm looking for a 100% command line solution, too. Thanks!

---

### Post by Whiffle on 2009-09-06
Do you want this to be automatic?  Or is this just a one time deal?  Alot of modules are loaded automatically.  For example, unplug your webcam, then plug it in, run "dmesg" or "lsmod", and it'll show you which module loaded.  Unplug it and run those again and it will tell you if the module was unloaded.

---

### Post by pythonscript on 2009-09-06
I'd like to know so that if I decide to unload them, I'll know which ones to unload. This way, I can write a script that will load all the modules I need for that piece of hardware, then simply run the script when I need to use that piece of hardware and never else. Also, this is a laptop, so unplugging most of the hardware is kind of difficult...

---

### Post by Whiffle on 2009-09-06
Oh i see.  I think I would probably boot the laptop up as normal, run lsmod, and then look up the modules here: [http://hardware4linux.info/modules/](http://hardware4linux.info/modules/)

---

### Post by pythonscript on 2009-09-06
Is that link a complete list? I looked up the first three modules on the list: binfmt_msc, ppdev, and bridge, and none of them were on that list.

---

### Post by Bachstelze on 2009-09-06
> **pythonscript said:**
> Is there a way to see which module(s) controls a certain piece of hardware?

```
lspci -k
```

---

### Post by Whiffle on 2009-09-06
> **HymnToLife said:**
> ```
lspci -k
```

Learn something new every day.  *smacks forehead*

---

### Post by pythonscript on 2009-09-06
> **HymnToLife said:**
> ```
lspci -k
```

That works great. As Whiffle said, learn something new every day; it's what I love about the forums.

---

