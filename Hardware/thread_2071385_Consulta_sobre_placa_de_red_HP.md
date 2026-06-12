---
title: "Consulta sobre placa de red HP"
date: 2012-10-15
forum: Hardware
---

### Post by ivaneneas on 2012-10-15
Hola, estoy por instalar Ubuntu 12.04.1 (Precise Pangolin) LTS en un server hp que posee dos placas de red HP NC375T QUAD. Mi duda es si esta version ya viene provista de algun driver para estas placas ya que en la web de HP no existe ninguno para estas distribuciones.
Desde ya muchisimas gracias por la ayuda que puedan brindarme.
Saludos desde Cordoba.

---

### Post by guillermolisi on 2012-10-16
Inicia el server desde un LiveCD y fijate como reconoce esas placas.
Lo mas importante es saber que integrado utilizan.

Por ejemplo, las Intel Doble Puerto Gigabit funcionan al toque tanto con Ubuntu como con RedHat ES.

---

### Post by z37a on 2012-10-17
HP desde hace mas de 1 ao ofrece soporte para Ubuntu, si se trata solo de la placa de red, quedate tranquilo que es 99% probable que funcione de 10 sin nada que tocar, el otro 1% bueno tal vez debas bajar un source y compilarlo, pero no creo que te pase eso!!!!

---

### Post by ivaneneas on 2012-10-17
Hola de nuevo, parece que estoy en el 1%, je.
Cuando comienzo a instalar me dice que esta haciendo falta un firmware no abierto y me pide el archivo **nx3fwct.bin** con la opcion de instalarlo desde un medio extraible durante la instalacion. Lo estuve buscando pero no he logrado dar con el.

---

### Post by z37a on 2012-10-17
> **ivaneneas said:**
> Hola de nuevo, parece que estoy en el 1%, je.
Cuando comienzo a instalar me dice que esta haciendo falta un firmware no abierto y me pide el archivo **nx3fwct.bin** con la opcion de instalarlo desde un medio extraible durante la instalacion. Lo estuve buscando pero no he logrado dar con el.


Fijate en este Link:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=4038767&prodTypeId=329290&prodSeriesId=4038765&swLang=8&taskId=135&swEnvOID=4049](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=4038767&prodTypeId=329290&prodSeriesId=4038765&swLang=8&taskId=135&swEnvOID=4049)

EDIT: Confirmo que el archivo esta en el link, es el driver que tenes que bajar, descomprimir el rpm(es un rpm que contiene dentro un tar.gz que contiene ese archivo y el driver).

Por otro lado, que servidor es el que estas instalando? un Proliant ML o DL? Modelo etc...? Por que mas alla de esto, si es un server HP tendrias que instalar el HP Smart Start CD, para poder validar las garantias de HP.

EDIT: Consejo, siempre en el sitio de HP poner para bajar en idioma ingles, en español no hay nada nunca, y cuando pones a bajar algo sea de SuSe/Red Hat/Debian/Ubuntu, siempre es el mismo paquete de linux que descarga, solo ponen los nombres por marketing(rara vez un paquete es solo para X distro).

---

