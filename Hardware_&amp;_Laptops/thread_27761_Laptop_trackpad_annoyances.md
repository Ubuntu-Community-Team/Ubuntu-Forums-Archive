---
title: "Laptop trackpad annoyances"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by anando on 2005-04-17
Hi,

I am really bugged by the trackpad on my laptop - I seem to be writing at random parts of the screen ... so I would like to ask you experts how to disable the trackpad when I am typing ... apparently such a help exists for warty but I havent found anything for hoary as yet.  

What is worse I tries loading the synaptics module in /etc/X11/xorg.conf ... and my X server wouldnt start - so I had to go back to uncommenting it. 

Please help ... 

Many thanks in advance,
Anando.

---

### Post by mendicant on 2005-04-17
If you have an alps trackpad, you may want to look at:

/usr/share/doc/xorg-driver-synaptics/README.alps

On a Vaio, I applied the alps.patch.gz to the kernel and rebuilt it, and now I can disable the click-on-tap behaviour, or modify the setting so it doesn't happen so often.

---

