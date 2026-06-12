---
title: "converting a primary partition to an extended one"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by catonano on 2009-07-19
Hello people,

I hope this is the right place for such a question. If it's not, I'm sorry, I apologize.

The subject says it all. I have 2 primary partitons on my drive: 

[LIST=1]
[*]/dev/sda3 is an extended partiton and contains a logical partitioon for the swap and another logical partition for my Ubuntu installation
[*]/dev/sda2 is a primary one, it used to contain XP now it's formatted in ext3 and I use it for data dumps
[/LIST]

I'd LOVE to be able to convert /dev/sda2 to an _extended_ partiton and inside that I'd put another bunch of logical partitions because I'd love to install Arch Linux also, to experience a different distro.

Now, the partitions editor doesn't allow me to do that. There's a menu item but it's greyed out and not available.

I don't see why. :-( What am I missing ?

Thanks so much for any hint
Catonano

---

### Post by catonano on 2009-07-19
Like this:

[IMG]http://imagebin.ca/img/kScMFy.png[/IMG]

Of course I deleted the partition and tried to create a new extended one in the empty space, but as you can see, only the first item is available, the other two are not.

Thanks again for any help
Cato

---

### Post by Partyboi2 on 2009-07-19
Hi, you can only have one extended partition per hard drive.

---

### Post by catonano on 2009-07-19
ouch ! :-( I didn'y know.

Thanks.
Cato

---

