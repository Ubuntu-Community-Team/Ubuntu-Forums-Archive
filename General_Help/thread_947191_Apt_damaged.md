---
title: "Apt damaged"
date: 2008-10-14
forum: General Help
---

### Post by Marcelo Ramone on 2008-10-14
I don't know how to resolve this apt problem...

> marcelo@linux:~$ sudo apt-get upgrade 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar `apt-get -f install' para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
  cron: Depende: sysv-rc (>= ? 2.86.ds1-14.1ubuntu45) pero 2.86.ds1-14.1ubuntu45 está instalado
E: Dependencias incumplidas. Pruebe de nuevo usando -f.
marcelo@linux:~$ sudo apt-get -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... Listo
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  apt-listchanges
Utilice «apt-get autoremove» para eliminarlos.
Los siguientes paquetes se ELIMINARÁN:
  apticron cron exim4-base exim4-daemon-light mailx ubuntu-standard
0 actualizados, 0 se instalarán, 6 para eliminar y 0 no actualizados.
Se liberarán 3310kB después de desempaquetar.
¿Desea continuar [S/n]? s
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 227, in <module>
    main()
  File "/usr/bin/apt-listchanges", line 72, in main
    status.readfile('/var/lib/dpkg/status')
  File "/usr/share/apt-listchanges/DebianFiles.py", line 81, in readfile
    self.stanzas += [ControlStanza(x) for x in open(file, 'r').read().split('\n\n') if x]
  File "/usr/share/apt-listchanges/DebianFiles.py", line 61, in __init__
    field, value = line.split(':', 1)
ValueError: need more than 1 value to unpack
dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/status' cerca de la línea 26787 paquete `libmono-cairo1.0-cil':
 nueva línea dentro del nombre del campo `<pkg-mono-group@lists.alioth.debian.org>'
E: Sub-process /usr/bin/dpkg returned an error code (2)
marcelo@linux:~$ sudo apt-get autoremove
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar `apt-get -f install' para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
  cron: Depende: sysv-rc (>= ? 2.86.ds1-14.1ubuntu45) pero 2.86.ds1-14.1ubuntu45 está instalado
E: Dependencias incumplidas. Pruebe de nuevo usando -f.
marcelo@linux:~$ sudo apt-get autoremove -f
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... Listo
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  apt-listchanges
Los siguientes paquetes se ELIMINARÁN:
  apt-listchanges apticron cron exim4-base exim4-daemon-light mailx ubuntu-standard
0 actualizados, 0 se instalarán, 7 para eliminar y 0 no actualizados.
Se liberarán 3777kB después de desempaquetar.
¿Desea continuar [S/n]? s
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 227, in <module>
    main()
  File "/usr/bin/apt-listchanges", line 72, in main
    status.readfile('/var/lib/dpkg/status')
  File "/usr/share/apt-listchanges/DebianFiles.py", line 81, in readfile
    self.stanzas += [ControlStanza(x) for x in open(file, 'r').read().split('\n\n') if x]
  File "/usr/share/apt-listchanges/DebianFiles.py", line 61, in __init__
    field, value = line.split(':', 1)
ValueError: need more than 1 value to unpack
dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/status' cerca de la línea 26787 paquete `libmono-cairo1.0-cil':
 nueva línea dentro del nombre del campo `<pkg-mono-group@lists.alioth.debian.org>'
E: Sub-process /usr/bin/dpkg returned an error code (2)
marcelo@linux:~$ 

> HELP!!

---

### Post by Marcelo Ramone on 2008-10-14
[SIZE=6]**It's solved!**[/SIZE]

I just removed **"sysv-rc (>? 2.86.ds1-14.1ubuntu45)**" from /var/lib/dpkg/status (listed as cron package dependency) and the problem was solved. I actualized the system flawless :guitar: 

**Hey, Ho, Let's Go!!!**

---

