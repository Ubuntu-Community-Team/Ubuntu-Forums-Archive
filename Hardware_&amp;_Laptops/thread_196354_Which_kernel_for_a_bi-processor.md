---
title: "Which kernel for a bi-processor?"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by isterios on 2006-06-14
Hello,

I am working on Xubuntu with a bi-xeon.

Which kernel may I choose for activate my two processors (+hyperthreading= 4 visible processors):

Actually, I have the default one:
2.6.15-20-386


Here are the installable kernels:
v   linux-image                                        
v   linux-image-2.6                                 
i   linux-image-2.6.15-20-386  
i A linux-image-2.6.15-23-386 
p   linux-image-2.6.15-23-686 
p   linux-image-2.6.15-23-K7
pi  linux-image-2.6.15-23-server 
p   linux-image-2.6.15-23-server-bigiron
i   linux-image-386 
p   linux-image-686 
p   linux-image-k7  
p   linux-image-server 
p   linux-image-server-bigiron 

So is there anyone  which works for multi-processors?

thks.

---

### Post by bikeboy on 2006-06-14
You need an SMP kernel. Since a Xeon is recent and Intel I'm guessing it's a 686 type but I'm not sure about that one.

[http://en.wikipedia.org/wiki/Symmetric_multiprocessing](http://en.wikipedia.org/wiki/Symmetric_multiprocessing)

---

### Post by isterios on 2006-06-14
Ok perfect, I installed the 686 and it rules. It supports SMP.

Thks.

---

