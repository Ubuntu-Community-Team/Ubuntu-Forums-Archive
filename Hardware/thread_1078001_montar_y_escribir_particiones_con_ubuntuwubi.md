---
title: "montar y escribir particiones con ubuntu/wubi"
date: 2009-02-22
forum: Hardware
---

### Post by joseluis on 2009-02-22
hola amigos
instalé Xubuntu con Wubi, pero no monta las particiones win.
Encontre el disco de win en la carpeta HOST, todos los archivos, puedo abrirlos, pero no puedo escrbir en el disco.
Instalé gparted para ver las particiones y logicamente me muestra solo una particion fat32 (la de win), con lo cual no puedo meterme en el fstab para modificar nada.
¿como se hace entonces para leer y escribir desde este metodo de instalación?
gracias

---

### Post by gmunioz on 2009-02-23
Hola jos....:

Instala desde Synaptic, disk-manager.

Luego pulsando:

sistema - administración - administrador de disco

Monta las particiones.

Saludos.

---

### Post by sajnox on 2009-02-23
Postea la salida del comando

```
sudo fdisk -l

```

---

### Post by joseluis on 2009-02-23
hola...el fdisk -l es
Disco /dev/sda: 30.0 GB, 30005821440 bytes
255 cabezas, 63 sectores/pista, 3648 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x99b999b9

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3647    29294496    c  W95 FAT32 (LBA)

El disk manager no lo encuentro en los repos. No lo pude instar ni con synaptic, ni cn agregar programas,ni con apt-get

---

### Post by joseluis on 2009-02-23
pude instalar el disk manager..pero aun no puedo escribir. el disk manager me muestra que el sda1 esta para montado en /media/sda1  y esta tildado soporte para escritura...
y no pasa nada

---

### Post by sajnox on 2009-02-24
Proba buscar disk-manager (no te olvides del guion del medio)

Para montar la unidad proba con lo siguiente:

sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1

Si eso funciona en el directorio /media/sda1 deberias tener montado el disco de windows y ya estamos para agregarlo en el fstab para que se monte cuando inicias el equipo

---

### Post by joseluis on 2009-02-24
el disco ya se monta..y todo bien, pero aún no puedo escribir en él!

---

### Post by sajnox on 2009-02-25
Eso es por que lo monta el root y es el unico que tiene permisos para hacerlo.

Che, alguien que pase la linea que agregar al fstab que hace poco borre la ultima particion NTFS que tenia en mi maquina

---

### Post by clasificado on 2009-03-04
Con poner users alcanzaba en mis épocas de 6.06

Tendría que probarlo en un wubi, que sé que tiene una vuelta rara con el bootstrap para iniciar desde ntfs y de ahi tunelizar el ext3

por ahi venga con sorpresa

clasificado

---

### Post by joseluis on 2009-03-04
> **sajnox said:**
> Eso es por que lo monta el root y es el unico que tiene permisos para hacerlo.

Che, alguien que pase la linea que agregar al fstab que hace poco borre la ultima particion NTFS que tenia en mi maquina

ok..todavía no pude solucionar el problema....cuando instalé el wubi me pidio poner user y pass. Le pongo tal y tal, entro con esto en el inicio..y resulta que no pasa nada. No puedo escribir en el disco. Si está entrando como rot no entiendo como entrar entonces para escribir...¿alguien que lo entienda y pueda ayudarme? gracias

---

### Post by clasificado on 2009-03-05
en principio, y para probar lo de root y eso

probá hacer abrir el thunar de xfce, pero con permisos de root
```
gksudo thunar
```
eso te va a abrir una instancia de thunar con la autoridad de un root.

andá al /host y hace algo, borra algo o create una carpeta, y fijate que onda

DEBERIAS DE PODER. Sino es otra cosa

clasificado

---

