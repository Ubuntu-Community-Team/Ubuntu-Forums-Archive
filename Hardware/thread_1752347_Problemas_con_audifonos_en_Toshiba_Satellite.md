---
title: "Problemas con audifonos en Toshiba Satellite"
date: 2011-05-07
forum: Hardware
---

### Post by vrolok on 2011-05-07
Hola.
Tengo un problema a la hora de conectar unos audifonos a mi laptop. La cuestion es que los altavoces si se escuchan bien, pero hasta ahora nunca le habia conectado unos audifonos a la maquina, y ahora que lo hice me encuentro con que al conectarlos, los altavoces siguen sonando. Lo que quiero saber es cómo hacerle para que cuando conecte los audifonos dejen de sonar los altavoces y sólo se escuchen los audifonos.
No se que datos necesiten para poder ayudarme, por lo pronto les digo que mi maquina es una laptop Toshiba Satellite.
Espero su ayuda.

---

### Post by Sortega on 2011-05-07
Hola, yo también tengo un Toshiba Satellite y se me presento el mismo problema. Primero que nada este problema en mi caso se soluciono con el kernel 2.6.38, pero en el caso de que no tengas instalado ese kernel se puede realizar lo siguiente:
1. Instalar el repositorio de Desarrollo de Audio en Ubuntu
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
```
2. Luego actualizar
```
sudo apt-get update
```
3. Ahora instalar el driver del modulo correspondiente a tu kernel
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
o en caso que tengas kernel PAE instalado
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)-pae
```
4. Realizar un upgrade
```
sudo apt-get upgrade
```
y reinicias.

Con todo lo anterior se debería solucionar el problema, pero hay un pero en esto. No se porque motivo se me activo un beep al reiniciar o apagar el equipo y todo paso al hacer esto pero al menos se soluciono el problema de los audífonos.

Espero que esto puedas solucionar tu problema.

Saludos

---

### Post by vrolok on 2011-05-07
Oye Sortega, para empezar gracias por contestar, bueno mi kernel es 2.6.32-31 por lo que hice lo que mencionas.
Pero al llegar al paso 3, la terminal me arroja esto:
```
vrolok@vrolok-laptop:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete linux-alsa-driver-modules-2.6.32-31-generic

```
Por lo que no creo que tenga caso hacer el upgrade, ya que no encontro lo buscado.
Quisiera saber como hiciste para tener el kernel 2.6.38 y si es posible, decirme como instalarlo, creo que con eso se resolveria mi problema

---

### Post by vrolok on 2011-05-07
Eso es todo!!!
Ya quedó!!!
Sólo le instale el kernel 2.6.38 y listo!!!
Se resolvió mi problema.
Gracias Sortega

Para quien le pueda pasar como a mi y quiera instalar el kernel 2.6.38 les dejo este link: 
[http://emslinux.com/como-instalar-el-kernel-2-6-38-en-ubuntu-linux-10-04-y-10-10/]("http://emslinux.com/como-instalar-el-kernel-2-6-38-en-ubuntu-linux-10-04-y-10-10/")

---

