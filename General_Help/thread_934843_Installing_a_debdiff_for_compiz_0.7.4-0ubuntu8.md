---
title: "Installing a debdiff for compiz_0.7.4-0ubuntu8"
date: 2008-10-01
forum: General Help
---

### Post by JinLab on 2008-10-01
I did a lot of searching, and found a fix to my problem here:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764)

I need to install a debdiff file, so I found a tutorial from the following wiki:

[https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff?highlight=(debdiff](https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff?highlight=(debdiff))

I decided to give it a shot and got stuck when I try to download the source for compiz

```
sudo apt-get source compiz
```

This returns files for compiz_0.7.4-0**ubuntu7**.  Im using hardy, so I'm not sure why ubuntu7 was pulled down for compiz.  I don't want to apply the patch because it looks like it does not pertain to this version of compiz.  Does anyone know how i can get compiz_0.7.4-0**ubuntu8** source instead using the sudo apt-get source command?  

In any event, I tried going on to the next step with the following command

```
sudo apt-get build-dep compiz
```

and received another error:

```
Note, selecting automake instead of automake1.10
Package libcairo-dev is a virtual package provided by:
  libcairo2-dev 1.6.0-0ubuntu2
You should explicitly select one to install.
E: Package libcairo-dev has no installation candidate
E: Failed to satisfy Build-Depends dependency for compiz: libcairo-dev
```

Any suggestions on what to?

If this can get resolved, I plan on the running these commands.

```
cd compiz-*
patch -p1 < ../compiz_0.7.4-0ubuntu8.debdiff
debuild -uc -us
sudo dpkg -i ../compiz*.deb
```

Thanks if you can help.

---

