---
title: "problema con ACPI en Toshiba"
date: 2009-06-08
forum: Hardware
---

### Post by gonzalonal on 2009-06-08
hola que tal? como verán soy nuevo en el foro, como en ubuntu. Por el momento me las he arreglado bastante bien, eh aprendido a usar la consola mínimamente y alguna q otras cosas.
Instale **Ubuntu 9.04 Desktop** 64 bits
Mi version de kernel es  :2.6.28-11-generic

Bueno mi problema es el siguiente: tengo una notebook toshiba A305-S6894, tiene un centrino dúo de 2ghz 4 gb de ram. El problema aparecio cuando suspendi la notebook un dia y al "despertarla" note que la notebook levantaba mucha temperatura cuando usaba mucho el micro y a todo esto el cooler ni se percataba. Leyendo por muchos lados entendi que era un problema de los ACPI. Segui varios tutoriales pero siempre tenia problemas para hacer lo que decian, capaz que por que soy muy novato no se. Tambien baje una programa llamado "toshset" pero al querer iniciarlo me dice:

gonzalo@Gonzalo:~$ su
Contraseña: 
root@Gonzalo:/home/gonzalo# toshset
**required kernel toshiba support not enabled.**
root@Gonzalo:/home/gonzalo# 

Segui buscando mediante este error, y lei otros tutoriales en los que tenia que copiar unos archivos y parches de los cuales muchos de ellos tenian los links de descarga vencidos asi que no pude hacer nada tampoco. En caso de servir para el pronostico, las conbinaciones fnfx tampoco funcionan.

Despues lei en var/log/messages el siguiente mensaje obviamente relacionado con el encendido del cooler, este se repite cada 5 segundos aprox:

Jun  7 16:26:37 Gonzalo kernel: [ 4948.159366] ACPI: Unable to turn cooling device [ffff88013f816880] 'off'
Jun  7 16:26:45 Gonzalo kernel: [ 4956.059681] ACPI: Transitioning device [FAN] to D3
Jun  7 16:26:45 Gonzalo kernel: [ 4956.059687] ACPI: Unable to turn cooling device [ffff88013f816880] 'off'
Jun  7 16:26:48 Gonzalo kernel: [ 4959.637645] ACPI: Transitioning device [FAN] to D3


Bueno espero que me puedan ayudar con este problema ya que tengo miedo de quemar algo en el pc por el levantamiento de temperatura. Recuerden que soy bastante novato, pero tengo muchas ganas de mejorar asi despues poder ayudar como ustedes.

Gracias
Gonzalo

---

### Post by luks911 on 2009-06-09
Bienvenido.
Aparentemente se trata de un bug[0] en el kernel que aparece y desaparece de versión en versión.
Ahí en Launchpad dejan al menos dos posibles soluciones hasta tanto no se arregle. Una[1] consiste en mover un archivo desde su ubicación original a tu home, el efecto es el mismo que con borrarlo, sólo que así lo conservas por si es necesario restaurarlo. En una terminal deberías ejecutar.

```
sudo mv /usr/share/initramfs-tools/hooks/thermal /home/tu_usuario
```

Donde tu_usuario es el nombre de tu usuario, claro.

La segunda[2] alternativa está probada en una Lenovo y consiste en pasarle un parámetro al kernel al inicio. En todo caso probá con lo otro antes y volvé a preguntar. Además puede aparecer alguien con una mejor idea. 
Saludos

[0] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/113081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/113081)
[1] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/113081/comments/25](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/113081/comments/25)
[2] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/113081/comments/32](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/113081/comments/32)

---

### Post by gonzalonal on 2009-06-09
hola de nuevo. gracias por responder.
Hice la primera opcion que me dijiste. con respecto al toshset sigue tirando el mismo error :
[B]gonzalo@Gonzalo:~$ sudo toshset
required kernel toshiba support not enabled.
gonzalo@Gonzalo:~$ 
[/B]
pero me imagino que la modificacion tiene que ver solo con el manejo de la temperatura. Si me podrias explicar mejor en que consiste el cambio te lo agradeceria mucho.
gracias
saludos

---

### Post by luks911 on 2009-06-09
Lo que te sugerí es mover el archivo thermal, ubicado en /usr/share/initramfs-tools/hooks/. Este archivo, por lo que veo, es un script que se lee al inicio y también cuando la máquina sale de suspensión volviendo a cargar los módulos encargados de manejar el ventilador. Por lo que dice el usuario en Launchpad, eso provoca algún conflicto con el bios y genera el problema.
De todos modos, si esto no soluciona el inconveniente o genera otro, podés revertirlo con la acción inversa:

```
sudo mv /tu_usuario/thermal /usr/share/initramfs-tools/hooks/
```

De paso:
sudo: porque vas a mover un archivo del sistema, por lo que necesitás permiso de superusuario o root. Eso te pide tu contraseña
mv: es el comando para mover un archivo.

---

### Post by gonzalonal on 2009-06-09
hice lo que me dijiste, primero una opcion y despues la otra. lamentablemente ninguna de las dos me funciono, y encima cuando prendia desde 0 la pc el cooler no andaba, pero al volver todo a su estado orginal comenzo a andar todo normalmente.
muchas gracias igual.

me podrias explicar como bajar el toshiba_acpi para lograr que funcionen las teclas fnfx y el toshset
muchas gracias de nuevo
saludos

---

