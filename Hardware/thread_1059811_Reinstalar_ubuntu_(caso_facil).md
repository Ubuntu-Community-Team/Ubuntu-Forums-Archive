---
title: "Reinstalar ubuntu (caso facil)"
date: 2009-02-04
forum: Hardware
---

### Post by nahuel_89p on 2009-02-04
Hola gente. Les paso a contar:
Tengo un disco duro 120GB, con ubuntu corriendo en una particion, y con datos en otra ntfs. El tema es que el ubuntu empezó a andar muy mal, y como los datos importantes (musica, fotos, etc) los tengo en la otra particion (la mas grande), quiero directamente reinstalar ubuntu hardy desde cero (tengo el cd de hardy nomas... dp upgradeo a intrepid) en la misma particion donde ya estaba, dejando SIN TOCAR y 100% CONSERVADA la particion donde tengo mis datos.

(Nota: todo esto lo estoy haciendo desde el livecd de hardy).
La mano viene asi: (transcripcion manual del GParted)
[B]
/dev/hdc - Gparted[/B] (mi disco duro)

**/dev/hdc1**    ( "ntfs" | Punto de montaje: "/media/disk" | "93 GB" | Opciones: "boot" ) 
[B]
/dev/hdc2 [/B] ( "extended" | "18.11 GB" | Opciones: "lba" )
___/dev/hdc5   ( "linux swap"| "2 GB" )
___/dev/hdc6   ( "ext3" | Punto de montaje: "/media/disk-1" | "15 GB" )
___/dev/hdc7   ( "linux swap" | "733 GB")

Tengo una swap de mas, creo que esa debio haber quedado de alguna instalación de otra distro, o de otra del mismo ubuntu. No estoy seguro, tampoco se si es relevante.
La /dev/hdc1 es la ntfs, donde tengo toda la musica, etc, que no quiero perder. 
Seguramente es facil, desde el instalador marcar para formatear hdc1 e instalar ahi mismo, pero quiero estar 100% seguro de no perder mis datos. 
Y lo que es programas, configuraciones del ubuntu, etc, no me importa.

Saludos!

---

### Post by euzkoarima on 2009-02-05
Si no te interesa conservar nada de lo que tenés en linux, lo más fácil para mi es que cuando instales pongas particionado manual, primero pasas a "espacio libre" todo lo que ahora está en /dev/hdc2 y después te creas 1 swap y una root o bin swap root y home, como vos prefieras.
No te va a tocar la ntfs y reordenás el resto.

Saludos,
Eduardo

---

