---
title: "problema con wifi"
date: 2010-06-23
forum: Hardware
---

### Post by santiago.ts13 on 2010-06-23
Buenas, hace dos días instale ubuntu y todavia ando un poco perdido con los pequeños problmas.
El unico que no pude arreglar hasta el momento es el de internet. Cuando usaba windows me conectaba desde mi cuarto de lujo a internet; pero ahora, si bien me reconoce la red wifi, no me deja conectarme a no ser que me ponga al lado del router.
:confused:
¿alguna idea? desde ya muchas gracias

---

### Post by santiago79 on 2010-06-25
instalaste el driver? o  fijate con el programa wifi radar creo que se llama que te las detecta.
por las dudas en la terminal teclea LSPCI y postea lo que te sale

---

### Post by santiago.ts13 on 2010-06-26
ey, muchas gracias por la respuesta! a la red me la detecta pero no se me conecta si no estoy al lado.
puse lo que me dijiste en la consola y esto aparecio:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

pero no entiendo nada XD jajaja. sugerencias?

---

### Post by guillermon on 2010-06-26
> **santiago.ts13 said:**
> si bien me reconoce la red wifi, no me deja conectarme a no ser que me ponga al lado del router.
¿alguna idea? desde ya muchas gracias
Hola santiago, lo que estás sugiriendo que es un tema de potencia? (porque sino sería capricho del sistema de conectarse solo cuando está cerca), entonces, con qué porcentaje recepta cuando no se conecta y cuando sí lo hace? yo me he conectado normalmente con un 15% sin problemas... Quizás puedas cambiar de aplicación de conexión, pero no sé sobre eso. Seguro alguien que sepa más te aconsejará mejor. Por lo pronto observa eso...

---

### Post by santiago.ts13 on 2010-06-26
Claro, o algo así. El problema está en la potencia, lo raro es que siempre tuve la misma potencia, solo que antes podía conectarme; ahora solo puedo cuando estoy al lado del ruter, esto es, cuando llega con máxima potencia la señal. (por eso había puesto el post en "software")
Estuve leyendo otros post con problemas con WiFi (ninguno como el mio) y por lo general recomendaban instalar el driver de windows. ¿creen que podría funcionar? El tema es que tampoco se hacerlo y no se cual driver instalar.

No se si eso les dice algo sobre la potencia

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:58:C3:35:A5
                    Channel:6
                    [COLOR="Red"]Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-25 dBm[/COLOR]  
                    Encryption key:on
                    ESSID:"CASA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s                            11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000014005181
                    Extra: Last beacon: 348ms ago
                    IE: Unknown: 000443415341
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A000110103B00010310470010C04EF6C04CB76EE241AB001E58C335A5104400010210210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D33303010080002008E1041000100

---

