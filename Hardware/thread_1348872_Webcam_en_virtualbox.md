---
title: "Webcam en virtualbox"
date: 2009-12-07
forum: Hardware
---

### Post by darkimedez on 2009-12-07
Hola a todos.

Les cuento que acabo de instalar mediante Virtualbox winXP dentro de mi karmic koala que me va de maravilla con el.

Mi unico problema es que no he podido hacer que mi window XP virtualizado reconozca la webcam.

Pensé que con instalar los drivers de mi pc (presario c700) bastaría, pero al parecer no basta eso, ya que no me funciona.

He tratado en miles de páginas de encontrar la solución, he googleado un montón y nada. Por favor si alguien de la comunidad pudiera ayudarme, estaría muy agradecido. Sospecho que tiene que ver un poco con la configuracion de mi win virtualizado, ya que tampoco me reconoce los puertos USB. 

Saludos Dario.

---

### Post by nopersona on 2009-12-07
Cuál versión de virtualbox instalaste? Necesitas la que ofrece el soporte USB.

---

### Post by Patriciologico on 2009-12-08
> **darkimedez said:**
> ...
Pensé que con instalar los drivers de mi pc (presario c700) bastaría, pero al parecer no basta eso, ya que no me funciona.
Saludos Dario.

No funciona asi, no sirve instalar drivers en el sistema virtualizado, sino que debe estar el hardware primero reconocido en el sistema anfitrión (en este caso Linux)

Hay dos versiones de Virtualbox:

- VirtualBox-OSE (Open Source Edition) si lo bajas desde synaptic te instala la version OSE. No trae soporte USB.

- La privada de SUN. que facilita el manejo de USB y trae algunas opciones extras, pero no es Libre. Para instalarla sigue [este manual]("http://www.pulsaf5.com/tutorial-instalacion-virtualbox-3-en-ubuntu-desde-repositorios/")  o la guia Ubuntu [http://www.guia-ubuntu.org/index.php?title=VirtualBox](http://www.guia-ubuntu.org/index.php?title=VirtualBox)

Saludos

---

### Post by moreback on 2009-12-08
En todo caso no sé si tendrás disponible la webcam en el sistema virtualizado, ya que posiblemente esté ocupado por Ubuntu.

---

### Post by Patriciologico on 2009-12-08
> **moreback said:**
> En todo caso no sé si tendrás disponible la webcam en el sistema virtualizado, ya que posiblemente esté ocupado por Ubuntu.

Mmm verdad, a todo esto que se trae darkimedez? ¿usar MSN messenger? ](*,) :D

---

### Post by moreback on 2009-12-08
Acabo de probar la webcam con la máquina virtual y sí la puedo activar, pero eso la desactiva en Ubuntu.

Uso VirtualBox 3.0.12 de Sun.

Saludos.

---

### Post by darkimedez on 2009-12-08
uso virtualbox OSE version 3.0.8

y si, lo instalé básicamente por el messenger live.

saludos, dario.

---

### Post by Patriciologico on 2009-12-08
Entonces a cambiar la version de Virtualbox.

¿No sera muchos recursos del sistema ocupados para mensajeria?

Podrias usar Wine. No quiero entrar en debates, de si es logico instalar linux para usar con wine, aplicaciones con alternativa.

[http://www.youtube.com/watch?v=V_XXuEPqErk](http://www.youtube.com/watch?v=V_XXuEPqErk) (en el video se ve funcionando, pero no se si se podra usar webcam)

Saludos

---

### Post by darkimedez on 2009-12-08
[moreback]("http://ubuntuforums.org/member.php?u=633286"), como lo hiciste para activar tu webcam en virtual box??

---

### Post by moreback on 2009-12-09
Usando la versión de Sun, voy al menú del VirtualBox, selecciono Dispositivos -> Dispositivos USB y luego activo la entrada que tiene mi webcam.

---

### Post by Quintacho on 2010-02-08
Mira, si a pesar de las indicaciones que te dieron, con las cuales debería funcionar, no funciona ve este [enlace]("http://envezdelpsiquiatra.wordpress.com/2009/05/25/instalar-y-tunear-virtualbox-en-ubuntu-9-04/") seguí las instrucciones y, luego de reiniciar, ahí estaba el dispositivo listo para ser usado, claro que luego tuve que buscar el driver de mi webcam para poder usarla desde el Windows virtualizado, pero esa es otra historia.

---

