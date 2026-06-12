---
title: "Actualizacion kernel"
date: 2010-01-04
forum: Instalación y Actualización
---

### Post by Iced_R on 2010-01-04
Holas a todos!!

Tengo un problema más o menos interesante. Tengo sistema dual en mi PC, y desde hace un tiempo q mi Karmic no me quiere bajar actualizaciones de kernel. Toy pegado en la versión 2.6.31-16 del kernel, siendo q sé q al menos existe en la lista de repositorios el kernel -17.

Y por otro lado, se me murió el teclado numérico! (Sé q no va aquí, pero no quiero abrir tantos threads xD). Sé q hardwarísitcamente hablando el teclado numérico está vivo, xq juego en GUIndows con él, pero en Karmic sólo funciona el Intro, nada más. ¿Alguna sugerencia? Yo ni siquiera sé cómo podría intentar resolverlo.


Saludos a todos

---

### Post by moreback on 2010-01-04
Por favor una sola pregunta por hilo, si no se desordena el foro.

Gracias.

---

### Post by Carlos C on 2010-01-04
Sí, para el tema del teclado por favor abre un hilo nuevo.

Respecto al kernel, yo también tengo Karmic:
```
carlos@carlos-laptop:~$ uname -r
2.6.31-16-generic
```

Me parece que está todo bien :confused:
Saludos.

---

### Post by kamus on 2010-01-04
Dudo mucho que sea problema de kernel, que distribución de teclado tienes instalado y configurado por defecto? en sistema->preferencias->teclado lo puedes revisar.

Saludos

---

### Post by moreback on 2010-01-04
> **Iced_R said:**
> Holas a todos!!

Tengo un problema más o menos interesante. Tengo sistema dual en mi PC, y desde hace un tiempo q mi Karmic no me quiere bajar actualizaciones de kernel. Toy pegado en la versión 2.6.31-16 del kernel, siendo q sé q al menos existe en la lista de repositorios el kernel -17.

Saludos a todos


No sé que depósitos estás viendo, ya que en el oficial el último en este momento es **linux-image-2.6.31-16-generic**.

Saludos.

---

### Post by Iced_R on 2010-01-05
Bueno, uno de mis compañeros de universidad, al hacer la actualización de Linux dp de instalarlo desde CD, tiene un kernel -17. Por eso es que pensé q había otro kernel más y yo taba pegado en un kernel anterior, pero si uds. me dicen q toy bien... 

Ah, y por lo del teclado, ya abrí otro hilo. Gracias, pueden cerrar.

---

### Post by Carlos C on 2010-01-05
Cada distro tiene sus propios criterios para determinar cuándo actualizar el kernel, si tu amigo tiene otra distribución perfectamente puede tener un kernel más nuevo. Incluso en el caso de Ubuntu si tienes una versión LTS o si es una versión server estos criterios se modifican. En mi caso tengo un equipo con Ubuntu Server 9.04 y su kernel es el 2.6.28-17-server :)

Saludos.

---

### Post by moFeta on 2010-01-07
Kernel o teclado?
Este es sobre el teclado.
Es fácil, me pasa todo el tiempo, creo que cuando actualiza el kernel.
Sistema > Preferencias > Teclado. En la pestaña que dice "Teclas de Ratón" desactiva el checkbox que dice "Permitir Controlar el Puntero usando el teclado numérico". Y listo.

---

### Post by CdK1 on 2010-01-08
Como señaló el bueno de  Carlos_C, cada distribución tiene sus propias actualizaciones de kernel, Ej.- 

CdK1@Caturra:/$ uname -r
2.6.32-trunk-686
CdK1@Caturra:/

Lo del teclado, sigue los pasos que te señalaron...

PD: Si quieres un kernel más nuevo, puedes ingresar a [http://www.kernel.org](http://www.kernel.org) y bajar el último más su parche y compilarlo...

---

### Post by Carlos C on 2010-01-08
Creo que la duda sobre el kernel está resuelta. El problema del teclado también se resolvió en el thread que abriste:

[http://ubuntuforums.org/showthread.php?t=1372960](http://ubuntuforums.org/showthread.php?t=1372960)

Me parece que para evitar más desorden lo mejor es cerrar este.

Saludos.

---

