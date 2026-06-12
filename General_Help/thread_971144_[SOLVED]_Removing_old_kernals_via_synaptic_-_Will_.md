---
title: "[SOLVED] Removing old kernals via synaptic - Will it remove just those on the Ubuntu"
date: 2008-11-04
forum: General Help
---

### Post by Mr_JMM on 2008-11-04
I have one HDD running Ubuntu (8.10) and a second running Kubuntu (8.04) (not to be discussed, I have my reasons). I want to remove the old Ubuntu kernels (leaving just the two most recent) using Synaptic. I have checked what's installed using ls -l and the list is lengthy.

My question is: The list of kernels in synaptic (found by searching "linux-image"); is it restricted to the Ubuntu kernels or will it also include those on the (of the) Kubuntu drive?

Can I safely remove all the old kernels in Synaptic without it effecting the Kubuntu drive / installation?

Many thanks as always,

James

---

### Post by exploder on 2008-11-04
You should be able to remove the old kernels without any problems. Take my advise though and make sure you remove old linux-ubuntu-modules first, by doing this they will not be stuck as residual config files. If you do not do it this way, you will end up searching in Nautilus to manually delete these.

---

### Post by Mr_JMM on 2008-11-05
Hi,

That sounds like good advice but could you tell me how to remove the old linux-ubuntu-modules please, I'm still quite new to this?

Also, just to confirm my original request, if I look at my menu.lst file I have a kernel 2.6.24-21-generic for both the Ubuntu and the Kubuntu installation. The 2.6.24-21-generic kernel that shows in Synaptic, will that just be for the Ubuntu installation? I need to be careful with this one as that is the latest kernal for the Kubuntu as it's still running 8.04 till some bugs are corrected. Sorry to labour this point but I need to be 100%.

Many thanks again,

James

---

### Post by Mr_JMM on 2008-11-06
*bump* (sorry)

---

### Post by geirha on 2008-11-06
Removing a package with synaptic in ubuntu will only remove the package for ubuntu, not kubuntu. To remove kubuntu kernels, you'll need to boot kubuntu and remove them.

---

### Post by Mr_JMM on 2008-11-06
Excellent. Thank you. That answers my original post but before I mark the thread as solved, I have more un answered question based on advice from exploder:
> Take my advise though and make sure you remove old linux-ubuntu-modules first

How do I remove these "modules"?

EDIT: I think another lost soul has answered it for me in the thread below but could you please advise if their method of using apt-get remove linux-ubuntu-modules-2.x.xx-xx-?????? is correct? If so I can finally mark thread as solved.

[http://ubuntuforums.org/showthread.php?t=972833]("http://ubuntuforums.org/showthread.php?t=972833")

Hopefully I won't have the same problems though.

---

### Post by geirha on 2008-11-06
Yes, should work. I just removed an old kernel and all module packages for it with this command:
```
sudo aptitude remove linux-{headers,image,restricted-modules,ubuntu-modules}-2.6.24-16-386
```

which is a short way of writing
```
sudo aptitude remove linux-headers-2.6.24-16-386 linux-image-2.6.24-16-386 linux-restricted-modules-2.6.24-16-386 linux-ubuntu-modules-2.6.24-16-386
```

---

