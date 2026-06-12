---
title: "problemas al actualizar compiz"
date: 2009-06-23
forum: Instalación y Actualización
---

### Post by zhelo on 2009-06-23
resulta que hoy se me paarecio una actualizacion del compiz, a traves del "gestor de actualizaciones", y decidi instalar.... se bajaron los paquetes, y ubo un error inesperado, puse enviar el error y lo hizo sin problemas, los pauqtees instalados estaban rotos asi que decidi desintalar esos paquetes rotos.... el asunto es que al reiniciar me quedo el escritorio asi con el tema en mal estado..... trato de cambiar el tema y se queda la barra igual fea  =O
ahora no se que hacer para que quede normal ya que cuando trato de abrir algunas aplicacion, simplemente no se abren


ademas cuando voy a sistemas->xxx-> apariencia

me dice algo que el gnome-setting-daemon no es compatible con el kde algo asi..

---

### Post by Carlos C on 2009-06-24
Título editado.

---

### Post by moreback on 2009-06-24
No entiendo.

---

### Post by Carlos C on 2009-06-24
zhelo, falta información en tu post. De partida, es necesario que digas qué paquetes desinstalaste y cuáles son los errores exactos que el sistema te da. De otra manera es muy difícil ayudarte.

---

### Post by CdK1 on 2009-06-24
sudo apt-get install && sudo apt-get update && sudo apt-get dist-upgrade

Luego borra los directorios de compiz en tu home -.compiz- y prueba al reiniciar X

---

### Post by Patriciologico on 2009-06-27
> **CdK1 said:**
> sudo apt-get install && sudo apt-get update && sudo apt-get dist-upgrade

Luego borra los directorios de compiz en tu home -.compiz- y prueba al reiniciar X

Una consulta ¿ese dist-upgrade puede hacerle actualizar a la versión superior de ubuntu?

---

### Post by moreback on 2009-06-27
> **Patriciologico said:**
> Una consulta ¿ese dist-upgrade puede hacerle actualizar a la versión superior de ubuntu?
Sólo si cambia su /etc/apt/sources.list apuntando a otra versión.

---

### Post by Patriciologico on 2009-06-27
> **moreback said:**
> Sólo si cambia su /etc/apt/sources.list apuntando a otra versión.

Gracias

---

