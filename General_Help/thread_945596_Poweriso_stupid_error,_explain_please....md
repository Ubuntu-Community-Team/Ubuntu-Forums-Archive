---
title: "Poweriso stupid error, explain please..."
date: 2008-10-12
forum: General Help
---

### Post by david sousa on 2008-10-12
Could you explain me why is this hapeppening?


david@David:~$ poweriso convert ola.daa -o ola.iso -ot iso

PowerISO   Copyright(C) 2004-2006 PowerISO Computing, Inc
            Type poweriso -? for help

ola.daa: File version mismatch. To open this file, please visit our website to get the latest version.
david@David:~$

---

### Post by TeXtonyx on 2008-10-12
Suppose you had PowerIso 4.2 and created a .uif or .daa file. I don't think that it's
backwards compatible, which means if you had PowerIso 4.1 (for instance) then you
can't open the newer file. I think ola.daa was created by a newer version than the
version of Poweriso that you have. But if this file were one that you created using
the same version of PowerIso that you are now using to try the conversion, and it
fails, I don't know why unless the command line syntax were incorrect.

---

