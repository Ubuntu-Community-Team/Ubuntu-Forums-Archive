---
title: "Instalar Kubuntu en un Packard Bell EasyNote s18"
date: 2009-09-14
forum: Instalación y Actualización
---

### Post by fisa on 2009-09-14
[I][COLOR=DarkRed]Editado por Carlos C: viene de [http://ubuntuforums.org/showthread.php?t=1248674](http://ubuntuforums.org/showthread.php?t=1248674)[/COLOR]
[/I] 
Buenas. Perdon por meterme en el hilo para preguntar sobre otra cosa, pero es que tengo el mismo modelo de notebook y hace poco intenté sin resultados instalarle Kubuntu. Pero veo que vos pudiste instalarle Ubuntu, así que te agradecería si podés darme una ayuda para hacerlo. 
Si queres abrimos un nuevo thread, o sino por mail para no ensuciar el foro. Te dejo mi mail por PM por cualquier cosa.

Saludos

---

### Post by Carlos C on 2009-09-14
> **fisa said:**
> Buenas. Perdon por meterme en el hilo para preguntar sobre otra cosa, pero es que tengo el mismo modelo de notebook y hace poco intenté sin resultados instalarle Kubuntu. Pero veo que vos pudiste instalarle Ubuntu, así que te agradecería si podés darme una ayuda para hacerlo. 
Si queres abrimos un nuevo thread, o sino por mail para no ensuciar el foro. Te dejo mi mail por PM por cualquier cosa.

Saludos

Hola, para ese tipo de duas tendrías que abrir un thread aparte. Además, te recuerdo que pedir ayuda por PM o mail va contra las normas de ubuntuforums.

Saludos.

---

### Post by fisa on 2009-09-15
> **Carlos C said:**
> Hola, para ese tipo de duas tendrías que abrir un thread aparte. Además, te recuerdo que pedir ayuda por PM o mail va contra las normas de ubuntuforums.

Saludos.

En primer lugar, disculpas.

Como aclaración, no justificación:
El tema era que si abría directamente un thread aparte, lo más probable es que Maciett no lo habría visto. Y no hay practicamente gente que trabaje con ese modelo de notebook, fue una tirada muy extraña para probar el mercado de netbooks. Por eso postee aquí, para que lo vea.
Respecto a PM, no es para pedirle ayuda, sino para pasarle mi correo, por si me quiere contactar para hablar por google talk. Creí que armar un thread para algo tan específico podría molestar.

Perdón.

---

### Post by Carlos C on 2009-09-15
> **fisa said:**
> En primer lugar, disculpas.

Como aclaración, no justificación:
El tema era que si abría directamente un thread aparte, lo más probable es que Maciett no lo habría visto. Y no hay practicamente gente que trabaje con ese modelo de notebook, fue una tirada muy extraña para probar el mercado de netbooks. Por eso postee aquí, para que lo vea.
Respecto a PM, no es para pedirle ayuda, sino para pasarle mi correo, por si me quiere contactar para hablar por google talk. Creí que armar un thread para algo tan específico podría molestar.

Perdón.
Al contrario, cuando tengan dudas específicas con mayor razón deben postearlas, porque significa que quienes estén en la misma situación agradecerán cualquier aporte. Si deseas que alguien mire un post tuyo puedes pegar el enlace a tu thread y así no interrumpes el hilo de la conversación.

Voy a separar tu duda en un thread aparte. Por favor dinos en qué consiste tu problema exactamente cuando tratas de instalar Kubuntu.

Saludos.

---

### Post by fisa on 2009-09-15
Bien, describo la situación y lo que hasta ahora Maciett me comentó:

Equipo: Packard Bell EasyNote S18P
(una de las primeras netbooks que salieron)

Con Kubuntu 9.04:
Antes de formatear e instalar intenté correrlo como Live CD. Inicia, pero no levanta la interfaz gráfica. La pantalla queda completamente en negro.
Pero se que está corriendo, porque puedo pasar a las tty, e incluso puedo apagar la máquina desde la interfaz gráfica con las combinaciones del teclado.

Con Ubuntu 9.04:
Maciett me envió un mail comentándome que le reconoció todos los periféricos excepto el wifi, incluso el video, que se lo tomó como genérico y solo le permite utilizar resolución 800x600.

Resumen: 
Kubuntu (KDE) en Live CD: no reconoce el video
Ubuntu (Gnome) instalado: sí reconoce el video

Así que en este momento no se si el problema está en el entorno gráfico (KDE vs Gnome), en los drivers que trae la distro (Kubuntu vs Ubuntu) o en el hecho de que lo corra como Live CD.

Puse ya a bajar Ubuntu, y mientras tanto voy a sacar toda la info de la máquina para formatearla y probar instalar Kubuntu.

Si la instalación de Kubuntu no anda, probaré después con Ubuntu.
Si Ubuntu termina de bajar antes de que saque todo de la máquina, lo pruebo como Live CD.

Apenas tenga resultados los comento.

---

### Post by fisa on 2009-09-16
Bueno, logré instalar Kubuntu 9.04
Comento los resultados por si a alguien le pasa:

- Live CD: no reconoce la placa de video

- Instalación dentro de Windows: no me dejó, me disparaba un error al intentar comenzar la instalación. El mensaje decía que la cantidad de strings pasados como argumentos no era válida, googleando el mensaje no aparecía en ningún lado.

- Instalación normal (partición aparte, o disco completo): funcionó a la perfección, reconoció todos los dispositivos salvo la placa wifi. Incluso detectó la pantalla táctil.


Así que ahora voy a intentar hacer andar la placa wifi. Si funciona lo posteo acá, y agrego un link en el otro thread que hablaba sobre eso.
(que me corrija alguien si se debe hacer de otra manera)

---

### Post by Carlos C on 2009-09-16
Me alegro que se resolviera. Si deseas preguntar o comentar tu experiencia con el wifi debes abrir un thread nuevo en el subforo "Software", explicando el modelo de tu notebook y la versión de Ubuntu que estás usando.

Saludos.

---

### Post by faPmasteRslaM on 2009-09-16
si , wifi un falo

---

### Post by egosumpaul on 2009-09-29
I installed Kubuntu in a PB Easynote S18, first time it didn't work. Since I collected information from many forums, I tried re-intalling, but in the first screen I choose F4 (as far as I remember) and I can see the screen with the proper resolution and everything is working but... wireless. That d**n wireless card is a pain, I just make it work with a Puppy Linux distro, but I cannot get used to that environment.
I red someone says I have to compile the source code for the driver. I have the source code from that google blog, but when I run make, to get the w35und.o file... I get two erros (error 1, error 2...). I'm a kind of newbie, since I migrated from windows after a traumatic experience from vista. I&#7743; moving all my computers at home and at work to Linux... but this small UMPC is a challenge.

Any suggestions..? How do I compile the drive? Any for-dummies tutorial?

---

### Post by egosumpaul on 2009-09-29
Jeje... escribí en inglés. Disculpas.

En resumen, el bendito driver necesita ser compilado para crear -"make"- un archivo del tipo w35und.o, que se transformará en w35und.ko... tengo el source code que bajé desde el blog de desarrollo de google. He hecho trabajar la wireless en Puppy Linux, pero no me agrada el escritorio que tiene... prefiero algo como Ubuntu.
He leído que la compilación tiene que ver con el kernel y su versión, al hacer "make", sigue el proceso, pero me da dos errores y no crea el archivo ".o" que necesito para instalar el driver.

Se agradecen desde ya las sugerencias... no creo que sea difícil, pero recién estoy aprendiendo a lidiar con estos traspiés de Linux.

---

### Post by moreback on 2009-09-29
Postea los errores que te da la compilación, sin eso no podemos hacer nada.

Saludos.

---

### Post by egosumpaul on 2009-09-29
OK... pero es larguito.


  	 	 	 	 	 	  egosumpaul@MiniMe:~/trunk/linux$ make                                                                     
 make -C /lib/modules/2.6.28-11-generic/build M=/home/egosumpaul/trunk/linux modules                       
 make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.28-11-generic'                              
   CC [M]  /home/egosumpaul/trunk/linux/new_wireless.o                                                     
 En el fichero incluído de /home/egosumpaul/trunk/linux/new_wireless.c:7:                                  
 /home/egosumpaul/trunk/linux/sysdef.h:44:25: error: ../wb35_ver.h: No existe el fichero ó directorio      
 /home/egosumpaul/trunk/linux/sysdef.h:45:31: error: ../mac_structures.h: No existe el fichero ó directorio
 /home/egosumpaul/trunk/linux/sysdef.h:46:24: error: ../ds_tkip.h: No existe el fichero ó directorio        
 /home/egosumpaul/trunk/linux/sysdef.h:47:26: error: ../localpara.h: No existe el fichero ó directorio      
 /home/egosumpaul/trunk/linux/sysdef.h:48:22: error: ../sme_s.h: No existe el fichero ó directorio          
 /home/egosumpaul/trunk/linux/sysdef.h:49:23: error: ../scan_s.h: No existe el fichero ó directorio         
 /home/egosumpaul/trunk/linux/sysdef.h:50:22: error: ../mds_s.h: No existe el fichero ó directorio          
 /home/egosumpaul/trunk/linux/sysdef.h:51:23: error: ../mlme_s.h: No existe el fichero ó directorio         
 /home/egosumpaul/trunk/linux/sysdef.h:52:23: error: ../roam_s.h: No existe el fichero ó directorio         
 /home/egosumpaul/trunk/linux/sysdef.h:53:25: error: ../bssdscpt.h: No existe el fichero ó directorio       
 /home/egosumpaul/trunk/linux/sysdef.h:54:24: error: ../sme_api.h: No existe el fichero ó directorio        
 /home/egosumpaul/trunk/linux/sysdef.h:55:25: error: ../gl_80211.h: No existe el fichero ó directorio       
 /home/egosumpaul/trunk/linux/sysdef.h:56:20: error: ../mto.h: No existe el fichero ó directorio            
 /home/egosumpaul/trunk/linux/sysdef.h:57:26: error: ../wblinux_s.h: No existe el fichero ó directorio      
 /home/egosumpaul/trunk/linux/sysdef.h:58:24: error: ../wbhal_s.h: No existe el fichero ó directorio        
 /home/egosumpaul/trunk/linux/sysdef.h:62:39: error: ../wpa/wb_wpa.h: No existe el fichero ó directorio     
 /home/egosumpaul/trunk/linux/sysdef.h:64:24: error: ../adapter.h: No existe el fichero ó directorio        
 /home/egosumpaul/trunk/linux/sysdef.h:66:25: error: ../mlme_mib.h: No existe el fichero ó directorio       
 /home/egosumpaul/trunk/linux/sysdef.h:67:20: error: ../knl.h: No existe el fichero ó directorio            
 /home/egosumpaul/trunk/linux/sysdef.h:68:22: error: ../sme_f.h: No existe el fichero ó directorio          
 /home/egosumpaul/trunk/linux/sysdef.h:69:23: error: ../mlme_f.h: No existe el fichero ó directorio         
 /home/egosumpaul/trunk/linux/sysdef.h:70:23: error: ../scan_f.h: No existe el fichero ó directorio         
 /home/egosumpaul/trunk/linux/sysdef.h:71:22: error: ../mds_f.h: No existe el fichero ó directorio          
 /home/egosumpaul/trunk/linux/sysdef.h:72:22: error: ../bss_f.h: No existe el fichero ó directorio          
 /home/egosumpaul/trunk/linux/sysdef.h:73:27: error: ../mlmetxrx_f.h: No existe el fichero ó directorio     
 /home/egosumpaul/trunk/linux/sysdef.h:74:23: error: ../roam_f.h: No existe el fichero ó directorio         
 /home/egosumpaul/trunk/linux/sysdef.h:75:22: error: ../mto_f.h: No existe el fichero ó directorio          
 /home/egosumpaul/trunk/linux/sysdef.h:76:24: error: ../wbhal_f.h: No existe el fichero ó directorio        
 /home/egosumpaul/trunk/linux/sysdef.h:77:26: error: ../wblinux_f.h: No existe el fichero ó directorio      
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘FreqToChannelNum’:                             
 /home/egosumpaul/trunk/linux/new_wireless.c:33: error: ‘BAND_TYPE_DSSS’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:33: error: (Cada identificador no declarado solamente se reporta una vez                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:33: error: para cada funcion en la que aparece.)                    
 /home/egosumpaul/trunk/linux/new_wireless.c:34: error: ‘BAND_TYPE_OFDM_24’ no se declaró aquí (primer uso en esta función)                                                                                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:40: error: ‘BAND_TYPE_OFDM_5’ no se declaró aquí (primer uso en esta función)                                                                                                      
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_scan’:                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:62: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                         
 /home/egosumpaul/trunk/linux/new_wireless.c:62: error: expected ‘;’ before ‘Adapter’                            
 /home/egosumpaul/trunk/linux/new_wireless.c:64: error: declaración implícita de la función ‘sme_set_bssid_list_scan’                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:64: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:65: error: ‘psSCAN’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_scan’:                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:82: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                         
 /home/egosumpaul/trunk/linux/new_wireless.c:82: error: expected ‘;’ before ‘Adapter’                            
 /home/egosumpaul/trunk/linux/new_wireless.c:83: error: ‘phw_data_t’ no se declaró aquí (primer uso en esta función)                                                                                                            
 /home/egosumpaul/trunk/linux/new_wireless.c:83: error: expected ‘;’ before ‘pHwData’                            
 /home/egosumpaul/trunk/linux/new_wireless.c:85: error: ‘WB_BSSDESCRIPTION’ no se declaró aquí (primer uso en esta función)                                                                                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:85: error: ‘pscan_bss’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:86: aviso: ISO C90 prohíbe las declaraciones mezcladas y código     
 /home/egosumpaul/trunk/linux/new_wireless.c:92: error: declaración implícita de la función ‘sme_get_scan_bss_count’                                                                                                            
 /home/egosumpaul/trunk/linux/new_wireless.c:92: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:105: error: declaración implícita de la función ‘sme_get_scan_bss’  
 /home/egosumpaul/trunk/linux/new_wireless.c:107: error: declaración implícita de la función ‘Assemble_IE’       
 /home/egosumpaul/trunk/linux/new_wireless.c:126: aviso: se pasa el argumento 1 de ‘iwe_stream_add_event’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:126: aviso: se pasa el argumento 3 de ‘iwe_stream_add_event’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:126: aviso: el paso del argumento 4 de ‘iwe_stream_add_event’ crea un puntero desde un entero sin una conversión                                                                   
 /home/egosumpaul/trunk/linux/new_wireless.c:126: error: faltan argumentos para la función ‘iwe_stream_add_event’                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:139: aviso: se pasa el argumento 1 de ‘iwe_stream_add_point’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:139: aviso: se pasa el argumento 3 de ‘iwe_stream_add_point’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:139: aviso: se pasa el argumento 4 de ‘iwe_stream_add_point’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:139: error: faltan argumentos para la función ‘iwe_stream_add_point’                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:153: aviso: se pasa el argumento 1 de ‘iwe_stream_add_event’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:153: aviso: se pasa el argumento 3 de ‘iwe_stream_add_event’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:153: aviso: el paso del argumento 4 de ‘iwe_stream_add_event’ crea un puntero desde un entero sin una conversión                                                                   
 /home/egosumpaul/trunk/linux/new_wireless.c:153: error: faltan argumentos para la función ‘iwe_stream_add_event’                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:159: error: ‘ESS_NET’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:164: error: ‘IBSS_NET’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:171: aviso: se pasa el argumento 1 de ‘iwe_stream_add_event’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:171: aviso: se pasa el argumento 3 de ‘iwe_stream_add_event’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:171: aviso: el paso del argumento 4 de ‘iwe_stream_add_event’ crea un puntero desde un entero sin una conversión                                                                   
 /home/egosumpaul/trunk/linux/new_wireless.c:171: error: faltan argumentos para la función ‘iwe_stream_add_event’                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:178: error: declaración implícita de la función ‘hal_get_rssi’      
 /home/egosumpaul/trunk/linux/new_wireless.c:178: error: ‘pHwData’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:178: error: ‘MAX_ACC_RSSI_COUNT’ no se declaró aquí (primer uso en esta función)                                                                                                   
 /home/egosumpaul/trunk/linux/new_wireless.c:183: aviso: se pasa el argumento 1 de ‘iwe_stream_add_event’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:183: aviso: se pasa el argumento 3 de ‘iwe_stream_add_event’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:183: aviso: el paso del argumento 4 de ‘iwe_stream_add_event’ crea un puntero desde un entero sin una conversión                                                                   
 /home/egosumpaul/trunk/linux/new_wireless.c:183: error: faltan argumentos para la función ‘iwe_stream_add_event’                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:199: aviso: se pasa el argumento 1 de ‘iwe_stream_add_point’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:199: aviso: se pasa el argumento 3 de ‘iwe_stream_add_point’ desde un tipo de puntero incompatible                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:199: error: faltan argumentos para la función ‘iwe_stream_add_point’                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_freq’:                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:222: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:222: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:224: aviso: ISO C90 prohíbe las declaraciones mezcladas y código    
 /home/egosumpaul/trunk/linux/new_wireless.c:227: error: ‘phw_data_t’ no se declaró aquí (primer uso en esta función)                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:227: error: expected ‘;’ before ‘pHwData’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:228: error: declaración implícita de la función ‘sme_get_connect_status’                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:228: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:231: error: ‘MEDIA_STATE_CONNECTED’ no se declaró aquí (primer uso en esta función)                                                                                                
 /home/egosumpaul/trunk/linux/new_wireless.c:234: error: declaración implícita de la función ‘sme_get_current_channel’                                                                                                          
 /home/egosumpaul/trunk/linux/new_wireless.c:235: error: declaración implícita de la función ‘sme_get_current_band’                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:245: error: ‘pHwData’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_range’:                                    
 /home/egosumpaul/trunk/linux/new_wireless.c:273: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:273: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:274: aviso: ISO C90 prohíbe las declaraciones mezcladas y código    
 /home/egosumpaul/trunk/linux/new_wireless.c:308: error: ‘PowerDbToMw’ no se declaró aquí (primer uso en esta función)                                                                                                          
 /home/egosumpaul/trunk/linux/new_wireless.c:324: error: ‘psLOCAL’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:358: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:360: error: ‘MEDIA_STATE_CONNECTED’ no se declaró aquí (primer uso en esta función)                                                                                                
 /home/egosumpaul/trunk/linux/new_wireless.c:375: error: ‘MODE_802_11_BG_IBSS’ no se declaró aquí (primer uso en esta función)                                                                                                  
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_mode’:                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:413: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:413: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:414: error: declaración implícita de la función ‘sme_get_bss_type’  
 /home/egosumpaul/trunk/linux/new_wireless.c:414: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:417: error: declaración implícita de la función ‘sme_get_desired_bss_type’                                                                                                         
 /home/egosumpaul/trunk/linux/new_wireless.c:423: error: ‘IBSS_NET’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:426: error: ‘ESS_NET’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:429: error: ‘ANYBSS_NET’ no se declaró aquí (primer uso en esta función)                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_mode’:                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:445: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:445: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:446: aviso: ISO C90 prohíbe las declaraciones mezcladas y código    
 /home/egosumpaul/trunk/linux/new_wireless.c:451: error: ‘IBSS_NET’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:454: error: ‘ESS_NET’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:457: error: ‘ANYBSS_NET’ no se declaró aquí (primer uso en esta función)                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:470: error: declaración implícita de la función ‘sme_set_desired_bss_type’                                                                                                         
 /home/egosumpaul/trunk/linux/new_wireless.c:470: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_rate’:                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:479: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:479: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:491: error: ‘psLOCAL’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:491: error: ‘RATE_54M’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:492: error: ‘RATE_48M’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:493: error: ‘RATE_36M’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:494: error: ‘RATE_24M’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:495: error: ‘RATE_18M’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:496: error: ‘RATE_12M’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:497: error: ‘RATE_9M’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:498: error: ‘RATE_6M’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:499: error: ‘RATE_11M’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:500: error: ‘RATE_2M’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:501: error: ‘RATE_1M’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:502: error: ‘RATE_AUTO’ no se declaró aquí (primer uso en esta función)                                                                                                            
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_rate’:                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:530: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:530: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:531: error: ‘psLOCAL’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_rts’:                                      
 /home/egosumpaul/trunk/linux/new_wireless.c:541: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:541: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:543: error: declaración implícita de la función ‘sme_set_rts_threshold’                                                                                                            
 /home/egosumpaul/trunk/linux/new_wireless.c:543: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_rts’:                                      
 /home/egosumpaul/trunk/linux/new_wireless.c:552: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:552: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:553: aviso: ISO C90 prohíbe las declaraciones mezcladas y código    
 /home/egosumpaul/trunk/linux/new_wireless.c:554: error: declaración implícita de la función ‘sme_get_rts_threshold’                                                                                                            
 /home/egosumpaul/trunk/linux/new_wireless.c:554: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_frag’:                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:565: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:565: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:567: error: declaración implícita de la función ‘sme_set_fragment_threshold’                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:567: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_frag’:                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:576: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:576: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:577: aviso: ISO C90 prohíbe las declaraciones mezcladas y código    
 /home/egosumpaul/trunk/linux/new_wireless.c:579: error: declaración implícita de la función ‘sme_get_fragment_threshold’                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:579: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_txpow’:                                    
 /home/egosumpaul/trunk/linux/new_wireless.c:590: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:590: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:592: error: declaración implícita de la función ‘sme_set_tx_power_level’                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:592: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_txpow’:                                    
 /home/egosumpaul/trunk/linux/new_wireless.c:600: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:600: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:601: aviso: ISO C90 prohíbe las declaraciones mezcladas y código    
 /home/egosumpaul/trunk/linux/new_wireless.c:605: error: declaración implícita de la función ‘sme_get_tx_power_level’                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:605: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_essid’:                                    
 /home/egosumpaul/trunk/linux/new_wireless.c:619: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:619: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:642: error: ‘psSME’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c:642: error: ‘ENCRYPT_TKIP’ no se declaró aquí (primer uso en esta función)                                                                                                         
 /home/egosumpaul/trunk/linux/new_wireless.c:647: error: ‘pGlobal_STA_Wpa’ no se declaró aquí (primer uso en esta función)                                                                                                      
 /home/egosumpaul/trunk/linux/new_wireless.c:670: error: declaración implícita de la función ‘CharToBin’         
 /home/egosumpaul/trunk/linux/new_wireless.c:685: error: ‘pSTA’ no se declaró aquí (primer uso en esta función)  
 /home/egosumpaul/trunk/linux/new_wireless.c:691: error: declaración implícita de la función ‘AP_PrePasswordHash’                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:691: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:695: error: declaración implícita de la función ‘sme_set_desired_ssid’                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_essid’:                                    
 /home/egosumpaul/trunk/linux/new_wireless.c:708: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:708: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:710: error: declaración implícita de la función ‘sme_get_desired_ssid’                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:710: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_sens’:                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:722: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:722: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:723: aviso: ISO C90 prohíbe las declaraciones mezcladas y código    
 /home/egosumpaul/trunk/linux/new_wireless.c:725: error: declaración implícita de la función ‘sme_get_rssi’      
 /home/egosumpaul/trunk/linux/new_wireless.c:725: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_encode’:                                   
 /home/egosumpaul/trunk/linux/new_wireless.c:748: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:748: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:760: error: ‘psSME’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c:772: error: ‘WEP_DISABLE’ no se declaró aquí (primer uso en esta función)                                                                                                          
 /home/egosumpaul/trunk/linux/new_wireless.c:780: error: ‘ENCRYPT_WEP’ no se declaró aquí (primer uso en esta función)                                                                                                          
 /home/egosumpaul/trunk/linux/new_wireless.c:787: error: ‘SHARE_AUTH’ no se declaró aquí (primer uso en esta función)                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:792: error: ‘OPEN_AUTH’ no se declaró aquí (primer uso en esta función)                                                                                                            
 /home/egosumpaul/trunk/linux/new_wireless.c:801: error: declaración implícita de la función ‘sme_set_add_wep’   
 /home/egosumpaul/trunk/linux/new_wireless.c:801: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:812: error: declaración implícita de la función ‘sme_set_encryption_status’                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_encode’:                                   
 /home/egosumpaul/trunk/linux/new_wireless.c:821: error: ‘PADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:821: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:822: aviso: ISO C90 prohíbe las declaraciones mezcladas y código    
 /home/egosumpaul/trunk/linux/new_wireless.c:825: error: ‘psSME’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c:825: error: ‘WEP_DISABLE’ no se declaró aquí (primer uso en esta función)                                                                                                          
 /home/egosumpaul/trunk/linux/new_wireless.c:830: error: ‘OPEN_AUTH’ no se declaró aquí (primer uso en esta función)                                                                                                            
 /home/egosumpaul/trunk/linux/new_wireless.c:845: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_encodeext’:                                
 /home/egosumpaul/trunk/linux/new_wireless.c:863: error: ‘NDIS_802_11_KEY’ no se declaró aquí (primer uso en esta función)                                                                                                      
 /home/egosumpaul/trunk/linux/new_wireless.c:863: error: expected ‘;’ before ‘Key’                              
 /home/egosumpaul/trunk/linux/new_wireless.c:864: error: ‘PADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:864: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:865: aviso: ISO C90 prohíbe las declaraciones mezcladas y código    
 /home/egosumpaul/trunk/linux/new_wireless.c:880: error: ‘Key’ no se declaró aquí (primer uso en esta función)   
 /home/egosumpaul/trunk/linux/new_wireless.c:881: error: ‘p’ no se declaró aquí (primer uso en esta función)     
 /home/egosumpaul/trunk/linux/new_wireless.c:899: error: declaración implícita de la función ‘sme_remove_default_key’                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:899: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:908: error: declaración implícita de la función ‘sme_clear_all_mapping_key’                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:916: error: declaración implícita de la función ‘sme_remove_mapping_key’                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:991: error: ‘HAL_KEYTYPE_WEP40’ no se declaró aquí (primer uso en esta función)                                                                                                    
 /home/egosumpaul/trunk/linux/new_wireless.c:997: error: ‘HAL_KEYTYPE_WEP104’ no se declaró aquí (primer uso en esta función)                                                                                                   
 /home/egosumpaul/trunk/linux/new_wireless.c:1003: error: ‘HAL_KEYTYPE_AES_CCMP’ no se declaró aquí (primer uso en esta función)                                                                                                
 /home/egosumpaul/trunk/linux/new_wireless.c:1009: error: ‘HAL_KEYTYPE_TKIP’ no se declaró aquí (primer uso en esta función)                                                                                                    
 /home/egosumpaul/trunk/linux/new_wireless.c:1031: error: declaración implícita de la función ‘sme_add_key’      
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_wap’:                                      
 /home/egosumpaul/trunk/linux/new_wireless.c:1056: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1056: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1057: aviso: ISO C90 prohíbe las declaraciones mezcladas y código   
 /home/egosumpaul/trunk/linux/new_wireless.c:1058: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:1059: error: ‘MEDIA_STATE_CONNECTED’ no se declaró aquí (primer uso en esta función)                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:1064: error: declaración implícita de la función ‘sme_get_bssid’    
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_wap’:                                      
 /home/egosumpaul/trunk/linux/new_wireless.c:1076: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1076: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1078: error: declaración implícita de la función ‘sme_set_desired_bssid’                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:1078: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_region’:                                   
 /home/egosumpaul/trunk/linux/new_wireless.c:1091: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1091: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1093: error: ‘psLOCAL’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_region’:                                   
 /home/egosumpaul/trunk/linux/new_wireless.c:1121: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1121: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1135: error: ‘psLOCAL’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:1155: error: declaración implícita de la función ‘GetSupportChanRange’                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:1155: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:1156: error: declaración implícita de la función ‘GetIbssChan’      
 /home/egosumpaul/trunk/linux/new_wireless.c:1157: error: declaración implícita de la función ‘Scan_SetScanChanRange’                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:1157: error: ‘psSCANREQ’ no se declaró aquí (primer uso en esta función)                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c:1158: error: declaración implícita de la función ‘sme_set_disassociate’                                                                                                            
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_ibss_freq’:                                
 /home/egosumpaul/trunk/linux/new_wireless.c:1166: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1166: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1167: aviso: ISO C90 prohíbe las declaraciones mezcladas y código   
 /home/egosumpaul/trunk/linux/new_wireless.c:1173: error: ‘psSME’ no se declaró aquí (primer uso en esta función)                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_ibss_freq’:                                
 /home/egosumpaul/trunk/linux/new_wireless.c:1187: error: ‘ChanInfo’ no se declaró aquí (primer uso en esta función)                                                                                                            
 /home/egosumpaul/trunk/linux/new_wireless.c:1187: error: expected ‘;’ before ‘chan’                             
 /home/egosumpaul/trunk/linux/new_wireless.c:1188: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1188: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1195: error: ‘chan’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c:1195: error: ‘BAND_TYPE_OFDM_5’ no se declaró aquí (primer uso en esta función)                                                                                                    
 /home/egosumpaul/trunk/linux/new_wireless.c:1197: error: ‘BAND_TYPE_OFDM_24’ no se declaró aquí (primer uso en esta función)                                                                                                   
 /home/egosumpaul/trunk/linux/new_wireless.c:1199: error: declaración implícita de la función ‘sme_set_IBSS_chan’                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:1199: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_ibss_mode’:                                
 /home/egosumpaul/trunk/linux/new_wireless.c:1210: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1210: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1211: aviso: ISO C90 prohíbe las declaraciones mezcladas y código   
 /home/egosumpaul/trunk/linux/new_wireless.c:1214: error: ‘psLOCAL’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:1214: error: ‘MODE_802_11_BG_IBSS’ no se declaró aquí (primer uso en esta función)                                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_ibss_mode’:                                
 /home/egosumpaul/trunk/linux/new_wireless.c:1230: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1230: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1238: error: ‘psLOCAL’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:1238: error: ‘MODE_802_11_BG_IBSS’ no se declaró aquí (primer uso en esta función)                                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c:1244: error: ‘MODE_AUTO’ no se declaró aquí (primer uso en esta función)                                                                                                           
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_scanning’:                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:1252: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1252: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1255: error: ‘psSCAN’ no se declaró aquí (primer uso en esta función)                                                                                                              
 /home/egosumpaul/trunk/linux/new_wireless.c:1256: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_pwd’:                                      
 /home/egosumpaul/trunk/linux/new_wireless.c:1270: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1270: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1273: error: ‘pGlobal_STA_Wpa’ no se declaró aquí (primer uso en esta función)                                                                                                     
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_ie’:                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1288: error: ‘ENCRYPT_DISABLE’ no se declaró aquí (primer uso en esta función)                                                                                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:1289: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1289: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1315: error: ‘psSME’ no se declaró aquí (primer uso en esta función)                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:1315: error: ‘Cipher_Tkip’ no se declaró aquí (primer uso en esta función)                                                                                                         
 /home/egosumpaul/trunk/linux/new_wireless.c:1316: error: ‘ENCRYPT_TKIP’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:1323: error: ‘Cipher_Ccmp’ no se declaró aquí (primer uso en esta función)                                                                                                         
 /home/egosumpaul/trunk/linux/new_wireless.c:1324: error: ‘ENCRYPT_CCMP’ no se declaró aquí (primer uso en esta función)                                                                                                        
 /home/egosumpaul/trunk/linux/new_wireless.c:1335: error: declaración implícita de la función ‘sme_set_auth_mode’                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:1335: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c:1335: error: ‘WPAPSK_AUTH’ no se declaró aquí (primer uso en esta función)                                                                                                         
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_ver’:                                      
 /home/egosumpaul/trunk/linux/new_wireless.c:1344: error: ‘VER_FILEVERSION_STR’ no se declaró aquí (primer uso en esta función)                                                                                                 
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_get_ssid_info’:                                
 /home/egosumpaul/trunk/linux/new_wireless.c:1354: error: ‘PWB32_ADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                       
 /home/egosumpaul/trunk/linux/new_wireless.c:1354: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1356: error: declaración implícita de la función ‘sme_get_ssid’     
 /home/egosumpaul/trunk/linux/new_wireless.c:1356: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)                                                                                                             
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_genie’:                                    
 /home/egosumpaul/trunk/linux/new_wireless.c:1373: error: ‘ENCRYPT_DISABLE’ no se declaró aquí (primer uso en esta función)                                                                                                     
 /home/egosumpaul/trunk/linux/new_wireless.c:1374: error: ‘PADAPTER’ no se declaró aquí (primer uso en esta función)                                                                                                            
 /home/egosumpaul/trunk/linux/new_wireless.c:1374: error: expected ‘;’ before ‘Adapter’                          
 /home/egosumpaul/trunk/linux/new_wireless.c:1402: error: ‘psSME’ no se declaró aquí (primer uso en esta función)                                                                                                               
 /home/egosumpaul/trunk/linux/new_wireless.c:1402: error: ‘Cipher_Tkip’ no se declaró aquí (primer uso en esta función)                                                                                                         
 /home/egosumpaul/trunk/linux/new_wireless.c:1403: error: ‘ENCRYPT_TKIP’ no se declaró aquí (primer uso en estafunción)
 /home/egosumpaul/trunk/linux/new_wireless.c:1405: error: ‘Cipher_Ccmp’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c:1406: error: ‘ENCRYPT_CCMP’ no se declaró aquí (primer uso en estafunción)
 /home/egosumpaul/trunk/linux/new_wireless.c:1430: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c:1430: error: ‘WPAPSK_AUTH’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c:1467: error: ‘WPA2PSK_AUTH’ no se declaró aquí (primer uso en estafunción)
 /home/egosumpaul/trunk/linux/new_wireless.c: En la función ‘test_set_auth’:
 /home/egosumpaul/trunk/linux/new_wireless.c:1485: error: ‘PADAPTER’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c:1485: error: expected ‘;’ before ‘Adapter’
 /home/egosumpaul/trunk/linux/new_wireless.c:1486: aviso: ISO C90 prohíbe las declaraciones mezcladas y código
 /home/egosumpaul/trunk/linux/new_wireless.c:1508: error: ‘Adapter’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c:1508: error: ‘OPEN_AUTH’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c:1510: error: ‘SHARE_AUTH’ no se declaró aquí (primer uso en esta función)
 /home/egosumpaul/trunk/linux/new_wireless.c:1518: error: ‘ENCRYPT_DISABLE’ no se declaró aquí (primer uso en esta función)
 make[2]: *** [/home/egosumpaul/trunk/linux/new_wireless.o] Error 1
 make[1]: *** [_module_/home/egosumpaul/trunk/linux] Error 2
 make[1]: se sale del directorio `/usr/src/linux-headers-2.6.28-11-generic'
 make: *** [all] Error 2
 egosumpaul@MiniMe:~/trunk/linux$ dir

---

### Post by moreback on 2009-09-30
Las primeras línea parecen indicar que hay un error en la ubicación de archivos.

/home/egosumpaul/trunk/linux/sysdef.h:44:25: error: ../wb35_ver.h: No existe el fichero ó directorio      
 /home/egosumpaul/trunk/linux/sysdef.h:45:31: error: ../mac_structures.h: No existe el fichero ó directorio
 /home/egosumpaul/trunk/linux/sysdef.h:46:24: error: ../ds_tkip.h: No existe el fichero ó directorio        
 /home/egosumpaul/trunk/linux/sysdef.h:47:26: error: ../localpara.h: No existe el fichero ó directorio
...

Creo que ese archivo sysdef.h tiene mal escritos los archivos de cabecera (que aparezca "../" me da para pensar eso). Por lo visto depende de otros archivos que están un directorio más arriba. ¿Seguro que no te falta descargar ningún paquete más? ¿Leíste el README o el INSTALL para ver los pasos de la compilación?

Saludos.

---

### Post by egosumpaul on 2009-10-01
Estimado Pablo;
diantres! no resulta... baje el source code de Google. Lo descomprimí tal cual venía. Ingresé a la carpeta "linux" hice make... me dió lo mismo de arriba. Luego procedía a seguir el instructivo del "README.TXT", hice lo siguiente con su resultado y nada:

egosumpaul@MiniMe:~/Documentos/trunk$ cd linux
egosumpaul@MiniMe:~/Documentos/trunk/linux$ cp Makefile.debug Makefile
egosumpaul@MiniMe:~/Documentos/trunk/linux$ make
make -C /lib/modules/`uname -r`/build M=/home/egosumpaul/Documentos/trunk/linux modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/egosumpaul/Documentos/trunk/linux/Makefile". Fix it to use EXTRA_CFLAGS.  Alto.
make[1]: *** [_module_/home/egosumpaul/Documentos/trunk/linux] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2
egosumpaul@MiniMe:~/Documentos/trunk/linux$

No sé que más hacer, en el UMPC funciona todo. De hecho estoy escribiendo desde él conectado a la LAN... pero necesito wireless o deberé volver a windows!!!!

Sugerencias? Leí por ahí que este driver n funciona con kernel 2.6.28.xx, pero quiero ser positivo.

---

### Post by moreback on 2009-10-02
¿Podrías dar el link de descarga? A lo mejor yo puedo intentar compilarlo en mi máquina y ver qué es lo que está pasando.

Saludos.

---

### Post by egosumpaul on 2009-10-02
Hola Pablo,
 bueno, no hay peor ciego que el no quiere ver... en el sitio de Google code para Winbond no había chequeado que existe un fix de un usuario con una fecha de mediados de 2009. Lo bajé, bastó hacer make en el directorio de la carpeta linux, y se generó el archivo w35und.ko necesario.
Ahora el tema es que cada vez que hago "insmod w35und.ko", se carga, KUBUNTU me dice que se cargó wlan0, y cuando la quiero activar... el laptop se cuelga, y... tengo que apagarlo para reiniciar. Además, no queda instalado el driver, es decir cada vez que necesito cargar el driver hay que insmod... ¿Existe alguna instrucción para dejar el driver instalado permanentemente?

Gracias por tu paciencia.

---

### Post by moreback on 2009-10-02
Para que te cargue automáticamente el driver al inicio, creo que tienes que agregar el nombre del módulo (sin el .ko) en el archivo **/etc/modules**.

---

### Post by rapidoherrera on 2009-10-03
compañeros yo tb tengo un s18 y estoy tratando con xubuntu los he leido y todo y no puedo conectar el wireless apesar de no ser un novato.....como quedo el tema????


saludos desde chile!!!\\:D/

---

### Post by egosumpaul on 2009-10-03
> **moreback said:**
> Para que te cargue automáticamente el driver al inicio, creo que tienes que agregar el nombre del módulo (sin el .ko) en el archivo **/etc/modules**.
 
No, no hay caso. Seguí tb. otro tutorial de cómo agregar el driver... pero no carga, y sigue colgándose.
Desgraciadamente tuve que volver a instalar Windows, porque necesito movilidad... pero no pierdo las esperanzas, volveré a intentar con UBNTU 9.10 cuando lo liberen.
 
Gracias otra vez Pablo

---

### Post by egosumpaul on 2009-10-03
> **rapidoherrera said:**
> compañeros yo tb tengo un s18 y estoy tratando con xubuntu los he leido y todo y no puedo conectar el wireless apesar de no ser un novato.....como quedo el tema????
 
 
saludos desde chile!!!\\:D/
 
Y has tratado con el Fix de google code??
Te dejo el link, a mí me solucionó el compilado:
[http://www.ozanuzer.com/winbondport-130509-trunk.tar.gz](http://www.ozanuzer.com/winbondport-130509-trunk.tar.gz)
y tienes que hacer insmod para instalarlo... pero yo no pude aprender a instalarlo permanentemente... y se cuelga. He llegado al punto de conectarse a mi red... y de ahí colgado...
 
Prueba por favor en Xubuntu y nos cuentas.
 
Saludos!!

---

### Post by rapidoherrera on 2009-10-10
sorry recien lei

que tuve un problema con xubuntu y lo deje de ocupar

en su momento ocupe el metodo que me pediste sin resultado, en todos los casos prefiero esperarme a fin de mes para probar con la nueva version 9.10

a todo esto te toma la bateria(a mi en xp me toma todo perfecto en xubuntu  uff puras pifias, lo acabo de formatiar para tener solo xubuntu..voy a volver a probar, saludos

---

### Post by egosumpaul on 2009-10-14
Ya dije que no me iba a dar por vencido fácilmente.
tengo Windows XP y ahora tb. UBUNTU 8.10 de un CD que andaba por ahí... compilé el último fix del driver... y como que agarraba señal... y luego se congelaba. Se me ocurrió utilizar otro net-manager y un foro sugería Wicd Network Manager, instalé y es bastante mejor... cuesta que agarre y es inestable (conecta-desconecta-conecta)... pero después de un tiempo tb. se puede congelar... lo probé unas 10 veces y fué algo así como un 40 por ciento de congelado.
Recuerdo que el kernel de esta versión de UBUNTU es 2.6.27-xx
Cargué la misma IP de la red a la que estaba conectado en las propiedades de la wlan0, con ifconfig wlan0 xxx.xxx.xxx.xxx up, como está descrito en el README.txt del driver, y mejoró bastante la estabilidad...
Alguna otra sugerencia...

---

### Post by Carlos C on 2009-10-15
> **egosumpaul said:**
> Ya dije que no me iba a dar por vencido fácilmente.
tengo Windows XP y ahora tb. UBUNTU 8.10 de un CD que andaba por ahí... compilé el último fix del driver... y como que agarraba señal... y luego se congelaba. Se me ocurrió utilizar otro net-manager y un foro sugería Wicd Network Manager, instalé y es bastante mejor... cuesta que agarre y es inestable (conecta-desconecta-conecta)... pero después de un tiempo tb. se puede congelar... lo probé unas 10 veces y fué algo así como un 40 por ciento de congelado.
Recuerdo que el kernel de esta versión de UBUNTU es 2.6.27-xx
Cargué la misma IP de la red a la que estaba conectado en las propiedades de la wlan0, con ifconfig wlan0 xxx.xxx.xxx.xxx up, como está descrito en el README.txt del driver, y mejoró bastante la estabilidad...
Alguna otra sugerencia...
Trata instalando el último kernel. Puedes encontrar instrucciones para instalar los últimos paquetes compilados para Ubuntu en el wiki:

[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)

Saludos.

---

### Post by egosumpaul on 2009-10-15
OK Carlos,
trataré... aunque no creo que se trate del Kernel, ya que he instalado tres versiones de UBUNTU, y es lo mismo. Fíjate que en Puppy Linux no me pasa... cargo bien el module y cero problema... hmmm, ahora me estoy acordando que el kernel del Puppy es más viejito... puede ser. Pruebo y les cuento.

saludos!

---

### Post by mamas6667 on 2009-11-02
En mi humilde experiencia.

No te cambies de Linux a Microsoft Windows, porque no funciona algun dispositivo.
Cambiate de distribucion de Linux, o de Version dentro de tu Distribucion favorita, hasta encontrar una en la cual todo funcione.

Respecto a tu problema con el dipositivo de red inalambrica.
Prueba usar NDISwrapper , hasta encontrar una soluccion nativa en linux.

Algunas veces los controladores para windows98 funcionan mejor que los de XP

[http://en.wikipedia.org/wiki/NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper)



Windows solo sirve para 4 cosas
1- Agarrarse virus.
2- Jugar.
3- Trabajar en algun programa que no exista en Linux/BSD, ojala sin internet.
4- Apoyar la infinita estupidez.

-------------------------------------------------------------------------------------------------------------------
In my humble experience.  

 Do not change from Linux to Microsoft Windows, because a device which does not work.  
 Switch your Linux distribution, or version of your favorite distribution, until you find one where everything works.  

 As for your problem with the wireless network device.  
 Try using NDISwrapper, untill you find a linux native solution.  

Sometimes Windows98 drivers work better than XP's

 [http://en.wikipedia.org/wiki/NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper)  



 Windows is only good for 4 things  
 1 - getting viruses.  
 2 - Playing.  
 3 - Working in a program that does not exist in Linux / BSD, hopefully without using internet.  
 4 - Support the infinite stupidity.

---

