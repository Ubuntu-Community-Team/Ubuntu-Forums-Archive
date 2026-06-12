---
title: "FujiXerox DocuPrint 255 (205, 305)"
date: 2009-05-01
forum: Hardware
---

### Post by computermacgyver on 2009-05-01
I have tried just about every driver I can think of for this printer with no success. All the postscript drivers print the postscript code (not the files), and the PCL drivers print random letters.

Has anyone had success with this printer (Docuprint 255) or another in the series (205 / 255 / 305)? I am running Hardy, and would happily upgrade if this will make the printer work, but I have large doubts about that and am wondering if anyone else has experience.

The URL for the Windows driver is here:
[http://download.fujixerox.co.jp/eng/docuprint/dp205series.html](http://download.fujixerox.co.jp/eng/docuprint/dp205series.html)

And when I had a windows client print a very basic textfile to a file with the driver it generated this output:
```

ESC%-12345X@PJL JOB MODE=PRINTER
@PJL SET JOBATTR="@LUNA=user"
@PJL SET OUTBIN=MAINTRAY
@PJL SET QTY=1
@PJL SET COPIES=1
@PJL SET JOBATTR="@TRCH=ON"
@PJL SET DUPLEX=OFF
@PJL SET BINDING=LONGEDGE
@PJL SET JOBATTR="@SPSE=AUTO"
@PJL SET JOBATTR="@MSIP=NORMAL"
@PJL SET RENDERMODE=GRAYSCALE
@PJL SET ECONOMODE=OFF
@PJL SET RET=ON
@PJL SET JOBATTR="@PBLK=OFF"
@PJL SET JOBATTR="@IREC=OFF"
@PJL SET JOBATTR="@TRAP=OFF"
@PJL SET JOBATTR="@IEXT=STANDARD"
@PJL SET JOBATTR="@BANR=DEVICE"
@PJL SET JOBATTR="@NLPP=1"
@PJL SET JOBATTR="@HOAD=I0A03084F"
@PJL SET JOBATTR="@JOAU=@user\SUN"
@PJL SET JOBATTR="@PODR=NORMAL"
@PJL SET JOBOFFSET=OFF
@PJL SET SLIPSHEET=OFF
@PJL SET PAPERDIRECTION=LEF
@PJL SET RESOLUTION=600
@PJL SET IMAGEADAPT=ON
@PJL SET BITSPERPIXEL=1
@PJL SET JOBATTR="@DRDM=RASTER"
@PJL SET JOBATTR="@TSCR=1"
@PJL SET JOBATTR="@GSCR=1"
@PJL SET JOBATTR="@ISCR=1"
@PJL ENTER LANGUAGE=PLW
%FXPLW-2.0.3%
%WINNT-5.1,PLWDRV-2432.1%
EA<90>FA^A^@<96>EP2"[2009,05/01,14:12:09][<96><B3><91><E8> - <83><81><83><82>
<92><A0>][10.3.8.100]"Ec^A^@^EEP^R"[100ms]StartPage"Aa=<F5><U+008F>^@^@^@^@^@^@
^@^@<BD><F5><U+008F>A9<F3><E8>DO<91>"FF^@AI^@ARAK^BAL^A^@^@^@^MAM^B^D^@^@^@DA%QDbB<96>^@^@^@^@^@^@<80>^@^@^@<U+0096>^@^@^@^@^@^@^@^@^@^@DC  ^C^B.^A^@L^@^Dq!<98>LDD^Aw^By^B^@^^^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@&^@>^@T^@e^@s^@t^@ ^@P^@r^@i^@n^@t^@ ^@T^@e^@s^@t^@ ^@P
^@r^@i^@n^@t^@ ^@T^@e^@s^@t^@ ^@P^@r^@i^@nD<A4>^X<AD>^B^@^B^@L^@L^@^F0<DA>0<FC>0<B8>DC       <88>^X<AD>^A^@^@^@^B^@(DC       <AE>^X<AD>^A^@^@^@^B^@1DC       
<D4>^X<AD>^A^@^@^@^B^@)EPESC"[110ms]EndPage of Logical"FBEDEP^\"[110ms]EndPage of Physical"EP^O"[110ms]EndJob"EBESC%-12345X@PJL COMMENT FXJOBINFO VERSION=1.0.0
@PJL COMMENT FXJOBINFO BEGIN
<B8>DC       <88>^X<AD>^A^@^@^@^B^@(DC       <AE>^X<AD>^A^@^@^@^B^@1DC       
<D4>^X<AD>^A^@^@^@^B^@)EPESC"[110ms]EndPage of Logical"FBEDEP^\"[110ms]EndPage of Physical"EP^O"[110ms]EndJob"EBESC%-12345X@PJL COMMENT FXJOBINFO VERSION=1.0.0
@PJL COMMENT FXJOBINFO BEGIN
@PJL COMMENT FXJOBINFO PDLTYPE=PDL[ARTEX]:VERSION[2.0.3]
@PJL COMMENT FXJOBINFO JOBTYPE=PRINT
@PJL COMMENT FXJOBINFO STOREDJOBTYPE=IMMEDIATE
@PJL COMMENT FXJOBINFO JOBCOPIES=1
@PJL COMMENT FXJOBINFO PAGECOPIES=1
@PJL COMMENT FXJOBINFO DUPLEXTYPE=SIMPLEX
@PJL COMMENT FXJOBINFO NUP=1
@PJL COMMENT FXJOBINFO POSTER=1
@PJL COMMENT FXJOBINFO BOOKLETTYPE=TYPE[NOBOOKLET]
@PJL COMMENT FXJOBINFO PAGEORDER=1TON
@PJL COMMENT FXJOBINFO SLIPSHEET=NOSLIPSHEET
@PJL COMMENT FXJOBINFO TONERSAVE=OFF
@PJL COMMENT FXJOBINFO PHYSICALPAGES=1
@PJL COMMENT FXJOBINFO LOGICALPAGES=1
@PJL COMMENT FXJOBINFO PAGEINFOBEGIN
@PJL COMMENT FXJOBINFO PAGEINFO=SIZE[210.0X297.0]:MODE[MONOCHROME]:INTRAY[0]
@PJL COMMENT FXJOBINFO PAGEINFOEND
@PJL COMMENT FXJOBINFO END
@PJL EOJ

```

It's definitely not postscript code, but it also doesn't seem to be PCL. Any ideas?

Many thanks,
Scott

---

### Post by comeez on 2009-07-20
I know this may come a bit late but I have the same printer here working. I use Generic Printer PCL5e Driver + CUPS. It works fine on both hardy and jaunty.

---

