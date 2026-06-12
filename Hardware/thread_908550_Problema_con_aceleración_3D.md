---
title: "Problema con aceleración 3D"
date: 2008-09-02
forum: Hardware
---

### Post by cdesseno on 2008-09-02
Hace poco que instalé el Hardy pero estoy teniendo problemas con la aceleración 3D. Se evidencia, por ejemplo, al ejecutar un proyecto con OpenGL o utilizando el mismo Google Earth (va lento y lagueado este último).

En cuanto a hardware, tengo una notebook HP 530, no tiene placa de video, pero si una integrada pasable.

Alguna solución? Gracias.

---

### Post by sajnox on 2008-09-02
Hola, podria ser un poco mas especifico en cuanto a la placa de video, si lo tenemos se nos puede hacer mucho mas facil darte una mano.

Si no lo tenes en el manual de la NB, lo podes buscar en las especificaciones en la pagina del fabricante

Saludos y no dejes de decirnos que maquina tenes que seguramente el problema es facil de solucionar

Saludos

---

### Post by cdesseno on 2008-09-02
Ahí están los datos: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/264170]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/264170") del xorg, lspci, etc. Gracias!

---

### Post by sajnox on 2008-09-02
Cpn respecto al Google Earth es muy comun que tengas que desactivar los efectos 3d, es un problema comun.

Respecto a la placa veo que es una Intel integrada, yo tuve dos maquinas con Intel integrada y mis experiencias fueron mas que buenas.

Los efectos de escritorio como te funcionan en la PC?

---

### Post by cdesseno on 2008-09-03
> **sajnox said:**
> Cpn respecto al Google Earth es muy comun que tengas que desactivar los efectos 3d, es un problema comun.

Respecto a la placa veo que es una Intel integrada, yo tuve dos maquinas con Intel integrada y mis experiencias fueron mas que buenas.

Los efectos de escritorio como te funcionan en la PC?

Con el Google Earth es MUY tedioso, anda lentísimo. Compiz anda perfecto, tengo plugins como el cubo, el efecto de cierre con fuego, etc. instalado.

---

### Post by sajnox on 2008-09-03
Probaste Google Earth con compiz desactivado?

Si estas con hardy instala el fusion icon y desde ahi elegis cual usar

```
sudo apt-get install fusion-icon
```

Version Lerena

```
sudo aptitude install fusion-icon
```

(Lo ultimo es un chiste para un amigo del foro, cualquiera de las dos es lo mismo para el caso)

---

### Post by cdesseno on 2008-09-03
Se ve que es otra cosa. Intenté desactivando compiz y nada.

---

### Post by sajnox on 2008-09-03
Siguiente paso ejecutarlo desde un terminal y ver que tipo de errores tira

---

### Post by cdesseno on 2008-09-03
Nop, no me tira errores.

Estuve buscando en Google, y parece que es un error en los drivers de la placa intel. A mucha gente le ocurre, especialmente con la misma notebook.

Gracias!

---

