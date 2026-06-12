---
title: "How to start nmbd at boot in 8.04?"
date: 2008-09-27
forum: General Help
---

### Post by MikeB23930 on 2008-09-27
I'm running Kubuntu 8.04.  Samba is set to start at boot in run level Multiuser (2).  Smbd starts at boot but nmbd doesn't.  If I restart Samba manually, nmbd starts. I cannot find nmbd listed in any of the run levels in System Services.  Can some one please tell me how to set things up so that both smbd and nmbd start at boot?

Thanks,

Mike

---

### Post by fsmithred on 2008-09-28
Never mind. There's only /etc/init.d/samba, but no /etc/init.d/smbd or /etc/init.d/nmbd.

---

