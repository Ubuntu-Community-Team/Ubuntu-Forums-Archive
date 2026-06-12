---
title: "lirc_serial - don't try to register things with the same name in the same directory"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by bruma on 2007-07-12
hi,

I'm trying to get to work my homebrew (Cesko variant) lirc_serial adapter on Feisty. I been using this adapter  successfully for few years on Fedora.

I tried this instructions [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty), but during configuration I can not choose "Cesko variant", therefore lirc_serail module is not working with may adapter.

So I decided to compile lirc_serial from latest sources  lirc-0.8.2.tar.bz2 and follow this [http://ubuntuforums.org/showthread.php?t=163496](http://ubuntuforums.org/showthread.php?t=163496)

lirc_serial module was compiled ok, but when I try to load it (modprobe lirc_serial), I get:

```
[  153.892000] kobject_add failed for lirc_serial.0 with -EEXIST, don't try to register things with the same name in the same directory.
[  153.892000]  [<c01ed9e9>] kobject_add+0x119/0x1a0
[  153.892000]  [<c02558b7>] device_add+0xb7/0x530
[  153.892000]  [<c02598e7>] platform_device_add+0xf7/0x150
[  153.892000]  [<f8a0d032>] init_module+0x32/0x304 [lirc_serial]
[  153.892000]  [<c02ecf59>] wait_for_completion+0x19/0xe0
[  153.892000]  [<c0143180>] __link_module+0x0/0x20
[  153.892000]  [<c013aae8>] kthread_stop+0x68/0x70
[  153.892000]  [<c014422d>] sys_init_module+0x15d/0x1ba0
[  153.892000]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[  153.892000]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[  153.892000]  =======================
```

What's the meaning of this error message?

Funny thing happen, at first compile and first modprobe lirc_serial was working OK, I even record some remotes, but after reboot I start getting this messages.

---

### Post by micasoft on 2007-07-19
I have same problem

---

### Post by bruma on 2007-09-02
> **bruma said:**
> hi,
I tried this instructions [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty), but during configuration I can not choose "Cesko variant", therefore lirc_serail module is not working with may adapter.


I figure it out how to add option for "Cesko variant", so I updated instructions on [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty).

---

