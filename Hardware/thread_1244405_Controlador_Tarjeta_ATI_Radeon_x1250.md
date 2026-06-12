---
title: "Controlador Tarjeta ATI Radeon x1250"
date: 2009-08-19
forum: Hardware
---

### Post by gran_gatsu on 2009-08-19
Soy nuevo en este mundillo de software libre, instale ubuntu 9.04 en mi notebook, pero no puedo instalar los controladores de video, los instala peor cuando lo quieor abrir me sale un mensaje:
'' Initialization error''
There was a problem initializing Catalyzt Control Center Linux edition. It could be caused by the following.
No ATI drivers is installed, or the ATI drivers is not functionaly properly.
please install the ATI driver appropiate for you ATI hardware, or configure using aticofig.

Me dice que no hay drivers instalados, como puedo instalarle los drivers de mi tarjeta a ubuntu?

Si no los puedo instalar tendre que volver a XP U.U

de antemano gracias :KS

---

### Post by Carlos C on 2009-08-19
Hola. El problema con esa tarjeta es que ATI dejó de dar soporte para ella. Por lo tanto una opción es usar los drivers libres. El problema es que con ese modelo específico su performance no es muy buena. Te sugiero instales los drivers que están en desarrollo. Para saber cómo hacerlo te recomiendo que mires este enlace en donde se te explica paso a paso el procedimiento:

[http://listento.jaketolbert.com/linux/solve-video-flicker-on-jaunty-with-ati-x1250/](http://listento.jaketolbert.com/linux/solve-video-flicker-on-jaunty-with-ati-x1250/)

Saludos.

---

### Post by gran_gatsu on 2009-08-19
Okas, entonces ¿es recomendable mantener el Ubuntu o no?

:KS

---

### Post by Carlos C on 2009-08-19
Eso no puedo decírtelo, es algo que debes decidir tú. Si quieres saber si es posible que tu tarjeta funcione correctamente en Ubuntu, pues mi opinión es que sí.
Saludos.

---

### Post by robertor on 2009-08-19
> **Carlos C said:**
> Eso no puedo decírtelo, es algo que debes decidir tú. Si quieres saber si es posible que tu tarjeta funcione correctamente en Ubuntu, pues mi opinión es que sí.
Saludos.

Concuerdo con Carlos C. En parte depende del uso que le des a tarjeta de video si es tan importante desechar uno u otro sistema.
Yo no ocupo mucho la aceleracion 3d y el driver radeon, me anda (en realidad, me andaba ahora estoy usando el mesa... de flojo no lo he cambiado) muy bien.
Saludos!
Roberto

---

### Post by gran_gatsu on 2009-12-19
Me mantuve con el mismo probleama, decidi al final dejar el pc con doble booteo y asi tener xp y ubuntu, pero necesito la grafica, he leido y leido y no entiendo nada de como usar los drivers libres, les agradeceria una manito ^^

---

### Post by gran_gatsu on 2009-12-19
Resulta que abro el xorg.conf y me aparece un documento vacio u.u, no entiendo  :popcorn:

---

### Post by Carlos C on 2009-12-20
Hola. Creo que tener ambos sistemas en tu caso es una buena idea. De esa manera puedes solucionar tus problemas en Ubuntu sin mayores apuros. Vamos por partes. ¿Qué versión de Ubuntu instalaste, Jaunty? Por favor escribe en el terminal:

```
lspci -nn | grep VGA
```

y copia acá lo que te salga. Creo que lo mejor es que intentes hacer lo que te dicen [acá]("https://help.ubuntu.com/community/RadeonDriver"). Por eso te pido que uses ese comando, para que sepamos si tu tarjeta está bien soportada.

Saludos.

---

### Post by radixs on 2010-01-11
> **gran_gatsu said:**
> Resulta que abro el xorg.conf y me aparece un documento vacio u.u, no entiendo  :popcorn:

Si quieres configurar tu xorg.conf automaticamente pudes hacerlo de la siguiente manera.

1. debes parar gdm, abres una terminal y tipeas:
```
sudo /etc/init.d/gdm stop
```NOTA: Quedaras sin entorno grafico.

2. te logueas con tu user y pass

3. Ahora procedemos a configurar el xorg de forma automatica.
```
sudo Xorg -configure
```Nota: esto no reemplazara tu xorg automaticamente, si no que guarda un archivo con nombre xorg.conf.new en el directorio root
```
/root/xorg.conf.new
```Antes de preceder a copiar tu nuevo xorg te suguiero que mires el archivo creado, asi podras observar que todo este en orden. Puedes hacerlo con la orden "cat" o "nano" (con nano puedes modificar el archivo)
```
nano /root/xorg.conf.new
```Si quisieran modificar el archivo antepon sudo

------------------------------

Para copiar el nuevo xorg creado, debes tipear
```
sudo cp /root/xorg.conf.new /etc/X11/xorg.conf
```Nota: si es que no tubieras el xorg.conf vacio crea un backup del archivo, esto lo puedes hacer tipeando:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```Para volver a levantar gdm solo basta con tipear:
```
sudo gdm
```Espero te sirva de algo la info ;)

---

### Post by radixs on 2010-01-11
> **Carlos C said:**
> Hola. El problema con esa tarjeta es que ATI dejó de dar soporte para ella. Por lo tanto una opción es usar los drivers libres. El problema es que con ese modelo específico su performance no es muy buena. Te sugiero instales los drivers que están en desarrollo. Para saber cómo hacerlo te recomiendo que mires este enlace en donde se te explica paso a paso el procedimiento:

[http://listento.jaketolbert.com/linux/solve-video-flicker-on-jaunty-with-ati-x1250/](http://listento.jaketolbert.com/linux/solve-video-flicker-on-jaunty-with-ati-x1250/)

Saludos.

Enlace roto :(

sorry por el multipost (UPSSS)

---

