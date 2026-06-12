---
title: "Problema con video en Intrepid (en Hardy andaba :( )"
date: 2008-11-02
forum: Hardware
---

### Post by Zeq on 2008-11-02
Bueno, mi problema es el siguiente a ver si alguien me puede dar una mano:

Actualice a Intrepid desde Hardy y los videos que solia ver en VLC o la webcam en Slype sin problemas, ahora como que titila la imagen o no la muestra del todo.

Tambien tengo un problema similar con Google Earth.

No se mucho de esto pero les tiro algunos datos a ver si sirven para diagnosticar el problema:

```
~$ glxinfo |grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```

```
~$ lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]

```

En Controladores de Hardware tengo el 'Controlador grafico FGLRX privativo para ATI/AMD' habilitado.

Entiendo que no tengo la aceleradora de video activada (es asi?)
Igualmente en Hardy tenia lo mismo y podia ver bien los videos.

Si alguien tiene idea de como se soluciona y/o como se activa la aceleradora les estaria agradecido. :)

---

### Post by faktorqm on 2008-11-04
Che y si instalas el libre no es mejor? Va, se me ocurre como alternativa por que en realidad no se que hacer con el privativo, pero dicen que el libre anda bien. Alguno que tenga ati por favor que heche luz sobre el asunto!
ahh y una aclaracion, si antes veias todo bien entonces seguro no tenias las cosas igual que ahora, antes tenias aceleracion y ahora no. Salu2!

---

### Post by Zeq on 2008-11-04
No tengo ningun probolema en usar el driver libre, el tema es que no se como instalarlo o donde conseguirlo y como activarlo para tener aceleracion 3D.

Si alguien sabe algo de esto y me quiere dar una mano, yo agradecido de antemano :)

---

### Post by faktorqm on 2008-11-04
Mira tenes este pero la verdad no me acuerdo si es el libre o no:

```
faktorqm@the-edge:~$ aptitude search fglrx
p   fglrx-amdcccle                                                                             - Dummy package for easy transition                                                                   
p   fglrx-amdcccle-envy                                                                        - Dummy package for easy transition                                                                   
p   fglrx-control                                                                              - Control panel for the ATI graphics accelerators                                                     
p   fglrx-control-envy                                                                         - Control panel for the ATI graphics accelerators                                                     
v   fglrx-driver                                                                               -                                                                                                     
v   fglrx-driver-dev                                                                           -                                                                                                     
p   fglrx-kernel-source                                                                        - ATI binary kernel module source                                                                     
p   fglrx-kernel-source-envy                                                                   - ATI binary kernel module source                                                                     
p   xorg-driver-fglrx                                                                          - Video driver for ATI graphics accelerators                                                          
p   xorg-driver-fglrx-dev                                                                      - Video driver for ATI graphics accelerators (devel files)                                            
p   xorg-driver-fglrx-dev-envy                                                                 - Video driver for ATI graphics accelerators (devel files)                                            
p   xorg-driver-fglrx-envy                                                                     - Video driver for ATI graphics accelerators                                                          
faktorqm@the-edge:~$ 
```

Alguien con ATI por favor? Salu2!!

---

### Post by Hei Ku on 2008-11-04
El fglrx es el propietario.

Aca estan las instrucciones y demas info para el driver libre.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Nikolopulus on 2009-03-23
¿nadie puede confirmar que anda bien ATI con el controlador libre?

---

### Post by Hei Ku on 2009-03-23
Depende de la placa que tengas, con el driver libre tenes hasta aceleracion 3D. Pero varia mucho segun el modelo.

Aca tenes una pagina con la explicacion de como instalarlo en Ubuntu y qué placas soporta, y hasta qué punto las soporta.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by GGsalas on 2009-03-24
Hola, yo tengo una laptop compaq presario 2500. Entiendo que la placa de video es ATI. Y el driver lo instaló ubuntu y funciona muy bien todo. 

Veo bien videos y Blender funciona muy bien. Los videos de youtube se ven medio mal en pantalla completa, pero entiendo que eso es por flash. Tengo activados los efectos de escritorios y la memoria compartida la puse en 32Mb.

Si me indican cómo, les doy la información que necesiten (no se como averiguar datos concretos de mi hardware o del driver)

Saludos.

---

### Post by Nikolopulus on 2009-03-29
Terminé por instalar el privativo que bajó automaticamente Ubuntu porque no tenía ganas de hacer el camino largo, por ahora anda 9 pts, el único problma que estoy teniendo es cuando recibo un mensaje nuevo en el amsn, la pantalla se pone negra por un segundo.

---

