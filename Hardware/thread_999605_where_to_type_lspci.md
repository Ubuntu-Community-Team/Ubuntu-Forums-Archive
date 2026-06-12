---
title: "where to type lspci"
date: 2008-12-02
forum: Hardware
---

### Post by curiouscustomer on 2008-12-02
sorry where do i type this to find my chipset?

---

### Post by lisati on 2008-12-02
> **curiouscustomer said:**
> sorry where do i type this to find my chipset?

Commands like "lspci" are usually entered from the command line, also known as the "terminal". In some flavours of Ubuntu (including Ubuntu and Xubuntu) it's on the Applications->Accesories menu. 

Another interesting command to learn about what's under the hood of your machine is:
```
sudo dmidecode
```

---

### Post by seren6ipity on 2008-12-02
Open a terminal by going to Applications > Accessories > terminal

Type 
lspci | grep Controller

> **curiouscustomer said:**
> sorry where do i type this to find my chipset?

---

