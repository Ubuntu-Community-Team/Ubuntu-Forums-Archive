---
title: "No puedo reinstalar controlador placa wireless d-link"
date: 2011-06-30
forum: Hardware
---

### Post by mano negra on 2011-06-30
Buenas,
   Tengo instalado una placa wireless d-link dwa-150. Uso ubuntu 10.10. Cada vez que se actualizaba el kernel tenía que reinstalar el driver siguiendo estas instrucciones y nunca tuve problema [www.ubuntu-es.org/node/138976](www.ubuntu-es.org/node/138976)
   El tema es que con la última actualización del kernel no puedo reinstalar el controlador. Lo probé mil veces. Luego en "controladores adicionales" me aparece que tengo activado un controlador pero que se encuentra en desuso. Lo desactivé, volví a instalar el driver original y nada.
   No se si tengo que desinstalar el dreiver viejo, en todo caso no se como se deinstala algo que lo hice compilando el código (con "make install" lo instalé). 
Eso.
Salu

---

### Post by mano negra on 2011-06-30
Hice algunas cosas: lo desinstalé con "make uninstall". Ya no me en "controladores adicionales". Lo vuelvo a instalar y nada...

---

### Post by biale on 2011-06-30
Fijate si los logs tiran algo interesante. Tambien proba en arrancar con el kernel anterior para intentar aunque sea seguir con algo.

---

### Post by mano negra on 2011-07-06
Yo lo solucioné. Desinstalé con make uninstall, borre la capeta donde tenía los driver y volví a instalar todo de vuelta.
Salu

---

