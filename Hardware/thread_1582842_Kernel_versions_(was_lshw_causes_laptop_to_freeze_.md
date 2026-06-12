---
title: "Kernel versions (was: lshw causes laptop to freeze up in Launchpad)"
date: 2010-09-27
forum: Hardware
---

### Post by mwildam on 2010-09-27
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614008](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614008)
Bug already has been fixed but there are starting some discussions - therefore I open this thread.

[QUOTE="cariboo907"]Why bother adding all the extra comments when the bug has been fixed?[/QUOTE]
There were just a few confirmations about the bug fixed.

                 [QUOTE="vmc"]cariboo907, good point! I think the  reason is these comment keep coming through our email account and people  think they have to reply. Just like I did :)
  I have been reading these emails,  but deleted them and never responded until now, since lshw has been fixed for a while.
[/QUOTE]
But there are also coming email notifications when the status of the bug has been changed. However, probably people forget when later addition comments coming via email.

But what I wonder a lot more:
Why is this bug an "Ubuntu kernel" bug not affecting other distris?

For a very long time I thought there is only one Linux kernel, but I start noticing differences when I could see different hardware pieces working well on Ubuntu but not on Fedora. Then I learned that different distributions apply their own kernel patches.

I am testing mobile internet sticks on a regular basis and each first beta of each new Ubuntu version has problems with the sticks. I imagine there could also be a patch applied again and again to the original kernel.

Why must it come that far? - Why do have to be so many kernel versions?

---

### Post by penguin42 on 2010-10-04
> But what I wonder a lot more:
> Why is this bug an "Ubuntu kernel" bug not affecting other > distris?

This bug was caused by a previous fix that was added to the Ubuntu kernel, and therefor doesn't affect the upstream kernel.

> For a very long time I thought there is only one Linux kernel, > but I start noticing differences when I could see different 
> hardware pieces working well on Ubuntu but not on Fedora. Then
> I learned that different distributions apply their own kernel 
> patches.

One kernel to rule them all would be great, but what tends to happen is that a distro has to make a decision on when to take a kernel to make their release, and their own users hit particular bugs; they get fixed and eventually the bug finds its way back upstream.   Also Ubuntu for example adds drivers in that haven't yet gone into upstream - it means we get wider driver support than the upstream kernel.  It's not an easy trade off.

> I am testing mobile internet sticks on a regular basis and each > first beta of each new Ubuntu version has problems with the 
> sticks. I imagine there could also be a patch applied again and > again to the original kernel.

Yeh some things are just too broken!   You can run the ubuntu daily kernels 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

that gets you the bleeding edge.

Dave

---

