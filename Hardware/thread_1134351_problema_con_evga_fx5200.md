---
title: "problema con evga fx5200"
date: 2009-04-23
forum: Hardware
---

### Post by Fendrixdaioart on 2009-04-23
hola este es mi primer post en el foro... y espero que puedan ayudarme con una placa EVGA Geforce FX5200 que no me quiere andar ni con envyng, ni con los controladores restrictivos y la verdad q trate de hacer andarla modificando el xorg.conf y no se reparo.. :S... 

De la unica forma q toma la placa es con el controlador 173 de accelerated graphics driver..
Espero que me ayuden a cambiar la resolucion de tal porq tomandome la plca me funciona  640 por 480 cosa que me limita bastante porque tengo q utilizar programas de diseño web y grafico.
Muchas gracias comunidad UBUNTU..

---

### Post by staar on 2009-04-23
decis que instalaste el controlador nvidia-173-xx? porque si es asi, ese es el correcto para esa serie de placas, los controladores mas nuevos ya no las soportan...

si estas con el problema de la resolución, lo que tenés que hacer es modificar el xorg.conf para agregarle los datos de tu monitor...

abri el xorg.conf```
sudo gedit /etc/X11/xorg.conf
```

anda a la sección "Monitor" y editala de acuerdo al monitor que tengas, lo importante es la parte de HorizSync y de VertRefresh, busca esos valores en el manual del monitor y colocalos....

te muestro la seccion monitor de mi xorg.conf, para que te des una idea...

```
Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Samsung"           
    ModelName      "Samsung SyncMaster 750(T)"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Gamma           1 
EndSection

```

saludos

---

