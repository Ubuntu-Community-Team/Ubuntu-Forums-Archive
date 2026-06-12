---
title: "Instalacion Ubuntu y Error GRUB y Pantalla Violeta"
date: 2020-06-26
forum: Hardware
---

### Post by ivan-damianoff on 2020-06-26
Hola como estan ? . Les comento soy nuevo en la comunidad , y nuevo en el uso de linux. En varias computadoras viejas pude instalar ubuntu sin problemas.
Me pasa que quiero experimentar la experiencia en forma diaria instalandolo en mi pc de escritorio ( tengo un rizen 5 y una GTX 1050 TI 4 GB) , el problema nace que cuando lo instalo y saco el usb de instalacion y reinicia me sale un error "minimal bash -Like editing ....." , cuando lo reinstalo nuevamente se me queda la pantalla violeta , solo me muestra el mouse. Es como que no iniciara .

Lei que lo de la pantalla violeta es que no reconoce los drivers para levantar mi placa de video o algo asi. 

La verdad me gustaria instalar ubuntu... pero estuve horas tratando de instalarlo y no pude , hasta Edite cosas que decian en ingles... y me rendi. Volvi a windows. 

Espero que me puedan ayudar.

Disculpen las molestias. 

Atte,

---

### Post by CelticWarrior on 2020-06-26
> tengo un rizen 5 y una GTX 1050 TI 4 GB

Bienvenido.

Es un hardware muy moderno y por eso requiere una instalación en modo UEFI y en unidades (drives) GPT. Además por la gráfica Nvidia también necesita controladores propietarios para funcionar correctamente. Pero lo primero es garantizar que el sistema inicializa correctamente. Si se trata de un dual-boot con Windows también hay que deshabilitar la funcionalidad de Fast Startup en Windows.

---

### Post by ivan-damianoff on 2020-06-26
No tengo mucha idea de lo que me estas comentando , Pero hay algun tutorial o algun lugar donde pueda hacer paso por paso esto para que pueda instalarlo ?

---

### Post by CelticWarrior on 2020-06-26
Instalar SOs, Ubuntu o Linux, implica (debería implicar) un conocimiento básico del hardware. Actualizaciones de firmware de la placa-base, BIOS/UEFI, esta en ese apartado.

En primero hay que descargar la actualización - UEFI ("BIOS") desde la página web de la marca y seguir sus instrucciones para lograrlo. Igual para la actualización de firmware del o de los SSDs aunque esta no es habitualmente tan necesaria cuanto la de UEFI("BIOS") pero si ayuda. Si, ya te imagino comentado que te va bien en Windows pero eso no es el tema. El tema es que quieres instalar Ubuntu y para eso mismo computadoras nuevas necesitan de estas actualizaciones si o si para que funcionen correctamente con Linux.

Después viene la instalación en modo UEFI, necesaria para que el hardware funcione bién y también fundamental para que reconozca el Windows en dual-boot (todo Windows 8 o posterior instalado por el fabricante es en modo UEFI por imposición de Microsoft, desde 2012): [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

