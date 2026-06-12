---
title: "Ayuda con Wireless, señal muy baja"
date: 2009-03-14
forum: Hardware
---

### Post by guillermon on 2009-03-14
Hola... el tema de acceder ahora a internet inalámbrica a sido todo un tema (problema)... no hubo foro que no lea ni deje de intentar, de que me reconozca en  mi Ubuntu HH, la nueva placa. Desde mi sentido común, probé 8.10, y tanto en 64 como en 32 reconocía de toque. Lo de la señal baja me dije "lo veo más adelante". He probado cambiando el rate a 11M, y nada cambia. Va una aclaración importante: en Win$, la señal es altísima; en Ubuntu, es muy baja (va entre 5% y 15%) pero lo peor es que oscila mucho y se desconecta. He intentado de todos modos instalar los drivers originales, y nada... 
     ¿estaré haciendo algo mal? o se podrá hacer otra cosa?
Tengo instalado 64 bits. El modelo de la placa es: Wireless-G PCI Adapter, marca Encore, modelo ENLWI- G2.
      Desde ya gracias. Saludos

Guillermo

---

### Post by Hei Ku on 2009-03-14
Podes poner el resultado de: lspci

Asi sabemos bien qué chipset usa tu placa.

Que programa usas para conectarte? Network Manager?

---

### Post by guillermon on 2009-03-14
> **Hei Ku said:**
> Podes poner el resultado de: lspci

Asi sabemos bien qué chipset usa tu placa.

Que programa usas para conectarte? Network Manager?
Hola Hei Ku, aquí posteo lspci:

guille@guille-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

         Por otra parte, en Información del programa que me conecta dice: Miniaplicación NetworkManager 0.7.0
         Espero sirva la info. Espero las respuestas. Desde ya gracias...
Guillermo

---

### Post by sergiom99 on 2009-03-15
Este es tu chipset:
> 01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd.** RTL-8185** IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
 

Buscando en los foros aparece mucha info, tal vez alguno te sirva:
[http://ubuntuforums.org/search.php?searchid=56770152](http://ubuntuforums.org/search.php?searchid=56770152)

Suerte!

---

### Post by guillermon on 2009-03-22
> **sergiom99 said:**
> Este es tu chipset:


Buscando en los foros aparece mucha info, tal vez alguno te sirva:
[http://ubuntuforums.org/search.php?searchid=56770152](http://ubuntuforums.org/search.php?searchid=56770152)

Suerte!

    Hola Sergio, he intentado varias veces ver en lo que me sugieres, y la verdad es que no he encontrado nada que me sirva (que solucione mi problema en realidad). El link que pusiste da error, me parece... Alguna otra idea?
    Más arriba me preguntaba qué software usaba para conectarme, hay otros? yo uso el que viene por defecto... Espero ideas, desde ya mil gracias!

---

### Post by sergiom99 on 2009-03-22
Hola Guillermo, el link ([http://ubuntuforums.org/search.php?searchid=57033821](http://ubuntuforums.org/search.php?searchid=57033821)) es el resultado de la busqueda en el foro usando los terminos "RTL-81852" que es el chipset de tu placa. Tira como 190 threads, asi que algo debe haber.

---

### Post by guillermon on 2009-03-25
> **sergiom99 said:**
> Hola Guillermo, el link ([http://ubuntuforums.org/search.php?searchid=57033821](http://ubuntuforums.org/search.php?searchid=57033821)) es el resultado de la busqueda en el foro usando los terminos "RTL-81852" que es el chipset de tu placa. Tira como 190 threads, asi que algo debe haber.

   Sergio, no sé porqué pero el link que pones a mi me lleva a un mensaje de error. En búsqueda el término RTL-81852, (logueado) no me arroja otro tema que el mío. En búsqueda avanzada, modificando los ítems (que no busque solo en mis temas) no lo he logrado.Sí he accedido a otros temas buscando directamente: "RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller". Por lo pronto no he leido algo que solucione mi problema, pues a muchos no le funcionaba, y luego logran que sí. En mi caso, con I.I. funciona, lo he probado en 32 y 64 bits (instalé éste último). No he conseguido (quizás por error) con tutoriales de ndiswrapper (tengo los drivers originales). Actualmente estoy usando la placa en cuestión, mi problema es que su señal es baja, se corta, y la velocidad es muy lenta. Reinicio en Win$ y corre rápido. ¿es un problema de Software, de Hardware, de Drivers? (seré yo el problema? Tedrá solución?) No sé qué responderme. No se casi nada de pcs, y de Software Libre solo sé sobre su proyecto y filosofía, el cual defiendo a capa y espada. Espero me comprendas. Un saludo.

---

### Post by guillermolisi on 2009-03-27
> **guillermon said:**
> Sergio, no sé porqué pero el link que pones a mi me lleva a un mensaje de error. En búsqueda el término RTL-81852, (logueado) no me arroja otro tema que el mío. En búsqueda avanzada, modificando los ítems (que no busque solo en mis temas) no lo he logrado.Sí he accedido a otros temas buscando directamente: "RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller". Por lo pronto no he leido algo que solucione mi problema, pues a muchos no le funcionaba, y luego logran que sí. En mi caso, con I.I. funciona, lo he probado en 32 y 64 bits (instalé éste último). No he conseguido (quizás por error) con tutoriales de ndiswrapper (tengo los drivers originales). Actualmente estoy usando la placa en cuestión, mi problema es que su señal es baja, se corta, y la velocidad es muy lenta. Reinicio en Win$ y corre rápido. ¿es un problema de Software, de Hardware, de Drivers? (seré yo el problema? Tedrá solución?) No sé qué responderme. No se casi nada de pcs, y de Software Libre solo sé sobre su proyecto y filosofía, el cual defiendo a capa y espada. Espero me comprendas. Un saludo.
No lei todo el thread asi que si lo que voy a preguntar ya se hablo, mis disculpas.

La asignacion de IP a la placa WiFi es dinamica ?
Si es asi, ponele una IP fija y mira si mejoro un poco la señal.

---

