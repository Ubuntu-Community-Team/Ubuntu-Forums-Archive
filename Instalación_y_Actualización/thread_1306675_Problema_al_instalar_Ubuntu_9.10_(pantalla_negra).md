---
title: "Problema al instalar Ubuntu 9.10 (pantalla negra)"
date: 2009-10-30
forum: Instalación y Actualización
---

### Post by VonlisT on 2009-10-30
Hola a todos los foreros.
  Hoy decidí bajarme la iso de ubuntu karmic koala para  aprovechar de formatear el sistema, ya que anoche dejé la crema en el sistema (ubuntu 9.04) intentando instalar una actualización de un driver (Wireless), la cosa es que ahora no carga ni el grub, así que decidí formatear para no tener que arreglarlo.
Ahora viene el problema, iInserto el CD del karmic, se ve el menú con las opciones y todo, pero cuando instalo el sistema no se ve nada, el liveCD carga ya que puedo escuchar el clásico sonido cuando se ingresa al sistema, solo se ve el memtest, he probado con vga=771 con noapic nolapic acpi=off etc....
nada de nada, lo más que he conseguido es que se vea una pantalla gris con algunos colores durante 1 segundo y luego vuelve a negra.
Realmente no sé que hacer.

Mi notebook es un HP Compaq 610 (Tarjeta de video integrada Intel X3100 no es muy buena pero salva en ubuntu 9.04, ojo,  [hay que actualizar el driver de alsa para para que funcione el sonido en ubuntu 9.04, sigan las instrucciones desde [aquí]("http://www.webupd8.org/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html") ]). Con la instalación de ubuntu 9.04 no tuve que agregar ni una opción especial.

Saludos a todos :D
-----------------------------------------------------------------

**EDICIÓN**:
  Resulta que me vi obligado a reinstalar ubuntu 9.04 para poder actualizar a 9.10 desde allí (muy primitivo de mi parte, ¿no?), funcionó perfecta la actualización (salvo un problema que ya postié en el foro), cuando reinicio me doy cuenta que se ve la misma pantalla negra con un efecto de degradado por 1 segundo y vuelve a negra, haciendo pruebas me di cuenta que era producto de la configuracion del kernel, ya que cuando me arranca el grub, apreto escape, selecciono el segundo kernel disponible (no el de modo recuperación) arranca, pero todo es muy lento, es un problema de la aceleradora de video. si quieren que arranque con el último kernel disponible para ubuntu 9.04 deben abrir el archivo /boot/grub/menu.lst como root y agregar la siguiente linea al kernel que queremos arrancar (el primero, por defecto): i915.modset=0
quedará algo como esto:
boot/vmlinuz-2.6.28-16-generic root=UUID=dd071afb-ff1d-4ca1-b970-1af2b182a730 ro **i915.modset=0** quiet splash
reinician y no aprenten nada, ahora debería arrancar normalmente, pero notarán la lentitud del sistema (seguramente es mi notebook, la tarjeta grafica no salva a nadie).

** NOTA IMPORTANTE:**
  Como buen aprendiz, intentando solucionar el problema, probé instalar Fedora 11, increiblemente tuve el mismo resultado que el liveCD de ubuntu 9.10, pero..... ahora se me ocurrió una nueva cosa, apreté tab para editar el arranque y agregué: i915.modset=0 increiblemente ahora arrancó a pesar de que no me reconoció el comando i915, según el boot. En el liveCD de ubuntu 9.10 funciona también (perfecto diría yo), solo apretas F6 y agregas: i915.modprobe=0 antes de los dos guiones "--". De todas formas no les recomiendo que instalen ubuntu 9.10 en este notebook ya que de igual forma estará lento el sistema, no así con Fedora 11 que por lo menos, el sistema Live corre de maravillas.

Saludos a todos y espero que le sirva de ayuda a alguien.

---

