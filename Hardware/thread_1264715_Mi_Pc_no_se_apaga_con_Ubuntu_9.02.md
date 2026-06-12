---
title: "Mi Pc no se apaga con Ubuntu 9.02"
date: 2009-09-12
forum: Hardware
---

### Post by PabloGNU/LINUX on 2009-09-12
Como dice el titulo tengo problemas con la energia del equipo. 
y la verdad que no se que podria ser. 

Cuando la apago se pone la pantalla en negro y se reinicia. 

Si alguien puede ayudarme se lo agradeceria.

---

### Post by gmunioz on 2009-09-12
Hola pab....:

Para apagar el ordenador:


Pulsa Aplicaciones --> Accesorios --> Terminal

ejecuta la orden:

```
sudo halt
```

---

### Post by PabloGNU/LINUX on 2009-09-12
No, no me funciona con Sudo halt

Prodia ser algo de la gestion de energia?

---

### Post by faktorqm on 2009-09-14
para mi es un problema de ACPI, pero antes de tocar un monton de cosas probate esto

```
sudo shutdown -h now
```

Creo que es lo mismo que te dijo Gabriel, pero por las dudas probalo. Si te sigue sin andar, podes probar tambien

```
sudo init 0
```

y ahi apaga tambien. Si en todos los casos reinicia, consulta. salu2!

---

