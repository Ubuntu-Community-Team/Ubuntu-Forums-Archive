---
title: "4TB Raid Setup"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by komodo9 on 2007-09-12
I just built a server that has 4TB worth of storage, and I was planning on using FreeBSD as the operating system behind it.

However now that everything's booted up and installed, I'm having all kinds of problems getting the 4TB partition to show the full size, so I'm looking around at other OS alternatives.

My question is, how is Ubuntu at handling very large slices?  Would I need to use gpt, or can ubuntu handle it natively with the installation program?

How is Ubuntu's large filesystem support?

---

### Post by komodo9 on 2007-09-13
No one?

---

### Post by psusi on 2007-09-13
You have to use GPT because the msdos partition table can only handle 2 TB.

---

