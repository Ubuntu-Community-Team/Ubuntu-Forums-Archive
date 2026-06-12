---
title: "CD can't boot"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by parkash on 2006-07-14
Okay, this is what happened...

I had Ubuntu Dapper, Windows, and a partiton with my docs. Then I was so bored... that I just decided to wipe out Windows (which I no longer used anyway) and install sth "new".  So I tried SourceMage. It worked really good, but was once again Linux...

Finally I installed PC-BSD, which I liked a lot. But now I couldn't boot into Ubuntu...  :???: 

That was a little too bad, so I booted the Dapper CD (in dispair, after many other attempts) and ran the install option. I chose the partitions and so on, accepted and started the installation. Just as it reached the part of copying new files, I aborted the process and powered off the laptop.

Now the only cd that my laptop reads is Gentoo. I cannot boot (as my Grub is still non-operational) and I cannot do anything else rather than boot Gentoo LiveCD...

](*,)

---

### Post by FenrisAbraxas on 2006-07-14
> **parkash said:**
> Okay, this is what happened...

I had Ubuntu Dapper, Windows, and a partiton with my docs. Then I was so bored... that I just decided to wipe out Windows (which I no longer used anyway) and install sth "new".  So I tried SourceMage. It worked really good, but was once again Linux...

Finally I installed PC-BSD, which I liked a lot. But now I couldn't boot into Ubuntu...  :???: 

That was a little too bad, so I booted the Dapper CD (in dispair, after many other attempts) and ran the install option. I chose the partitions and so on, accepted and started the installation. Just as it reached the part of copying new files, I aborted the process and powered off the laptop.

Now the only cd that my laptop reads is Gentoo. I cannot boot (as my Grub is still non-operational) and I cannot do anything else rather than boot Gentoo LiveCD...

](*,)

If ypu didn't format the Ubuntu installation use the Gentoo LiveCD to install grub again.

```
 grub install hda 
```

i thik that should do it :P i never had any problems with grub since i installed Gentoo like 2 years ago :P so i don't remember the steps to install it from the livecd

---

### Post by parkash on 2006-07-15
hmm.. I never got Grub working once more... And, since my CD doesn't work anymore, there's nothing that I can do right now...

I just wanted to post this to tell you guys that maybe it's a little dangerous to interrupt an installation so abruptly... I think that's what damaged my Optical Drive. 

BTW, now I can't boot anything.

---

