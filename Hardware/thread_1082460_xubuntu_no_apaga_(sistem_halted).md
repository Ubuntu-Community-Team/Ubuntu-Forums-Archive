---
title: "xubuntu no apaga (sistem halted)"
date: 2009-02-27
forum: Hardware
---

### Post by granjero on 2009-02-27
cuando cliqueo el icono de la puertita y después pongo apagar la pc hace un proceso de apagado casi normal hasta que llega a un mmonton de números entre corchetes y **sistem halted**... y no apaga....

que podrá ser?

muchas gracias de antemano!

salud!

---

### Post by granjero on 2009-03-01
SOLVED

encontré la solución! 

modifique el menu.lst

```
sudo mousepad /boot/grub/menu.lst
```

agregué la linea **acpi=force** al final de la primer linea que empieza con kernel...

kernel  /boot/vmlinuz-2.6.24-23-generic root=UUID=d68ef891-ac41-444c-a31d-d4afa4f5b66e ro quiet splash **acpi=force**

también modifique /etc/modules 

```
sudo mousepad /etc/modules 
```

agregué **acpi=off apm=power_off**

salud!

---

