---
title: "Problema de temperatura con lapto toshiba A135"
date: 2007-07-26
forum: Hardware
---

### Post by seba2611 on 2007-07-26
Bueno ya pude instalar el ubuntu y quedo perfecto salvo por un detalle q acabo de notar y es el siguiente, con el vista cada cierto tiempo o depende la aplicacion o exigencia q le este dando a la laptop se activa un ventilador q ventila un poco y se vuelve a apagar pero con el ubuntu no y note q la temperatura de la maquina es mayor en la parte de abajo y donde apoyo las manos mientras tipeo y el ventilador nunca se activo, no tuve cuelgues ni nada y aparentemente todo lo q pruebo funciona bien pero tengo miedo de hacerle mal ya q no se disipa bien el calor , esto podra solucionarse alguien tiene idea???

---

### Post by Hei Ku on 2007-07-26
tenes instalado el lm-sensors? podes instalarlo desde los repos y eso te permite verificar la temperatura de la maquina. En KDE tenes que instalar el ksensors, no se cual sera el programa para el gnome, pero seguramente lo podes encontrar en synaptic.

---

### Post by kowal on 2007-07-26
Para monitorizar la temperatura podés instalar lm_sensors:

[http://www.guia-ubuntu.org/index.php?title=Monitorizar_temperaturas_de_hardware](http://www.guia-ubuntu.org/index.php?title=Monitorizar_temperaturas_de_hardware)

Y para controlar los fans podés usar esta guía:

[http://ubuntuguide.org/wiki/Ubuntu:Edgy_Sp#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy_Sp#How_to_control_fan_speed_.28lm-sensors.29)

---

### Post by seba2611 on 2007-07-27
Instale el lm-sensors y lo active desde klos servicios ahora voy a leer un poco para ver como se usa muchas gracias!!!!ah una cosa me parece que el cooler funciona pero no con la misma potencia q lo hace con el Vista...

---

### Post by jorgito on 2007-07-27
Hola, 

Tengo una duda... el lm-sensors es necesario para ver la temperatura solamente, o hace falta para controlar (regular) la temperatura de la CPU? Si fuera esto ultimo me parece medio peligroso andar dependeniendo de un programa para encender el ventilador...
En
/proc/acti/thermal_zone/THRM/
hay un archivo "temperature" donde se puede ver una temperatura que va cambiando en funcion de la carga de la maquina.
Si esto ya esta disponible antes de instalar el lm-sensors, no se puede usar directamente?

Por otro lado lei tambien (ver [http://doc.gwos.org/index.php/Lm-sensors_hddtemp](http://doc.gwos.org/index.php/Lm-sensors_hddtemp))
que los pasos a seguir para instalarlo dependen de si uno tiene o no algo que se llama "dynamic /dev".
Y eso que viene a ser?

Saludos!

---

### Post by seba2611 on 2007-07-27
eso q decis me parece q es para monitorear el disco rigido , aca tb hay algo de eso mira:
]http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29[/URL]

---

### Post by Druiling on 2007-12-31
Hola a todos, yo tengo un problema similar pero con un Asus A6. No sé si es que hay algún problema con la targeta gráfica o que pero me llega el portátil a unas temperaturas muy muy altas, de tal manera que si tengo por ejemplo un juego lanzado o bien el correo evolution y el FireFox a la vez, sin ninguna aplicación o programa más, la temperatura se dispara y tengo que cerrar todo para que baje y se recupere. 
La verdad es que cuando funcionaba con windows, este era un problema recurrente, pero ultimamente en Ubuntu, también me pasa y no sé que es lo que puede estar ocurriendo.
Tengo instalados los Im-sensors y una aplicación que monitorea en tiempo real "gkrellm" que funciona muy bien, ya que he comparado sus lecturas con las de la consola, pero no sé que podría hacer para que bajase la temperatura.
Si a alguien se le ocurre algo, se lo agradecería.
Feliz año 2008 a todos.

---

### Post by Hei Ku on 2007-12-31
Lo que podes hacer es instalar los modulos para que el micro no funcione siempre a maxima potencia. En el caso de AMD, es el sistema cool 'n quiet, Intel tiene uno similar pero no recuerdo el nombre. Esto se llama frequency scaling, y lo podes buscar en este mismo foro, o en el general de ubuntu que hay varios tutos de como hacerlo.

Justamente con el calor que esta haciendo pude chequear como funciona. Normalmente la temperatura de mi CPU esta en 30-35. En el momento de compilar un programa se va a 60, y despues vuelve a bajar apenas termina.

De todas maneras, siempre depende la maquina que tenga los fans suficientes para bancarse los picos de temperatura en un nivel razonable. Mis fans oscilan entre 2000RPM en carga normal, y llegan a 6000RPM cuando el CPU levanta temperatura.

---

### Post by Mister X on 2008-01-02
Mirá, en mi laptop (HP) el manejo del cooler es por hardware y no por soft, creo que en todas las laptops es asi.

---

### Post by Druiling on 2008-01-02
Mister X, puedes explicar más ampliamente esto que dices?. Lo pido por que yo soy profana y aunque me esfuerzo en leer todo lo que puedo, no acabo de entender demasiado las especificaciones.
Gracias.

---

### Post by UomO_BongA on 2008-01-02
Si la laptop se recalienta comprate una lata de aire comprimido y dale una buena soplada al disipador... yo lo tengo que hacer casi una vez por mes, los disipadores de las laptop son muy compactos, bastan 2 pelos de gato y un poco de polvo para taparse.

---

### Post by Mister X on 2008-01-03
> **Druiling said:**
> Mister X, puedes explicar más ampliamente esto que dices?. Lo pido por que yo soy profana y aunque me esfuerzo en leer todo lo que puedo, no acabo de entender demasiado las especificaciones.
Gracias.

Lo que digo es que el manejo del ventilador de la CPU no lo hace el sistema operativo ni ningun programa instalado, lo realiza directamente la laptop, por un tema de seguridad, ya que es mucho mas probable que falle el software y deje de funcionar el ventilador, con el cosiguiente daño por sobrecalentamiento para la laptop.

saludos

---

### Post by loboesa on 2009-08-27
Yo tengo una laptop Toshiba A305D que con Vista trabaja bien (teniendo en cuenta que es Vista), le instale Ubuntu y las teclas de función, el bluetooth y los ventiladores dejaron de funcionar.

Supongo que el control de los ventiladores es una mezcla entre hardware, BIOS y sistema operativo.

Puedo sobrevivir sin las teclas de función o del Bluetooth, pero no sin ventiladores, después de unos minutos se calienta mucho, sobrepasando los 75ºC con el riesgo de quemarse.

Le instalé Omnibook y con ello logré activar el bluetooth y los ventiladores, pero generó inestabilidades en la máquina. (se prende sola después de 4 seg de haberla apagado). Aclaro que esto puede ser porque la versión de omnibook que encontré no soporta la laptop que tengo pero me arriesgue a no encontrar otra opción. Si soporta la de ustedes igual y les funcione, chéquenlo. (Existe otro similar pero no recuerdo el nombre).

Por el momento me veo obligado a seguir con vista por la salud de mi laptop y estoy pensando en la virtualización para poder utilizar linux.

ESPERO QUE LOS FABRICANTES DEN SOPORTE A SUS PRODUCTOS PARA MÁS DE UN SO O LA INFORMACIÓN NECESARIA PARA QUE LA COMUNIDAD PUEDA DESARROLLAR SUS PROPIOS CONTROLADORES.

---

