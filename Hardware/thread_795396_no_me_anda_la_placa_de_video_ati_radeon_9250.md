---
title: "no me anda la placa de video ati radeon 9250"
date: 2008-05-15
forum: Hardware
---

### Post by larvaciega on 2008-05-15
Hola soy nuevo en linux y logre que ande todo pero no puedo hacer que ande la placa de video ati radeon 9250 ya probe con el gestor de sinaptic y tampoco cuando quiero configurarla me tira 

augusto@larvaciega:~$ sudo aticonfig --desktop-setup=horizontal
[sudo] password for augusto:
Data incomplete in file /etc/X11/xorg.conf
        Device section "Configured Video Device" must have a Driver line.
aticonfig: Parsing the configuration file failed.
The above error messages are reported from XFree86 and may assist you in
diagnosing the problem with your configuration input file. Try use -f option
to generate a new configuration file.

---

### Post by sajnox on 2008-05-15
Las placas ati son todo un tema.

Por lo que veo te bajaste el driver de ati de la pagina, pero resulta que instalar el driver de ati no es lo mas facil del mundo si lo haces asi.

Primera pregunta: Te bajaste el driver de ati por que lo instintivo que hubieras hecho en windows o por algo en particular?

Lo primero que te aconsejo con el driver de ati es que no hagas nada, la maquina te instala un driver libre si reconoce la placa, si te pide usar controladores restringidos....No los Uses!!!

Proba habilitar los efectos del escritorio, si te los toma es que tenes la placa habilitada correctamente.

2) Si igual queres usar los drivers de ati te recomiendo que uses envy (programa que descarga y configura los drivers para ati y nvidia), lo bajas de la pagina del programador [www.albertomilone.com](www.albertomilone.com)

---

### Post by larvaciega on 2008-05-15
Gracias. en realidad lo baje porque lei en un post de este forum que decia como bajarlo e instalarlo pero igual no funciono. la verdad es que anda pero la calidad de imagen no es buena y los efectos 3d no se ven bien. por otra parte no puedo usar la salida de Tv de la placa y el sistema de control de donde lo habilito me tira el error que mostre antes.

---

### Post by larvaciega on 2008-05-15
ahi probe los efectos de escritorio pero no me los carga por ejemplo no me hace el escritorio como cubo. supongo que no esta cargando la placa o puede ser algo mas??

---

### Post by sajnox on 2008-05-15
Para saber si tenes aceleracion 3d en un consola escribi lo siguiente

```
glxinfo | grep direct
```

si respnde Yes, es que la placa esta bien habilitada, por otro lado a que te referis con que los efectos 3d no se ven bien, generalmente se ven o no.

---

### Post by Hei Ku on 2008-05-15
proba con envy, o en el caso de la 9250, con el driver libre radeon que anda bien para esas placas. yo tengo la 9200 con el driver libre y compiz anda de 10. Aclaro que nunca la probe mucho con juegos.

---

### Post by larvaciega on 2008-05-16
gracias a los dos, probe las dos cosas y esta funcionando. en relidad formatie y cargue de vuelta todo y esta corriendo joya. otra cosa hey ku sabes como puedo hacer andar la salida de TV?

---

### Post by Hei Ku on 2008-05-16
no recuerdo haberla probado en ubuntu. pero segun me acuerdo, con reiniciar teniendo la tv conectada, eso deberia tomarla.
y si no, busca en wiki.ubuntu.com por radeon, ahi habia varios tips sobre como configurar el xorg para que tome todo.

---

### Post by mikeollie1 on 2009-11-27
Mira aquí [https://bugs.launchpad.net/ubuntu/+s...ti/+bug/444139](https://bugs.launchpad.net/ubuntu/+s...ti/+bug/444139) post #41, me funcionó perfecto con mi Radeon 9250 y karmic koala.
Un saludo

---

### Post by Mauro22 on 2009-11-27
1 año y pico tiene esto...

---

