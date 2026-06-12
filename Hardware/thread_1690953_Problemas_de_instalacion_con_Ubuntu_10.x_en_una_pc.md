---
title: "Problemas de instalacion con Ubuntu 10.x en una pc con mother chino"
date: 2011-02-19
forum: Hardware
---

### Post by selapablod on 2011-02-19
Hola gente!! Que tal??
Mi nombre es pablo y me estoy iniciando en el mundillo del software  libre de la mano de Ubuntu. He realizado varias instalaciones sin  ninguna gran complicación y siempre que me he encontrado con algun  inconveniente lo he logrado solucionar con la ayuda de los foros.
 Ahora me encuentro con el siguiente problema al cual no le encuentro solución:
Trato de instalar ubuntu 10.4 o 10.10 en un PC y cuando aparece la  pantalla de selección de idiomas se mueren el teclado y el mouse. He  podido instalar la versión 9.4 de Ubuntu, pero no pude actualizarlo.  Tambien llegue a instalar el 10.4 desactivando todas las opciones del  mother, pero a los pocos segundos de iniciarse me ocurre el mismo  problema: no tengo ni mouse ni teclado. Tambien probe reemplazar la  memoria y tampoco funciono. Sinceramente no se que hacer y no encuentro  en internet alguien a quien le haya sucedido.
 De la marca del mother no tengo mucha descrpción, lo unico que dice es: MADE IN CHINA
 Agradezco mucho cualquier tipo de ayuda ya que tengo varias maquinas  iguales (con el mismo mother de mier...) en el laburo y necesito  instalarle puntualmente la versión 10.4
 Saludos!!!

---

### Post by guillermolisi on 2011-02-19
Que placa de video tiene esa maquina ? Es integrada ? Cuanta memoria usa la placa de video ?

Cuando inicias con el CD de 10.04, te aparece un menu en modo caracter con opcion en teclas de funcion ? Fijate que F6 te permite iniciar en modo VGA (Standard) para evitar problemas con algunas placas de video y Xorg (el servicio base para el escritorio grafico, teclado y mouse, entre otras dispositivos de I/O).

Si logras que por lo menos te abra una consola (sin entorno grafico) podras obtener informacion de detalle con ```
sudo lshw
```de todo tu hardware.

---

