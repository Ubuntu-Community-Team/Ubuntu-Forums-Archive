---
title: "Drivers para mi placa. Via Chrome9"
date: 2009-05-09
forum: Hardware
---

### Post by zoroastro444 on 2009-05-09
Quiero instalar los drivers de mi placa de video para intalar los efectos de escritorio pero creo que no son compatibles con Linux creo, les paso el log de las carasteristicas.

00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
04:04.0 Communication controller: Conexant Systems, Inc. Conexant SoftK56 Data/Fax Modem (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

---

### Post by Hei Ku on 2009-05-09
Probaste de instalarle el driver Openchrome?

Lo otro que te puedo decir es que tenés 2 opciones:
- Transpirar tratando de instalar los drivers para todo eso que tenés de VIA, que puede no funcionar, pero que vas a aprender un montón a lo largo del camino. Básicamente, si tenés paciencia vas a salir sabiendo de Linux a la fuerza.

- Meterte a mercadolibre, comprarte un mother ASUS y una placa nvidia, y sacar todo andando a la media hora de ponerlo en tu maquina.

El presupuesto, o tus ganas, te pueden inclinar por una opcion o por otra, pero no digas que no te avisamos.


PD: Movido al subforo de hardware, ya que la placa se puede patear. Y en el caso de una placa VIA, realmente se lo merece.

---

### Post by goldenfox on 2009-05-09
hola tengo exactamente el mismo problema que zoroastro444
pero tengo una placa ProSavage8 KM266/KL266 y desde hardy que vengo intentando
no estoy en pos de comprar una nueva placa(me encantaria pero me faltan $$)
y google no me sirvió de mucho 
hasta haora solo encontré a 1 sola persona que lo logro en un post viejo de un foro (le mande un mp pero nunca fue respondido) y la verdad es que me gustaría para usar efectos simples

---

### Post by guillermolisi on 2009-05-09
> **goldenfox said:**
> hola tengo exactamente el mismo problema que zoroastro444
pero tengo una placa ProSavage8 KM266/KL266 y desde hardy que vengo intentando
no estoy en pos de comprar una nueva placa(me encantaria pero me faltan $$)
y google no me sirvió de mucho 
hasta haora solo encontré a 1 sola persona que lo logro en un post viejo de un foro (le mande un mp pero nunca fue respondido) y la verdad es que me gustaría para usar efectos simples
Este tema esta recontra trillado.

Tengo dos placas Asus con chipset VIA.
Revise, oportunamente, todo lo referido a aceleracion con esa placa de video, vi que un par de tipos dicen que la hicieron funcionar, pero despues de intentrar y reintentar en varias y distintas oportunidades, opte por poner nVidia y se termino la cuestion.

Es mas caro para el bolsillo pero mis ojos y las endorfinas agradecidas por cada peso invertido. Con el tiempo que le dedique podria haber aprendido muchas otras cosas mas utiles y no solo que ese chipset. VIA y OpenArena son una verdadera porqueria.

---

### Post by pahbloo.marks on 2009-05-22
Olá, eu tenho uma placa de vídeo com a mesma descrição do zoroastro444. Mas infelizmente minha máquina é um laptop. O que é que eu faço então?????

----------------------------------
Desculpe escrever em português, *pero no hablo español!!!* hahahah

---

### Post by guillermolisi on 2009-05-22
> **pahbloo.marks said:**
> Olá, eu tenho uma placa de vídeo com a mesma descrição do zoroastro444. Mas infelizmente minha máquina é um laptop. O que é que eu faço então?????

----------------------------------
Desculpe escrever em português, *pero no hablo español!!!* hahahah
Oi, tudo bem ?

VC está f****o com o laptop e chipset VIA Chrome 9.

Nao pode trocar placa, entao só pode trocar o laptop ou tentar o driver "vesa". Logicamente sem efeitos especias na tela.

PS:   Desculpe escrever sem alguns acentos. É bem difícil com o teclado em Español. Seja Bem Vindo a nosso foro.

---

