---
title: "Gestor de Red se cierra y no encuentra redes wifi en Lenovo s10"
date: 2011-08-26
forum: Hardware
---

### Post by rominitita on 2011-08-26
Hola chicos, he visto que este es un problema un poco recurrente. Pero  tengo diferencias con el resto de las consultas sobre el wifi y los  lenovo s10.

Hace varios meses que tengo este netbook con ubuntu 10.10 y particionado con windows 7. 

Este ultimo tiempo en ubuntu el programa que reconoce las redes (el gestor de red) se  cierra inesperadamente. Sobre todo cuando la conexión es menor a un 80% y  no puedo volver a encontrar el programa para abrirlo o simplemente ver  que pasa. 

Además, intentando ver ese asunto.. Active el controlador "broadcom B43 wireless driver" en Otros controladores y desde ahi que antes que se cierre el gestor de red no encuentra ninguna conexión. Volví a desactivar el controlador, pero esto no ha provocado ningun cambio.

No se si esto tendrá relevancia pero lo coloco igual:
En dispositivo de red esta seleccionado interfaz de bucle local.
Y ademas solo esta para seleccionar el interfaz ethernet

Esperando su ayuda. Gracias!!

---

### Post by biale on 2011-08-28
Se cierra el gestor de redes /o/ simplemente inhabilita wireless?

De todas maneras las maniobras del gestor de redes serían...

# Reinicia al gestor de redes
  sudo service network-manager stop
  sudo rm /var/lib/NetworkManager/NetworkManager.state
  sudo service network-manager start

---

### Post by rominitita on 2011-08-29
Gracias por la respuesta.
Me pasan las dos cosas.
Pero mientras funciona el gestor, se inhabilita el wireless...

qué hago con el wifi?

---

### Post by guillermolisi on 2011-08-29
Y por que no actualizar a la version 11.04 eligiendo, al inicio de sesion Ubuntu Classic ?

La 11.04 con la version de kernel que esta usando deberia funcionar mejor que la 10.10 para esa placa de red, inclusive con el NManager.

---

### Post by rominitita on 2011-08-29
Era una opción que estaba analizando, pero prefiero esperar a que salga la próxima actualización y sobrevivir hasta esa fecha.
Lo curioso es que o había tenido problemas hasta hace 2 semanas..

---

### Post by guillermolisi on 2011-08-29
Yo no esperaria, sobre todo porque luego te sera mas facil actualizar a la 11.10

---

