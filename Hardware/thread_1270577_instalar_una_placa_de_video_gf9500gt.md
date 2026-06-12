---
title: "instalar una placa de video gf9500gt"
date: 2009-09-19
forum: Hardware
---

### Post by janomdq on 2009-09-19
Buenas, es la primera vez que uso alguna distribucion de linux, depsues de estar toda la tarde tratando de instalar mi placa de video una gf9500gt de 1gdrr2. estoy a punto de desistir. Si alguien me podria ayudar se lo agradeceria. busque por todos lados, pero no puedo encontrar solucion. bueno si alguien me puede ayudar gracias, pero sino tendre q volver a xp =/

---

### Post by guillermolisi on 2009-09-19
Edite tu mensaje porque es parte de las normas vigentes y aceptadas por cualquiera que participe manejarse con una escritura que sea entendible por la mayor cantidad de gente posible.
El foro no es una lista local de e-mail, es internacional y escribiendo adecuadamente mejoras tu posibilidades que alguien entienda tu situacion y te ayude.

Ademas, un asunto que diga "ayuda" no habla del problema, asi que tambien lo modifique para que sea mas representativo.


En la seccion Normal Threads de la pagina principal de el sub foro del Team de Argentina encontraras cantidad de sticky threads con informacion sumamente util para saber como manejarte y aprovechar el foro.

Luego, que version de Ubuntu estas usando ?


Movido a hardware porque una placa de red se puede patear.

---

### Post by josecuervo86 on 2009-09-19
No se que habrás instentado hacer (no lo especificas), pero lo primero que hay que hacer en tu caso es ir a **Sistema > Administración > Controladores de Hardware**. Si tu placa es compatible, entonces te recomendara una serie de drivers. Paso siguiente **elegis uno** y apretas **Activar**. Luego de reiniciar, tu placa debería estar funcionando con los drivers activados

---

### Post by janomdq on 2009-09-20
tengo el ubuntu 8.4 deskx64, trate de instalar antes el 9.04 pero me salia error e/s y bueno termiine probando el 8.4.
ahora bien el problema q tengo es q en controles de harware no aparece nada, baje los drivers de nvidia, googleando encontre como cerrar el modo grafico, entrar con cuenta root e instalar los, pero al momento de la instalacion me sale un error con server x o algo similar.
por las dudas tengo un phemon x3 8650, en una M52Ls3p, con la Gf9500gt 1gb ddr2.

---

### Post by pablo.s on 2009-09-20
¿Qué sucede si instalas

```
sudo apt-get install envyng-core envyng-gtk
```

en tu sistema?

---

### Post by janomdq on 2009-09-20
> **pablo.s said:**
> ¿Qué sucede si instalas
 
```
sudo apt-get install envyng-core envyng-gtk
```
 
en tu sistema?
 probe tambien pero no me recnoce la placa

---

### Post by josecuervo86 on 2009-09-20
A ver, en una terminal escribi:

```
lspci
```
y mostranos el resutltado (pegalo)

---

### Post by janomdq on 2009-09-20
> **josecuervo86 said:**
> Haber, en una terminal escribi:

```
lspci
```y mostranos el resutltado (pegalo)
  
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0640 (rev a1)

---

### Post by josecuervo86 on 2009-09-20
> ```
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0640 (rev a1)
```

La placa no esta reconocida, y me temo que es debido a que usas 8.04. Probaria haciendo un upgrade a 8.10, lo cual podes hacer mediante el Gestor de Actualizaciones (Sistema > Administración > Gestor de Actualizaciones).

---

### Post by janomdq on 2009-09-20
> **josecuervo86 said:**
> La placa no esta reconocida, y me temo que es debido a que usas 8.04. Probaria haciendo un upgrade a 8.10, lo cual podes hacer mediante el Gestor de Actualizaciones (Sistema > Administración > Gestor de Actualizaciones).

lo probe y cuando pongo actualizar chan! sale esto

Imposible obtener cdrom:[Ubuntu 8.04.3 _Hardy Heron_ - Release amd64 (20090713.1)]/dists/hardy/main/binary-amd64/Packages.gz  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs
Imposible obtener cdrom:[Ubuntu 8.04.3 _Hardy Heron_ - Release amd64 (20090713.1)]/dists/hardy/restricted/binary-amd64/Packages.gz  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

y tengo tambien en un dvd el 9.4 pero ese no lo puedo instalar, cuando boteoo del dvd y pongo para instalar me dice "error E/s" y me pide reiniciar

---

### Post by josecuervo86 on 2009-09-20
Ok, antes que sigamos, anda a **Sistema > Administración > Origenes del Software** y fijate si no tenes marcado que actualice desde el **Cd-Rom**. Si esta marcado, **desmarcalo**. Despues anda a la sección donde dice **"Descargar desde"** y apreta donde dice "Otro" (apreta sobre la solapa). Se te va a abrir una nueva ventana. Apretá donde dice **"Seleccionar el mejor servidor"**, va a empezar a buscar y seguramente te recomendara los brasileros. Acepta. Luego volve al **gestor de actualizaciones** y proba si anda.

---

### Post by pablo.s on 2009-09-20
Aunque también se puede
configurar que actualice a
9.04 teniendo el DVD (o no?)

---

### Post by josecuervo86 on 2009-09-20
Mmmm, creo que si, pero la verdad no estoy seguro. Si alguien sabe, que aporte :D

---

### Post by pablo.s on 2009-09-20
Teoricamente si configura
los repositorios del DVD
como main - universe le
hace una actualización a
9.04. Podría probar luego
hacer un dist-upgrade...
Todo teoria, aclaro.

Y sino también sin hacer
la actualización pero bajando
con envy los drivers 180
tiene que funcionar?

---

### Post by josecuervo86 on 2009-09-20
Yo intente actualizar una vez poniendo como repo el cd, y no funciono. Luego me entere que eso se puede hacer con el alternate, no asi con el cd comun. Aclaro que esto ultimo lo leí por ahi y no se si es 100% asi.

---

### Post by pablo.s on 2009-09-20
Aha, es cierto, porque el
Live tiene el paqueterio de
forma comprimida con Squash,
peeero el Alternate (el cual le
recomiendo a todos los muchachos 
y muchachas) trae los pools con
los paquetes en .deb y sirve
para alguna actualización.
El DVD creo que trae los dos, el
Live y el Alternate.

---

### Post by josecuervo86 on 2009-09-20
Ahh, ahi cambia la cosa. Bueno, esa sería otra opción entonces. Esperemos a ver si se le soluciona al menos el problema de la actualización y despues vemos lo del DVD

---

