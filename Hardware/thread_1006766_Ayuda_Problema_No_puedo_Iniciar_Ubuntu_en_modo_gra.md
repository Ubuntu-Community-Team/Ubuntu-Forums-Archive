---
title: "Ayuda Problema No puedo Iniciar Ubuntu en modo grafico"
date: 2008-12-09
forum: Hardware
---

### Post by --Lutari-- on 2008-12-09
hola necesito ayuda tenia intalado ubuntu 8.04 y actualize a 8.10 pero ahora cuandi la enciendo me carga el logo de ubuntu y luego me aparecen una consola que pide mi login y contraseña y de alli ya no pasa a la pantalla de inisio de sesion en otros palabras se queda en modo texto y no se que comandos usar o que configurar para poder iniciar y llegar a la apantalla de ubuntu ayudenme es urgente Dios los va a bendecir.

---

### Post by Hei Ku on 2008-12-09
Probá con este comando:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Si no, posteá que placa de video tenés y si sabes, que driver usas. Preferentemente con el comando lspci, asi vemos el modelo exacto.

EDIT: Edite el nombre del thread para que se entienda por dónde viene el problema.

---

### Post by faktorqm on 2008-12-09
y despues de ese comando escribi

```
sudo /etc/init.d/gdm restart
```

si no con el te dijo (bien de todas maneras) Hei Ku reconfiguras la placa de video (capaz tuviste algun problema...) pero no hace mas nada digamos. Ahi reinicias la parte que te muestra el cartel de login grafico con las cosas. 
Si te tira error de algo postealo a ver que paso. Salu2!!

---

