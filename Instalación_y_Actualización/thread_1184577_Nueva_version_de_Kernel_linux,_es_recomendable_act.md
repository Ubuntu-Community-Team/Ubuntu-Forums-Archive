---
title: "Nueva version de Kernel linux, es recomendable actualizar."
date: 2009-06-11
forum: Instalación y Actualización
---

### Post by flakojaime on 2009-06-11
HOla.

Vi hoy en la pagina que salió la versión 2.6.30 del núcleo de Linux.

Es recomendable actualizar?

Tengo un notebook  dell, y por lo que leí, resuelve algunos conflictos.

Gracias...

---

### Post by pagondel on 2009-06-12
hola flakojaime, la verdad es que para que pudieras actualizar el kernel deberias a) compilarlo o b) esperar que alguien lo empaquetara de forma no oficial, dado que los guidelines de Ubuntu a la hora de las actualizaciones indican q Ubuntu no cambiara la version, ya sea del kernel o de algun software en especifico, en una actualizacion a menos que sea necesario. Actualmente la version Alpha 2 de Karmic Koala viene con el kernel .30, pero no es recomendable que la uses a menos que quieras participar de su desarrollo, y nunca usandola como version estable... 
Saludos!

---

### Post by flakojaime on 2009-06-13
Hola

Ok, entonces espero....

Voy a bajar karmic koala para un vistazo..

gracias!

---

### Post by EnriqueK on 2009-06-13
Desde el siguiente enlace lo puedes bajar precompilado, listo para  instalar sin mas trámites.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by flakojaime on 2009-06-13
Hola.

Bueno, tambien lo bajamos y probamos..

gracias!

---

### Post by zhelo on 2009-06-18
resulta que se me actualizo el kermel de la version 2.6.28.-11  (creo que esa es la version) a la version 2.3.28.-13, el asunto es que cuando debo elegir a cual SO deseo entrar(ya que tengo windows y ubuntu), me aparece ubuntu 2.6.28.-11 y mas arriba ubuntu 2.3.28.-13, entro a ubuntu 2.3.28.-13, pero me preocupa la otra version que se queda ahi no mah, que ahago?, la borro?, esta bien que aparesca ahi como opcion para ingresar a ubuntu???

---

### Post by CdK1 on 2009-06-18
Caturra:/home/CdK1# dpkg --get-selections | grep linux-image
linux-image-2.6-amd64                           install
linux-image-2.6.26-2-amd64                      install
linux-image-2.6.29-2-amd64                      install
Caturra:/home/CdK1# 

Te muestra las versiones instaladas

En mí caso borrare éste:

linux-image-2.6.26-2-amd64                      install

Caturra:/home/CdK1# apt-get remove --purge linux-image-2.6.26-2-amd64
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se ELIMINARÁN:
  linux-image-2.6.26-2-amd64*
0 actualizados, 0 se instalarán, 1 para eliminar y 91 no actualizados.
Se liberarán 82,5MB después de esta operación.
¿Desea continuar [S/n]? S
(Leyendo la base de datos ...  00%
88999 ficheros y directorios instalados actualmente.)
Desinstalando linux-image-2.6.26-2-amd64 ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.29-2-amd64
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader
Purgando ficheros de configuración de linux-image-2.6.26-2-amd64 ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.29-2-amd64
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools
Caturra:/home/CdK1# 

Listo, ten en cuenta que puedes tener dos kernel, ejemplo uno que estés compilando a tu gusto y uno genérico por si tienes errres, respecto de los cambios del 2.6.29 a 2.6.30, bueno ve su Changelog y ve si esos cambios te benefician xD

---

### Post by aledruetta on 2009-06-19
Hola Comunidad!

Actualizé el kernel, de la versión 2.6.28-11 a la 2.6.28-13. El problema es que en la versión nueva del kernel no me funciona la máquina virtual que creé con VirutalBox versión 2.2.4 r47978. Con el kernel anterior sí.

¿Qué debería hacer para solucionar este problema?

Saludos y muchas gracias,
Alejandro.

---

### Post by kamus on 2009-06-19
> **aledruetta said:**
> Hola Comunidad!

Actualizé el kernel, de la versión 2.6.28-11 a la 2.6.28-13. El problema es que en la versión nueva del kernel no me funciona la máquina virtual que creé con VirutalBox versión 2.2.4 r47978. Con el kernel anterior sí.

¿Qué debería hacer para solucionar este problema?

Saludos y muchas gracias,
Alejandro.

Deberia haber recompilado el controlador automaticamente con dkms, de todas maneras puedes ejecutar:
```

sudo /etc/init.d/vboxdrv setup

```

y ya va..

---

### Post by zhelo on 2009-06-19
> **CdK1 said:**
> Caturra:/home/CdK1# dpkg --get-selections | grep linux-image
linux-image-2.6-amd64                           install
linux-image-2.6.26-2-amd64                      install
linux-image-2.6.29-2-amd64                      install
Caturra:/home/CdK1# 

Te muestra las versiones instaladas

En mí caso borrare éste:

linux-image-2.6.26-2-amd64                      install

