---
title: "Retorno de microfono!!"
date: 2009-09-01
forum: Hardware
---

### Post by baleoj on 2009-09-01
Hola gente, que tal, soy nuevo usando ubuntu.

Tengo el siguiente problema: No puedo escucharme por el microfono. El microfono anda, si grabo con el grabador de sonido me toma la voz, todo bien. Pero yo quiero hablar y escuchar al mismo tiempo lo que estoy diciendo. 
 Creo que usando programas puedo grabar y escuchar al mismo tiempo, pero yo quiero hacerlo sin grabar. Segun un post viejo un flaco pudo hacerlo con el jack control, pero segui un monton de guias y nunca lo pude instalar bien, no se me conecta.

Como puedo hacer?

muchas gracias!!

---

### Post by baleoj on 2009-09-03
Vamos, no puede ser que nadie sepa!!

---

### Post by Hei Ku on 2009-09-03
Si, puede ser. Todos los días llegan preguntas de cosas que se hacen por primera vez.

---

### Post by pablo.s on 2009-09-03
Probá con Audacity.
Asegurate que los
volumenes de entrada 
y salida estén lo 
suficientemente fuerte.

---

### Post by baleoj on 2009-09-03
Lei que con audacy y otros programas de grabación se puede hacer. (grabas y escuchas al mismo tiempo lo que se graba) Pero yo no quiero grabar. Si no tendría que estar grabando todo el tiempo. Yo quiero conectar el mic, hablar y que salga por los parlantes lo que digo!

En este post una persona pregunta lo mismo [http://ubuntuforums.org/archive/index.php/t-1060424.html](http://ubuntuforums.org/archive/index.php/t-1060424.html) pero lo logra instalando el jack control y haciendo un monton de configuraciones. Yo intente instalarlo, siguiendo al pie de la letra las instrucciones pero cuando doy a iniciar me tira error, no se puede conectar. Asi que no pude usando el jack :S

por eso pregunto aca, capaz hay otra manera de hacerlo

muchas gracias

---

### Post by pablo.s on 2009-09-03
> **baleoj said:**
> Lei que con audacy y otros programas de grabación se puede hacer.

Si, es asi, probá lo que
te cuento, monitorea y no
tenés que grabar con
Audacity. Pero no lo has
probado. Todavia.

> **baleoj said:**
> por eso pregunto aca, capaz hay otra manera de hacerlo


Y, mirá, monitorear el
nivel de grabación creo
que también lo hace Ardour,
Jokosher, en fin, dos o tres
más hay...

---

### Post by baleoj on 2009-09-03
como monitorear?

vos decis que configurando el audacy (u otro programa) aunque no este grabando, me toma esa configuracion para cuando use el microfono sin poner record en el programa? 
bueno voy a probar y les digo q onda

gracias

---

### Post by pablo.s on 2009-09-04
> **baleoj said:**
> como monitorear?

En un estudio de grabación
antes de grabar una pista se
comprueba que la señal no
sature, que por tener muy
altos los volúmenes arruine
la toma. Por lo tanto se usan
los displays de nivel, que
marcan porcentajes y colores.
Vos queres escucharte sin
grabar. Eso se llama monitorear,
entonces.

---

### Post by baleoj on 2009-09-04
Lo hice y se puede, pero se escucha MUY BAJO, eso que puse los parlantes al maximo volumen, y tambien desde linux tengo el volumen alto.

Como puedo hacer para que se escuche fuerte?

en el tutorial dice que para escucharse hay que poner en preferencias una opcion, la pongo pero luego no puedo cerrar preferencias, no tengo un boton para guardar los cambios ni nada, tampoco puedo volver al programa, lo tengo que cerrar desde el monitor del sistema =S

gracias!

---

### Post by pablo.s on 2009-09-04
Escribí en una terminal

```
alsamixer
```

y subí los volumenes con
las teclas de función. Al
finalizar salis con la tecla
Escape.
Luego volvé a Audacity y
fijate si tenés mejor resultado.

PD: Prestá más atención a
los menús de los programas.

---

### Post by baleoj on 2009-09-04
Dios, tenes razon, se salia con escape, pasa que apretaba muy rapido y no me lo tomaba.

Puse lo de alsamixer, y ya tenia todo al mango porque los subi desde el control de volumen.

EDIT: Bueno ahora si logre hacerlo. Me escucho, pero tengo un insoportable ruido de fondo. Logre disminuirlo bajando el volumen de Front Mic y de Linea de entrada. Aunque saque el microfono, el zumbido sigue. Esto es un problema del parlante, no? o configurando el programa se puede sacar? (el zumbido aparece xq tengo q poner al mango el parlante)

Muchisisimas gracias

---

