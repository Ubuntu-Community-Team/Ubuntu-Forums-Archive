---
title: "Installing nvidia drivers on kunubu, help"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by desypher on 2005-04-07
Hey guys,

Does anyone know how i can install the new nvidia drivers on my kubuntu.i am not sure which version i'm running but im sure that the kernel is '2.6.10-5-386'. How can i install the kernel-source? Because that's the only thing i need so i can install it. Also is there any application for managing kubuntu like mandrake's 'Control Centre'?

Thanks, DesyphER

---

### Post by Nis on 2005-04-07
[QUOTE=desypher]Hey guys,

Does anyone know how i can install the new nvidia drivers on my kubuntu.i am not sure which version i'm running but im sure that the kernel is '2.6.10-5-386'. How can i install the kernel-source? Because that's the only thing i need so i can install it. Also is there any application for managing kubuntu like mandrake's 'Control Centre'?

Thanks, DesyphER[/QUOTE]
 Have you tried using Synaptic to install nvidia-glx?  Or maybe just 
```

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

```
in a konsole.

---

