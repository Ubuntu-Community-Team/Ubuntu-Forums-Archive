---
title: "Mi tarjeta wifi no es reconocida por Ubuntu ¿Qué hago?"
date: 2010-02-19
forum: Hardware
---

### Post by Carlos C on 2010-02-19
Si ocurre que Ubuntu no llegara a reconocer tu tarjeta wifi (algo cada vez menos común) existe más de una alternativa a tu disposición. Te sugiero algunos pasos sencillos:

**1. Determina el modelo exacto del ship de tu tarjeta**. Escribe en el terminal:

 ```
lspci -vnn | grep Wire
```También, puedes usar el comando [lshw]("http://ubuntuforums.org/showthread.php?t=1171656"). Si te confundes en este paso, **[COLOR=DarkRed]lo más recomendable, es que publiques en el foro la información que te entrega [huuf]("http://ubuntuforums.org/showthread.php?t=1410952")[/COLOR]**.

**2. Revisa la documentación de Ubuntu** mantenida por la comunidad:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

**3. Entra en tu panel superior**, en *Sistema-->Administración-->Controladores  de hardware.* Verifica que no haya algún driver privativo disponible. No es la mejor solución pero a veces es la única, sin embargo, repito, esto es cada vez menos necesario.

**3. Revisa el listado de tarjetas soportadas en Linux de Linux wless**, es bastante completo:

[http://linux-wless.passys.nl/?lang=espanol](http://linux-wless.passys.nl/?lang=espanol)

Con eso podrás saber qué driver funciona con tu tarjeta.

4. **Si estás confundido** o no sabes como solucionar algún problema [[COLOR=DarkRed]**te sugiero que uses huuf**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1410952") para generar un reporte de tu equipo y postearlo en el subforo "Hardware" (sí, este mismo).

---

### Post by Felipexs on 2010-05-27
o tambien se puede como en este video tutorial 

[http://www.youtube.com/watch?v=T0ovUDP-1NU&playnext_from=TL&videos=8M045BA-Wag](http://www.youtube.com/watch?v=T0ovUDP-1NU&playnext_from=TL&videos=8M045BA-Wag)

---

