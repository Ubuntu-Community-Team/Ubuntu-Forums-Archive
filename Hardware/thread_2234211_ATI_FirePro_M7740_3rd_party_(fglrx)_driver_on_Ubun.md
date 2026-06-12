---
title: "ATI FirePro M7740 3rd party (fglrx) driver on Ubuntu"
date: 2014-07-13
forum: Hardware
---

### Post by ozanerdemb on 2014-07-13
Hi All,

I'm using Ubuntu 13.04 on Dell Precision 6500 Notebook with ATI FirePro M7740 graphic card.

The actual driver, [AMD] nee ATI RV740/M97 GL [FirePro M7740], is working well even though it is NOT sufficient to run decent games.
By decent, I mean even aging games demanding some 3D effect.

I searched on this forum as well as on the internet to find out the proprieatry (fglrx) Catalyst driver which would work fine for my graphic card. On:

[LIST=1]
[*]AMD/ATI's official site (support.amd.com/en-us/download), when I choose Notebook Graphics, Mobility FirePro Series, Dell Precision M6500 (FirePro M7740 Mobility), only Windows System drivers are shown :( 
[*]This forum, there is a post dated 24/12/2009 without any answer about the proprietary working drivers 
[*]The internet (Google), it's written on some forums that the old Catalyst Drivers should work (e.g. fglrx v8.91.4 or firepro_8.982.2_linux_x32x64_143295), however:
[LIST]
[*]it's also written that these driver have, general installation/compatibility problems and they are buggy (do you have any experience?) 
[*]there is no written/posted evidence that these drivers support FirePro M7740 (does any of use use M7740 with fglrx?) 
[/LIST]
      
[/LIST]
  
As an unlucky guy who bought a laptop without knowing that ADM/ATI drivers were problematic to be installed (especially for old graphic cards), I'd like to know if one of you, as a ubuntu warrior/expert, would be able to help me please (I know; it'd be better to search in advance before buying it)?

PS: I also installed Windows for this graphic card performance issue... I finally posted this message because whenever I searched for an answer, I found contradictory posts but no clear answer. If resolved, this thread will absolutely help to other Ubuntu users (on M6500 laptops) as well.

---

### Post by Mark Phelps on 2014-07-13
Sorry, but the closest HD series to that card is the 4x series -- and AMD dropped Linux support for that series last summer.  The latest Ubuntu version that would work with fglrx drivers for that card is 12.04.1.  The only working drivers for newer Ubuntu versions are the default Radeon drivers -- which you have already installed and working.

---

### Post by Yellow Pasque on 2014-07-13
Ubuntu 13.04 is EOL. You would get better performance with 14.04: [http://www.phoronix.com/scan.php?page=article&item=amd_legacy_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_legacy_ubuntu1404&num=1)

---

