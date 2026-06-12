---
title: "Dell vostro 1520 no conecta con wifi"
date: 2010-07-21
forum: Hardware
---

### Post by Palomay on 2010-07-21
Hola, tengo una dell vostro 1520, le instale ubuntu pero no me conecta al wifi alguien sabe como solucionarlo?

Pd la tarjeta inalambrica es broadcom

---

### Post by Patriciologico on 2010-07-21
Hola Palomay

Te recomiendo leer [http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475) ya que ingresas a una comunidad nueva es bueno que sigas el orden que llevamos. Tu post fue movido.

Respecto a tu problema, conectate a internet por cable, actualizas y en controladores de hardware te aparecerán dos, ambos sirven, googlea la licencia de uso de cada uno y las características para ver con cual te quedas, pero ambos funcionan.

Saludos

---

### Post by Palomay on 2010-07-21
Gracias por tu respuesta Guillermo, ya hicimos eso y no dio resultado, tuve que dejar windows vista en mi computador pero quiero volver a intentar con ubuntu, existe algún otro metodo?

---

### Post by Patriciologico on 2010-07-21
Cual es el modelo Broadcom que tienes?

---

### Post by Palomay on 2010-07-21
Disculpa se que la marca es broadcom pero no se como ver el modelo, tengo windows vista, me podrias explicar como hacerlo porfavor?

---

### Post by Patriciologico on 2010-07-21
Ahi estamos mal, no conozco windows vista, pero con programa llamado everest puedes ver en detalle las caracteristicas de tu pc. Seguro hay alguna forma en windows de hacerlo mas directo pero no la recuerdo ahora, ni tengo un pc cerca para explorar (puede ser en administracion de Hardware)

---

### Post by Palomay on 2010-07-21
Gillermo, este es el modelo **Dell wireless 1397 wlan mini-card** mi compu es un dell vostro  1520

---

### Post by Patriciologico on 2010-07-21
Palomay eso no nos da cual es el chipset de la wlan, un hardware puede tener la misma marca y modelo pero un chipset distinto.

Ahora me voy a un examen y no puedo seguir ayudando, pero te recomiendo leas este thread que te puede ser de ayuda

[http://ubuntuforums.org/showthread.php?t=1307077](http://ubuntuforums.org/showthread.php?t=1307077)

---

### Post by salva99 on 2010-07-28
Hola chicos

A mi me pasa lo mismo. Acabo de instalar ubuntu 10.04 en un portatil dell vostro 1520. He activado los dos controladores de hardware que ofrece ubuntu y en redes inalambricas me muestra que esta desactivada y no hay manera de activarla.

¿Alguna idea?

---

### Post by asterix77 on 2010-07-28
¿A que te refieres con "los dos controladores"? ¿Al controlador de la tarjeta gráfica más el de la tarjeta inalámbrica?

A) Bueno aunque parezca simple la pregunta pero: ¿prendes tu wifi?, es decir enciende el led, te digo esto porque en alguna oportunidad no lo podía hacer con la combinación de teclas de mi notebook, y solo lo hacía desde la terminal

#sudo ifconfig wlan0 up

B) Según mi opinión Network Manager no me gusta como gestor de redes, ya que tuve muchos problemas para conectame vía inalámbrica (con una broadcom 4312), por lo que instalé WICD con el cual no he tenido ningún problema (la instalación de este, desinstala automáticamente Network Manager)

C) Digita lo siguiente en la terminal y pégalos acá (con el wifi activado)

#lsmod

#ifconfig

#iwconfig

E) Específicamente ¿a qué te quieres conectar? (router, a un AP, otro pc, etc). Si es a Internet ¿quién es tu proveedor de servicios?

Saludos

---

### Post by salva99 on 2010-07-28
Ya está funcionando :)
Gracias Asterix por tu ayuda pero antes de haber leido tus buenos consejos encontré un post en ingles comentaban que el problema se solucionaba actualizando la BIOS del portatil. Yo tenía la A02 y en la página web de DELL proporcionan la actualización a la A08.

He ejecutado el programita..... solo funciona bajo windows :(...... y luego al arrancar con ubuntu ya me reconocia la wifi  :D

---

### Post by RafaelG on 2010-07-29
> **Palomay said:**
> Hola, tengo una dell vostro 1520, le instale ubuntu pero no me conecta al wifi alguien sabe como solucionarlo?Pd la tarjeta inalambrica es broadcom

[SIZE=2]Palomay, 

Yo tambien tengo un Dell Vostro y desde la version 9.04 que presento problemas cuando paso a una nueva version justamente con el Driver de la tarjeta inalambrica cosa que solucione tan facil como:

Ir Hardwares Drivers el cual por defecto realiza la descarga de los Drivers faltantes que en este caso es el Broadcom STA wireless Driver el cual hace funcionar tu tarjeta inalambrica pero obviamente para descargar el driver debe terner una conexion la cual puede ser conectando basicamente con un cable de red directamente con el Modem o en su defecto con un Modem inalambrico de alguna empresa de telecomunicacion. 

Ahora el rendimiento de la tarjeta con  este Driver Broadcom STA wireless es muy discutible ya que en varios forums hay quienes con pruebas de testeo han reportado disminucion en el alcance y poca estabilidad en la conexion inalambrica.

En conclusion las tarjetas Wireless Network Card 802.11 b/g/n no tiene rendimiento al 100% en Ubuntu cosa que da para pensar ya que Dell uno de los mas grandes fabricantes de Notebook trabaja directamente con esta tarjeta inalambrica. 

Y para finalizar mi post, este Thread no deberia ser considerado como Hardware.
[/SIZE]

---

### Post by asterix77 on 2010-07-29
Bueno a mi cuando instalé la versión 10.4, me aparecieron dos controladores para mi tarjeta de red Broadcom; una era Broadcom STA, y la otra era la versión Broadcom B43. Tuve algunos problemillas con la primera, asì es que opté por dejar la B43.
 
Saludos

---

### Post by themasterdark on 2010-07-29
se puede instalar cualquiera de los dos, el Sta, o B43.

Para mi caso funcionan sin ningún problema con ambos drivers, la diferencia es que con el B43, puedo hacer auditoria con aircrack =), incluso permite inyección de paquetes.

Saludos =)

---

### Post by asterix77 on 2010-07-30
A eso justamente me refería al decir algunos problemillas, no podía realizar auditorias con el STA, y no podía tampoco inyectar. 

También cuando quise hacer un punto de acceso con mi tarjeta inalámbrica de mi notebook, solo lo pude hacer con el B43.

Saludos

---

### Post by bichopro on 2010-08-03
boton derecho sobre el icono: activar inalambrica

---

