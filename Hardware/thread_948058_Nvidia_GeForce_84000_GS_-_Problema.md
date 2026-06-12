---
title: "Nvidia GeForce 84000 GS - Problema??"
date: 2008-10-14
forum: Hardware
---

### Post by Mauro22 on 2008-10-14
Buenas Sr. Sras y chico/as !!
 
 
A ver si me dan una mano con esta placa...
 
 
 
La historia es corta, compre esta placa para reemplazar la onboard (nVidia GF 6100) y parece que no fue buena idea...
 
 
Situacion:
 
1) Cambio de placa y arranco Ubuntu (8.04 con Gnome), 2 minutos y se cuelga todo menos el mouse, 3 minutos muere X, 5 minutos reacciona el teclado (Posibilidad de pasarme a modo texto y reiniciar) - Ojo al piojo, es solo la parte grafica, la PC nunca se cuelga.
 
2) Será Ubuntu? Reinicié, ente al XP. "Nuevo HW encontrado" bla bla bla, puse el CD de la placa, pide reiniciar, todo OK. Entra a XP y luego idem. 2 minutos, se traba todo y a diferencia de Ubuntu, XP nunca se recompone...
 
3) Sera Ubuntu? Sera XP? Sera la placa? Dicen que la tercera es la vencida...
Reset y cargo el Vista, instalo los drivers, reinicio y aca estoy... con problemas pero no tanto...
 
 
 
Drivers??
 
 
Mas info: de vez en cuando aparecer rayas de colores como si fueran ese subrayado que uno hace a mano alzada (medio ondulado como olas)...  Eso es la placa o los drivers?
 
 
Tengo una laguna en la cabeza... ya no puedo pensar.
 
 
 
 
 
Si me pueden dar una mano, se los agradeceria.
 
 
 
 
Saludos!!

---

### Post by santiagoward2000 on 2008-10-14
Hola Mauro!
Yo tengo la misma placa y anda sin problemas en Ubuntu y en XP (no tengo Vista en esta máquina). Seguro que es un tema de drivers. No sé cuáles usa la 6100, pero esta usa los nvidia-glx-new. Si la otra usaba los viejos y quedaron instalados, puede que de ahí venga el problema.
Saludos!

---

### Post by niko_3100 on 2008-10-14
probaste instalando los drivers de envy? yo tengo una nvidia geforce 7150 integrada y los drivers del repositorio no me andaban bien pero los de envy van como piña.

---

### Post by Mauro22 on 2008-10-15
He decidido que es problema de la placa en si.


3 S.O (ubuntu, xp y vista) y en los 3 falla sea con:

* Drivers genericos a.k.a vesa en linux, standard VGA en windows.
* Drivers que viene con el cd + envy
* Drivers actualizados de la pagina (que tambien proporcionan el sh para linux)


Gracias niko_3100 y santiagoward2000 por tomarse el tiempo


No se si darlo por solved. :S

---

### Post by faktorqm on 2008-10-15
Yo me fijaria que no tenga ningun conflicto conocido con la placa on board, conflicto de IRQ, tipo de AGP (o PCI-E), velocidad del mismo, version de bios, bus de memoria, y configuracion del bios en si. Salu2!

---

### Post by victor_nesta on 2008-10-16
y a eso agregarle, el tema fuente. Si es muy mala da problemas. Proba con otra de mas potencia
Obvio descartamos que ayas-allás comprado una VGA refurbished o algo similar

---

### Post by vampichoke on 2008-10-16
lo de la fuente es importante ya ese tamaño de gforce chupa bastante.

pero si decis q no te anda en win con los drivers. guarda q no te haya venido mala (razonando q la compraste nueva y no 2da mano).digo x q a un amigo hara 3 meses con una 8600 gt pci-e le andaba mal tmb le batieron q era problema de su pci. mentira.

 hizo quilombo y se la cambiaron. 

(estan viniendo malas las nvidia gforce xfx) =/

---

