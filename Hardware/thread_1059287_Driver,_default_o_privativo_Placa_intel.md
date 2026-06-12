---
title: "Driver, default o privativo? Placa intel"
date: 2009-02-03
forum: Hardware
---

### Post by NickCis on 2009-02-03
Hola tengo una placa intel 82810 Dc 100, las onboard, que vienen con la Compaq Presario 5473. Tengo una instalacion minima de Ubuntu 8.04, utilizando Openbox como WM.
Y me preguntaba que diferencia tiene usar el driver de video que viene por default con ubuntu a usar el privativo de Intel, obtendre un mejor rendimiento o algun beneficio?.

Pagina de donde se descarga el driver: [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=798&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=798&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

Lo que me devuelve al hacer un lspci:
```
oldpc@oldpc:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810 DC-100 (GMCH) Graphics Memory Controller Hub (rev 02=
00:1e.0 VGA compatible controller: Intel Corporation 82810 Dc-100 (CGC) Chipset Graphics Controller (rev 02)

``` 
(eso es lo que esta relacionado con la placa, tengo xterm y tengo que copiarlo a mano, si hay alguna manera de hacer un ctr c, ctr v , que alguien me diga xD...)

Saludos.

---

### Post by Hei Ku on 2009-02-03
Hmmmm, el driver de Intel es libre. Lo podes bajar directo de git y compilarlo vos mismo si queres.

En realidad la pregunta es si usar la ultima version o no. Eso depende de si tenes algun problema con la version actual. Las versiones que vienen en los repositorios tienden a ser mas estables.

---

### Post by NickCis on 2009-02-03
Ahhh,,, algo que no sabia :P, pero entonces, actualmente estoy usando el driver de intel (yo nunca lo instale si no se instalo solo, yo no lo hice xD)?. El Ubuntu te lo instala solo?.

Me podes explicar como lo instalo, y compilo, por favor...

Saludos.

P.D.: no tengo ningun problema con lo que tengo instalado ahora, solo queria saber si instalarlo me generaria algun beneficio en rendimiento, :P

---

### Post by Hei Ku on 2009-02-03
No, probablemente no te de ningun beneficio. Y compilar un driver no es algo que haria salvo que tengas alguna necesidad.

Como son parte del kernel, los drivers de intel se activan solos si detectan que tenes la placa. Que ricura, no? :D

---

