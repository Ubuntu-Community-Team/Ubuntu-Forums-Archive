---
title: "Como agrego 1 HD IDE al SATA de mi PC?"
date: 2008-05-24
forum: Hardware
---

### Post by atari130xe on 2008-05-24
Gente, tengo una PC nueva que viene con un HD SATA de 260GB, donde tengo instalado (en 3 particiones) XP (para los juegos de mi sobrino), una "/" y una -la más grande- con mi /home. todo funciona de maravillas (el tema del sonido lo "solucioné" cambiando el sonido on board por la PCI 5.1 que tenia en la otra PC). Ahora decidí agregarle a esta nuueva PC el H IDE de 80GB que tenia la otra PC, donde tenía: en una partición: Elive, y en las otras 2 (/ y /home). Resulta que al colocarlo el sistema sencillamente NO FUNCIONA, se cuelga en el GRUB con error 15, 13, y otros más, es obvio que la PC bootea en el IDE (a pesar de hice el cambio en el BIOS de sequencia de Booteo), lo tuve que sacar porque no arrancaba, alguien podria indicarme como hacer el paso a paso para poder agregarle ese disco, tengo mucha data y me gustaria poder utilizarla. 
Mother Asus M2N sli, bios Award (el azul jeje).
gracias!:)

---

### Post by Mauro22 on 2008-05-24
Cuando pones un disco en otra pc con otro hardware, tenes que reinstalar el sistema.


Yo cuando cambie la pc, ubuntu, andaba por ahi nomas, se colgaba, no arrancaba, etc, 


Tenes que reinstalar la /, ya que tenes /home aparte no vas a perder nada.

---

### Post by faktorqm on 2008-05-24
Muchachos por favor no pierdan la calma. Yo mismo lo he hecho y aunque reinstalar es la solucion a todos los problemas, no siempre el problema es insolucionable sin reinstalar. 

**Aclaracion: los dos discos son IDE, solo que uno es SATA (Serial ATA, ATA Serial) y el otro PATA (Parallel ATA, ATA paralelo).**

Los errores del grub son por que cambió el hardware, entonces te esta leyendo cualquier cosa, de hecho, si pones un live-cd, que ocurre? seguramente veas todos los discos...

Ahora bien, mas allá de todo eso, el problema pasa a ser como reconoce el orden de los discos la mother, es decir, seguramente tenes tantos problemas con el grub por que cambiaron de orden, entonces no sabe a donde arrancar.

Lo que tendrias que fijarte es, con el disco desconetado el orden de los discos, y luego poner el PATA como secundario esclavo (por ejemplo), y asegurarte de que el disco SATA estaba donde estaba antes. Ahi deberia arrancar sin ningun problema y a partir de ahi es otro paso montarlo cuando inicia y esas cosas.

Salu2!

---

### Post by UBUjuan on 2008-05-25
el ubuntu es el 8.04? porque hicieron un cambio: ahora todos los discos se nombran sdX... sea ide o sata. el problema debe ser que cuando instalaste el el sata te lo reconocio como sda y luego al agregar el ide, este paso a ser sda y el anterior sdb, por ende la particion / ahora es sdb1 y por eso no arranca el grub.
Posible solucion: configura el ide como esclavo a ver si te lo reconoce como sdb.

---

