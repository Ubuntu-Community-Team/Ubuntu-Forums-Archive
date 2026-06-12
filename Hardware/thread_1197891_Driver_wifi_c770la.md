---
title: "Driver wifi c770la"
date: 2009-06-26
forum: Hardware
---

### Post by NoblezaPikardo on 2009-06-26
Hola a todos.
A ver si alguien me puede ayudar con esto. Tengo una compaq c770la, le puse ubuntu 9.04 y no puedo hacer funcionar el wifi... maldito driver. Lo demás anda todo perfecto. Estube buscando unos días en la web y vi que muchos tienen el mismo problema. Seguí algunas recomendaciones o tutoriales pero no hubo caso. Si alguien tiene idea de como puedo solucionarlo, le agradezco me diga como.
Gracias

---

### Post by luks911 on 2009-06-27
Lo primero: en una terminal ejecutá ```
lspci
``` y ```
lshw -C Network
```
y pegá las salidas acá. Así podemos ver qué placa tenés, qué modulo trata de usar, etc.

---

