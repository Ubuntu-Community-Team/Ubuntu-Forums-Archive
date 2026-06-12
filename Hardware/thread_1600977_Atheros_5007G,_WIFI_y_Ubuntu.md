---
title: "Atheros 5007G, WIFI y Ubuntu"
date: 2010-10-19
forum: Hardware
---

### Post by chulelinux on 2010-10-19
Dado que nunca pude hacer andar el chip realtek 8185 en ubuntu (con Güin no tenía problemas) me dispuse a comprar otra placa wifi que sea compatible y barata así que fui por la tp-link con chip atheros 5007G. La idea es usarla para una red ad hoc que comparta internet (speedy) con una notebook que usa fundamentalmente XP y tiene un atheros 5007EG que anda de maravillas (en Güin y en linux también no tiene problemas). 
La tp-link no tuvo problemas y fue reconocida de una por ubuntu 10.10. Las máquinas se conectaban y mi alegría ya imaginaba la erradicación definitiva del Güin del pc de escritorio. Pero al rato, di cuenta de que la red era absolutamente inestable. Las máquinas la mayor parte están a dos metros de distancia y el tema es que a cada rato se corta la conexión. Además los doc o carpetas compartidas el ubuntu me las reconoce cuando puede o quiere y etcs. 
Alguien sabe o me puede ayudar a optimizar o solucionar esto?
Saludos

---

### Post by hectorivand on 2010-10-20
> **chulelinux said:**
> Dado que nunca pude hacer andar el chip realtek 8185 en ubuntu (con Güin no tenía problemas) me dispuse a comprar otra placa wifi que sea compatible y barata así que fui por la tp-link con chip atheros 5007G. La idea es usarla para una red ad hoc que comparta internet (speedy) con una notebook que usa fundamentalmente XP y tiene un atheros 5007EG que anda de maravillas (en Güin y en linux también no tiene problemas). 
La tp-link no tuvo problemas y fue reconocida de una por ubuntu 10.10. Las máquinas se conectaban y mi alegría ya imaginaba la erradicación definitiva del Güin del pc de escritorio. Pero al rato, di cuenta de que la red era absolutamente inestable. Las máquinas la mayor parte están a dos metros de distancia y el tema es que a cada rato se corta la conexión. Además los doc o carpetas compartidas el ubuntu me las reconoce cuando puede o quiere y etcs. 
Alguien sabe o me puede ayudar a optimizar o solucionar esto?
Saludos

No tenes suerte querido...

¿Contame sobre tu topología de red? en Windows también se genera eso de que no podes acceder a los otros equipos? como te conectas, mediante un router que hace de nodo o modo ad-hoc?

Saludos
Nacho

---

### Post by chulelinux on 2010-10-20
Entre speedy y mi red ad hoc no voy a ningún lado.... 
PC de escritorio con ubuntu y conectada por cable a speedy que comparte internet a una notebook con xp por red ad hoc wireless. Conectar se conecta y comparte internet pero se corta a cada rato... El tema es que si lo hago de güin escritorio a güin notebook anda sin problemas y también lo hacía con la otra placa, por eso desestimé que sea una cuestión de interferencia o de la notebook.
Todo está configurado bien, con ips fijas, y de hecho se conectan y logro compartir internet pero se corta de nada y vuelve a reconectar. La gestión del wifi lo hago con network-manager y ya probé hacerlo sin el mismo y es lo mismo. Con wicd no puedo porque se me desconecta el cable cuando conecto el wifi. iwconfig me tira esto y wlan anda con ath5k. ¿Otra vez la pifié con la placa o hay algún parámetro que alguien sepa pueda mejorar? Gracias.

wlan1     IEEE 802.11bg  ESSID:"estamos"  
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: F6:85:E1:18:94:CF   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by hectorivand on 2010-10-20
> **chulelinux said:**
> Entre speedy y mi red ad hoc no voy a ningún lado.... 
PC de escritorio con ubuntu y conectada por cable a speedy que comparte internet a una notebook con xp por red ad hoc wireless. Conectar se conecta y comparte internet pero se corta a cada rato... El tema es que si lo hago de güin escritorio a güin notebook anda sin problemas y también lo hacía con la otra placa, por eso desestimé que sea una cuestión de interferencia o de la notebook.
Todo está configurado bien, con ips fijas, y de hecho se conectan y logro compartir internet pero se corta de nada y vuelve a reconectar. La gestión del wifi lo hago con network-manager y ya probé hacerlo sin el mismo y es lo mismo. Con wicd no puedo porque se me desconecta el cable cuando conecto el wifi. iwconfig me tira esto y wlan anda con ath5k. ¿Otra vez la pifié con la placa o hay algún parámetro que alguien sepa pueda mejorar? Gracias.

