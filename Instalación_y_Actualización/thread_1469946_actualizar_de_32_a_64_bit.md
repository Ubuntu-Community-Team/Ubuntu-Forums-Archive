---
title: "actualizar de 32 a 64 bit"
date: 2010-05-02
forum: Instalación y Actualización
---

### Post by asterix77 on 2010-05-02
Estimados:

Una consulta, tengo jaunty 32 bit instalado en mi pc, quiero actualizarme a lucid lynx pero de 64 bit. No tengo home separado, por lo que ¿será posible actualizarlo sin tener que formatear, y por supuesto no perder mis archivos?. En otro pc actualicé windows vista de 32 bit a windows 7 64 bit, y para mi sorpresa, conservó mis archivos, pero no sé si sucederá lo mismo acá.

Saludos

---

### Post by Carlos C on 2010-05-02
Se ve difícil, sin tener el home separado creo que deberás formatear todo. Mejor es que respaldes y luego instales separando el home.

Saludos.

---

### Post by asterix77 on 2010-05-03
hummm
 
Creo que es lo mejor, así en futuras actualizaciones no tendré esos problemas.
 
 
Saludos

---

### Post by EnriqueK on 2010-05-03
Puedes respaldar tu carpeta de usuario y luego la repones en el nuevo sistema tenga o no la /home separada. Por ejemplo si haces 
cd /tmp
sudo tar -zcvf cuenta.tar.gz /home/$USER
Esto te va a crear en directorio temporal /tmp un archivo llamado cuenta.tar.gz que será una copia comprimida de tu carpeta de usuario.
Cuanto toque reponer creando la cuenta con el mismo nombre de usuario, copiar el archivo cuenta.tar.gz  al directorio /tmp de la nueva instalación y luego pones
 sudo -i
 rm -Rf /home/usuario
 cd /tmp
 tar -zxvf cuenta.tar.gz --directory /
Referente a la migración en si. puedes usar Synaptic, en la instalación actual entra a Archivo--> Guardar selecciones como--> marcas el casillerro "guardar el estado completo mo solo los cambios" , le das un nombre  y al aceptar te generará un archivo de textos en tu carpeta de usuario y que tendrá el listado de todos los paquetes instalados, este archivo lo llevas a la nueva instalación y una vez definidos los repositorios que sean los mas equivalentes posibles, entra a Synaptic-->Archivo--> Leer selecciones , doble ckick sobre el archivo de textos  generado antes -->Aplicar-->Aceptar y a esperar . esta espera puede ser muuuy larga.

---

### Post by asterix77 on 2010-05-03
Está muy bueno EnriqueK lo que indicas de Synaptic. Otra razón más para escoger Ubuntu,  desconocía esa opción.


Saludos

---

### Post by EnriqueK on 2010-05-03
No necesariamente pasa solo con Ubuntu, usando este método instalé Debian Lenny 32 bits, basado en una lista de paquetes sacada de una instalación de Ubuntu 64 bits.

---

### Post by Carlos C on 2010-05-06
¿Lo damos por resuelto?

---

### Post by asterix77 on 2010-05-06
Si Carlos, completamente.


Saludos

---

### Post by asterix77 on 2010-05-06
Si Carlos, completamente.


Saludos

---

### Post by asterix77 on 2010-05-06
Si Carlos, completamente.


Saludos

---

### Post by asterix77 on 2010-05-06
Si Carlos, completamente.


Saludos

---

### Post by asterix77 on 2010-05-06
Si Carlos, completamente.


Saludos

---

### Post by moreback on 2010-05-08
Creo que a Carlos_C le quedó claro, no había para que repetir tanto jajaja

---

### Post by Sortega on 2010-05-08
+1 xD

---

### Post by isaimartinez on 2011-03-31
Una consulta, tengo poco tiempo en el fabuloso mundo de ubuntu y me gustaria saber si al tener instalado ubuntu 10.04 de 64 bit el cual deseo actualizar a la version ubuntu 10.10, esta se actualiza a la version de 64 bit de ubuntu 10.10???

gracias

---

### Post by asterix77 on 2011-04-01
Si lo haces a través del gestor de actualizaciones o por la terminal a través del comando

$[I]update-manager -d

Te respetará la arquitectura, si lo haces por livecd, asegurate que corresponda a la arquitectura de 64 bit.

Eso si, antes de actualizar por internet, asegurate de tener todo actualizado en la versión anterior.

Mira este link para más detalle:

[http://angelverde.info/como-actualizar-a-ubuntu-10-10-maverick-meerkat-10-04-lucid-lynx-karmic/](http://angelverde.info/como-actualizar-a-ubuntu-10-10-maverick-meerkat-10-04-lucid-lynx-karmic/)


Saludos
[/I]

---

