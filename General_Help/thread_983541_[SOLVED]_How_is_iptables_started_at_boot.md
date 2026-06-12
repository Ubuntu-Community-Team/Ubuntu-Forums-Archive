---
title: "[SOLVED] How is iptables started at boot?"
date: 2008-11-15
forum: General Help
---

### Post by bowens44 on 2008-11-15
Iptables is starting up at boot and loading rules from a file called iptables.rules in the /etc directory. I have a vague recollection of creating a script to do this but I can't find it.  I thought the script would be in /etc/init.d/ but it isn't.

Is there a way for me to tell how iptables is launched?

thanks

---

### Post by iponeverything on 2008-11-15
> **bowens44 said:**
> Iptables is starting up at boot and loading rules from a file called iptables.rules in the /etc directory. I have a vague recollection of creating a script to do this but I can't find it.  I thought the script would be in /etc/init.d/ but it isn't.

Is there a way for me to tell how iptables is launched?

thanks

look under /etc/network/

maybe in pre-up/

---

### Post by bowens44 on 2008-11-15
> **iponeverything said:**
> look under /etc/network/

maybe in pre-up/

No, it's not there. 

Thanks for the reply

---

### Post by bowens44 on 2008-11-15
> **iponeverything said:**
> look under /etc/network/

maybe in pre-up/

Found it, it was in the interfaces file in /etc/network/   thanks for pointing me in the right direction!!!

---

