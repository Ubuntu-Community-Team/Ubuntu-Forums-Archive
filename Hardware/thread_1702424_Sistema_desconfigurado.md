---
title: "Sistema desconfigurado"
date: 2011-03-07
forum: Hardware
---

### Post by Cholon on 2011-03-07
hola mi problema es que estaba ocuapando un programa, creo que se llama photorec que es para recuperar archivos borrados y creo que este provoco desconfiguraciones en el sistema, cuando trato de abrir una terminal, se abre pero esta no me muestra nada se queda con un fonfo plomo , igual cuando abro cualquier otra cosa como el monitor del sistema me pasa lo mismo, cuando le doy a la opcion de apagar o reiniciar me muestra el cuadrito para confirmar pero este no tiene nada adentro, pero si le ago un click a la posicion donde me acuerdo que estaba el boton paradarle a confirmar si funciona ¿nose si se entiende¿ no puedo ni imprimir pantalla para explicar porque no me lo abre, e igual en firefox tengo problemas supongamos abro una pagina y se queda en la anterior y cuando apreto alguna flecha o algo recien cambia por lo que supongo que tambien tiene que ver con la imagen que se queda como pegada tambien me pasa que al abrir la particion del disco donde esta mis archivos que estan en windows me sale un mensaje que dice No se pudo montar Sistema de archivos de 32 GB Error creating moint point: No space left on device

---

### Post by guillermolisi on 2011-03-07
Cuantos discos tiene esa PC ? De que tamaño son ? Cuantas particiones y de que tamaño posee cada uno ?

El mensaje que mencionas advierte que una particion no se pudo montar porque la particion / (root, raiz) se ha quedado sin espacio libre suficiente como para trabajar adecuadamente.

---

### Post by Cholon on 2011-03-07
Tengo un disco de 40 Gb  las particiones estan divididas en este tamaño aproximadamente  ntfs 32 gb swap 512 mb ext4 6 gb

---

### Post by guillermolisi on 2011-03-07
> **Cholon said:**
> Tengo un disco de 40 Gb  las particiones estan divididas en este tamaño aproximadamente  ntfs 32 gb swap 512 mb ext4 6 gb

6 Gb para / directory es demasiado poco. Solamente con actualizaciones, archivos temporales y programas que instales con el pasar del tiempo se llenara enseguida (como ya ocurrio). Ni hablar si en tu home directory estas guardando archivos.
Esto es lo que impide que se monten otras particiones tales como la NTFS que mencionas.

Mi recomendacion, sin indagar mucho en el uso que le das a esa maquina, es que el / directory tenga alrededor de 20 Gb para no tener problemas.

En caso de no poder redimensionar las particiones, entonces **limpiar cuidadosamente** archivos viejos, obsoletos, temporales, paquetes viejos, etc. Es decir, hacer espacio eliminando archivos que no utilices mas.

---

### Post by Cholon on 2011-03-07
muchas gracias no se me habia ocurrido simplemente desintalar paquetes o programas, ya se arreglo todo  gracias

---

### Post by Hakunka-Matata on 2011-03-07
Pongase en el Terminal el codigo```
df -h
``` a ver informaciones sobre los discos que hay.  Si se puede ver algo en la pantalla

---

