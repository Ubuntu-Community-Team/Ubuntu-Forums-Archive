---
title: "Filesystem for external drive for Ubuntu and OS X"
date: 2008-08-06
forum: General Help
---

### Post by DrQuincy on 2008-08-06
I've just bought a new external drive and I want to be able to plug it into either my Ubuntu box or my Macbook Pro and read and write to it.

Which would be best to use? I'm not sure Linux has hfs+ support and I don't think that Mac can do ext3.

Any ideas?

Thanks.

---

### Post by jerome1232 on 2008-08-06
according to this [http://www.kernelthread.com/mac/osx/arch_fs.html](http://www.kernelthread.com/mac/osx/arch_fs.html)

looks like fat32, :( unless you can add on support for other filesystems.

---

### Post by DrQuincy on 2008-08-06
Hi, thanks for that.

Hell will freeze over before I use fat32. :)

I favour hfs+, 

In the meantime . . . I couldn't find anything online but if you put hfs+ into Synaptic there is a package called hfsplus that adds support. I will try it tonight. Hopefully, that will do that job.

Thanks.

---

### Post by jerome1232 on 2008-08-06
Lol didn't even think about that
i did a apt-cache search hfs+ and these two looked promising (probably what you are looking at in synaptic)

hfsplus - Tools to access HFS+ formatted volumes
hfsutils - Tools for reading and writing Macintosh volumes

---

### Post by DrQuincy on 2008-08-06
Thanks you found the same two I did. I'll try it when I get home tonight and will post the result.

I've read you have to disable journaling but that's fine.

---

