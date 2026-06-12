---
title: "Kubuntu problemas tarjeta inalámbrica Broadcom STA"
date: 2010-01-04
forum: Hardware
---

### Post by Inlefort on 2010-01-04
Hola, tengo ubuntu ya hace un buen tiempo, ahora querai probarlo con el entorno kde, 
instale Kubuntu, pero no me reconoce la tarjeta inalambrica :O
en ubuntu usa un controlador privativo
el controlador se llama Controlador inalámbrico Broadcom STA

el modelo de mi laptop es  Compaq presario CQ40-320la
la trarjeta inalambrica   WLAN 802.11 b/g 

mi pregunta es si puedo conseguir los drivers e instalarlos en kubuntu y como 
Gracias de antemano

---

### Post by Carlos C on 2010-01-04
Por favor escribe en el terminal:
```
lspci -vnn | grep 14e4
```y dinos el resultado que te entrega ese comando.

Movido al subforo "Hardware" y cambiado el título por uno más descriptivo.
Por favor no olvides leer [esto]("http://ubuntuforums.org/showthread.php?t=1162750").

Saludos.

---

### Post by CdK1 on 2010-01-06
Si te funciona ese driver en Ubuntu, OBVIAMENTE te funcionará en Kubuntu...

---

