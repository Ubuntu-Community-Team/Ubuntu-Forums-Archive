---
title: "problema en pantalla"
date: 2010-06-04
forum: Hardware
---

### Post by =V= on 2010-06-04
Hola 

dejo una consulta

Tengo ubuntu 10.04 desktop en una  netbook dell inspiron 11z.

Noto que  en intervalos de algunos minutos  se produce sobre la pantalla
una especie de "parpadeo"...o algo asi como cuando hay una interferencia por 
celular y la pantalla se mueve...

la verdad no tengo idea a que se puede deber ...si alguien tiene idea , se agradece
la ayuda..

muchas gracias como siempre..
saludos !

---

### Post by WooS on 2010-06-05
> **=V= said:**
> Hola 

dejo una consulta

Tengo ubuntu 10.04 desktop en una  netbook dell inspiron 11z.

Noto que  en intervalos de algunos minutos  se produce sobre la pantalla
una especie de "parpadeo"...o algo asi como cuando hay una interferencia por 
celular y la pantalla se mueve...

la verdad no tengo idea a que se puede deber ...si alguien tiene idea , se agradece
la ayuda..

muchas gracias como siempre..
saludos !




saca la computadora del horno!! jajajaj
fijate si no tenes algo cerca como un parlante o algun dispositivo q pueda estar j******o
espero q lo puedas solucionar

---

### Post by =V= on 2010-06-07
jaaaaa...

noo..la saque del horno y sigue...terrible

---

### Post by silverhuman on 2010-06-09
> **=V= said:**
> Hola 

dejo una consulta

Tengo ubuntu 10.04 desktop en una  netbook dell inspiron 11z.

Noto que  en intervalos de algunos minutos  se produce sobre la pantalla
una especie de "parpadeo"...o algo asi como cuando hay una interferencia por 
celular y la pantalla se mueve...

la verdad no tengo idea a que se puede deber ...si alguien tiene idea , se agradece
la ayuda..

muchas gracias como siempre..
saludos !

Tengo el mismo problema, en una Dell inspiron 1545 tarjeta grafica intel GM45, solo en la version 10.4 de Ubuntu; la 9.10 corre perfectamente. Probé actualizando los controladores y sigue con el mismo problema. Es un bug creo que todavia no la corrigen, me queda por instalar la ultima version del controlador de mi tarjeta y compilar haber como va el tema.

---

### Post by rco251 on 2010-06-15
hola a todos, a mi me pasa igual, tengo una lenovo con placa de video intel 4 series mobile..
si alguien logro solucionarlo le agradeceria que lo comente gracias..

---

### Post by =V= on 2010-06-15
hola

todavia no encontre solucion al problema...si llego a encontrarla ..doy aviso

saludos

---

### Post by rco251 on 2010-06-19
hola.
Estan seguros de que es problema de ubuntu y no de un problema de hardware o algo asi??

---

### Post by silverhuman on 2010-06-24
Bueno gente, he solucionado el problema agregando las siguientes lineas:

```
sudo gedit /etc/default/grub
```

a continuación, busque esta línea en el archivo de texto: 
GRUB_CMDLINE_LINUX ""

y la modifique de esta manera:
GRUB_CMDLINE_LINUX " i915.powersave=0 " 

a continuación guarde.


Por otra parte he instalando la ultima versión estable del kernel de linux la 2.6.34; ingresar a ```
[http://kernel.ubuntu.com](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)
``` y descargar los siguientes paquetes:

*linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb	
*linux-headers-2.6.34-020634_2.6.34-020634_all.deb	
*linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb

A continuación explico el procedimiento:

Aclaro que esta es una de las formas que existe para poder compilar, a mi criterio la mas sencilla, en este caso es un kernel genérico y no uno personalizado.

RECOMENDACIONES MUY IMPORTANTES:

- Crear una carpeta con el nombre kernel 2.6.34 y poner los 3 archivos que has bajado dentro (así no te complicarás).

- NO ELIMINAR el kernel antiguo después de instalar el nuevo.

Desde un terminal nos ubicamos en la carpeta que creamos en mi caso kernel 2.6.34

```
cd /home/tu_usuario/kernel 2.6.34
```
Luego tecleamos:

```
sudo dpkg -i *.deb
```

Y comenzara la instalación. Una vez terminado el paso anterior podemos comprobar si efectivamente se instalaron los nuevos paquetes con el navegador nautilus situándonos en las carpetas /usr/src, donde podremos apreciar que efectivamente se instalo el nuevo kernel.

*linux-headers-2.6.34-020634_2.6.34-020634
*linux-headers-2.6.34-020634_2.6.34-020634-generic

Si todo finalizo correctamente, reiniciamos la máquina.

NOTA: este procedimiento funciona con cualquier kernel que se instale.

Por el momento todo funciona perfectamente, aclaro que yo no estoy utilizando compiz por lo cual no puedo dar fe del mismo rendimiento. Saludos

---

### Post by =V= on 2010-06-25
hola silver 

muchas gracias por el aporte !

voy a probar a ver que tal corre y despues cuento 

saludos !

---

