---
title: "[SOLVED] dell inspiron 1420 - Intel 3945ABG"
date: 2008-12-26
forum: Hardware
---

### Post by llove on 2008-12-26
Hola, estoy con una laptop que me prestaron, probando Gutsy no tuve problemas en conectarme, pero con Hardy o Intrepid no puedo conectarme con WPA, si a un router con WPA2, sin seguridad no probe, El tema es que me gustaria poder usar intrepid, probe varias soluciones de las que encontre en el foro, como usar wicd en lugar del network manager y nada, lo mismo, al menos con WPA, con WPA2 y wicd no probe. Tambien intente usar otros drivers como lo indican aca [https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy) pero tampoco, ahora me aparece como DISABLED si hago lshw -C NETWORK.


Saludos.

---

### Post by luks911 on 2008-12-26
¿Ahora qué driver estás usando? ¿Probaste hacer lo contrario de lo que dice el link, es decir usar ipw3945, que es el que venía en Gutsy? Acá[0] un tutorial para hacerlo. 

Saludos

[0] [http://www.ubuntu-es.org/index.php?q=node/88882](http://www.ubuntu-es.org/index.php?q=node/88882)

---

### Post by llove on 2008-12-27
me parece que estoy usando iwl3945, ahora pruebo con la guia esa y comento como fue. gracias.

---

### Post by llove on 2008-12-27
probe con esa guia y anduvo de una, probe la misma guia con un clean install en intrepid y me tiro un error no me acuerdo cual, pero esta andando, de hecho estoy conectado ahora. saludos.

---

### Post by luks911 on 2008-12-27
Buenísimo, me alegro.

Saludos:lolflag:

---

