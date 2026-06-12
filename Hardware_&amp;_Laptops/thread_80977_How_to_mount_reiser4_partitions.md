---
title: "How to mount reiser4 partitions?"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by rcerreto on 2005-10-23
Not sure whether this is the right place to post.
Advanced apologies if it's not :) 

reiser4 partitions look supported in breezy and I'm able to create one using mkreiser4, but... I found no way to mount it.

Of course I know how to use the 'mount' command :-)
but there seem to be no support for reiser4 in it

Am I missing something?

---

### Post by Kyral on 2005-10-23
[quote=rcerreto]Not sure whether this is the right place to post.
Advanced apologies if it's not :) 

reiser4 partitions look supported in breezy and I'm able to create one using mkreiser4, but... I found no way to mount it.

Of course I know how to use the 'mount' command :-)
but there seem to be no support for reiser4 in it

Am I missing something?[/quote]

Try installing reiser4progs and libreiser4-dev

---

### Post by rcerreto on 2005-10-24
Kyral,
thanks for your replay.
I did install both but to no avail.
My personal guess is that breezy ships with mkreiser4 allowing you to create reiser4 partition but the stock breezy kernel does not support them.
Why that is anybody's guess.
Looking at the config file into the source tree I found several flags related to reiserfs but none for reiser4.
I presume that you have to patch and recompile the kernel to support reiser4 file systems.
Can anyone confirm that, please?

---

### Post by Mathboy on 2005-10-29
I too would like to use reiser4 and am unable to mount it in Breezy.
Anybody found a solution? :)

---

### Post by hachre on 2005-11-13
There is no reiser4 support in Ubuntu.
If you want reiser4 you have to compile your own kernel.
If you don't know how to do that you don't want reiser4.

If you do, but don't know where to get the patches check out my other post here:
[http://www.ubuntuforums.org/showpost.php?p=490130&postcount=2](http://www.ubuntuforums.org/showpost.php?p=490130&postcount=2)

---

### Post by mykey on 2005-11-19
[QUOTE=hachre]There is no reiser4 support in Ubuntu.
If you want reiser4 you have to compile your own kernel.
If you don't know how to do that you don't want reiser4.

If you do, but don't know where to get the patches check out my other post here:
[http://www.ubuntuforums.org/showpost.php?p=490130&postcount=2](http://www.ubuntuforums.org/showpost.php?p=490130&postcount=2)[/QUOTE]

tanks a lot for the links ;)

---

