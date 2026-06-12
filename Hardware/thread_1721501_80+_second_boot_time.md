---
title: "80+ second boot time"
date: 2011-04-04
forum: Hardware
---

### Post by belim on 2011-04-04
I am experiencing painfully slow boot times on kubuntu 10.10.

I have been trying to get to the bottom if it which so far has produced no joy, I have attached a bootchart from my system startup and I was wondering if someone could possibly point me in a direction to investigate? :)

I was wondering if it was caused by running BTRFS but I dont want reinstall with EXT4 just yet in case its not btr causing the problem. 

[IMG]http://i55.tinypic.com/29opv2p.png[/IMG]

Any help or pointers would be appreciated :)

Just saw how that displayed so this is a direct link....

[http://tinypic.com/r/29opv2p/7](http://tinypic.com/r/29opv2p/7)

---

### Post by davidmohammed on 2011-04-04
even with your second link the image is too low resolution to understand.

---

### Post by belim on 2011-04-05
So it is! :)

This is better

[http://img846.imageshack.us/i/benlaptopmaverick201104.png/]("http://img846.imageshack.us/i/benlaptopmaverick201104.png/")

Thanks

---

### Post by davidmohammed on 2011-04-05
why are you using the natty kernel not the maverick kernel?

Can you post the boot results when booting from the original maverick kernel so that we can compare?

---

### Post by belim on 2011-04-05
I am using the Natty kernel for the new BTRFS features.

Same problem booting from 2.6.35-28 though. 

[http://img219.imageshack.us/i/benlaptopmaverick201104.png/]("http://img219.imageshack.us/i/benlaptopmaverick201104.png/")

Edit: It is actually slightly slower.

---

### Post by lithopsian on 2011-04-05
Looks like you have some slow modprobes and fsck tasks early on, but other than that the boot looks OK until kdm starts.  You have something on ext2 which is really slowing things up, but other stuff also.  lsb_release is also slow, not sure why.  I don't see readahead and you might want to configure that if boot time is important to you.  Does it work with BTRFS?

kdm_greet sits there for ages but I assume you just didn't log in immediately?

You have a massive preload task but since it runs while you are staring at the login dialog it isn't really hurting anything.  Unfortunately once you are logged in, the preload doesn't seem to have hot the right stuff because there is still loads of disk IO.

---

### Post by davidmohammed on 2011-04-05
a few bug reports

[here]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/642389") - ureadahead problems with btrfs

[here]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/716736") - slow boot with btrfs

and there are a few more if you google it.

Looks like btrfs is your issue.  I would reinstall and use ext4 - you might like to try just using btrfs for a separate /home partition.  That should fix slow boot issues and you can use the journalling aspects of btrfs for all of you vital /home files whilst all of the more "static" stuff use ext4

---

