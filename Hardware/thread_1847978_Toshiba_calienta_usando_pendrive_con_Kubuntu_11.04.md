---
title: "Toshiba calienta usando pendrive con Kubuntu 11.04"
date: 2011-09-21
forum: Hardware
---

### Post by aregnando on 2011-09-21
Hola a todos, tengo una consulta que luego de andar bastante por google no pude encontrar una respuesta concreta. El tema es el siguiente, tengo una notebook Toshiba Satellite L305 con un dual core, 1 Gb de ram, en la máquina tengo instalado Win vista y anda medianamente bien sobre todo el tema de temperatura de la máquina, normalmente ronda los 50º C, el tema es la quiero formatear e instalarle Kubuntu 11.04 el tema es que actualmente lo estoy corriendo desde un pendrive persistente y la temperatura nunca baja de los 68º y a veces se dispara teniendo que apagar la máquina para que no se sobre caliente.
La pregunta es, sucede esto porque estoy usandolo desde el pendrive y al instalarlo se corrige o bien es un problema habitual y hay que tocar algún archivo de configuración para que esto no suceda.
En fin no me gustaría que por este motivo no pueda instalarlo.
Gracias y saludos a todos.

---

### Post by guillermolisi on 2011-09-21
El efecto no esta relacionado con la forma en que se corre el sistema operativo, esta relacionado con las diferencias en como cada uno utiliza el hardware de la maquina en donde los drivers para sus componentes pueden variar mucho, particularmente si la placa de video no es bien detectada y no se le aplica el driver correcto y, a raiz de ello, el mayor trabajo lo realiza la CPU

---

### Post by aregnando on 2011-09-22
Gracias Guillermo por tu respuesta, esta máquina viene con "Mobile Intel Graphics Media accelerator 4500M" dice que es memoria de gráficos compartida dinamicamente asignada, por lo que pude ver no hay drivers específicos para este sistema en Ubuntu, corregime si me equivoco, y me parece que tal como vos decís el trabajo lo hace por completo el procesador.
No se si habrá alguna solución para esto.

---

### Post by guillermolisi on 2011-09-23
> **aregnando said:**
> Gracias Guillermo por tu respuesta, esta máquina viene con "Mobile Intel Graphics Media accelerator 4500M" dice que es memoria de gráficos compartida dinamicamente asignada, por lo que pude ver no hay drivers específicos para este sistema en Ubuntu, corregime si me equivoco, y me parece que tal como vos decís el trabajo lo hace por completo el procesador.
No se si habrá alguna solución para esto.
Proba con una sesion Live usando la beta 2 de la 11.10 que viene con el kernel 3 de Linux e incluye drivers para hardware moderno y una leve mejora en el consumo de energia.

De paso podras ver si tu hardware de video es adecuado para usar Unity 3D y Gnome 3. Si no lo es automaticamente deberia realizar un fallback a Unity 2D o Gnome 2 (classic).

---

