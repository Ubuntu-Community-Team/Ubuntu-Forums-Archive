---
title: "Particion SWAP"
date: 2008-10-17
forum: Hardware
---

### Post by gonzalo4018 on 2008-10-17
Hola...

Al instalar Ubuntu, Le puse al SO 37 GB y al otro disco (SWAP), le puse 40 GB!!!!:lolflag:, cuando lo ideal serian 2 o 3, por lo que lei, como hago para sacarle 38 GB de los que tengo en ese y mandarselos al de Windows?

---

### Post by eddietours on 2008-10-17
creo que lo puedes hacer con gparted

---

### Post by Thalskarth on 2008-10-17
> **eddietours said:**
> creo que lo puedes hacer con gparted

Lo mejor es que arrancas el sistema con un LiveCD, podes usar el de ubuntu mismo o sino, te recomiendo el de [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php").

Una vez que arranca el liveCD, abri el Gparted, selecciona la particion SWAP, boton derecho -> Cambiar tamaño

achicala hasta lo que desees... y luego, lo mismo con la de windows o cualquier otra 'agrandandola' para que ocupe el espacio que quedo libre...


PD: Si la particon sale bloqueada (icono de candado), boton derecho en el gparted... desbloquear :)

---

### Post by gonzalo4018 on 2008-10-18
no lo puedo hacer desde windows con partition magic?

---

### Post by pol666 on 2008-10-18
si por que no. pero lo mejor es usar el live cd

---

### Post by gonzalo4018 on 2008-10-18
como hago?
Entro con el Live CD de Ubuntu, y despues, donde ecuentro el programa?
me explicarias?

---

### Post by santiagoward2000 on 2008-10-18
> **gonzalo4018 said:**
> como hago?
Entro con el Live CD de Ubuntu, y despues, donde ecuentro el programa?
me explicarias?

Hola!
Una vez que entraste con el LiveCD andá a **Sistema > Administración > Editor de Particiones**.
Ahí podés modificarlas. Fijate que tenés que desmontarlas antes de poder editarlas con click derecho, desmontar. También a la de SWAP, le hacés click derecho, desactivar intercambio.
Suerte!

---

### Post by gonzalo4018 on 2008-10-18
Ok, gracias

---

### Post by santiagoward2000 on 2008-10-19
> **gonzalo4018 said:**
> Ok, gracias

De nada! :)
¿Anduvo?

---

### Post by gonzalo4018 on 2008-10-19
> **santiagoward2000 said:**
> De nada! :)
¿Anduvo?

la de SWAP si, no anduvo para agregarle mas al de XP

---

