---
title: "[SOLVED] Problemas con Placa de Video nVidia"
date: 2008-10-10
forum: Hardware
---

### Post by Gpafundi on 2008-10-10
Hola a todos.Tengo un problema con mi Ubuntu. La situación es la siguiente: Instalo mi ubuntu 8.04.1 de 64 bits correctamente. Una vez instalado lo primero que hago es instalar la placa de video (tengo una nVidia Geforce 9600GT) de la siguiente forma (a ver si hice algo mal).

Primero instale el BUILD-ESSENTIAl (leí un un tutorial que era necesario para instalar la placa de video).

Despues ALT + CTRL + F1

sudo /etc/init.d/gdm stop

cd Escritorio (que es donde lo tengo bajado)

sudo sh NVIDIA-Linux-x86_64-177.80-pkg2.run

le doy a todo que si y después

sudo /etc/init.d/gdm start

vuelvo al entorno grafico y todo anda bien pero, cuando reinicio mi pc entra el entrono en modo de baja resolución como si no tuviera placa de video. Para hacer andar otra vez todo bien tengo que reinstalar la placa de video. No se que problema hay, no se si son los pasos que hago o si es la versión 8.04.1 del ubuntu (con otras versiones no me pasaba) o no se.

Espero sus respuestas ansiosamente porque hasta que no solucione esto, sigo con mi asqueroso XP. Gracias.

---

### Post by faktorqm on 2008-10-10
Hola, caiste en manos de un tutorial no del todo correcto. Si logras entrar al entorno grafico, anda a sistema -> administracion -> gestor de paquetes synaptics, y luego busca el paquete "envy-ng". Cuando termina, cerras synaptics y vas a aplicaciones -> herramientas del sistema -> envy-ng.
Ahi te pregunta si tenes ATI o NVIDIA y te instala todo automaticamente con 2 clicks y en el 95% de los casos no vas a tener ningun problema mas.
Si seguis con problemas postea. Espero que te haya servido. Salu2!!!

---

### Post by LianRome on 2008-10-11
Hola
Siguiendo la instalación con el .run (en vez de instalar el Envy) creo que lo que te falta es deshabilitar el módulo "nv".
Puedes ir a este tutorial, que en mi caso anduvo muy bien: [http://www.ubuntu-es.org/index.php?q=node/86489](http://www.ubuntu-es.org/index.php?q=node/86489)

Una cosa a tener en cuenta es que cada vez que salga un kernel nuevo (cosa que hace bastante no ocurre), seguramente se te desconfigure el entorno gráfico y debas hacer este procedimiento de nuevo.

Espero que te sea de utilidad. ¡Saludos!

---

### Post by majatu on 2008-10-12
Probaste con el control de hardware privativo? en Sistema/Administracion/Controladores de Hardware.

O sino bajate los drivers para Linux desde la web de nVidia.

---

### Post by Gpafundi on 2008-10-13
Listo, muchísimas gracias a todos. Me había faltado lo deshabilitar el modulo nv.

Por si las alguien tiene el mismo problema que yo o si alguien necesita instalar los controladores de nvidia dejo los pasos (ya que yo como novato busque y encontré uno mal hecho).

Primero instale el BUILD-ESSENTIAl.

Despues ALT + CTRL + F1

sudo /etc/init.d/gdm stop

cd Escritorio (que es donde lo tengo bajado)

sudo sh NVIDIA-Linux-x86_64-177.80-pkg2.run

le doy a todo que si y después

sudo nano /etc/default/linux-restricted-modules-common

y buscas la linea que dice disabled_modules=""

dentro pones nv de tal forma que queda así:

Disabled_modules="nv"

guardas con control+0

y sales con control+x

sudo /etc/init.d/gdm start

---

