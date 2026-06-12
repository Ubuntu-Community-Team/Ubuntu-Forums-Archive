---
title: "Hp deskjet ink advantage k109"
date: 2010-07-06
forum: Hardware
---

### Post by RafaelG on 2010-07-06
[SIZE=2]Saludos a todos los Ubunteros,

Tengo el siguiente inconveniente compre una HP deskjet Ink Advantage k109, tengo el repositorio HPLIP 3.10.2 instalado y al momento de alinear imprime la hoja con el requerimiento pero cuando deseo imprimir un documento o una Hoja de prueba desde el mismo HPLIP aparece como si funcionara correctamente pero la impresora no imprime. 

Googliando en HP y Launchpad aparentemente necesito la version 3.10.5 la cual deberia funcionar sin problema alguno. He tratado de instalar la version pero no he podido dar con el howto de la instalacion.
[/SIZE]

---

### Post by Carlos C on 2010-07-06
Y si pruebas con esto?
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by RafaelG on 2010-07-07
> **Carlos C said:**
> Y si pruebas con esto?
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

[SIZE=2]Carlos C,[/SIZE]

[SIZE=2]Habia probado con ese Link sin tener exito ya que no podia ingresar a las instrucciones. Para poder acceder a las intrucciones en mi caso particular tuve que ingresar previamente los siguientes codigo en terminal cosa que en las Instrucciones de HP no lo inidica. 

[/SIZE][SIZE=2]Para Finalizar el Post tuve que realizar esta instalacion  de la version [/SIZE][SIZE=2]HPLIP [/SIZE][SIZE=2]3.10.5  la cual es la version mas actualizada y que viene por defecto en  Maverick ya que en la version actual de Karmic HPLIP 3.10.2 no funciona  correctamente con el modelo de mi impresora HP.  [/SIZE]
```
[SIZE=3]cd ~/Desktop
chmod +x hplip-3.10.5.run
sh hplip-3.10.5.run[/SIZE]
```

---

### Post by RafaelG on 2010-07-31
> **RafaelG said:**
> [SIZE=2]Para Finalizar el Post tuve que realizar esta instalacion  de la version [/SIZE][SIZE=2]HPLIP [/SIZE][SIZE=2]3.10.5  la cual es la version mas actualizada y que viene por defecto en  Maverick ya que en la version actual de Karmic HPLIP 3.10.2 no funciona  correctamente con el modelo de mi impresora HP.  [/SIZE]

[SIZE=2]
Estimados Ubunteros,

Por alguna extrana razon mi Printer volvio a presentar problemas y logicamente volvi a la fuente **HP Link** me he percatado que salio la version HPLIP 3.10.**6**  descargue el nuevo driver y tuve que volver hacer toda la configurasion indicada en HP pero con esta nueva version y Listo Problema Solucionado.[/SIZE]

**HP Link**> [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