wlan1     IEEE 802.11bg  ESSID:"estamos"  
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: F6:85:E1:18:94:CF   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Más que comando, primero quiero ver donde esta el problema. tira el resultado del siguiente comando.

```
iwlist scan
```

Saludos

---

### Post by hectorivand on 2010-10-20
Otra cosa...

No te dio la opción de instalar drivers privativos?

---

### Post by chulelinux on 2010-10-21
No, no me ofreció instalar privativos... Ahora hice algo que no había hecho y es correr la notebook con ubuntu también y la conexión se mantiene sin mayores sobresaltos aunque es un poco lenta pero me abre otra perspectiva. El tema es que esa se usa en xpp. El comando que me señalas arroja esto. Saludos. 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 92:32:E0:18:94:AF
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Nosotros"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000004e7f526c
                    Extra: Last beacon: 388ms ago
                    IE: Unknown: 00084E6F736F74726F73
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD070050F202000100
          Cell 02 - Address: 94:0C:6D:E9:75:B0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Hendrix"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002475e62181
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000748656E64726978
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000940C6DE975B0960C6DE975B064002C010808

---

### Post by hectorivand on 2010-10-21
> **chulelinux said:**
> No, no me ofreció instalar privativos... Ahora hice algo que no había hecho y es correr la notebook con ubuntu también y la conexión se mantiene sin mayores sobresaltos aunque es un poco lenta pero me abre otra perspectiva. El tema es que esa se usa en xpp. El comando que me señalas arroja esto. Saludos. 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 92:32:E0:18:94:AF
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Nosotros"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000004e7f526c
                    Extra: Last beacon: 388ms ago
                    IE: Unknown: 00084E6F736F74726F73
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD070050F202000100
          Cell 02 - Address: 94:0C:6D:E9:75:B0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Hendrix"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002475e62181
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000748656E64726978
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000940C6DE975B0960C6DE975B064002C010808

Estaba pensando que tal vez el nivel de señal era bajo y el de perdida mayor.

Tenés teléfonos inalámbricos? proba con cambiar el canal de trabajo. por ahí hay algo que te esta haciendo interferencia.

De todos modos voy a ver si encuentro algo con respecto a esa atheros.

Saludos
Nacho

---

### Post by chulelinux on 2010-10-22
Nacho, conectáste dos neuronas que se negaban... Lo del teléfono lo había desestimado (ni siquiera pensado) porque en su momento sí lo tuve que hacer y lo cambié justamente porque el anterior me hacía ruido en la placa con realtek... 
Ayer probé desconectarlo, igual creyendo que ni ahí, y deja vù... La señal como tiró con el comando es baja pero no se corta... No se corta... no se corta!.. 
La mala suerte que decías en un post anterior no fue con la placa sino con el teléfono ja ja. Voy a tratar de cambiar el canal de transmisión a ver si modifica algo aunque no creo pero ya apareció una causa... 
En que archivo modifico el parámetro del canal de transmisión y demases de la conexión? en interfaces no? ¿no?

Si aparece algo que ayude a mejorar la señal buenísimo pero en definitiva el problema del corte era ni más ni menos que el teléfono. También más allá de que ande bien voy a cambiar el driver de la notebook del xp a ver si ayuda también.

Gracias porque la paciencia ya estaba al límite entre esto y un par de cosas que tengo que seguir configurando y me daba bronca porque había buscado algo soportable en modo nativo por ubuntu.

Saludos

---

### Post by hectorivand on 2010-10-22
> **chulelinux said:**
> Nacho, conectáste dos neuronas que se negaban... Lo del teléfono lo había desestimado (ni siquiera pensado) porque en su momento sí lo tuve que hacer y lo cambié justamente porque el anterior me hacía ruido en la placa con realtek... 
Ayer probé desconectarlo, igual creyendo que ni ahí, y deja vù... La señal como tiró con el comando es baja pero no se corta... No se corta... no se corta!.. 
La mala suerte que decías en un post anterior no fue con la placa sino con el teléfono ja ja. Voy a tratar de cambiar el canal de transmisión a ver si modifica algo aunque no creo pero ya apareció una causa... 
En que archivo modifico el parámetro del canal de transmisión y demases de la conexión? en interfaces no? ¿no?

Si aparece algo que ayude a mejorar la señal buenísimo pero en definitiva el problema del corte era ni más ni menos que el teléfono. También más allá de que ande bien voy a cambiar el driver de la notebook del xp a ver si ayuda también.

Gracias porque la paciencia ya estaba al límite entre esto y un par de cosas que tengo que seguir configurando y me daba bronca porque había buscado algo soportable en modo nativo por ubuntu.

Saludos

Excelente, me alegra que ya estés a un paso de solucionarlo. 

