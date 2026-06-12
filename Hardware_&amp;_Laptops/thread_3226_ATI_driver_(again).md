---
title: "ATI driver (again)"
date: 2004-11-04
forum: Hardware &amp; Laptops
---

### Post by fmou on 2004-11-04
Hi,
Does anyone know if the ATi radeon mobility U1 (320 IGP) graphic card is supported by the fglrxdriver?
Thanks for any reply.
F

---

### Post by fng on 2004-11-04
he's a pain in the ass, isn't he :)
I've been also trying to get it working with the flgrx driver on a friends notebook.

I found a nice thread on the gentoo forums, but it involves the radeon driver, compiling your own kernel and patching X.org server.
[http://forums.gentoo.org/viewtopic.php?t=238541&highlight=compaq+envo+ati+driver](http://forums.gentoo.org/viewtopic.php?t=238541&highlight=compaq+envo+ati+driver)
[http://forums.gentoo.org/viewtopic.php?t=206675&highlight=envo+ati+driver](http://forums.gentoo.org/viewtopic.php?t=206675&highlight=envo+ati+driver)

---

### Post by wallijonn on 2004-11-05
FireGL8700/8800: Driver for chipset: 
        ATI RV250 Id (R9000),
	ATI RV250 Ie (R9000), ATI RV250 If (R9000), ATI RV250 Ig (R9000),
	ATI RV250 Ld (M9), ATI RV250 Le (M9), ATI RV250 Lf (M9),
	ATI RV250 Lg (M9), ATI RV280 5960 (R9200 PRO),
	ATI RV280 Ya (R9200LE), ATI RV250SE Yd (R9200SE),
	ATI RV250 5C61 (M9+), ATI RV250 5C63 (M9+), ATI R200 QH (R8500),
	ATI R200 QL (R8500), ATI R200 QM (R9100), ATI R200 QT (R8500),
	ATI R200 QU (R9100), ATI R200 BB (R8500), ATI RV350 AP (R9600),
	ATI RV350SE AQ (R9600SE), ATI RV350 AR (R9600 PRO),
	ATI RV350 NP (M10), ATI R300 AD (R9500), ATI R300 AE (R9500),
	ATI R300 AF (R9500), ATI R300 AG (Fire GL Z1/X1),
	ATI R300 ND (R9700 PRO), ATI R300 NE (R9700/R9500 PRO),
	ATI R300 NF (R9600 TX), ATI R300 NG (Fire GL X1),
	ATI R350SE AH (R9800SE), ATI R350 AK (Fire GL unknown),
	ATI RV350 AS (Fire GL T2), ATI RV350 AT (Fire GL T2),
	ATI RV350 AU (Fire GL T2), ATI RV350 AV (Fire GL T2),
	ATI RV350 AW (Fire GL T2), ATI R350 NH (R9800),
	ATI R350LE NI (R9800LE), ATI R350 NJ (R9800),
	ATI R350 NK (Fire GL X2), ATI RV350 NT (WS/M10), ATI R420 JH,
	ATI R420 JI, ATI R420 JJ, ATI R420 JK, ATI R420 JL, ATI R420 JM,
	ATI R420 JN, ATI R420 JP, ATI RS300 IGP, ATI RS350 IGP

If you see:
ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon 9200PRO 5960 (AGP), ATI Radeon 9200 5961 (AGP),
	ATI Radeon 9200 5962 (AGP), ATI Radeon 9200SE 5964 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP), ATI Radeon Mobility 9600 (M10) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2 (M11) NV (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP)

then chances are that you're trying to use the ATI web drivers and not the Debian SPM supplied drivers.

---

### Post by Slovak on 2004-11-05
[QUOTE=fmou]Hi,
Does anyone know if the ATi radeon mobility U1 (320 IGP) graphic card is supported by the fglrxdriver?
Thanks for any reply.
F[/QUOTE]
No, there is no native linux support for that, if you want it you need SUSE9.1 pro's custom ATI drivers made for their custom kernel. In other words you need SUSE if you want that ATI working.

---

### Post by daniels on 2004-11-06
[QUOTE=Slovak]No, there is no native linux support for that, if you want it you need SUSE9.1 pro's custom ATI drivers made for their custom kernel. In other words you need SUSE if you want that ATI working.[/QUOTE]
No, you don't.  It works fine with standard Ubuntu.

---

### Post by trukulo on 2004-11-12
I have a laptop with IGP 320M with ubuntu (warty), everything works well except 3D acceleration, even tvout is working perfectly.

I use xine and totem-xine to see movies, and i don't have any problem.

So yes, IGP 320M it's ubuntu supported out-of-the-box (without 3D).

---

### Post by gravious on 2004-12-16
[QUOTE=fmou]Hi,
Does anyone know if the ATi radeon mobility U1 (320 IGP) graphic card is supported by the fglrxdriver?
Thanks for any reply.
F[/QUOTE]

Yes. I know. It doesn't, damn it.
(at least I'm nearly sure, recently I tried it on Gentoo and it didn't autodetect my U1 (320 IGP) and my card wasn't on a subsequent list of supported card it displayed.)

---

### Post by telmo on 2004-12-31
[QUOTE=daniels]No, you don't.  It works fine with standard Ubuntu.[/QUOTE]

Do you mean with 3D? 
Because my ATI Mobility Radeon 9600 works fine in Ubuntu, but with NO 3D support!

---

### Post by jocko96b on 2006-04-19
I have a Radeon 200m and I can't even install - goes through several motions of initial boot, then just a blank screen.  How can I at least get ubuntu installed, then start playing with the particulars?

---

