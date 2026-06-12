---
title: "¡Ayuda! No puedo instalar nada, ni programas ni actualizaciones"
date: 2014-08-19
forum: Instalación y Actualización
---

### Post by Clotilde_Gonzalez on 2014-08-19
¡Hola a tod@s! Espero puedan ayudarme, acabo de comenzar a migrar a Linux y entiendo muy poco. Instalé Ubuntu 14 32bits y no he podido instalar absolutamente nada, siquiera las actualizaciones. Esto es lo que aparece:

"Falló la operación con el paquete

installArchives() failed: 
Extrayendo plantillas para los paquetes: 44% 
Extrayendo plantillas para los paquetes: 89% 
Extrayendo plantillas para los paquetes: 100% 
 Extrayendo plantillas para los paquetes: 44%
Extrayendo plantillas para los paquetes: 89% 
Extrayendo plantillas para los paquetes: 100% 
 Extrayendo plantillas para los paquetes: 44%
Extrayendo plantillas para los paquetes: 89%
Extrayendo plantillas para los paquetes: 100% 
Selecting previously unselected package libaacs0:i386. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% 
[B]dpkg: unrecoverable fatal error, aborting: 
 reading files list for package 'linux-headers-3.13.0-32': Input/output error 
Error in function:  [/B]

¡Muchas gracias!

---

### Post by dave131 on 2014-08-19
From user El _Shrander in 2010:

		 				 				 					 				 		 			 				[INDENT] 					I suggest you visit the Spanish forums at [this address]("http://www.ubuntu-es.org/?q=forum"). / Te recomiendo que visites los foros en español que podrás encontrar en [esta dirección]("http://www.ubuntu-es.org/?q=forum"). 				[/INDENT]

---

### Post by ubudog on 2014-08-19
Mmm, eso parece una problema con el disco, pero tal vez que esto te ayude:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.ko
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo dpkg --configure -a
```

---

