---
title: "Escritura lenta en disco"
date: 2009-11-25
forum: Hardware
---

### Post by ponchomx on 2009-11-25
Hola a todos, estoy usando Ubuntu 9.10 y se me han presentado varios problemas, pero el que verdad me inquieta es el de que la escritura -o el guardar datos en disco duro- se ha vuelto exageradamente lenta para archivos grandes (más de 500 megas). Hasta hace unos días el descomprimir un archivo, por ejemplo de unos tres gigas dilataba unos cuantos minutos, ahora tarda horas... Si quiero recomprimir o copiar un vídeo, por ejemplo, el copiado -escritura sobre el disco- lleva horas.

Esto usando mi carpeta home, de un disco duro de 300 gigas, particionado en tres: hda1 para / (20 gigas), hda5 para home (250 gigas) y swat (2 gigas).

Mi Pc
Atlhon 64x2 +5000
Ram DDR2 2 Gigas a 800mhz
Vídeo onboard ATI  HD3200
Audio PCI Audagy SE SoundBlaster

¿Existe alguna forma de comprobar la integridad del disco duro?
¿Alguna idea?

Gracias por adelantado.

---

### Post by guillermolisi on 2009-11-25
Las causas que se me ocurren podrian ser:

[LIST]
[*] Disco con gran cantidad de errores lo que significaria que esta pidiendo el recambio ASAP (As Soon As Possible)
[*] Poco espacio libre en el disco, lo que dificultaria toda maniobra que precise de espacio extra para desarrollarse, como descomprimir archivos
[*] Controladora de disco/motherboard con problemas (podrian ser por causas termicas tambien)
[*] Disco rigido trabajando en un rango de temperatura excesivo (lo que termina "cocinando" la unidad y al correspondiente reemplazo)
[*]Si toda la maquina funciona lenta, siempre, podria ser la fuente de alimentacion que esta llegando al limite de su vida util (tambien aqui juega la temperatura)
[/LIST]
Mi consejo es instalar smartmontools y ya sea via grafica (mediante applets/widgets) o por consola monitorear la temperatura y la cantidad de errores (esta en los repositorios).

Para revisar la integridad del filesystem, se puede correr "fsck" (este utilitario se corre automaticamente despues de cierta cantidad de veces que se monta el file system y al principio del inicio de la maquina, antes de iniciar el entorno grafico).

Revisar los logs del sistema, particularmente /var/log/dmesg y /var/log/messages.

Nunca esta de mas darle una revisada al interior de la PC (si es desktop) y limpiar las ventilaciones y disipadores con aire. Si es notebook, limpiar las ventilaciones.

---

### Post by alfplayer on 2009-11-25
Se me ocurre que puede estar relacionado con los reportes existentes de problemas con el sistema de archivos ext4.

---

### Post by biale on 2009-11-26
Mas o menos lo que ya dijeron:
(1) Sistema/ Administracion/ Utilidad de discos.  "Mas detalles".
(2) Con el CD de instalación "gparted". "Verificar" todas las particiones y mirar bien/ anotar todo lo que tira: es el fsck
(3) Paquete xsensors. Electricidad y ventiladores.

Saludos...

---

### Post by ponchomx on 2009-11-26
Gracias por los comentarios. En utilidades de Disco me aparece en rojo:

> Contador de sectores reubicados
Count of remapped sectors. When the hard drive finds a read/write/verification error, it marks the sector as "reallocated" and transfers data to a special reserved area (spare area)

> Estimación:
Advertencia

> Valor:
Normalizado: 100
Peor: 100
Umbral: 36
Valor: 20 Sectores

Sigo buscando...

---

### Post by guillermolisi on 2009-11-26
Con esos datos empezaria a buscar un disco nuevo antes de que la cosa empeore.

Revisa el tema de la temperatura de trabajo en regimen del disco porque es uno de los principales factores que logran este tipo de degradaciones (y uno de los que menos atencion se le da en general en maquinas desktop).

---

### Post by ponchomx on 2009-11-26
La Herramiienta de disco indica 20 sectores erroneos y la temperatua 39 grados celcius.
¿crees necesario el cambio o existe forma de "brincar esos sectores? ¿o la cosa tendra  a dregradardse?

