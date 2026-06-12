---
title: "No se conecta Huawei e176 con Entelpcs en Lucid"
date: 2010-05-12
forum: Hardware
---

### Post by ferossan on 2010-05-12
Hola

Estoy tratando de hacer conexión a internet con el modem Huawei e176 de Entelpcs en Lucid. El modem en sí es reconocido, aparece en el listado del NetworkManager y lo configuré para imovil.entelpcs.cl, pero nada, no conecta.
Alguien lo pudo configurar? Es necesario instalar algo extra en Lucid?
Gracias!

---

### Post by asterix77 on 2010-05-12
Con Network ese modem funciona no muy bien, a veces conecta y aveces no (al menos en karmic me pasó). Lo mejor y más fácil es que te bajes los siguientes paquetes deb de la siguiente página [https://forge.betavine.net/frs/?group_id=12&release_id=272](https://forge.betavine.net/frs/?group_id=12&release_id=272), escoges el que corresponde a tu distro y arquitectura, lo instalas con un click y listo.

[ozerocdoff_0.4-2]("https://forge.betavine.net/frs/download.php/539/ozerocdoff_0.4-2_amd64.deb")

[usb-modeswitch_0.9.4-1]("https://forge.betavine.net/frs/download.php/416/usb-modeswitch_0.9.4-1_i386.deb")

[vodafone-mobile-connect_1.99.17-8]("https://forge.betavine.net/frs/download.php/421/vodafone-mobile-connect_1.99.17-8_all.deb")


Lo bueno de esto es que te permite cambiar de red igual que en windows (edge o hspa)


Saludos

---

### Post by ferossan on 2010-05-12
> **asterix77 said:**
> Con Network ese modem funciona no muy bien, a veces conecta y aveces no (al menos en karmic me pasó). Lo mejor y más fácil es que te bajes los siguientes paquetes deb de la siguiente página [https://forge.betavine.net/frs/?group_id=12&release_id=272](https://forge.betavine.net/frs/?group_id=12&release_id=272), escoges el que corresponde a tu distro y arquitectura, lo instalas con un click y listo.

[ozerocdoff_0.4-2]("https://forge.betavine.net/frs/download.php/539/ozerocdoff_0.4-2_amd64.deb")

[usb-modeswitch_0.9.4-1]("https://forge.betavine.net/frs/download.php/416/usb-modeswitch_0.9.4-1_i386.deb")

[vodafone-mobile-connect_1.99.17-8]("https://forge.betavine.net/frs/download.php/421/vodafone-mobile-connect_1.99.17-8_all.deb")


Lo bueno de esto es que te permite cambiar de red igual que en windows (edge o hspa)


Saludos

Gracias. Tomé la info como referencia, pero no usé exactamente esos binarios. Simplemente instalé usb-modeswitch desde los repositorios oficiales de Lucid y ya. Conectado.
En general, no recomiendo instalar binarios sin saber de dónde provienen. Tampoco es recomendable instalar cualquier repositorio ppa, es fácil "quebrar" el sistema si no se tiene cuidado.
Gracias otra vez por la "pista" :P

---

### Post by macropovov on 2010-09-01
ferossan podrias detallar como se activó tu modem usando el usb-modeswitch?

he buscado y leído en diversos foros y eres el único que trata sobre este modem especifico y que además logró hacerlo funcionar

saludos!

---

### Post by RafaelG on 2010-09-08
> **ferossan said:**
> Hola

Estoy tratando de hacer conexión a internet con el modem Huawei e176 de Entelpcs en Lucid. El modem en sí es reconocido, aparece en el listado del NetworkManager y lo configuré para imovil.entelpcs.cl, pero nada, no conecta.
Alguien lo pudo configurar? Es necesario instalar algo extra en Lucid?
Gracias!


Ferossan,

Yo sinceramente tengo el mismo dispositivo y la verdad que no tuve que   realizar ninguna configuracion extra mas que conectarlo a una entrada  USB y cuando ya es reconocido por el Network Manager entonces  simplemente poner la ubicacion, posteriormente seleccionar la compania  operadora en mi caso es EntelPCS en Chile y listo Aceptar y el  dispositivo funciona sin mayor problema de hecho tengo entendido que  para la gran mayoria funciona de ese modo ya que cuando quise comprar  uno me recomendaron este modelo por lo facil para configurar  en Ubuntu.

Saludos!

---

### Post by asterix77 on 2010-09-08
Con ese modem a mi me pasaba algo curioso, al usar cualquier live-CD o pendrive-live, el sistema me reconocía fácilmente el modem, solo bastaba con seguir las instrucciones de network manager y listo, internet al instante. Pero al instalar el sistema en mi notebook, no sé por que razón, no me lo reconocía bien y siempre tuve problemas para realizar la conexión. Solo se me arregló la situación instalando los paquetes mencionados en el post anterior.

Saludos

---

