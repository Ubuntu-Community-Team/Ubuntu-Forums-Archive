---
title: "How to see all 4 gig of RAM?"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by danfluidmind on 2006-06-19
I've searched a hundred different ways on Google and haven't found an answer to this. Could someone please tell me how to get Linux to see all 4 gig of RAM in my machine? I've installed Ubuntu 6.06 onto an Alienware desktop with 4 gig of RAM. But when I run 'top' it says I only have 3 gig. I'm gonna be running 5 or 6 instances of VMware, so I need that extra gig.

Does anyone know what I need to do to access that fourth gig of RAM?

Thanks a lot.
--Dan

---

### Post by Ocxic on 2006-06-19
you have to enable the option in your kernel. the only way i know to do this is to compile your own kernel, there is a guide on how to compile a kernel on here, and it mentiens the ram thing.

---

### Post by RawMustard on 2006-06-21
Yep me too, windows is the same tho, only sees 3 gig but uses all 4, something about the way it reserves some or something like that.  Never did get an explination why linux doesn't see it all, or whether it even uses it all.  Sorry I couldn't be of more help, I asked this over a year ago and never got any responses in several places, seems no one knows or is not willing to tell :(

---

### Post by Ocxic on 2006-06-21
oi. ubuntu can and will use/see/report all 4GB of ram, you simply have to eneble that option in your kernel when it's compiled. and the only way to do that that i knw of is to compile your own kernel, there should be a guid in the how-to or tips and trick forums.

---

### Post by RawMustard on 2006-06-25
the smp kernels are already enable for 4 gig of ram, it's not the answer!

---