Gracias.

---

### Post by guillermolisi on 2009-11-26
> **ponchomx said:**
> La Herramiienta de disco indica 20 sectores erroneos y la temperatua 39 grados celcius.
¿crees necesario el cambio o existe forma de "brincar esos sectores? ¿o la cosa tendra  a dregradardse?

Gracias.
Para saber si se esta degradando habria que ver como evoluciona, con el consecuente riesgo de quedarse sin disco en cualquier momento.
Un excepcion seria tener conocimiento de cuantos sectores malos tenia antes de comenzar a usarlo, haber tomado nota de esos valores inciales, cosa que no siempre se hace.

39°C no me parece mal pero habria que verificar a que valor llega en pleno uso (actualizando paquetes, compilando, con mucho swapping, descomprimiendo archivos, etc.)

La informacion que pasaste dice que ha normalizado 100 sectores y este fue el valor mas alto alcanzado hasta ahora. El umbral de riesgo de 36 (por lo menos es lo que interpreto). Ademas es un warning, no solo informativo.

Esta "reubicacion" de pistas malas preserva la capacidad del disco pero degrada su rendimiento (haciendo que su temperatura de trabajo se eleve).

---

### Post by ponchomx on 2009-11-29
Platico mi experiencia.

Gracias a alfplayer, biale y sobre todoa **guillermolise** por sus comentarios y sugerencias.

El Disco duro parece haber llegado a su limite, en el tenia instalado en una partición a parte el SO y dejo simplemente de funcionar, al correr ubuntu en live ya no me lo reconocía. Mientras pensaba como poder recuperar mis datos adquirí un disco duro nuevo, de 1 tb, lo instale y volví a correr ubuntu life y en esta segunda ocasión si me reconocio el disco duro dañado, paso siguiente desde la consola me pongo como superusuario "sudo -s" y formateo el disco duro nuevo, dejándolo en dos particiones, una para el so y otra para los archivos y comienzo el copiado... Después de seis horas logre rescatar mi información. Desinstalo el Disco duro dañado e instalo Ubuntu 9.10 x64 o eso trate ya que me arrojo un error, la verdad, no apunte el número de bug, pero leí que el actualizar el kernel soluciona ese problema. De hecho instale pero no me corrió el sistema gráfico si bien pude haber actualizado desde consola, mejor opte por probar el de 32 bits y la verdad después de dos días la pc anda como rayo, bueno ya me había acostumbrado a la lentitud del disco dañado, lo mejor esta nueva versión, la 9.10 me reconoció mi soundblaster, también las anteriores versiones, pero ahora no tuve que editar ningún archivo y desde preferencias de sonido me puse a disfrutar mi 5.1.

Gracias a todos y Salu2

---

### Post by guillermolisi on 2009-11-29
O sea que despues de todo ese trabajo que te tomaste, no solo solucionaste tu problema sino que mejoraste la usabilidad del sistema. Es asi ?

---

### Post by alfplayer on 2009-11-29
La advertencia no parece tener mucha seriedad. Puede ser un falso positivo como se reporta en el bug 438136 ([https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)).

---

### Post by guillermolisi on 2009-11-30
> **alfplayer said:**
> La advertencia no parece tener mucha seriedad. Puede ser un falso positivo como se reporta en el bug 438136 ([https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)).
Por que no parece ser seria la advertencia ? Por que hay un bug reportado sobre falsos positivos ?

Y si fuera un falso positivo, cual seria la razon por la que ese disco funciona lento ?

---

### Post by alfplayer on 2009-11-30
> **guillermolisi said:**
> Por que no parece ser seria la advertencia ? Por que hay un bug reportado sobre falsos positivos ?

Y si fuera un falso positivo, cual seria la razon por la que ese disco funciona lento ?

ponchomx dijo que falla para archivos grandes (no aclaró para archivos de tamaño menor).

El bug de falsos positivos es un bug que parece ser muy popular. La herramienta parece ser muy sensible. Cuando instalé karmic tenía por lo menos dos discos de los cinco que tengo conectados a mi computadora de trabajo con esa alarma, y se que los discos funcionan bien.

Lo de la escritura lenta también puede ser un problema de software (por ejemplo se me ocurre que puede ser un problema de drivers o en el sistema de archivos), además de todos los listados en la primera respuesta.

