---
title: "Problema con partición"
date: 2008-08-03
forum: Hardware
---

### Post by sartrejp on 2008-08-03
Les explico lo que pasa a ver si alguno puede darme una mano.
Cuando inicio la Pc me hace el routine check de disco. Cuando llega a sda4 (la partición /home) me da el siguiente error:
has 10 multiply-claimed blocks shared with 1 file
/dev/sda4: Recycled/Dg13.rar inode #9068614mod tino Aug 2 18:00:00 2008

Me dice que ponga la contraseña root o presione ctrl+D para "skip" (no se como traducirlo pero entiendo lo que quiere decir)
Si aprieto ctrl+D inicia normalmente y a simple vista no hay problema
Si pongo la contraseña root me dice que corra fsck con las opciones -a o -p en forma manual, pero cuando voy a hacerlo me advierte de los "severage filesystem damage" que puede haber al correr fsck sobre un disco montado, y al ser el home, no puedo desmontarlo.

¿Que puedo hacer?

¿Hago fsck desde el live-cd?

Alguien sabe que puede ser ese error y si hay algún modo (otro) de solucionarlo)

Tengo Windows instalado en la misma pc, en otra partición, pero no me deja hacer scandisk sobre la partición que tiene el problema (es ext3).
Si alguien tiene una respuesta.... les agradezco

---

### Post by Hei Ku on 2008-08-03
Lo mejor es que corrar el fsck desde un LiveCD. Primero hacé backup de la partición, obviamente.

---

