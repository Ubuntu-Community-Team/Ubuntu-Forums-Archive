---
title: "Problema grabar DVD's con K3b"
date: 2011-01-11
forum: Hardware
---

### Post by fmalvez on 2011-01-11
Hola a todos, espero que anden bien..
Soy newbie en Ubuntu y recientemente instale el Ubuntu 10.04 LTS. Me encuentro con la necesidad de grabar archivos en DVD's y para hacerlo instale el K3b. Luego de grabar el primer DVD, sin problema alguno, cuando quise seguir grabando el programa me devolvió distintos errores de grabación constantes en todas las velocidades posibles.
Les comento que mi grabadora es una LG HL-DT-ST DVDRAM GSA-H42N y los DVD son Verbatim DVD+R 16X.

Les paso el log para los entendidos que me puedan ayudar:
-----------------------------------------------------------------

Burned media
-----------------------
DVD+R

Devices
-----------------------
HL-DT-ST DVDRAM GSA-H42N RL01 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R secuencial, DVD-R doble capa secuencial, DVD-R doble capa salteado, DVD-RAM, DVD-RW sobrescritura restringida, DVD-RW secuencial, DVD+RW, DVD+R, DVD+R doble capa, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Sobrescritura restringida, Salto de capa] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 1579793 (3235416064 bytes)

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.5 (KDE 4.4.5)
QT Version:  4.6.2
Kernel:      2.6.32-27-generic

Used versions
-----------------------
mkisofs: 1.1.10
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 4.1x1352KBps.
          0/3235416064 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
=== last message repeated 2 times. ===
   14974976/3235416064 ( 0.5%) @3.2x, remaining 46:35 RBU 100.0% UBU   2.9%
   33488896/3235416064 ( 1.0%) @4.0x, remaining 25:29 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=41a0h failed with SK=4h/TRACKING SERVO FAILURE]: Input/output error
:-( write failed: Input/output error
/dev/sr0: flushing cache
:-[ FLUSH CACHE failed with SK=4h/TRACKING SERVO FAILURE]: Input/output error
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=4h/ASC=A0h/ACQ=80h]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=4gms -use-the-force-luke=tracksize:1579793 -speed=4 -use-the-force-luke=bufsize:32m