Por lo que entiendo, 20 es el valor de sectores reubicados que es bastante menor al valor del umbral que es 36, lo que dejaría la posibilidad de que siga funcionando.

Se podría revisar el disco con la herramienta de diagnóstico del fabricante y/o probarlo con otra versión de ubuntu u otra distribución.

---

### Post by ponchomx on 2009-12-01
Pues de ese tipo de cosas se aprende, de hecho muchos dicen que linux te exige conocimiento de tu sistema. Tuve que hacer usos de los procesos de montar y desmontar, los discos duros, todo el trabajo se llevo desde un live CD,en este caso de Ubuntu 9.10. Al quedar grabados los datos, procedí a instalar el SO en una partición aparte, ya resguardados mis cosas, y o sorpresa los datos estaban  a nombre de root, con el consiguiente problema para poder acceder a ellos, al principio opte a cambiar los permisos de manera masiva con el comando chmod y recursivamente -R.

Pero al ser archivos y directorios los resultados no eran muy buenos así que me tope con la opción de cambiar el usuario propietario:

> sudo chown nombre * -R

El resultado fue bastante bueno y lo mejor pude recuperar el archivo de .mozilla, con mis marcadores y claves guardadas, habré que respaldar más seguido.

Esta tragedia termino en lección y lo mejor pude recuperar mis archivos y lo único que gaste fueron en un Cd y por obvias razones el nuevo disco duro.

Gracias y Salu2

---

### Post by ponchomx on 2009-12-01
> **alfplayer said:**
> ponchomx dijo que falla para archivos grandes (no aclaró para archivos de tamaño menor).

El bug de falsos positivos es un bug que parece ser muy popular. La herramienta parece ser muy sensible. Cuando instalé karmic tenía por lo menos dos discos de los cinco que tengo conectados a mi computadora de trabajo con esa alarma, y se que los discos funcionan bien.

Lo de la escritura lenta también puede ser un problema de software (por ejemplo se me ocurre que puede ser un problema de drivers o en el sistema de archivos), además de todos los listados en la primera respuesta.

Por lo que entiendo, 20 es el valor de sectores reubicados que es bastante menor al valor del umbral que es 36, lo que dejaría la posibilidad de que siga funcionando.

Se podría revisar el disco con la herramienta de diagnóstico del fabricante y/o probarlo con otra versión de ubuntu u otra distribución.

Alfplayer, yo quisiera echar la culpa de este problema ala energía eléctrica. En verano, a mediados de año en esta parte del continente, hace mucho viento y los apagones son una constante acá en México. La verdad nunca le había puesto mucha atención a verificar mi disco duro, tengo discos duros de 40 y 80 gb de 8 años de antigüedad y continúan funcionando. Este disco que se arruino apenas paso del año, pero en la maquina que lo tengo instalado la tengo prendida día y noche seguidos y esta más expuesta a las inclemencias del tiempo.

Tenia una pentium 4 a 1.4 con 512 de Ram a 100 y disco duro de 80 gb, con ella me estrene en RedHat 9 la última versión antes de Fedora, también tuve Mandrake, ahora Mandriva y Debian 3.0. No te miento esa maquina duro casi tres años ininterrumpidos día y noche solo se apagaba cuando no había luz eléctrica. Hace tres meses le instale el Xubuntu 9.04 para regalarla a unos sobrinos y ellos felices con su pc.

Sobre los archivos. Descomprimir un archivo de 700 megas llego a tardar hasta 15 minutos y los congelamientos ya eran constantes. Creeme en un principio le eche la culpa al SO hasta pensaba muy seriamente cambiar a otro SO (Debian, Fedora o Slackware). Pero esto me sirvió, con eso de que aprende uno en el camino lo que va necesitando... E

Salu2

---

### Post by biale on 2009-12-01
> hace mucho viento y los apagones son una constante acá en México. 

sería un buen caso para una UPS.  Saludos

---

### Post by lula on 2009-12-01
Me dice al iniciar que uno o más discos están fallando y  continuación que el disco tiene muchos sectores erroneos, que puede ser? Hace un par de horas intale Ubuntu 9.10 y es la primera vez que uso Linux.

---

