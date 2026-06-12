---
title: "Minimal install"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by avinazz on 2009-10-24
**hi all,**

I want to make a minimal install of ubuntu .
i've tried using Ubuntu minimal install and Ubuntu server install.
what i found is ubuntu server is far more slim than minimal ubuntu.

[B]installation process:

-- [/B]ubuntu minimal installed in vmware server where it downloads everything what it requires after a base system install.  **size: 849MB** (didn't ask for packages)

**--**ubuntu server installed in vmware where it gives manual package selection option, but never ask for any package. i guess i'm supposed to install other packages after the system has been setup.  **size: 470MB**   

**Target:**
i want to wind up required package within a limit of 400mb.
this is going to be a NAS server.


it seems _**ubuntu server**_ is an option to go with.

Plz help me to shrink this OS further.

Any help is appreciated.
Thanks.

---

### Post by kerry_s on 2009-10-24
why? there are distros just for nas, most less then 100mb.

if you just want to do it by yourself try a debian lenny base instead, debian does not tie everything together, so it should be far smaller.

---

### Post by hal10000 on 2009-10-24
Take a look at this thread, where the same issue is discussed: [http://ubuntuforums.org/showthread.php?p=8156002](http://ubuntuforums.org/showthread.php?p=8156002)

---

### Post by avinazz on 2009-10-24
Thank you guys....

i m going to try FreeNAS today.....

but my point still remains the same....

i would better like to change my question. i.e

if someone has any idea what packages or libraries or other stuffs could be removed?

a bit of info from diff. people will surely help me.

thanks again.

---

### Post by kerry_s on 2009-10-24
> if someone has any idea what packages or libraries or other stuffs could be removed?

the problem is in ubuntu the packages are tied together, so even removing simple things can leave you with a non-working install.
you can try it & see what breaks, just remember ubuntu uses upstart, so careful with removing running things & if i remember right, trying to remove apparmor will break networking, theres a metapackage "ubuntu-base" i think, might want to look what that has pulled in.

i tried trimming the base a few times, but always broke it, its very hard picking the right stuff to remove. good luck.

---

### Post by avinazz on 2009-10-26
Thanks kerry for such useful info...

i m always in state of learning.....and m still not much use to with linux.


Right now i'm suppose to reduce the Ubuntu server size as much as possible.....
but so far it seems to have limitation as per your suggestion.

I m going to do RnD today again......hope i would find something really substantial.


Thank u all......but this thread is still open

---

