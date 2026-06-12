---
title: "Problema linea comandos"
date: 2013-02-23
forum: Instalación y Actualización
---

### Post by Zamma on 2013-02-23
Hola a tod@s!   Recien instalo Ubuntu en mi pc (loptop--no tiene la disquera) fue dificil y extrano... se abre como una terminal, en negro la pantalla, y me salen dos opciones 'links', los cuales me lleban a diferentes "versiones", una obscura, casi no se ve, y la otra, la cual esta bien definida y clara, dice 'recuperada', ahi hago click, desde esta version es desde donde funciono ahora. -- es esto lo apropiado? ahora bien, no se si es el mismo problema o es otro diferente - por esto tengo que intentar explicarlo todo - cuando voy a la linea de comandos me da estos errores, que no se si seran el resultado o concecuencia de esta instalacion bizarra -- aun despues de haber reiniciado el equipo varias veces como lei en algun post en la seccion en ingles -- en fin, he aqui:    zammatta@ubuntu:~$ apt-get update E: No se pudo abrir el fichero de bloqueo «/var/lib/apt/lists/lock» - open (13: Permiso denegado) E: No se pudo bloquear el directorio /var/lib/apt/lists/ E: No se pudo abrir el fichero de bloqueo «/var/lib/dpkg/lock» - open (13: Permiso denegado) E: No se encontró un archivo de réplica «/var/lib/dpkg/» zammatta@ubuntu:~$   Saludos!

---

### Post by sirriffsalot on 2013-02-23
Uhm, en Inglés, por favor? Traductor Google no traduce lo suficientemente bien como para que me entienda!

---

### Post by Zamma on 2013-02-23
En cualquiera de las dos lenguas puedo leer -- solo se me dificulta escribir bien en ingles, usamos ambas? gracias!

---

### Post by schragge on 2013-02-23
> **Zamma said:**
> ```
zammatta@ubuntu:~$ apt-get update
E: No se pudo abrir el fichero de bloqueo «/var/lib/apt/lists/lock» - open (13: Permiso denegado)
E: No se pudo bloquear el directorio /var/lib/apt/lists/
E: No se pudo abrir el fichero de bloqueo «/var/lib/dpkg/lock» - open (13: Permiso denegado)
E: No se encontró un archivo de réplica «/var/lib/dpkg/»
zammatta@ubuntu:~$
```
Try
```
[color=red]sudo[/color] apt-get update
```

---

### Post by sirriffsalot on 2013-02-23
No puedo entender español muy bien, espero a alguien que habla español con fluidez le puede ayudar. Crucemos los dedos :) 

Aunque yo no creo que estos foros son para españoles .. ¡Lo siento!

---

### Post by Zamma on 2013-02-23
zammatta@ubuntu:~$ sudo apt-get update [sudo] password for zammatta:  Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease Des:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]           Des:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49,6 kB]             Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    Des:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [63,1 kB]        Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise InRelease                              Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates InRelease                      Des:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1.950 B] Des:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [22,2 kB]    Des:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1.382 B]  Des:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [237 kB]   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports InRelease                    Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise Release.gpg                            Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates Release.gpg  Des:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3.968 B] Des:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [69,9 kB] Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports Release.gpg                  Des:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2.368 B] Obj [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex           Obj [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex     Obj [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex     Obj [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex       Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise Release                                Obj [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en             Obj [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en       Obj [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en       Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates Release                        Obj [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en         Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports Release                      Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/main Sources                           Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/restricted Sources                     Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/universe Sources                       Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/multiverse Sources Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/main i386 Packages Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/restricted i386 Packages Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/universe i386 Packages Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/multiverse i386 Packages Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources   404  Not Found Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages   404  Not Found Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/main TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/multiverse TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/restricted TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/universe TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/main Sources Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/restricted Sources Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/universe Sources Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/multiverse Sources Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/main i386 Packages Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/restricted i386 Packages Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/universe i386 Packages Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/multiverse i386 Packages Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/main TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/multiverse TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/restricted TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/universe TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/main Sources Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-es_ES Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-es Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/restricted Sources Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/universe Sources Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/multiverse Sources Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/main i386 Packages Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/restricted i386 Packages Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/universe i386 Packages Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/multiverse i386 Packages Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/main TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/multiverse TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/restricted TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/universe TranslationIndex Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/main Translation-es Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/main Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/multiverse Translation-es Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/multiverse Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/restricted Translation-es Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/restricted Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/universe Translation-es Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise/universe Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/main Translation-es Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/main Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/multiverse Translation-es Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/multiverse Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/restricted Translation-es Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/restricted Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/universe Translation-es Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-updates/universe Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/main Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/multiverse Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/restricted Translation-en Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) precise-backports/universe Translation-en Descargados 452 kB en 3seg. (124 kB/s) W: Imposible obtener [http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found  W: Imposible obtener [http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found  E: Algunos archivos de índice fallaron al descargar. Se han ignorado, o se han utilizado unos antiguos en su lugar zammatta@ubuntu:~$

---

### Post by schragge on 2013-02-23
There's no need to use ubun-tor PPA for precise: tor, privoxy,  polipo, and vidalia are in the official repository.
```

sudo apt-add-repository --remove ppa:ubun-tor/ppa
sudo apt-get update

```

---

### Post by Zamma on 2013-02-24
zammatta@ubuntu:~$ sudo apt-add-repository --remove ppa:ubun-tor/ppa [sudo] password for zammatta:  You are about to remove the following PPA from your system:  This ppa publishes the latest version of tor, vidalia, polipo and privoxy.   Up-to-date versions of polipo and privoxy are backported to previous release of Ubuntu (currently: Oneiric, Natty, Maverick, Lucid, Karmic, Hardy).  More info: [https://launchpad.net/~ubun-tor/+archive/ppa](https://launchpad.net/~ubun-tor/+archive/ppa) Press [ENTER] to continue or ctrl-c to cancel removing it

---

### Post by schragge on 2013-02-24
[http://packages.ubuntu.com/precise/tor](http://packages.ubuntu.com/precise/tor)
[http://packages.ubuntu.com/precise/privoxy](http://packages.ubuntu.com/precise/privoxy)
[http://packages.ubuntu.com/precise/polipo](http://packages.ubuntu.com/precise/polipo)
[http://packages.ubuntu.com/precise/vidalia](http://packages.ubuntu.com/precise/vidalia)

---

