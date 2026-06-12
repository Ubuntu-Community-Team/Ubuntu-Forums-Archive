---
title: "(Fan) cooling not working after suspend on edgy"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by joao.lourenco on 2006-12-02
Hi,

First of all, I have to say this was working all right on dapper with 2.6.15 kernel! ](*,)

After upgrading from dapper to edgy, the fans stopped to work decently **after** hibernating to disk (I've tried ASCPI hibernate and suspend2, same problem in both).  If I reboot, the fans work all right again!

With "the fans stopped to work decently" I mean
```
$ ls /proc/acpi/fan/
C254  C255  C256  C257
~$ cat /proc/acpi/fan/*/state
status:                  off
status:                  off
status:                  off
status:                  on
```

Fan C257 is on and changes speed when needed, but others are temporarily "dead".

I've tried to unload and reload modules "thermal" and "fan" with no success.

I've tried kernel 2.6.15 (from dapper) in edgy and it works all right, so it's a kernel issue.

Oh, BTW, my laptop is a HP/Compaq nx 8220.

Any help would be greatly appreciated, and I hate to shutdown my system (I used to spend weeks without rebooting). I'm considering to switch back to dapper kernel, but would like to find the nature of the problem anyway...

Cheers,
João Lourenço

---

