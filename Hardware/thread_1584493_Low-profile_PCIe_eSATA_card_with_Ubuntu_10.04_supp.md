---
title: "Low-profile PCIe eSATA card with Ubuntu 10.04 support?"
date: 2010-09-29
forum: Hardware
---

### Post by T.J. Crowder on 2010-09-29
Can anyone recommend a **low-profile** PCIe eSATA card that's supported by Ubuntu 10.04? (Preferably kernel support, but drivers are fine.) Since I [can't get the on-board eSATA of my new desktop working]("http://ubuntuforums.org/showthread.php?p=9895653"), I'm looking for workarounds...

Thanks in advance,
--
T.J. Crowder
tj / crowder software / com

---

### Post by cascade9 on 2010-09-29
I saw your other thread, but I have no idea what is causing your problems. Intel is normally good for things like eSATA, so it should work, but obviously not. :( 

You could try a SATA to eSATA converter.

---

### Post by T.J. Crowder on 2010-09-29
> **cascade9 said:**
> You could try a SATA to eSATA converter.

**Doh!** I should have thought of that, not least because the enclosure isn't relying on the eSATA for power...

That would be **such** a better idea than a PCIe card.

Thanks,

-- T.J. :-)

---

### Post by T.J. Crowder on 2010-09-29
Hi,
> **cascade9 said:**
> I saw your other thread, but I have no idea what is causing your problems. Intel is normally good for things like eSATA, so it should work, but obviously not. :(

You inspired me to make one last go of it, and you know what? It works out of the box. It was a build quality issue with the machine, [details here]("http://ubuntuforums.org/showpost.php?p=9903356&postcount=6").

Thanks, I had pretty much given up until your post!

-- T.J.

---

### Post by cascade9 on 2010-09-29
No problem. ;) 

I'm sort of glad that is was a backplate issue. While I'm not intels biggest fan, it would be very disappointing to see them having problems with eSATA. 

BTW, I've had a case that I had to shave a few 100s of a mil from the place where the backplate mounts in, because of just the same problem you had (bowing backplate).

---

