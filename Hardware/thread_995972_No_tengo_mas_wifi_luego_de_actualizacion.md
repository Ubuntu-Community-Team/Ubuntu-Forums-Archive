---
title: "No tengo mas wifi luego de actualizacion"
date: 2008-11-28
forum: Hardware
---

### Post by sitiomatic on 2008-11-28
Hola a todos.
Hoy me aparecio el simbolito de actualizar (uso 8.10) y le di ok.
En algun momento aparecio una pregunta sobre actualizar o no algo (la verdad es que ni mire) y le di actualizar.
La cosa es que cuando booteo no tengo mas wifi. Yo estaba usando madwifi.
Modifique el arranque para que inicie por defecto con la version anterior o sea 2.6.27-7 y todo anda bien
Si inicio con la nueva (2.6.27-9) no tengo wifi ni anda el led obviamente que modifique en el sysctl.
Hay manera de arreglar esto para que todo funcione actualizando el kernel? Como seria el procedimiento normal para la proxima vez?
Gracias miles

---

### Post by luks911 on 2008-11-28
Sencillo: volvé a compilar e instalar madwifi como lo habías hecho. Esto te va a pasar cada vez que haya una actualización del kernel, porque lo compilaste para la versión que se está utilizando.

Sobre si hay alternativa, una es que uses otro driver. No sé que placa tenés, pero yo uso madwifi para la Atheros AR5007EG y podría usar otro driver instalando linux-backports-modules-intrepid. No lo hago porque no me sirvió del todo, aunque a otros sí. 
Otra es buscar la forma de que se autocompile y autoinstale luego de cada actualización del kernel. Vor, compañero del foro, lo hizo para los drivers de Nvidia con un script y algo más ([http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)). Pero mis conocimientos apenas si llegan para recompilar madwifi tras cada nueva versión del kernel. :-P

Saludos

---

### Post by sitiomatic on 2008-11-28
> **luks911 said:**
> Sencillo: volvé a compilar e instalar madwifi como lo habías hecho. Esto te va a pasar cada vez que haya una actualización del kernel, porque lo compilaste para la versión que se está utilizando.

Saludos

Esas son exactamente las palabras que temia oir jejeje
Gracias

---

