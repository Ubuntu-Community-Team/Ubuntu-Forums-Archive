---
title: "error de tratamiento, en el fichero `/var/lib/dpkg/status'"
date: 2009-07-17
forum: Instalación y Actualización
---

### Post by NightWishmaster on 2009-07-17
lo siento mucho pero yo tengo problemas con mi ubuntu 9.04 y quisiera saber como solucionarlo

el problema es que al intentar instalar actualizaciones o software aparece

E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. 
E: _cache->open() failed, please report.

y ya ejecute en terminal sudo dpkg --configure -a

y aparece esto 

~$ sudo dpkg --configure -a
dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/status' cerca de la línea 22221:
 nombre de paquete inválido (el carácter `
' no está permitido (solamente se permiten letras, dígitos caracteres `-+._'))

tambien ejecute en terminal sudo dpkg -C


y aparece

sudo dpkg -C
dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/status' cerca de la línea 22221:
 nombre de paquete inválido (el carácter `
' no está permitido (solamente se permiten letras, dígitos caracteres `-+._'))


y por ultimo intente sudo dpkg -r --force-remove-reinstreq openoffice.org

y aparece

dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/status' cerca de la línea 22221:
 nombre de paquete inválido (el carácter `
' no está permitido (solamente se permiten letras, dígitos caracteres `-+._'))


como ven siempre dice lo mismo y ya no se que hacer:confused::confused::confused: porfavor nececito ayuda URGENTE
muchas gracias por atender mi pregunta y espero su respuesta gracias de antemano

---

### Post by Carlos C on 2009-07-18
Hola. Separé tu post en un thread independiente porque creo que es un problema diferente.

Te sugiero que pruebes haciendo una copia de seguridad del archivo que presenta problemas, luego lo elimines e intentes actualizar de nuevo. De esa manera si no funciona siempre puedes volver atrás.

Para hacer la copia de seguridad:
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.back
```Luego borras el archivo original:
```
sudo rm /var/lib/dpkg/status
```Ahora intenta actualizar nuevamente y ve qué te dice:
```
sudo apt-get update
```

---

### Post by EnriqueK on 2009-07-18
En** /var/backups** se almaceman varios respaldo del archivo **status** (dpkg.status.1.gz  .... dpkg.status.6.gz , debes descomprimirlos y luego los renonmbras a **atatus** y finalmete lo usas para reemplazar al archivo status originmal , sugiero ir probando con el mas reciente y si no resulta, con el que le sigue y así hast5a dar con alguno que solucione el problema.

---

### Post by agustinflames on 2009-07-20
El pingüino dice que:

```
dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/status' cerca de la línea 22221:
nombre de paquete inválido ([COLOR="Red"]el carácter `
' no está permitido[/COLOR] (solamente se permiten letras, dígitos caracteres `-+._'))
```

según entiendo lo que dice ahí, se habría 'colado' de alguna manera extraña algun caracter rarito?
yo abriría dicho fichero en nano y me iría a la linea en cuestión y hecharle una miradita (claro está después de hacen un backup).
Si no lo es así, entonces todavía persisten mis problemas de comprensión lectora de la básica jajajaj
Saludos !

---

### Post by alexelprogramador on 2010-05-27
> **EnriqueK said:**
> En** /var/backups** se almaceman varios respaldo del archivo **status** (dpkg.status.1.gz  .... dpkg.status.6.gz , debes descomprimirlos y luego los renonmbras a **atatus** y finalmete lo usas para reemplazar al archivo status originmal , sugiero ir probando con el mas reciente y si no resulta, con el que le sigue y así hast5a dar con alguno que solucione el problema.

hola

arrelgé el problema haciendo exactamente lo que dice enrique

solo hay que descomprimir el ultimo fichero dpkg.status.(el mayor numero) de la carpeta **/var/backups** y meterla en la carpeta **/var/lib/dpkg**

tambien hay que renombrar el archivo descomprimido, que seria pasar del archivo: **dpkg.status.0** a nombrarlo simplemente **status**

---

### Post by Carlos C on 2010-05-28
> **alexelprogramador said:**
> hola

arrelgé el problema haciendo exactamente lo que dice enrique

solo hay que descomprimir el ultimo fichero dpkg.status.(el mayor numero) de la carpeta **/var/backups** y meterla en la carpeta **/var/lib/dpkg**

tambien hay que renombrar el archivo descomprimido, que seria pasar del archivo: **dpkg.status.0** a nombrarlo simplemente **status**

Gracias por el dato, es bueno tenerlo presente para futuras consultas.

---

