---
title: "downgrade PERL"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by poysama on 2008-12-17
I have Ibex.

It seems to have Perl 5.10

I am currently setup-ing KOHA opensource library system and it really says that i need Perl 5.8 because there's a bug with 5.10.

How can I downgrade 5.10 to 5.8?

I'm not much of an advanced Linux user by the way so please explain in simple terms if you ever have any idea.

Thanks.

ALSO, what release has the 5.8 version?

---

### Post by lovelyvik293 on 2008-12-17
I think you can downgrade the perl with the help of synaptic package manager.

---

### Post by poysama on 2008-12-17
> **lovelyvik293 said:**
> I think you can downgrade the perl with the help of synaptic package manager.

I tried experimenting on that but I can't seem to find a 5.8 package.

---

### Post by poysama on 2008-12-17
Okay..I found perl on synaptic.. just plain Perl..went to its properties and went to Versions. Only saw 5.10 there. I found a 5.8 on Perl Website but I seem can't uninstall everything in the synaptic. When I try to mark it for removal it shows me several packages that it will remove and I'm not sure if installing the package from Perl's Website will install those.

---

### Post by lovelyvik293 on 2008-12-17
You can install the perl from it's site and to use this perl 5.8 make a link to this perl like:-
```

ln -s /path-to-perl-5.8  perl

```

---

### Post by superoptimo on 2009-01-14
It's some late for reply this thread. But my advice is to not make a link to the downloaded Perl 5.8.

I also found Perl 5.10 very buggy and unstable. People of Ubuntu have made a big mistake by choosing it for their Intrepid release. They just are damaging the entire project by building the core system on top of this faulty component.

I also tried to install a previous version of perl. But it make things worst, because many of the ubuntu components (Dpkg as an example) are hard linked to the Perl 5.10 modules, and they just had stop working then. So finally I have to keep two versions of perl. One is the ActivePerl 5.8 version installed apart on the /opt folder for the problematic scripts that present segfaults with 5.10, and the other is the original shipped with Intrepid (5.10) for the hardlinked Ubuntu components.

I hope that Ubuntu people give users an option to downgrade the Perl version to 5.8, that would repair this issue.

---

