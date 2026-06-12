---
title: "SSD Question"
date: 2011-06-12
forum: Hardware
---

### Post by fleamour on 2011-06-12
When upgrading from a traditional spinner to a SSD, can I clone old drive accross or do I need a fresh install to benefit from SSD's superior speed?

---

### Post by trozamon on 2011-06-12
There might be a difference in how the file system works(I'm not sure on that, but I don't think so), but I know for sure there are different drivers to use SSDs versus HDDs. I suggest backing up important files and doing a fresh install.

---

### Post by psusi on 2011-06-12
You can clone the existing system.  Also, as I wrote in [http://wiki.ubuntu.com/Lvm](http://wiki.ubuntu.com/Lvm), one of the nice things of using LVM is that when I got my SSD, I could move the root partition over to it from my old drives on the fly without rebooting.

---

### Post by trozamon on 2011-06-12
Oh, I didn't know LVM could do that.

---

### Post by fleamour on 2011-06-13
> **psusi said:**
> You can clone the existing system.  Also, as I wrote in [http://wiki.ubuntu.com/Lvm](http://wiki.ubuntu.com/Lvm), one of the nice things of using LVM is that when I got my SSD, I could move the root partition over to it from my old drives on the fly without rebooting.

Woah! That looks a bit hardcore.

Can I use Clonezilla instead?

---

### Post by psusi on 2011-06-13
Sure.

---

### Post by YesWeCan on 2011-06-13
There are some performance and longevity tweaks that can be applied, for example:
[http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190](http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190)
I don't know what is needed with what kernel any more, but you may wish to look into this.

---

### Post by fleamour on 2011-06-13
> **psusi said:**
> Sure.

I am more comfortable with a GUI.

---

### Post by fleamour on 2011-06-13
> **YesWeCan said:**
> There are some performance and longevity tweaks that can be applied, for example:
[http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190](http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190)
I don't know what is needed with what kernel any more, but you may wish to look into this.

Thanks.

---

