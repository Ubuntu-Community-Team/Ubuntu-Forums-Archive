---
title: "ATI 4850 vs Ubuntu 9.10"
date: 2009-12-07
forum: Hardware
---

### Post by VashTheStampede on 2009-12-07
Hola a todos! Vengo batallando desde la versión anterior del ubuntu y todavía sigo sin poder instalar la ATI 4850. Probé muchos métodos pero con todos llego a lo mismo, la pantalla en negro y el monitor que me dice que se fue de rango. ¿Alguien me podría dar una mano? Había probado con el Ubuntu 9.10 64-bit y ahora tengo el de 32-bit porque pensé que ese podría ser el problema pero aún así no funciona.
En la pagina de ATI dan un pdf para instalar y ahí pide unas librerias que tienen que estar pero algunas de esas no las encuentro.

¿Alguien me podría ir explicando paso a paso como debo hacerlo para la version 9.10 de ubuntu? Casi una explicación para dummies ya que soy nuevo en linux y muchas cosas casi básicas no las se.

Desde ya muchas gracias


---------------------------------------
Micro: AMD Pheno X4 9550; Mother: ASUS M3A78-EM; Disco: Seagate 250 GB; Monitor: LCD ViewSonic 19'' VA902b; Placa de video: XFX ATI Radeon HD 4850

---

### Post by Applelnx on 2009-12-08
Hola Vash. Cuando recien instalas Ubuntu, te funciona? Si entendi bien, lo que estas necesitando es la aceleracion 3D, para lo que tenes que instalar los drivers privativos. Con que metodos probaste a hacer la instalacion? 

Por mi parte, cuando trate de instalar los drivers desde hardware restringido no me funciono y me hizo desastres. Yo segui las instrucciones de ATI.

---

### Post by VashTheStampede on 2009-12-08
Ni bien instalo linux tengo modo gráfico pero hay algunos flicks de video medio raros cuando carga por ejemplo. Igual no me deja poner resolución mayor a 1024x768, debe de estarle faltando el driver correcto, ¿verdad? Cuando recien instala pone el vesa me parece.
Los drivers privativos a los que hacés referencia son los de la pagina de ATI, ¿no?. Ando intentando usar esos. En las instrucciones de ATI dice que para instalar los drivers hay que poner unas librerias que no puedo encontrar. ¿Cómo hago para ponerlas?
Estoy siguiendo estas instrucciones para instalar

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Las que dicen de instalar los drivers de manera manual

---

### Post by euzkoarima on 2009-12-09
Yo instale en 9.04 64 bits y me anduvo, pero no tuve tiempo de pasar esa pc a 9.10.

Por las dudas, yo baje los drivers y las instrucciones desde [aquí]("http://support.amd.com/us/gpudownload/Pages/index.aspx").

Fijate si te resulta más fácil.

Saludos,
Eduardo

---

### Post by ponchomx on 2009-12-09
> **VashTheStampede said:**
> Ni bien instalo linux tengo modo gráfico pero hay algunos flicks de video medio raros cuando carga por ejemplo. Igual no me deja poner resolución mayor a 1024x768, debe de estarle faltando el driver correcto, ¿verdad? Cuando recien instala pone el vesa me parece.
Los drivers privativos a los que hacés referencia son los de la pagina de ATI, ¿no?. Ando intentando usar esos. En las instrucciones de ATI dice que para instalar los drivers hay que poner unas librerias que no puedo encontrar. ¿Cómo hago para ponerlas?
Estoy siguiendo estas instrucciones para instalar

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Las que dicen de instalar los drivers de manera manual

Ese método ya no es muy común, ahora la instalación suele ser sin muchas complicaciones. Si puedes ingresar de manera grafica, despues de bajarte el driver de la pagina de AMD/ATI, el correspondiente a tu tarjeta solo teclea desde la consola en el lugar donde tengas el driver que bajaste:

> sudo sh ./ati-driver-installer*.run

y aparecera de manera grafica el instalador. Si no te es posible acceder al modo grafico con **Ctrl + Alt +F1** ingresaras a consola y haz lo mismo:

> sudo sh ./ati-driver-installer*.run

Despues de esto reinicias:

> sudo reboot

Vengo usando un chip de ati, el HD3200 y la verdad en este año las mejoras han sido muy significativas, ya no es mucho lo que tenemos que envidiar a los de nvidia, aunque en otra maquina tengo una Gforce 9600gt y va de perlas.

Salu2 y Suerte.

---

### Post by VashTheStampede on 2009-12-09
euzkoarima: yo hice eso pero en el pdf con información sobre la instalación me dice que necesito determinadas librerias para instalar el driver y no todas las encuentro.

ponchomx: Cuando me aparece el modo grafico de instalación, ¿le doy para que genere lo paquetes específicos para mi version de linux o que simplemente los instale? Yo hice eso antes y me pasaba lo mismo.

