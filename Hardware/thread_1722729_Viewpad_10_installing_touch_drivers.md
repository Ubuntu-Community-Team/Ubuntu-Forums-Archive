---
title: "Viewpad 10 installing touch drivers"
date: 2011-04-06
forum: Hardware
---

### Post by -=[gizmo]=- on 2011-04-06
Hi

I've just installed Ubuntu 10.10 on my viewsonic touchpad 10.
and I've been following the tut at
```

http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html

```

But when I get to the part when I use git to clone the driver folder.

Its hangs on 17%   o.O

My terminal output:
```

Cloning into enac-drivers...
remote: Counting objects: 1008, done.
remote: Compressing objects: 100% (828/828), done.
fatal: The remote end hung up unexpectedlyKiB | 7 KiB/s   
fatal: early EOF
fatal: index-pack failed

```


-----------------------------------------------------------------------

I've fixed it by writen a shell script that just looped the downloaded worked

```

#!/bin/bash

git clone git://git.lii-enac.fr/linux-input/enac-drivers

while test $? -ne 1
do
echo "Trying... again"
git clone git://git.lii-enac.fr/linux-input/enac-drivers
done

echo "done XD"

```

---

### Post by koua29 on 2011-05-24
the enac driver work fine on the FEPAD (WINPAD) tablet.
Look here my vidéo : [http://www.tablette-pc.net/tablette-tactile-pc/tablette-tactile-fepad-winpad-sous-linux-ubuntu-10-10/]("http://www.tablette-pc.net/tablette-tactile-pc/tablette-tactile-fepad-winpad-sous-linux-ubuntu-10-10/")

---

