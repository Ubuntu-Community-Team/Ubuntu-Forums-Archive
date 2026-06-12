---
title: "no funciona microfono integrado cq40...sonido ok"
date: 2009-09-20
forum: Hardware
---

### Post by danesparce on 2009-09-20
Hola, tengo una laptop compaq CQ40-505la e instlae ubuntu 9.04
No tenia sonido y en otro post encontre q  Carlos C decia q al archivo /etc/modprobe.d/alsa-base.conf: agregara lo siguiente

 	Code:
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel  el sonido funciona bien...pero el microfono integrado No Funciona....en preferencias agregar Captura y Captura1 q se supone es el microfono pero en control de volumen 
estan silenciados, los habilito y cierro y cuando vuelvo a abrir aparecen de nuevo mudos
Gracias

---

