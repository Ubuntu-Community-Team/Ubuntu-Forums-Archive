---
title: "unable to unmount external hard disk"
date: 2009-02-19
forum: Hardware
---

### Post by panmoto on 2009-02-19
I have xubuntu 8.10 (it was ubuntu then I installed xubuntu desktop via synaptic).

the problem is I can not unmount external harddisk with Thuran even as root. Have no problem with mounting. 

I got either this error messages :
- org.freedesktop.hal.storage.unmount-others auth_admin_keep_always <-- (privilege, result).

or :
- An unknown error occured.

But the strange thing is when I run XFE as root, it is unmount-able.  So my question is :
1. how to enable Thuran to unmount?
2. how to unmount without being root? My other PC with Ubuntu 8.10 have no problem like this.

Thanks in advance.

---

### Post by superkret on 2009-03-23
I have exactly the same problem with Thunar. I already tried a fix from another thread which said that the gnome-mount tool and Thunar don't get along well. So I first disabled Thunars automount function, but that didn't work. Secondly, I removed gnome-mount which didn't fix it either. I'd really appreciate some help since I didn't find any other fix either.

Thanx in advance.

---

### Post by superkret on 2009-03-23
Edit: Problem solved (sort of), by switching to pcmanfm, which I like better, anyway.

---

