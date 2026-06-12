---
title: "some help needed"
date: 2008-10-02
forum: General Help
---

### Post by siddharths7 on 2008-10-02
i m new bee for ubantu
i just install it inmy d drive in 8 gb space is allocated to it
but i want to unistall it i go to add and remove option in my windows xp
i click it on uninstall but it will not uninstal from there nothing happen
so i go to d drive and delete the folder which contain ubantu

but still when i boot my system there is option of ubantu will u help me how to remove the ubantu from dual boot option from boot loader from my laptop

---

### Post by ibuclaw on 2008-10-02
Sorry to hear that you're leaving :(

I don't know much about Windows, so forgive me if I'm wrong.

In "Run As" or "Run Command" type in
```
msconfig
```

And in one of the tabs there should be the information of the **boot.ini** file there.

Just remove the Ubuntu entry and shorten the "timeout=10" time to, say, 2 seconds.

Regards
Iain

So long, and thanks for all the fish...

---