Caturra:/home/CdK1# apt-get remove --purge linux-image-2.6.26-2-amd64
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se ELIMINARÁN:
  linux-image-2.6.26-2-amd64*
0 actualizados, 0 se instalarán, 1 para eliminar y 91 no actualizados.
Se liberarán 82,5MB después de esta operación.
¿Desea continuar [S/n]? S
(Leyendo la base de datos ...  00%
88999 ficheros y directorios instalados actualmente.)
Desinstalando linux-image-2.6.26-2-amd64 ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.29-2-amd64
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader
Purgando ficheros de configuración de linux-image-2.6.26-2-amd64 ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.29-2-amd64
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools
Caturra:/home/CdK1# 

Listo, ten en cuenta que puedes tener dos kernel, ejemplo uno que estés compilando a tu gusto y uno genérico por si tienes errres, respecto de los cambios del 2.6.29 a 2.6.30, bueno ve su Changelog y ve si esos cambios te benefician xD

[COLOR=Red]me dice que yo no soy super usuario para continuar
[/COLOR]

---

### Post by CdK1 on 2009-06-19
Estimado zhelo:

                     Hay ciertas cosas que uno las aprende LEYENDO, cosa que tú NO haces..., es bastante interesante ver el gusto que tienes por usar Ubuntu, pero no haría mal LEER un poco..., porque como veo NO has leído NADA.

                     Acerca de tú "error", antepone "sudo" a los comandos, sin comillas... y por favor no me preguntes que son los "comandos"..., suerte

---

### Post by zhelo on 2009-06-19
> **CdK1 said:**
> Estimado zhelo:

                     Hay ciertas cosas que uno las aprende LEYENDO, cosa que tú NO haces..., es bastante interesante ver el gusto que tienes por usar Ubuntu, pero no haría mal LEER un poco..., porque como veo NO has leído NADA.

                     Acerca de tú "error", antepone "sudo" a los comandos, sin comillas... y por favor no me preguntes que son los "comandos"..., suerte

pero si no pusiste niun sudo al inicio :S
ya filo
ya rregle el asunto
gracias

---

### Post by Carlos C on 2009-06-19
zhelo, me llama la atención tu pregunta. Si otra persona la hiciera entendería, pero has utilizado varias veces "sudo", a raíz de otras consultas que has hecho, por lo que debieras saber de qué se trata. Además, entiendo que eres estudiante de ingeniería informática. No lo digo para agredirte, sino que quiero pedirte que te tomes esto un poco más seriamente.

Para saber de qué se trata sudo puedes mirar acá:

[http://www.guia-ubuntu.org/index.php?title=Sudo](http://www.guia-ubuntu.org/index.php?title=Sudo)

---

### Post by radixs on 2009-06-20
> **zhelo said:**
> pero si no pusiste niun sudo al inicio :S
ya filo
ya rregle el asunto
gracias

Compañero a realizado varias preguntas en las cuales le an hecho anteponer "sudo" si ubieras leído tan solo 10 minutos algo de la documentacion existente te habrias dado cuenta que para realizar cambios, instalar paquetes, entre otros, no se puede realizar siendo un usuario ordinario por ende para poder realizarlos tienes que realizarlos como el administrador de la maquina.

Nunca te haz peguntado por que cuando instalaz un paquete en agregar o quitar te pide contraseña?
o tambien cada vez qeu editas la sources.list siempre es "sudo gedit /etc/apt/sources.list" y no "gedit /etc/apt/sources.list" esto lo podrias modificar sin "sudo" estando logueado como "root".

PD: nadie nace sabiendo por ende si quieres apreder y realizar menos preguntas, la leectura es obligaoria.

Nota: google ahora es tu mejor amigo, asi que a tomarle mas atencion ;)

100% de acuerdo con Carlos_c

---

### Post by aledruetta on 2009-06-20
> **kamus said:**
> Deberia haber recompilado el controlador automaticamente con dkms, de todas maneras puedes ejecutar:
```

sudo /etc/init.d/vboxdrv setup

```y ya va..

Gracias Kamus, funcionó a la perfección!
Saludos,
Alejandro.

---

### Post by guillermolisi on 2009-06-22
> **zhelo said:**
> [COLOR=Red]me dice que yo no soy super usuario para continuar
[/COLOR]
Antepone sudo a cada comando apt/dpkg. Te pedira tu clave de usuario y no se mostrara nada en la pantalla (por seguridad).

---

### Post by aledruetta on 2009-09-07
Estoy probando Alpha 5 de Karmic. Hasta hora, me resultó más estable el Alpha 3, con esta nueva versión he tenido varios mensajes de error y cuelgues que no tuve con la 3.

---

### Post by guillermolisi on 2009-09-07
> **zhelo said:**
> [COLOR=Red]me dice que yo no soy super usuario para continuar
[/COLOR]
Antepone "sudo" (sin las comillas) al resto de la linea de comando que queres ejecutar.

Te pedira que ingreses tu clave de usuario y luego ejecutara sin que vuelva a salir ese mensaje.

Con sudo tu cuenta de usuario se arroga los privilegios de superusuario/administrador del sistema (root).

---