Ahora pregunto, ¿este linux usa la configuración de video del XOrg.conf o la saca de algún otro archivo? Porque me hace unos cambios en el XOrg.conf pero no pone valores de refresh ni valores de resoluciones.

Igual voy a probar a ver que pasa y les comento. Gracias por las respuestas

---

### Post by Tosh78 on 2009-12-11
Mira, yo tengo una ATI tambien, otro modelo, pero la instalacion es la misma. Generalmente, en Ubuntu, esas librerias ya vienen instaladas. Yo nunca tuve que instalarlas y los drivers me andan perfecto. Proba asi. 
Si te da cosa, podes ir a Sistema-Administracion-Synaptic y buscarlas por ahi.

---

### Post by euzkoarima on 2009-12-12
> **VashTheStampede said:**
> euzkoarima: yo hice eso pero en el pdf con información sobre la instalación me dice que necesito determinadas librerias para instalar el driver y no todas las encuentro.


Disculpá la tardanza, pero estoy a mil con el laburo (de hecho ahora estoy en un intervalito del mismo).
Yo no recuerdo haber necesitado nada más, pero no importa, copia los errores que te de, vemos que paquetes te están faltando y los instalamos.

Saludos,
Eduardo

---

### Post by VashTheStampede on 2009-12-14
Sigo sin poder hacerlo funcionar. Esto es lo que hice esta vez y lo que pasó:

Instalé Ubuntu 9.10 64-bit desde cero. Ni bien entro, no hago updates como antes solía hacerlo, y saco un par de librerias que leí por ahí son las que usa por defecto para la ATI y que si se dejan crean conflicto. Estás librerías son modalises-fglrx o algo así y la Radeon. Cuando reinicio me pone el modo gráfico en 800x600 así que supongo que si estaba usando esas librerías. Despues pongo para instalar los drivers que bajé de la pagina de ATI y de las 2 opciones que tira pongo la primera, no la de crear los paquetes especificos para la distribución sino la otra, y me salta "ERROR: vcdk is missing. Installation aborted!". Leí por ahí que necesitaba poner las librería ia32-libs, lo hice y nada...

---

### Post by euzkoarima on 2009-12-17
A ver, hace rato que lo hice y no me acuerdo bien, pero los pasos que yo seguí fueron:

1 instale 64
2 corri todos los updates
3 instale lo que baje de ati y puse que genere paquete para distribución
4 instale el paquete generado.

Probá así, eventualmente borrando las librerías que comentas.

Saludos,
Eduardo

---

### Post by VashTheStampede on 2010-01-05
Sigue sin funcionar. Pruebo como dijo euzkoarima pero no funciona. Me tiene harto. Quiero ponerme a usar linux pero si va a ser así la cosa la verdad que no.
Leí por ahí que capaz tengo que editar a mano el xorg.conf para ponerle las resoluciones y los VSync y HSync según las especificaciones del monitor. Tengo la info pero no se como editarlo.

Aca pongo la imagen que tengo de las especificaciones de mi monitor por las dudas

Seguiré intentando...

---

### Post by guillermolisi on 2010-01-05
> **VashTheStampede said:**
> Sigue sin funcionar. Pruebo como dijo euzkoarima pero no funciona. Me tiene harto. Quiero ponerme a usar linux pero si va a ser así la cosa la verdad que no.
Leí por ahí que capaz tengo que editar a mano el xorg.conf para ponerle las resoluciones y los VSync y HSync según las especificaciones del monitor. Tengo la info pero no se como editarlo.

Aca pongo la imagen que tengo de las especificaciones de mi monitor por las dudas

Seguiré intentando...
Para editar el archivo /etc/X11/xorg.conf podes usar nano, gEdit, vim, kate, etc.

Suponiendo que usas nano: ```
sudo nano /etc/X11/xorg.conf
```

Una vez editado el archivo, tenes que encontrar unas lineas como las que siguen:
> Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "Samsung SyncMaster"
        HorizSync       30.0 - 81.0
        VertRefresh     56.0 - 75.0 donde HorizSync tiene los limites de frecuencias para el barrido horizontal de tu monitor y VertRefresh las del barrido vertical.

---

### Post by VashTheStampede on 2010-01-08
Con muchísima alegría quisiera comentarles que gracias a su ayuda y a leer incansablemente páginas varias de internet conseguí hacer funcionar linux con los drivers de la página de ATI.

Por alguna razón que desconozco no toma automáticamente los valores del monitor así que edité a mano el xorg.conf y le puse las resoluciones y los valores de frecuencia. Se ve que cuando edité anteriormente el archivo lo había hecho mal y por eso no funcionaba. Ahora cometí un error pero me fijé en el log y pude solucionarlo. Tortuoso el camino pero aprendí muchas cosas así que, como dicen, no hay mal que por bien no venga.

Sin embargo tengo muchos flickeos que no se de que son y que estoy investigando a ver que pasa. Cuando carga linux y cuando ejecuto algo que utiliza la placa aparecen. Ya veré.

Por lo pronto muchas gracias a todos!!

---

