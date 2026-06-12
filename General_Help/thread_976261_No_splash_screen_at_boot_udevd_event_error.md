---
title: "No splash screen at boot: udevd_event error?"
date: 2008-11-09
forum: General Help
---

### Post by SAFokkens on 2008-11-09
Hello!

I've upgraded from Hardy to Intrepid. Almost everything is working fine except two problems.
The first one is that I only see the splash screen with the orange bar going from left to right and back. After that, the bar should grow from left to right. But that's when the graphics disappear and I'm back in textmode.
At the first line it says:
```
udevd_event: run_program: open /dev/null failed no such file or directory
```

The system still boots, but without the splash screen. I've already compared the UUID of my swap partition in fstab and blkid, they're the same.

My second problem (caused by the above? I really don't that much about Linux :( ) is that my network shares in fstab are not mounted automatically anymore. In Hardy this was no problem. When the system is booted up and I issue
```
sudo mount -a
```
it's working, but how do I get it to mount it at boot, like in Hardy?

I hope anyone can help me.

Thank in advance!

---

### Post by SAFokkens on 2008-11-10
Hello!


I've searched the forum but I couldn't find a solution to my problem.
Is there somebody here who has a suggestion?

The problem started since 8.10. In 8.04 everything was running fine.


Thanks!

---