El canal lo cambias desde los settings de la conexión adhoc de tu linux y en Windows desde propiedades de la placa wifi en administrador de dispositivos.

Cuando los cambies, cuentame si la falla sigue estando o si el caso se solucionó completamente. 

Saludos
Nacho

---

### Post by chulelinux on 2010-10-26
Le dí un poco de tiempo así veía bien si andaba. Ahora bien, al final el principal problema era el teléfono. Con la otra placa (realtek) y en el otro Sistema no tenía problemas, pero con esta hace ruido. Así que llevando el teléfono a la otra punta se me mejoró la cuestión. Asimismo cambié el driver de la notebook con xp poniendo (después de probar varios) el anteúltimo de atheros que fue el mejor que me andaba. 
Igualmente hay una flucturación de potencia pero que no llega a ser tal como para cortarse la señal que me interesa de la red ad hoc, que solo falla cuando acerco la notebook al teléfono (inalámbrico)un ratito.
Gracias Nacho por la ayuda, y antes de ponerle el solved te quería preguntar ¿dónde está el archivo para cambiar el canal de transmisión? Gráficamente no está la opción pero por terminal no sé donde se ubica el archivo. Creía que era este /etc/NetworkManager/system-connections/conexiónXprueba (pero no está la opción aquí)
Saludos

---

### Post by hectorivand on 2010-10-26
> **chulelinux said:**
> Le dí un poco de tiempo así veía bien si andaba. Ahora bien, al final el principal problema era el teléfono. Con la otra placa (realtek) y en el otro Sistema no tenía problemas, pero con esta hace ruido. Así que llevando el teléfono a la otra punta se me mejoró la cuestión. Asimismo cambié el driver de la notebook con xp poniendo (después de probar varios) el anteúltimo de atheros que fue el mejor que me andaba. 
Igualmente hay una flucturación de potencia pero que no llega a ser tal como para cortarse la señal que me interesa de la red ad hoc, que solo falla cuando acerco la notebook al teléfono (inalámbrico)un ratito.
Gracias Nacho por la ayuda, y antes de ponerle el solved te quería preguntar ¿dónde está el archivo para cambiar el canal de transmisión? Gráficamente no está la opción pero por terminal no sé donde se ubica el archivo. Creía que era este /etc/NetworkManager/system-connections/conexiónXprueba (pero no está la opción aquí)
Saludos

El archivo, no tengo idea, capaz alguien con más expertise te lo puede responder.

En la opción gráfica si esta. Te digo porque lo veo :D edita la conexión, seleccionas la pestaña inalámbrica, luego seleccionas la conexión, (el nombre) pones editar y desde ahí cambias el canal.

Lookea este Screenshot que te adjunto.

---

### Post by chulelinux on 2010-10-26
Totalmente... el tema es que no me da la opción de modificar el canal.  /home/cristian/Escritorio/sinopción.png 
Debe ser que la placa quizás no lo permita o algo porque no tengo habilitado el menú y en el archivo que te señalé antes tampoco está la línea channel. Igual por lo que leí en ad hoc es conveniente usar canales altos y predeterminadamente anda en canal 10 según tira el comando iwlist scan... 
Igual con el teléfono lejos anda bastante bien je je y se logró que la red sea estable con las placas más baratas del mercado. Armar una red ad hoc y compartir internet al final era posible, solo que el chip realtek 8185 a mi no me anduvo ni para atrás y si por suerte el atheros.
Gracias Nacho
pd: si aparece la forma de cambiar el canal buenísimo para saber como hacerlo pero el problema ya estaría solucionado antes de lo que imaginaba.

---

### Post by hectorivand on 2010-10-26
> **chulelinux said:**
> Totalmente... el tema es que no me da la opción de modificar el canal.  /home/cristian/Escritorio/sinopción.png 
Debe ser que la placa quizás no lo permita o algo porque no tengo habilitado el menú y en el archivo que te señalé antes tampoco está la línea channel. Igual por lo que leí en ad hoc es conveniente usar canales altos y predeterminadamente anda en canal 10 según tira el comando iwlist scan... 
Igual con el teléfono lejos anda bastante bien je je y se logró que la red sea estable con las placas más baratas del mercado. Armar una red ad hoc y compartir internet al final era posible, solo que el chip realtek 8185 a mi no me anduvo ni para atrás y si por suerte el atheros.
Gracias Nacho
pd: si aparece la forma de cambiar el canal buenísimo para saber como hacerlo pero el problema ya estaría solucionado antes de lo que imaginaba.

Que cosa rara esa... :S por ahí alguien con más expertise nos puede ayudar.

Saludos
Nacho

---

### Post by biale on 2010-10-26
Probaría hacerlo por consola con el comando (sudo) iwconfig...

---

### Post by chulelinux on 2010-10-29
Ok probaremos y gracias...

---

