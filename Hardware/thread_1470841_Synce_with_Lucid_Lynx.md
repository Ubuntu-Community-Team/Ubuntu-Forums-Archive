---
title: "Synce with Lucid Lynx"
date: 2010-05-03
forum: Hardware
---

### Post by Frantique on 2010-05-03
Because HAL was removed from Lucid Lynx we cannot use anymore Synce for syncing our PDA-s running WM6. Does anyone knows how to bypass this problem?

---

### Post by gurukreff on 2010-05-12
I have the following problem with Synce:

```
marko@marko-desktop:~$ synce-pls

** (process:1497): CRITICAL **: synce_info_from_hal: Failed to initialise hal context: (null): (null)
process 1497: Attempt to remove filter function 0x7fee70783d90 user data 0x11b2e90, but no such filter has been added
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'
```


I've done everything that's mentioned in the Ubuntu installation guide in the Synce Wiki, just as i did in Karmic, it worked fine then, but now i can't get it to work.

I imagine it's got something to do with hal, but i checked synaptic and the package was installed, so i don't know what you mean. [Other people are having the same problem]("http://ubuntuforums.org/showthread.php?t=1324210&highlight=synce"), i posted there too with the hope that we could get some assistance...

Is there any way to fix this issue? :confused:

Thanks

---

### Post by dowcet on 2010-05-15
> **gurukreff said:**
> i checked synaptic and the package was installed

If you mean the "hal" package itself, that might not be enough. I think you also need the package called "synce-hal".

---

