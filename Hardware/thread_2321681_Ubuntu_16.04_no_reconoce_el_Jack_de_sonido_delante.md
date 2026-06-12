---
title: "Ubuntu 16.04 no reconoce el Jack de sonido delantero"
date: 2016-04-23
forum: Hardware
---

### Post by drazhe on 2016-04-23
Hola nuevamente, un problema que noté al instalar **Ubuntu 16.04 LTS x64 Final** es que no reconoce el conector de micrófono y salida de auriculares delantera de la PC, dicho jack se que funciona porque en la versión 14.04 que venía utilizando hasta hoy funcionaba perfectamente y en Fedora también... 

solo funciona el conector trasero y antes funcionaban los dos, ¿Hay alguna manera de solucionarlo?

Muchas gracias!

---

### Post by dpinzonb on 2016-05-03
Tengo el mismo problema, los jacks de sonido delanteros no funcionan con Ubuntu 16.04

---

### Post by labotica on 2016-08-24
Tengo el mismo problema. También en Ubuntu 16.04 y mi tarjeta de sonido es HDA Intel PCH IDT 92HD89E2

---

### Post by papibe on 2016-08-24
Hola drazhe.

Se ven las salidas y entradas delanteras en la lista de dispositivos en Sound -> Input?

Puedes ejectutar este par de comandos y pegar el resultado (copia el texto con el mouse)?
```
aplay -l

pacmd list
```
Saludos.

P.D.: Puede que sea necesario que haya algún cable conectado para que aparezca valido.

---

