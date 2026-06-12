---
title: "Por qué no es bueno apagar el equipo a lo bruto"
date: 2009-07-01
forum: Hardware
---

### Post by jorval on 2009-07-01
Hola amigos. Sabes por qué no es bueno apagar el computador empleando el botón de apagado o por qué un corte de luz puede provocar un desastre. Mejor les copio lo que encontré. Seguramente casi todos lo saben, pero quizás aún hay algunos como yo que no tienen idea del por qué.

"¡No apague la computadora directamente! ¡Se arriesga a perder valiosos datos! A diferencia de la mayoría de las versiones de DOS, no es una buena idea apagar la llave de alimentación de la computadora así como así cuando termine de utilizarla. Si reinicia la máquina con el botón de reset sin antes tomar las debidas precauciones será igual de pernicioso. Linux tiene una antememoria o caché&#769; que mejora el rendimiento del disco. Esto significa que temporalmente guarda en RAM información perteneciente al sistema de almacenamiento permanente Las diferencias entre lo que Linux cree que hay en el disco y lo que efectivamente está almacenado en el disco se sincronizan cada 30 segundos. Si desea apagar o reiniciar la computadora, necesitará ejecutar algún procedimiento que indique a Linux que debe detener el sistema de cachéy actualizar la información en el disco".

---

### Post by aledruetta on 2009-07-02
Interesante, Jorval, no sabía esto.

Últimamente tuve una serie de problemas en los que Ubuntu se tildaba y no me dejaba otra opción mas que "apagar a lo bestia".
Sería bueno saber, en esos casos, qué procedimiento existe para no correr riesgos con el sistema.

Saludos,
Alejandro.

---

### Post by Carlos C on 2009-07-02
Existe una forma de reiniciar el sistema en esos casos. Consiste en mantener apretadas las teclas Control+ImprPant y, sin soltarlas, escribir: RSEIUB. En pocas palabras lo que hace esta combinación de teclas es lo siguiente:

R: Devuelve el control al teclado.
S: Sincroniza los sistemas de archivos y las unidades montadas (aquí se evitan muchos de los problemas que Jorval señala)
E: A cada proceso le envía la señal Term.
I: A todos los procesos le envía la señal KILL.
U: Desmonta todos los sistemas de archivos.
B: Reinicia.

Si en vez de reiniciar prefieres hacer un shut down puedes reemplazar la "B" por una "O".

---

### Post by radixs on 2009-07-02
> **Carlos C said:**
> Existe una forma de reiniciar el sistema en esos casos. Consiste en mantener apretadas las teclas Control+ImprPant y, sin soltarlas, escribir: RSEIUB. En pocas palabras lo que hace esta combinación de teclas es lo siguiente:

R: Devuelve el control al teclado.
S: Sincroniza los sistemas de archivos y las unidades montadas (aquí se evitan muchos de los problemas que Jorval señala)
E: A cada proceso le envía la señal Term.
I: A todos los procesos le envía la señal KILL.
U: Desmonta todos los sistemas de archivos.
B: Reinicia.

Si en vez de reiniciar prefieres hacer un shut down puedes reemplazar la "B" por una "O".

Excelente info Carlos_C. Esta se va si o si a mi blog

---

### Post by Carlos C on 2009-07-02
Más información:

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://lxr.linux.no/linux/Documentation/sysrq.txt](http://lxr.linux.no/linux/Documentation/sysrq.txt)

---

### Post by moreback on 2009-07-03
Lo malo del Alt+SysRq+REISUB es que si se te cuelgan las X pierdes también el teclado.

---

### Post by Carlos C on 2009-07-03
No siempre, me han pasado ambas cosas, que al colgarse las x he perdido el teclado y nada funciona, pero en otras ocasiones que se ha colgado el entorno gráfico, he perdido aparentemente respuesta del teclado, pero este ha vuelto ha la vida al apretar R. Ojo que con eso no quiero decir que Ubuntu se me pasa colgando jeje.

---

### Post by RafaelG on 2009-07-03
> **moreback said:**
> Lo malo del Alt+SysRq+REISUB es que si se te cuelgan las X pierdes también el teclado.


Moreback eso mismo me ha pasado a mi y no puedo hacer nada en el teclado tampoco, en ese caso que puedo hacer cuando tampoco responde el teclado? por que la idea tampoco es apagarlo desde el Boton de On/Off.

---

### Post by Carlos C on 2009-07-03
En esos casos ya no hay muchas posibilidades. Me temo que si la combinación de teclas no te funciona no queda otra que apagar el equipo a la fuerza. Amenos que el equipo tenga un servidor ssh funcionando. En ocasiones es posible acceder al sistema remotamente por ssh.

---

### Post by jorval on 2009-07-03
A mi se me pega el sistema al apagarlo: Sistema --> Salir --> Apagar y ahí se pega el sistema, puedo mover el puntero pero nada más. He tratado con CTRL+ImprPant+ RSEIUB y no sucede nada. Finalmente lo apago con CTRl+ALT+Retroceder. Esto me sucede regularmente cada 10 apagadas del equipo más o menos ¿por qué? No tengo idea pero no me ha causado problemas hasta ahora. Saludos.

---

### Post by aledruetta on 2009-07-04
> **jorval said:**
> A mi se me pega el sistema al apagarlo: Sistema --> Salir --> Apagar y ahí se pega el sistema, puedo mover el puntero pero nada más. He tratado con CTRL+ImprPant+ RSEIUB y no sucede nada. Finalmente lo apago con CTRl+ALT+Retroceder. Esto me sucede regularmente cada 10 apagadas del equipo más o menos ¿por qué? No tengo idea pero no me ha causado problemas hasta ahora. Saludos.

Ahí, si no me equivoco, lo que estás haciendo es reiniciar las X. En Jaunty esa combinación de teclas está desactivada, pero hay varios post donde dice cómo activarla otra vez. Pero me parece que no es el caso de que el sistema se cuelgue sino el servidor gráfico. 

Disculpen si estoy diciendo cualquier cosa...

---

### Post by jorval on 2009-07-06
Más información sobre el apagado seguro:

[http://util-pc.com/blog/2009/03/10/apagado-seguro-en-linux-con-la-tecla-sysrq/]("http://util-pc.com/blog/2009/03/10/apagado-seguro-en-linux-con-la-tecla-sysrq/")

Al leer este artículo me quedó la duda sobre lo que dice: [HTML]Para usar la opción necesitamos primero tenerla compilada en el kernel[/HTML] pues cuando yo usé la tecla mágica no me funcionó y a lo mejor se debe a lo que aquí dice ¿cómo se compilará en el kernel? ¿alguien podrá explicarlo? Gracias.

Ha, y otra cosa importante. Unos dicen que hay que apretar la tecla CTRL y otros la ALT. ¿Cual es la correcta? Y si fuese ALT a mi no me da la mano para hacerlo junto con la ImpPan+otra  ¿¿¿¿????

---

