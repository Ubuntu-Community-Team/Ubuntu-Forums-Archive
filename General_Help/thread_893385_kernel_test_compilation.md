---
title: "kernel test compilation"
date: 2008-08-18
forum: General Help
---

### Post by jasex on 2008-08-18
So i was building a test kernel before I went to sleep... bad thing is, is that the make kpkg command filled up my hard drive space on my root partition before it could finish... is there a way, while compiling to make it go to my home partition then install it?

---

### Post by sdennie on 2008-08-18
You can actually use make-kpkg as a non-root user from your home directory without any problems.  There may be drawbacks to this that I'm not aware of but, it does work and the only part where you actually need root is to do the install with dpkg.  You may also be able to save some (actually, a lot) of disk space prefixing make-kpkg with some env variables.  I use:

```

INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 fakeroot make-kpkg --initrd --append-to-version=-version_name kernel_image kernel_headers

```

On a dual core, that will greatly speed up the compile (I think it takes around 20-30 minutes on my machine) and make the installed kernel much, much smaller on disk.

Another tip for releasing some probably wasteful disk space is to clean the apt cache:

```

sudo apt-get clean

```

---

### Post by jasex on 2008-08-18
Thanks :D it helped a lot... now I face a new problem... forgot to compile in Alsa... support... is there any way to add it without going through this crap again?

---

### Post by sdennie on 2008-08-19
Probably.  Just download the latest driver (you just need the actual driver) from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page), untar it and, once in the directory it creates and while running the new kernel try:

```

./configure
make
sudo make install

```

I generally build with ALSA support but compile the latest version afterwards so, I'm not sure if that will work for you.  It's also possible to automate the process at installation time by putting a script in /etc/kernel/postinst.d.  You'd have to modify this a bit for your needs but, it's the general idea:

```

#!/bin/bash

echo "Building ALSA drivers for $1" >&2
cd /usr/src/alsa
make clean 2>&1 > /dev/null

./configure --with-kernel=/lib/modules/$1/build --with-cards=hda-intel 2>&1

make install 2>&1 > /dev/null

exit 0

```

---

