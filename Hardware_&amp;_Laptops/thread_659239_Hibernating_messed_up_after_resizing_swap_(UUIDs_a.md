---
title: "Hibernating messed up after resizing swap (UUIDs are changing)"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by vidak on 2008-01-05
Hi all!
I've bought some RAM for my laptop, and decided to add some more swap space. The resizing went OK, but the swap partition didn't activate. I changed /etc/fstab to contain
/dev/sda2        swap            swap    defaults              0       0
instead of the old UUID. Now swap was working, but hibernating seems to fail all the time. While booting the hibernated system, it does a normal boot, as nothing would be on sda2.
After some search, I found out that one should change /etc/initramfs-tools/conf.d/resume too to contain the correct UUID. After doing this, nothing has changed. The UUID of /dev/sda2 seems to change from time to time :confused:
It had already 
4a1d75be-42b0-4dba-b908-19d456868ec7
259efe07-4db5-4a70-8ca2-a0159d98b62d
a few other values and is now
80da6e39-19c5-47d8-8b5d-ec542813c18f
according to the output of sudo vol_id /dev/sda2.
](*,)

I've tried to migrate to uswsusp for hibernating, but it messes up the sound (there is no sound after coming back). Using hibernate (/usr/sbin/hibernate) does the same, as the default acpi hibernating script (nothing)

I have no idea what to do now...

Any ideas? any help would be highly appreciated...

---

### Post by vidak on 2008-01-06
I think the mystery of changing UUID is revealed. Whenever I found my swap not working, I ran
```
mkswap /dev/sda2
swapon -a
```
It wasn't clear from the man page, but I read somewhere that mkswap changes the UUID of the partition.
I think that when I hibernated the system, the memory was saved to the swap. When rebooting, something happened which prevented the system to come back, and a normal boot was made, with the content of RAM still being on the swap, so the swap couldn't be used as swap (is that so?). So I ran mkswap again, etc...

The remaining issues:
The system came back after hibernation with normal boot again, but the swap was mounted correctly (OK, that's not a problem it's just a bit odd)

The swap is now working OK, the UUID will be constant, I hope. 
If ```
/etc/initramfs-tools/conf.d/resume
``` contains the corrent UUID, the system is still unable to resume from hibernation. kern.log.0 contains the following messages

```

Dec 31 02:13:09 ... kernel: [ 8701.760000] PM: suspend-to-disk mode set to 'shutdown'
...
Dec 31 10:57:03 ... kernel: [   21.044000] Unable to find swap-space signature

```

Any ideas?
[B]
UPDATE:
[/B]The uuid has been changed again, without mkswap after an unsuccessful resuming. :confused:

---

