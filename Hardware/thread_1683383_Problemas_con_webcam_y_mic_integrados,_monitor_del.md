---
title: "Problemas con webcam y mic integrados, monitor dell sp2208wfp"
date: 2011-02-07
forum: Hardware
---

### Post by joa-san on 2011-02-07
Hola estoy teniendo problemas con mi ubuntu 10.10 ya que no puedo hacer que reconozca la webcam y el mic del monitor, si bien al ejecutar el comando lsusb me da lo siguiente:

joa-san@Honshin:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 05a9:2643 OmniVision Technologies, Inc. Monitor Webcam
Bus 001 Device 002: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Aparentemente ve a la webcam y los usb. Los usb funcionan pero ni el cheese ni el guvcview reconocen la cam.
Cuando recién instale los paquetes UVC arrancó y andaba todo pero luego de volver el gnome a sus parámetros por defecto dejo de funcionar, desinstalé y volví a instalar los paquetes UVC y anduvieron pero al reiniciar la máquina dejaron de funcionar otra vez. Alguna sugerencia? Soy nuevo en esto y no se que más podía hacer.
Un dato más antes de instalar los paquetes UVC y hacer que la webcam anduviera. Después de instalar los drivers current de NVIDIA. Al iniciar la máquina antes de que arranque el escritorio tengo este mensaje:

xxxxxx] UVCVIDEO failed to query (XX) UVC probe control (-32) (exp 26)
xxxxxx] UVCVIDEO: Failed to initialize device (-5)

(las "x" son numeros que cambian y luego de esos dos renglones aparece el nombre de mi equipo para logear pero que no da tiempo a hacerlo y inicia directamente.

Eso es toda la info que puedo darles si hay algo más diganme como hacerlo y les paso

---

