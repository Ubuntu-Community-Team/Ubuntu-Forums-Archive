---
title: "No puedo conectarme a Internet después de instalar un router"
date: 2008-12-27
forum: Hardware
---

### Post by Drieska on 2008-12-27
Bueno, el titulo explica algo, pero mejor doy un poco de info de fondo:

Antes de haber conseguido un Router (D-Link Modelo DIR 300) me había mandado una odisea para conseguir conectarme a internet con un modem ZyXEL (Prestige 600). Después de tocar al azar, descubrí pppoeconf que hizo que funcara tranquilamente.

En mi partición con Windows XP, instalé el router para preparar una conexión wi-fi en mi casa. En Windows XP funca de lo màs bien, el problema surge cuando me metí a Ubuntu (Versión 8.10), que directamente dejó de conectarse a Internet. Probé de vuelta con pppoeconf y detecta eth0 y pan0, pero no recibe la solicitud desde el ISP. (Calculo que ni siquiera puede mandarlo).

¿Qué tengo que hacer para que Linux pueda usar el router y conectarme a Internet?

Si falta información, díganme que agrego. Gracias de antemano.

---

### Post by guillermolisi on 2008-12-27
> **Drieska said:**
> Bueno, el titulo explica algo, pero mejor doy un poco de info de fondo:

Antes de haber conseguido un Router (D-Link Modelo DIR 300) me había mandado una odisea para conseguir conectarme a internet con un modem ZyXEL (Prestige 600). Después de tocar al azar, descubrí pppoeconf que hizo que funcara tranquilamente.

En mi partición con Windows XP, instalé el router para preparar una conexión wi-fi en mi casa. En Windows XP funca de lo màs bien, el problema surge cuando me metí a Ubuntu (Versión 8.10), que directamente dejó de conectarse a Internet. Probé de vuelta con pppoeconf y detecta eth0 y pan0, pero no recibe la solicitud desde el ISP. (Calculo que ni siquiera puede mandarlo).

¿Qué tengo que hacer para que Linux pueda usar el router y conectarme a Internet?

Si falta información, díganme que agrego. Gracias de antemano.
O sea que tenes un modem ADSL y un router inalambrico D-Link DIR-300, cierto ?
El modem ADSL esta en modo bridge y por eso usas pppoe, correcto ?
El tema es que agregaste en el medio al DIR-300 y dejo de discar, si ?
Si es esto ultimo correcto, tenes que configurar el DIR-300 para que disque pppoe (cosa que antes hacia el Windows) asi el Zyxel se conecta al ISP.

Si no entendi nada, por favor aclarar asi puedo aportar algo.

---

### Post by luks911 on 2008-12-27
Si es como entendió guillermolisi, otra opción es poner el Zyxel en modo router así: [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132)

---

### Post by Mauro22 on 2008-12-28
Yo tengo exactamente lo mismo, el mismo model y el mismo router.


Lo mejor es poner el zyxel en modo router y listo!!

---

### Post by Drieska on 2008-12-28
> **Mauro22 said:**
> Yo tengo exactamente lo mismo, el mismo model y el mismo router.


Lo mejor es poner el zyxel en modo router y listo!!

Probé intentando poner el Zyxel como router, pero directamente no me permite conectarme a internet.

Voy a tomar la opción de configurar el router nuevo para que me disque el pppoe. La cosa es, como lo hago?

---

### Post by faktorqm on 2008-12-29
Pone el zyxel en modo router como te pasaron ahi el link, y conecta una sola pc configurada con dhcp, solo para ver si anda. Si navegas bien, saca la pc del zyxel y conecta el zyxel al router a la boca que dice wan (normalmente) y tu pc a otra boca del nuevo router. luego decile al nuevo router que ponga dhcp en wan y en lan y se acabo el problema, deberias salir navegando al instante. 
Si tenes dudas sobre configuraciones anteriores, resetea los 2 dispositivos a valores de fabrica y listo. Salu2!

---

### Post by Drieska on 2008-12-29
> **faktorqm said:**
> Pone el zyxel en modo router como te pasaron ahi el link, y conecta una sola pc configurada con dhcp, solo para ver si anda. Si navegas bien, saca la pc del zyxel y conecta el zyxel al router a la boca que dice wan (normalmente) y tu pc a otra boca del nuevo router. luego decile al nuevo router que ponga dhcp en wan y en lan y se acabo el problema, deberias salir navegando al instante. 
Si tenes dudas sobre configuraciones anteriores, resetea los 2 dispositivos a valores de fabrica y listo. Salu2!

Cabe mencionar que no puedo ponerme en modo router ya que al poner los valores del link, no puedo telnetear al modem.

---

### Post by lega on 2008-12-29
Y si probas dejar el modem en modo bridge y poner los datos de tu coneccion en el router?
Yo hice así en su momento con un modem de Arnet y un router Linksys, o sea los datos que usas con el pppoeconf ponelos en el router, configurá una cuenta PPPoE como dijo guillermolisi y a tu maquina configurala para que conecte por dhcp, yo creo que así debería andar

---

### Post by faktorqm on 2008-12-29
> **faktorqm said:**
> Si tenes dudas sobre configuraciones anteriores, resetea los 2 dispositivos a valores de fabrica y listo

me pide que escriba algo para poder postear, pero no queria hacerlo

---

### Post by Drieska on 2008-12-29
> **lega said:**
> Y si probas dejar el modem en modo bridge y poner los datos de tu coneccion en el router?
Yo hice así en su momento con un modem de Arnet y un router Linksys, o sea los datos que usas con el pppoeconf ponelos en el router, configurá una cuenta PPPoE como dijo guillermolisi y a tu maquina configurala para que conecte por dhcp, yo creo que así debería andar

¿Cómo hago esto? Olvidé mencionar que mi experiencia con Ubuntu y networking en general no es muy grande.

Una cosa, suponiendo que pueda poner el modem como router, perdería la característica de tener una IP dinámica? Porque el servicio que Speedy me está dando me cambia la IP en cada reconexión.

---

