---
title: "can't believe it, security update speed slow like hell"
date: 2008-11-29
forum: General Help
---

### Post by dollylamb on 2008-11-29
hey guys,

anyone ever got crazy when doing security update like me? on my box, any update packages from security.ubuntu.com always drive me crazy. For example: linux-image-2.6.27-9.generic package (23 megs) took me over 6 hours to complete with download speed is 1000 bps, what a shame!

btw: im on 4MB ADSL line & everything is ok except security.ubuntu.com :(

---

### Post by anthro398 on 2008-11-29
Perhaps you should try using a mirror rather than the main server.  You can change that in Synaptic under Settings>Repositories.

---

### Post by dollylamb on 2008-11-29
no man, the download speed for any other updates are good enough (~170KB/s - 250KB/s) for me except anything from **security.ubuntu.com** & this repository seem not to have a substitute !?

---

### Post by dollylamb on 2008-11-30
it seems no one knows what is going on :(

---

### Post by gombadi on 2008-11-30
I don't know what is going on but I know how you feel.

From Sydney any update is slow and I dread doing any large updates like OpenOffice.Org or the kernel.

Our local mirror is actually on an IP address in the UK (the other side of the world) and it looks like we share the same machines as the US.

For us security updates also come from the other side of the world.

If the world is using the same IP range for security updates as Australia and the US use for all updates then I guess the links are overloaded.

```

lroger@dave:~$ dig +short au.archive.ubuntu.com
91.189.88.45
91.189.88.46
91.189.88.31
lroger@dave:~$ dig +short us.archive.ubuntu.com
91.189.88.46
91.189.88.31
91.189.88.45
lroger@dave:~$ dig +short security.ubuntu.com
91.189.88.37


```

---

