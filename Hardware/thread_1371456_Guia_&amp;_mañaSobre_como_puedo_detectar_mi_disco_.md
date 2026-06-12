---
title: "Guia &amp; maña:Sobre como puedo detectar mi disco o partición,sin perder datos (facil)"
date: 2010-01-03
forum: Hardware
---

### Post by Fitmoos on 2010-01-03
En este tema enseñaré manera en que mi Xubuntu 9.10 ( Ubuntu ) en mi eeepc me reconoció mi segundo disco duro ( quizás también sirve para particiones ), cosa que no había podido hacer. En cierta manera esto es una 'maña' como le decimos los chilenos, de que procedimiento que se utilizó no es el tradicional, este tema lo abro con el fin de se arregló esta mañana y sirva como guía.

A través de este método usted no perderá archivos.

Condiciones
tenemos un disco o partición no reconocida, la cual él sistema operativo cuando uno ingresa a '/media' otra carpeta donde se sitúa en los discos duros, éste no aparece. 

Paso1
colocamos en la barra superior, o la llamada 'Lugares' la opción de búsqueda de archivos o 'search for file'. 

Paso 2

Se le abriera una ventana con el nombre de 'Catfish' que sería el programa que busca archivos. Entre las opciones de búsqueda, esta la opción de en la carpeta que se quiere buscar, en la extraña 'carpeta' con lo que 'otro' (ya pudo notar que dentro las opciones de búsqueda de estar el disco duro no reconocido, no lo coloque).

paso 3
ahora la ventana 'elija carpeta', seleccione el disco duro que no ha sido reconocido. Posterior a eso, le solicitará la clave del administrador, coloqusela. Ahora cierre la carpeta.

Paso final.
Meterse a la raíz del sistema de archivos, seleccione la carpeta 'media'. Ahora puede ver su disco duro y explorarlo sin problema alguno.

Advertencia: 
- Este procedimiento debe ser colocado cada vez que se enciende el computador.
- A través de este método usted no perderá archivos.

Este chistoso metodo fue descubierto con un pariente politico llamado 'Leandro' (en la vida real), que es experto en Linux.

---

### Post by moreback on 2010-01-04
Tengo la impresión que tu usuario no está autorizado para montar unidades automáticamente.

Revisa con **Sistema -> Administración -> Usuarios y grupos** tu usuario y verifica que tenga activado el privilegio "*Montar sistemas de archivos en espacio de usuario (FUSE)*". Ojo que tienes que desbloquear primero usando el botón que sale al lado de **Pulse para realizar los cambios**.

Si haces algún cambio tienes que deslogearte y volver a entrar para que se apliquen estos privilegios.

También revisa las opciones de **Sistema -> Preferencias -> Gestión de archivos**, pestaña Soportes.

Saludos.

---