mkisofs
-----------------------
1579793
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using COD_OP_NEGRAS_TH3_DUB_PA000.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part38.rar (CoD.Op.Negras.Th3_Dub.part37.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA001.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part37.rar (CoD.Op.Negras.Th3_Dub.part36.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA002.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part36.rar (CoD.Op.Negras.Th3_Dub.part35.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA003.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part35.rar (CoD.Op.Negras.Th3_Dub.part34.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA004.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part34.rar (CoD.Op.Negras.Th3_Dub.part33.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA005.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part33.rar (CoD.Op.Negras.Th3_Dub.part32.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA006.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part32.rar (CoD.Op.Negras.Th3_Dub.part31.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA007.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part31.rar (CoD.Op.Negras.Th3_Dub.part30.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA008.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part29.rar (CoD.Op.Negras.Th3_Dub.part28.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA009.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part28.rar (CoD.Op.Negras.Th3_Dub.part27.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA00A.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part27.rar (CoD.Op.Negras.Th3_Dub.part26.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA00B.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part26.rar (CoD.Op.Negras.Th3_Dub.part25.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA00C.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part25.rar (CoD.Op.Negras.Th3_Dub.part24.rar)
Using COD_OP_NEGRAS_TH3_DUB_PA00D.RAR;1 for  COD BlackOps 2 de 2/CoD.Op.Negras.Th3_Dub.part24.rar (CoD.Op.Negras.Th3_Dub.part23.rar)
  0.03% done, estimate finish Tue Jan 11 20:30:05 2011
  0.06% done, estimate finish Tue Jan 11 20:30:05 2011
  0.10% done, estimate finish Tue Jan 11 20:30:05 2011
  0.13% done, estimate finish Tue Jan 11 20:30:05 2011
  0.16% done, estimate finish Tue Jan 11 20:30:05 2011
  0.19% done, estimate finish Tue Jan 11 20:30:05 2011
  0.22% done, estimate finish Tue Jan 11 20:30:05 2011
  0.25% done, estimate finish Tue Jan 11 20:30:05 2011
  0.29% done, estimate finish Tue Jan 11 20:30:05 2011
  0.32% done, estimate finish Tue Jan 11 20:30:05 2011
  0.35% done, estimate finish Tue Jan 11 20:30:05 2011
  0.38% done, estimate finish Tue Jan 11 20:30:05 2011
  0.41% done, estimate finish Tue Jan 11 20:30:05 2011
  0.44% done, estimate finish Tue Jan 11 20:30:05 2011
  0.47% done, estimate finish Tue Jan 11 20:30:05 2011
  0.51% done, estimate finish Tue Jan 11 20:30:05 2011
  0.54% done, estimate finish Tue Jan 11 20:30:05 2011
  0.57% done, estimate finish Tue Jan 11 20:30:05 2011
  0.60% done, estimate finish Tue Jan 11 20:30:05 2011
  0.63% done, estimate finish Tue Jan 11 20:30:05 2011
  0.67% done, estimate finish Tue Jan 11 20:30:05 2011
  0.70% done, estimate finish Tue Jan 11 20:30:05 2011
  0.73% done, estimate finish Tue Jan 11 20:30:05 2011
  0.76% done, estimate finish Tue Jan 11 20:30:05 2011
  0.79% done, estimate finish Tue Jan 11 20:30:05 2011
  0.82% done, estimate finish Tue Jan 11 20:30:05 2011
  0.85% done, estimate finish Tue Jan 11 20:30:05 2011
  0.89% done, estimate finish Tue Jan 11 20:30:05 2011
  0.92% done, estimate finish Tue Jan 11 20:30:05 2011
  0.95% done, estimate finish Tue Jan 11 20:30:05 2011
  0.98% done, estimate finish Tue Jan 11 20:30:05 2011
  1.01% done, estimate finish Tue Jan 11 20:30:05 2011
  1.05% done, estimate finish Tue Jan 11 20:46:01 2011
  1.08% done, estimate finish Tue Jan 11 20:47:06 2011
  1.11% done, estimate finish Tue Jan 11 20:46:37 2011
  1.14% done, estimate finish Tue Jan 11 20:46:10 2011
  1.17% done, estimate finish Tue Jan 11 20:45:43 2011
  1.20% done, estimate finish Tue Jan 11 20:45:19 2011
  1.23% done, estimate finish Tue Jan 11 20:46:16 2011
  1.27% done, estimate finish Tue Jan 11 20:45:52 2011
  1.30% done, estimate finish Tue Jan 11 20:45:29 2011
  1.33% done, estimate finish Tue Jan 11 20:45:07 2011
  1.36% done, estimate finish Tue Jan 11 20:44:46 2011
  1.39% done, estimate finish Tue Jan 11 20:44:26 2011
  1.43% done, estimate finish Tue Jan 11 20:45:17 2011
  1.46% done, estimate finish Tue Jan 11 20:44:57 2011
  1.49% done, estimate finish Tue Jan 11 20:44:38 2011
  1.52% done, estimate finish Tue Jan 11 20:44:20 2011
  1.55% done, estimate finish Tue Jan 11 20:44:02 2011
  1.58% done, estimate finish Tue Jan 11 20:44:49 2011
  1.61% done, estimate finish Tue Jan 11 20:44:32 2011
  1.65% done, estimate finish Tue Jan 11 20:44:15 2011
  1.68% done, estimate finish Tue Jan 11 20:43:59 2011
  1.71% done, estimate finish Tue Jan 11 20:43:43 2011
  1.74% done, estimate finish Tue Jan 11 20:44:26 2011
  1.77% done, estimate finish Tue Jan 11 20:44:11 2011
  1.80% done, estimate finish Tue Jan 11 20:43:56 2011
  1.84% done, estimate finish Tue Jan 11 20:43:41 2011
  1.87% done, estimate finish Tue Jan 11 20:43:28 2011
  1.90% done, estimate finish Tue Jan 11 20:43:14 2011
  1.93% done, estimate finish Tue Jan 11 20:43:53 2011
  1.96% done, estimate finish Tue Jan 11 20:43:40 2011
  1.99% done, estimate finish Tue Jan 11 20:43:27 2011
  2.03% done, estimate finish Tue Jan 11 20:43:14 2011
  2.06% done, estimate finish Tue Jan 11 20:43:02 2011
  2.09% done, estimate finish Tue Jan 11 20:43:38 2011

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid COD BlackOps2/2 -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-federico/k3bgL1643.tmp -rational-rock -hide-list /tmp/kde-federico/k3bJb1643.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-federico/k3bhu1643.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-federico/k3bEq1643.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid COD BlackOps2/2 -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-federico/k3bLH1643.tmp -rational-rock -hide-list /tmp/kde-federico/k3brc1643.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-federico/k3bHq1643.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-federico/k3buh1643.tmp

-----------------------------------------------------------------

Bueno espero su pronta respuesta

Muchas Gracias!

Saludos,
Federico

---

### Post by guillermolisi on 2011-01-11
> **fmalvez said:**
> 
:-[ WRITE@LBA=41a0h failed with SK=4h/TRACKING SERVO FAILURE]: Input/output error
:-( write failed: Input/output error
/dev/sr0: flushing cache
:-[ FLUSH CACHE failed with SK=4h/TRACKING SERVO FAILURE]: Input/output error
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=4h/ASC=A0h/ACQ=80h]: Input/output error

Federico
Segun el log que pasaste pareceria que la unidad esta fallando al querer posicionar el cabezal (Servo Tracking Failure) o, cosa que me parece mas dificil, que el programa este calculando una direccion fisica en el disco que la unidad no puede lograr (al posicionar el cabezal), como si estuviera fuera de rango fisico.

Digo que me parece muy dificil que sea la ultima alternativa porque uso K3B desde el 2007 y las veces que tuve problemas no estaban relacionados con el programa.

Esa unidad en otra maquina, ideal si tuviese Linux, funciona bien ?
Graba CDs sin problemas ? No estaras pasado de la capacidad maxima que permite grabar el DVD ? (K3B avisa sobre esta condicion pero deja la decision al usuario).

---

### Post by fmalvez on 2011-01-12
> **guillermolisi said:**
> Esa unidad en otra maquina, ideal si tuviese Linux, funciona bien ?
Graba CDs sin problemas ? No estaras pasado de la capacidad maxima que permite grabar el DVD ? (K3B avisa sobre esta condicion pero deja la decision al usuario).

Hola guillermolisi, gracias por la rápida atención.
Te comento que actualmente tengo el disco particionado con Windows XP SP3 y por otro lado el Ubuntu 10.04 LTS. En el Windows tengo instalado el ImgBurn y pude grabar sin problemas los mismos archivos en los mismos DVD's que con el Kb3 no me dejaba, si bien solucione la necesidad de grabar los archivos sigo sin entender porque se me complica hacerlo en Ubuntu.

Saludos,
Federico

---

