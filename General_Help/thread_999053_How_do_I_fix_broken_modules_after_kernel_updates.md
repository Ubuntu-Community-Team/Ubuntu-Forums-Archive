---
title: "How do I fix broken modules after kernel updates?"
date: 2008-12-01
forum: General Help
---

### Post by peterx14 on 2008-12-01
Hi all,

Could anyone tell me how to deal with broken kernel modules?

I've just applied kernel updates to my (rather old) 7.10 (Gutsy) install. This upset VirtualBox-OSE... although since I wasn't using it before, it wasn't a big deal. I was only able to resolve this by downloading a new VirtualBox package direct from the Sun website despite hours of googling for solutions... there are plenty of suggestions, but none seemed to work for me.

Now I've also discovered that TrueCrypt no longer works. I'm able to work-around this at the moment, and I hope to upgrade completely to Intrepid as soon as I can... but really I'm after general information on how to resolve these problems.

It's a bit of a pain finding things breaking especially when they're things I really _need_! :D

So, here's truecrypt's output these days:
```
$ truecrypt -u secret.tc /mnt/truecrypt/
Enter peterx14's or root's system password: 
Enter password for '/home/peterx14/secret.tc': 
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.22.ko': -1 Invalid module format
FATAL: Module truecrypt not found.
Failed to load TrueCrypt kernel module
```

And my kernel version is:
```
$ uname -a
Linux kafka 2.6.22-16-generic #1 SMP Mon Nov 24 18:28:27 GMT 2008 i686 GNU/Linux

```

If my life depended on it, what can I do to fix this myself?

Thanks in advance! :D

---

### Post by binbash on 2008-12-01
for truecrypt , remove the deb you installed and reinstall it

---

### Post by peterx14 on 2008-12-01
Wow - fastest reply ever!! Thanks!

I had already tried that, although I hadn't removed it first. I just did "complete removal" via Synaptic, and then clicked on the .deb package to reinstall. But it is still giving the same message as before.

I _could_ download a newer deb package from the TrueCrypt website.... but part of the exercise here is to try and fix the problem with what I've got!

What I've got btw is the file "truecrypt_4.3a-0_i386.deb"

---

### Post by binbash on 2008-12-01
remove it via purge command(sudo apt-get purege truecrypt) or synaptic complete removal.Download a NEW file from turcrypt.org, generate the deb, install it.If it does not work, let me know


PS : IT is important, remove it via PURGE  or complete removal

---

### Post by peterx14 on 2008-12-01
Truecrypt.org appears to be down right at the minute ( typical! :D ) but I will try as soon as I can.

Just so I can get my head around the problem though, is the issue that the .deb I have was built for a previous kernel [minor] release, and now the new kernel is sufficiently different that it breaks truecrypt?

---

### Post by binbash on 2008-12-01
THere was a security update at kernels and you have to re-compile/re-install all the external modules.The security update caused this.You probably wont see this issue at later kernels.

---

### Post by peterx14 on 2008-12-01
Fair enough! Thanks loads for your help -- I'll report back if I can't get a fresh trucrypt working! ;)

---

### Post by cl0v3r on 2008-12-29
Hi, 

I ran into the same problem after an automatic update from kernel 2.6.22-15 to 2.6.22-16 (I use the amd64 version). I got the following in message.log:
"truecrypt: disagrees about version of symbol struct_module"

I tried the 'sudo apt-get purge truecrypt and reinstall but end up with the same problem.

I decided to get the latest release from truecrypt.org, which is truecrypt-6.1a (x64) but it warned me that it requires kernel 2.6.24. I do not want to risk updating to 8.04 just yet so I checked for an earlier release.  I got truecrypt-5.1a and this one works perfectly well.  However, there is some change in the command line interface (which now use the interactive mode by default).

For example, to mount my truecrypt partition, I now need to type:
>truecrypt --text --keyfiles= --protect-hidden=no --mount /dev/sdb1 /media/tc

while before it was only:
>truecrypt --user-mount /dev/sdb1 /media/

Anyway, all is working fine now, I may try to update later on.

---

