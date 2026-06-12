---
title: "Problema conexion a internet a través de Router ."
date: 2009-08-09
forum: Hardware
---

### Post by stritets on 2009-08-09
Hola a todos los usuarios.
Es la primera vez que posteo aqui. Y bueno, recurro porque tengo un problema con mi conexion a internet, les explico:
Tengo Telefónica, y solía conectarme directmante desde mi tarjeta de red al modem adsl mediante PPPoE.
Pero todo cambió cuando me compré un router inalambrico para crear un pequeña red en mi casa, es un Linksys WRT54G2.
De hecho, ahora es el router quien se conecta, ya que uso la opcion PPPoE que este incorpora.
En windows no tengo problema, pero mi sorpresa fue cuando inicié mi kubuntu. No había conexion.
Naturalmente, intenté reconfigurar mi conexion mediante pppoeconf. Pero no hubo caso.
He googleado, y la unica solucion que me ha funcionado, a medias, es la de editar el archivo /etc/network/interfaces y decirle que la conexion es por dhcp. (la verdad es que estoy tan tupido que no rcuerdo especificamente qué linea).
Desde entonces, no sé por qué, ahora se conecta, pero cuando voy al status del router, este aparece como desconectado, y mi impresion, es que pppoeconf está causando alguna clase de conflicto (cuando lo configuré por primera vez, le dije que deseaba conectarme al inicar sistema), ahora cada vez que me salgo de mi linux y entro a wingates, para ver si hay algun problema, debo reiniciar el router (On/Off) para que este vuelva a tomar IP del modem adsl (XAVI AMPER 8021R). Apagar y encender el router es muy perjudicial.
Les doy mas info:
-Mi tarjeta es eth2 (sé que deberia ser eth0, :lolflag: pero vaya a saber yo porque la tomó como 2, y eso q no tengo otra ethernet).
-El router es 192.168.2.1 (por motivos de conflictos con el modem adsl, tuve q cambiar a segmento 2).
-Tengo DHCP habilitado en el router, y bueno, no sé que otros antecedentes mas entregarles.

Todas la ideas son bienvenidas.

---

### Post by Carlos C on 2009-08-10
Hola. He movido tu post al subforo "Hardware". Por favor, antes de volver a crear un thread recuerda leer las normas:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

He publicado en cada subforo lo que corresponde publicar en cada uno.
Saludos.

---

