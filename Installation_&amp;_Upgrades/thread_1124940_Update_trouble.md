---
title: "Update trouble"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by ecuato on 2009-04-13
Hi.
I need help please:

I runs the update manager and appears:


Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Vaya, excedió el número de descripciones que este APT es capaz de manejar., E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_universe_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'


I red in a forum and wrote:

sudo rm -vf /var/lib/apt/lists/*

after

sudo apt-get update && sudo apt-get upgrade

and the terminal shows

Des:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-es
Des:2 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-es
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy Release.gpg
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy/all Translation-es
Des:3 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-es
Des:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg [189B]
Des:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-es [8071B]
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-es
Des:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-es
Des:7 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-es
Des:8 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release [7007B]
Des:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58,5kB]
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy/all Packages
Des:10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [51,2kB]
Des:11 [http://archive.canonical.com](http://archive.canonical.com) hardy Release [6998B]
Des:12 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid Release.gpg [189B]
Des:13 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Translation-es [3978B]
Err [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy/all Packages
404 Not Found
Des:14 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Translation-es [386kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Des:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release [65,9kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Des:16 [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages [2085B]
Des:17 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58,5kB]
Des:18 [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources [884B]
Des:19 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources [1550B]
Des:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [5212B]
Des:21 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages [3642B]
Des:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [28,4kB]
Des:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources [60,9kB]
Des:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages [179kB]
Des:25 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Translation-es [557kB]
Des:26 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [3517B]
Des:27 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [103kB]
Des:28 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [6736B]
Des:29 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [46,6kB]
Des:30 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [1105B]
Des:31 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [11,9kB]
Des:32 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [11,5kB]
Des:33 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [77,1kB]
Des:34 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [26,2kB]
Des:35 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Translation-es [66,6kB]
Des:36 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [903B]
Des:37 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [156kB]
Des:38 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-security Release.gpg [189B]
Des:39 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Des:40 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Translation-es [3978B]
Des:41 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Translation-es [573kB]
Des:42 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [8024B]
Des:43 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Translation-es [69,2kB]
Des:44 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Translation-es [558kB]
Des:45 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed Release.gpg [189B]
Des:46 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/restricted Translation-es [4820B]
Des:47 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/main Translation-es [602kB]
Des:48 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/multiverse Translation-es [83,0kB]
Des:49 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/universe Translation-es [668kB]
Des:50 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports Release.gpg [189B]
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/restricted Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/main Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/multiverse Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/universe Translation-es
Des:51 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid Release [65,9kB]
Des:52 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-security Release [51,2kB]
Des:53 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates Release [51,2kB]
Des:54 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed Release [51,2kB]
Des:55 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports Release [51,2kB]
Des:56 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Packages [8408B]
Des:57 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Packages [4542kB]
Des:58 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Packages [1256kB]
Des:59 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Packages [199kB]
Des:60 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Sources [3113B]
Des:61 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Sources [505kB]
Des:62 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Sources [95,8kB]
Des:63 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Sources [1981kB]
Des:64 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-security/restricted Sources [1154B]
Des:65 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-security/main Sources [28,7kB]
Des:66 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-security/multiverse Sources [1860B]
Des:67 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-security/universe Sources [7958B]
Des:68 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Packages [8117B]
Des:69 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Packages [321kB]
Des:70 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Packages [10,9kB]
Des:71 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Packages [91,5kB]
Des:72 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Sources [2474B]
Des:73 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Sources [102kB]
Des:74 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Sources [4118B]
Des:75 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Sources [20,6kB]
Des:76 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/restricted Packages [2788B]
Des:77 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/main Packages [69,3kB]
Des:78 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/multiverse Packages [14B]
Des:79 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/universe Packages [13,8kB]
Des:80 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/restricted Sources [564B]
Des:81 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/main Sources [28,8kB]
Des:82 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/multiverse Sources [14B]
Des:83 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/universe Sources [4712B]
Des:84 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/restricted Packages [14B]
Des:85 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/main Packages [80,0kB]
Des:86 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/multiverse Packages [14B]
Des:87 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/universe Packages [38,8kB]
Des:88 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/restricted Sources [14B]
Des:89 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/main Sources [15,8kB]
Des:90 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/multiverse Sources [14B]
Des:91 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/universe Sources [13,1kB]
Descargados 14,3MB en 3min33s (66,9kB/s)
W: Imposible obtener [http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz](http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz) 404 Not Found

E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.



At last i wrote:

sudo gedit /etc/apt/sources.list

and shows:

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid restricted universe main multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports restricted main multiverse universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#ULTAMATIX REPOS START

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy all

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy all

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#ULTAMATIX REPOS END


Anyone knows what happen?

Please help me.


Pd. Sorry my bad english






	
Fecha / Hora
Lunes, 13 Abril 2009 22:06

---

### Post by Ericyzfr1 on 2009-04-13
It seems that you have too many. You should try to go to Software sources and select only the necessary items then, it will update your list.

---

