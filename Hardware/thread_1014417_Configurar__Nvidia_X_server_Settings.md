---
title: "Configurar  Nvidia X server Settings"
date: 2008-12-17
forum: Hardware
---

### Post by erdosain9 on 2008-12-17
Hola quería saber cómo hacer para guardar los cambios... porque resulta que al poner guardar me dice "Unable to create new X config backup"... y la dirección.

Un saludo y gracias

---

### Post by luks911 on 2008-12-17
Dos posibilidades: 1) ejecutá nvidia-settings como root, o sea con sudo delante; 2) fijate que en el último menú de nvidia-settings, llamado nvidia-settings configuration, esté desmarcada la casilla que dice Include X Display Names in the Config File.

---

### Post by hictio on 2008-12-18
No estoy muy seguro si te entiendo, pero yo lo que hago es no ejecutarlo como root -es decir, sin el sudo- y cuando selecciono guardar, guardo el archivo el mi $HOME, y despues, o re-escribo el /etc/X11/xorg.conf del sistema, o sino incorporo los cambios que sugiere el xorg.conf de NVIDIA.

---

### Post by luks911 on 2008-12-18
En realidad, lo ejecuto edsde el menú como mi usuario, no como root. Pero creo que no tengo problemas pra grabar porque tengo desmarcada aquella casilla que señalaba antes. Al menos en su momento el problema lo había resuelto así, en Gutsy :-P

---

