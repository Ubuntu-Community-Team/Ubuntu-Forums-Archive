---
title: "Migrar de Red Hat a Ubuntu server"
date: 2009-05-28
forum: Instalación y Actualización
---

### Post by sapodrilorenacuagator on 2009-05-28
bueno amigos esta es mi primera consulta de muchas
 
aca en la empresa tenemos un server Linux con la distribucion Red Hat 9 y quiero montar un server Ubuntu...
 
mi pregunta es la siguiente
 
como hago para la migracion de datos??
 
tengo q hacer todo manual o hay alguna aplicacion o metodo mas facil
 
de antemano muchas gracias

---

### Post by augias on 2009-05-28
si los datos estan en un directorio de /home/*, puedes hacer una particion nueva en el mismo disco duro y migrar el directorio home en su cabalidad hacia esa particion. Luego, al instalar ubuntu, eliges esa particion para ser montada como tu /home. eso se hace en el particionador que viene en el disco de instalacion de ubuntu y ubuntu server. 

Esto permite que todas las preferencias que tenias de todos tus programas queden guardadas. A la hora de reinstalar tal o tal otra aplicacion, en teoria, esta aplicacion se cargará tal como lo tenias configurada anteriormente. 

No tengo experiencia con red hat y no estoy seguro si, teniendo diferentes versiones de un programa, sean 100% compatibles. La idea es que si. Yo guarde mi home en una particion diferente y me cambie de ubuntu 8.10 a 9.04 y, aunque varios programas venian más nuevos que los de 8.10, se cargaron tal como lo habia dejado. 

Ojala confirme o matize mi respuesta alguien con mas experiencia!

---

### Post by moreback on 2009-05-29
No creo que exista mucha compatibilidad con Ubuntu 9.04 ya que Red Hat 9 se liberó en el 2003. En 6 años las aplicaciones han evolucionado bastante. Creo que el amigo tiene que revisar qué funciones cumplían ese equipo y de acuerdo a esto respaldar la información de /etc, /var/www, etc. No creo que haya usado mucho el /home ya que es un servidor.

El proceso es manual solamente.

Saludos.

---

