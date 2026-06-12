---
title: "Fallo al instalar linux en Aspire Z5751"
date: 2011-07-08
forum: Hardware
---

### Post by Einfachlacm on 2011-07-08
Hola,

Recurro al foro porque no logro de ninguna manera instalar ningun SO nuevo en la computadora que acabo de comprar.

Se trata de la [Acer Aspire Z5751]("http://support.acer.com/mx/es/acerpanam/desktop/2010/acer/aspire/AspireZ5751/AspireZ5751nv.shtml"). Las caracteristicas de la AIO son las siguientes:
- Intel i5 3,2 Ghz
- Nvidia GT320M  1024 Mb
- 6 Gb ram ddr 3
- Hd 1 tb
- Monitor 23'

Traté de arrancar via USB live y CD live con:
- Ubuntu 11.04 64 bits
- Mint 11 64 bits
- Mint 10 KDE 32 bits
- Mandriva 2011 RC 1 64 bits
- ElementaryOS 0.1

Con todos me pasa lo mismo, luego de la carga de la BIOS la pantalla se queda negra con un guion titilando a la izquierda en el margen superior.
Y no pasa nada.

Traté por las dudas con XP Pro, y me aparecio el error azul (lol) en la instalacion. Asi que tampoco pude.

Ahora lo curioso.

Para probar coloqué algunos viejos cds de Mint 7 y Mint 7 KDE y arranco sin problemas (salvo por la resolucion que estaba demasiado grande para el monitor). Luego trato con Ubuntu 10.04 y... la unica que arranca bien pasando la parte de black screen, pero también anda bien la resolucion.

Probé USB y CD, Probé Netbootin y Live CD Creator, probé varias distros diferentes. Que anden las viejas y no las nuevas es incomprensible. De la 10.04 para aca no anda ninguna. Lei comentarios en internet de gente que ya utiliza esta misma computadora con las nuevas versiones (11.04) y no tienen ningun problema.

Encontré también algo que quizas tiene que ver con los problemas, una actualizacion de Bios: [BIOS for Linux Updates default SATA mode to 'Native IDE'.]("http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=3351"). No entiendo para que sirve pero quizas tiene alguna relacion. Por otra parte, solo aparecen las explicaciones de flasheo de la BIOS desde Windows (que no logro instalar) y DOS, para el cual agradeceria explicaciones de como puedo hacer.

En las versiones que logro ejecutar, wireless no detecta nada y lo mas extranio, el la conexion ethernet por cable tampoco, por lo que no tengo acceso a internet.

Ahora tengo instalada la 10.04 sin poder conectar a internet ni por wireless ni por cable.

Alguna idea?

Gracias.

---

### Post by gmunioz on 2011-07-09
Prueba con Linux Mint Debian 64 bits

[http://www.linuxmint.com/edition.php?id=75](http://www.linuxmint.com/edition.php?id=75)

---

### Post by Einfachlacm on 2011-07-11
Voy a probar y luego cuento resultados.

---

### Post by Einfachlacm on 2011-07-12
Linux Mint Debian Edition solo carga el grub y luego cuando le doy entrar en modo normal o en "compatibily mode" me aparece el error siguiente: "device descriptor read/64 error -110", y ahi se queda.

Linux Mint 11 en modo normal y modo compatibily me abre el SO en la consola con un error diciendo shell-init: error retrieving current directory: getcwd: cannot acces parent directories: No such file or directory. Le doy startx y me dice getcwd failed.

Actualicé la BIOS a esta nueva version de hace dos meses:
BIOS for Linux Updates default SATA mode to 'Native IDE'. 
[http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=3351](http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=3351)

Los pasos anteriores los probé con dos modos  "Native IDE" y "AHCI" de la BIOS de "Integrated Peripherals > Onboard SATA mode", y los resultados fueron los mismos.

Windows 7 y Ubuntu 10.04 (pero sin WIFI ni Ethernet) andan.

Ahora si se me acabaron las ideas, pensé que con la actualizacion de BIOS iba a andar.

Se les ocurre algo?

Gracias.

---

### Post by guillermolisi on 2011-07-12
Por que usas 64 bits ? Porque tenes mas de 3 Gb RAM ?

Tengo una note con 4 Gb RAM y procesador de 64 bits pero la implementacion del BIOS no esta completa y hay caracteristicas fundamentales para administrar el mapeo de memoria por encima de los 3Gb que no estan disponibles.

Me canse de los errores, similares a los que describis, y termine instalando 32 bits con kernel PAE. Nunca mas tuve problemas.

Puedo usar toda la memoria, funciona todo el software y ahorro en consumo de Mbs RAM (los SO de 32 bits consumen algo menos de RAM que los de 64).

Y respecto del rendimiento, nunca note la diferencia.

---

### Post by gmunioz on 2011-07-13
Errores de este tipo:
[I]device descriptor read/64 error
[/I]
Suelen aparecer al intentar leer, escribir o manipular un dispositivo de almacenamiento, generalmente discos rígidos Western Digital de 1TB de capacidad.
Se debe a que los discos rígidos presentaba esos errores con los sistemas GNU/Linux al ser detectado y enumerado como un nuevo dispositivo.
A partir del el kernel 2.6.10 el método de enumeración de los dispositivos fue cambiado para seguir un algoritmo como el de Windows, si bien el estándar permite ambos métodos, muchos dispositivos requieren y prefieren el método de Windows.

Es posible resolver este problema eliminando todas las particiones existentes con fdisk, para luego crearlas y darle formato.
No es problema de sectores defectuosos, sino de errores de detección por parte de los sistemas GNU/Linux.

---

### Post by guillermolisi on 2011-07-13
Entonces por que tampoco funciona con Windows XP ?

---

### Post by gmunioz on 2011-07-13
Sobre Windows ni idea. 
El error lo informa un sistema Gnu/Linux.
¿El formato previo del disco quizás?
Edito:
Buscando en la red parece que Windows XP tiene problemas al momento de usar discos duros de teras, debido a que los fabricantes usan para ellos un nuevo formato que establece sectores de 4,096 bytes en lugar de 512.

---

### Post by Einfachlacm on 2011-07-17
Hola,

Finalmente pude instalar Mint 11 con un live CD y el comando "noapic".

Con respecto a Win, terminé instalando 7 en lugar de XP, creo que era un problema de reconocimiento del disco SATA. Igual para mi no es Win sino PES2011 SO.

Gracias.

---

