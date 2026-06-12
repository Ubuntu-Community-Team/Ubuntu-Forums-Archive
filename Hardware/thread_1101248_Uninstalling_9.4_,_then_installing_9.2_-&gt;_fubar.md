---
title: "Uninstalling 9.4 , then installing 9.2 -&gt; fubar"
date: 2009-03-20
forum: Hardware
---

### Post by terrax on 2009-03-20
Hello everyone.

I'm not here to complain, because its my own fault installing an alpha driver :) The Catalyst 9.4.

But now when I have removed it (purged), and installed the older fglrx 9.2, something is completely wrong.

The computer starts op, and compiz works. But opengl games / tvout doesn't work correctly. When running an opengl game there is texture corruptions. And when I plugin a tv, X freeze.

So where is the hidden files from the removed 9.4, which haven't been removed proberly? Symlinks?

Actually this is not the first time this is happending. I tried it once before, and I had to reinstall kubuntu. I just liked the 9.4, I tried it again :)

So anybody got any "tricks" to find the problem and solve it without a reinstall?


Computer:
Kubuntu 8.10
Radeon HD3650 mobility.

---

### Post by mtbsoft on 2009-03-20
Just a thought but it might be better to ask this over at the ATI site, they're more likely to know I would guess.

Oh... and good luck.

---

### Post by terrax on 2009-03-20
Why? Its deb related I think. And I don't think the Ati knows the packaging system as well as ubuntu users.

Anyway, I would be glad if anyone had an idea.

---

### Post by markbuntu on 2009-03-20
You cannot remove that driver completely with apt-get purge since apt did not install it. You need to run the uninstaller script usr/share/ati/fglrx-uninstall.sh. But since you have most likely purged that file your best bet would be to uninstall the 9.2 driver using the script. reinstall the 9.4 driver and then uninstall it with the script then reinstall the 9.2 driver.

It is very important to properly remove previous drivers before installing new ones or you will have problems.

---

### Post by terrax on 2009-03-20
> **markbuntu said:**
> You cannot remove that driver completely with apt-get purge since apt did not install it. You need to run the uninstaller script usr/share/ati/fglrx-uninstall.sh. But since you have most likely purged that file your best bet would be to uninstall the 9.2 driver using the script. reinstall the 9.4 driver and then uninstall it with the script then reinstall the 9.2 driver.

It is very important to properly remove previous drivers before installing new ones or you will have problems.

I always install the fglrx drivers as deb files. Making the deb files with the --buildpkg command. So apt SHOULD actually remove it all.

Anyway, I found the problem. It was some wrong symlinks against my libGL.1.2.so...

Thanks anyway :-)

---

### Post by markbuntu on 2009-03-20
Making debs from unsupported sources with --buildpkg is no guarantee that everything will be returned to the way it was when you remove them. As you have learned. apt cannot do everything that a supplied uninstaller script can, like fix broken sym links.

---

