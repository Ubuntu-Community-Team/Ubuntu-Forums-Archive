---
title: "Problema con sonido 5.1"
date: 2009-08-01
forum: Hardware
---

### Post by Oxdise on 2009-08-01
Buenas gente, bueno mi problema es el siguiente, hace un tiempo usaba ubuntu 8.10 hardy heron y tuve el mismo problema ahora que uso 9.04 jaunty jackalope, tengo un subwoofer 5.1 y resulta que cuando inicio con windows funciona el audio a la perfección, pero en ubuntu solamente suenan 2 parlantes de los pequeños cuando reproduzco musica y los demás quedan mudos incluyendo el woofer que es el que da toda la emoción.

he intentado solucionar editando un xorg creo donde sustituia una linea que tenía un 2 (que supuestamente era el que ordenaba reproducir solamente por 2 parlantes la música) y lo cambié a 6, fue algo que vi en un blog y después cambiar todo a Pulse Audio pero no pasó nada con eso (disculpen la mediocre explicación pero no tengo buena memoria en cuanto a cosas que hago)

ese es mi problema y mi tarjeta de sonido es una C-media Ac'97 audio device

---

### Post by Carlos C on 2009-08-01
Hola ¿Lo que tienes es un laptop? Por favor, escribe en el terminal:
```
lspci
```
y luego copia acá lo que te salga. Partamos por eso y luego vemos qué puede estar fallando.
Saludos!

---

### Post by Oxdise on 2009-08-02
no, no es laptop es pc de escritorio normal.

esto me salió en el terminal.




00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by radixs on 2009-08-03
Si pruebas con un pelicula que esta en 5.1 deberian sonar todos tus parlantes... pero si escuchas MP3 no sonara pues estos no estan en 5.1... Men no es de mala onda, pero solo basta con buscar en este mismo foro, no me preguntes donde lo respondi pero asi es:

Lo primero que tenemos que hacer es crear un archivo .asoundrc :

```
sudo gedit /home/tu_usuario/.asoundrc
```Pegas lo siguiente y salvas: 

```
pcm.!default { 
 
type plug 
 
slave.pcm "surround51" 
 
slave.channels 6 
 
ttable.0.0 0.5 
ttable.1.1 0.5 
ttable.0.2 0.5 
ttable.1.3 0.5 
ttable.0.4 0.5 
ttable.1.4 0.5 
ttable.0.5 0.5 
ttable.1.5 0.5 
 
route_policy duplicate 
 
}
```Nota importante: Esta configuracion recuerdo que trae secuelas, si bien tendras salida 5.1 pero no podras escuchar multiples sonidos, me refiero a que si estas escuchando musica con tu reproductor y quieres escuchar un video de youtube u otro sonido no podras. sin alguien sabe como solucionar ese problema que aporte con su grano de arena ;)

---

### Post by Oxdise on 2009-08-04
y dónde se supone que lo tengo que guardar

---

### Post by radixs on 2009-08-04
> **Oxdise said:**
> y dónde se supone que lo tengo que guardar

Pffff señor esta todo explicado en el post.

---

### Post by Carlos C on 2009-08-04
> **Oxdise said:**
> y dónde se supone que lo tengo que guardar
Hola. Cuando radixs te dice que escribas:
```
sudo gedit /home/tu_usuario/.asoundrcse
``` crea un archivo oculto (si un archivo empieza por punto es un archivo oculto, el sistema no lo muestra amenos que tú se lo digas) en la carpeta /home/nombreusuario, es decir, en tu home. Como el archivo ya está creado, cuando guardes los cambios simplemente quedará en tu home.
Saludos.

---

### Post by Oxdise on 2009-08-05
no me funcionó y lo hice tal como decía, el error era porque no me había fijado que tenia que reemplazar por mi nombre de usuario pero lo corregí y sigue igual.

---

### Post by Carlos C on 2009-08-05
Una opción es que pruebes lo que hicieron en este thread:

[http://ubuntuforums.org/showthread.php?t=760091&page=2](http://ubuntuforums.org/showthread.php?t=760091&page=2)

Fíjate en los post [15]("http://ubuntuforums.org/showpost.php?p=4990327&postcount=15") y [17]("http://ubuntuforums.org/showpost.php?p=5199903&postcount=17"). Te recomiendo respaldar el archivo antes de hacer cambios (así puedes volver atrás sin problemas) y renombrar o borrar el archivo ".asoundrcse" que acabas de crear.
Saludos.

---

