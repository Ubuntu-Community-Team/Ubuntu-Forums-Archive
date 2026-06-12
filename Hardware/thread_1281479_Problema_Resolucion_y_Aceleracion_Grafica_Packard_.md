---
title: "Problema Resolucion y Aceleracion Grafica Packard Bell MX37-v-035"
date: 2009-10-03
forum: Hardware
---

### Post by victor androide on 2009-10-03
Hola a todos Bueno resulta que Buscando opciones de sistemas operativos llegue con Ubuntu, es muy bueno y estable por lo que e visto en otros computadores pero el problema es en el mio que 
primero no me funcionan los efectos graficos.
no puedo cambiar la resolucion es eso lo que necesito ayuda porfavor !!!!!

las caracteristicas de mi packard bell:
MarcaPackard Bell ModeloMX37 ProcesadorIntel Celeron M 530 Velocidad del Procesador1.73  GHzHDCapacidad del HD80  GBytesInterface del HD5400 RPM MemoriaMemoria RAM2048  MBytesCD / DVDMídias CompatiblesDVD-RW DisplayPantalla15.4  pulgadasWidescreenSí Red y MódemEntradas / SalidasRJ-45 , RJ-11Entrada USB4  Puerta(s)

---

### Post by Patriciologico on 2009-10-04
Hola Victor, bienvenido al foro del Team Ubuntu Chile.

 Antes que todo te sugiero leas [las normas del foro]("http://ubuntuforums.org/showthread.php?t=1162750") para que no vuelvas a cometer el error de postear en un lugar equivocado (tu post lo he movido).

 Lamentablemente tu problema es de tarjeta grafica y no nos indicas cual es, aunque creo es un chip integrado SIS 330. Ademas debes informar que version de Ubuntu estas usando.

Para ver que chip grafico tienes utiliza el comando

```
lspci |grep VGA
```

Si el chip es SIS como creo, (en la categoria de las unichrome, osea baja) no pienses en efectos graficos. Se que puede se frustrante, como me sucedio a mi con un Winmodem al iniciarme en Linux, pero con el tiempo tendras oportunidad de comprar hardware compatible.

Saludos!

---

