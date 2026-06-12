---
title: "does slmodem driver support conexant modem?"
date: 2009-02-26
forum: Hardware
---

### Post by kaos_frack on 2009-02-26
Is my modem supported by the slmodem package?

```

# lspci | grep -i modem
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)

```

First I don't know whether it is an intel or conexant modem.
Many people say that the only supported driver is the one at linuxant.com but I've found many people with the same modem (or at least with the same "lspci | grep -i modem" output) who managed to get their modems working with the smart link driver.
I'm totally confused. I'm getting the famous No Dialtone error. Well it could be due to various reasons, but for now I just would like to know whether it's supported by slmodem or not, so that I can confidently continue to work on this.

To sum up:
1. Is that Intel or Conexant modem?
2. Does slmodem work with it?
3. Has anyone with the same modem had success with it using slmodem?

I would very very grateful to get answers to these questions and I think this would very very helpful for many newcomers.

Here's the links that say slmodem works:
[http://megawiki.org/wiki/MSIMegaBookM510cFedora4](http://megawiki.org/wiki/MSIMegaBookM510cFedora4)
[http://www.gentoo-wiki.info/Gateway_450XL](http://www.gentoo-wiki.info/Gateway_450XL)
[http://tuxmobil.org/samsung_q30_jamie_linux.html](http://tuxmobil.org/samsung_q30_jamie_linux.html)
[https://wiki.ubuntu.com/LaptopTestingTeam/CompalCL56](https://wiki.ubuntu.com/LaptopTestingTeam/CompalCL56)
[http://forums.gentoo.org/viewtopic-p-2910612.html#2910612](http://forums.gentoo.org/viewtopic-p-2910612.html#2910612)
[http://armin.emx.at/vaio_vgn-t2xp/](http://armin.emx.at/vaio_vgn-t2xp/)
[http://209.85.229.132/search?q=cache:4ciO78NTARoJ:www.zethost.org/zblog/%3Fpage_id%3D64+slmodem+%2200:1f.6+Modem:+Intel+Corporation+82801DB/DBL/DBM+(ICH4/ICH4-L/ICH4-M)+AC%2797+Modem+Controller%22&amp;hl=en&amp;ct=clnk&amp;cd=9&amp;client=opera](http://209.85.229.132/search?q=cache:4ciO78NTARoJ:www.zethost.org/zblog/%3Fpage_id%3D64+slmodem+%2200:1f.6+Modem:+Intel+Corporation+82801DB/DBL/DBM+(ICH4/ICH4-L/ICH4-M)+AC%2797+Modem+Controller%22&amp;hl=en&amp;ct=clnk&amp;cd=9&amp;client=opera)
[http://www.gentoo-wiki.info/Acer_TravelMate_4050](http://www.gentoo-wiki.info/Acer_TravelMate_4050)
[http://www.kcore.org/?menumain=4&amp;menusub=1](http://www.kcore.org/?menumain=4&amp;menusub=1)
[http://foomagic.org/wiki/index.php/R40](http://foomagic.org/wiki/index.php/R40)
[http://oasis.dit.upm.es/~jantonio/personal/aspire1410/](http://oasis.dit.upm.es/~jantonio/personal/aspire1410/)
[http://www.freewebs.com/duckzland/r100fc5.html](http://www.freewebs.com/duckzland/r100fc5.html)
[http://spikeypillow.com/category/1/blogid/1](http://spikeypillow.com/category/1/blogid/1)
[http://www.sctree-it.com/component/content/article/50-intel-winmodem-thinkpad-t41-on-ubuntu-804.html](http://www.sctree-it.com/component/content/article/50-intel-winmodem-thinkpad-t41-on-ubuntu-804.html)
[http://tm290.tuxfamily.org/#Winmodem](http://tm290.tuxfamily.org/#Winmodem)
[http://translate.google.com/translate?hl=en&amp;sl=de&amp;u=http://wiki.ubuntuusers.de/SmartLink&amp;ei=eEedSfe4EeTSjAfjpNW-BQ&amp;sa=X&amp;oi=translate&amp;resnum=1&amp;ct=result&amp;prev=/search%3Fq%3Dslmodem%2B%252200:1f.6%2BModem:%2BIntel%2BCorporation%2B82801DB/DBL/DBM%2B(ICH4/ICH4-L/ICH4-M)%2BAC%252797%2BModem%2BController%2522%26start%3D40%26hl%3Den%26client%3Dopera%26rls%3Den%26sa%3DN](http://translate.google.com/translate?hl=en&amp;sl=de&amp;u=http://wiki.ubuntuusers.de/SmartLink&amp;ei=eEedSfe4EeTSjAfjpNW-BQ&amp;sa=X&amp;oi=translate&amp;resnum=1&amp;ct=result&amp;prev=/search%3Fq%3Dslmodem%2B%252200:1f.6%2BModem:%2BIntel%2BCorporation%2B82801DB/DBL/DBM%2B(ICH4/ICH4-L/ICH4-M)%2BAC%252797%2BModem%2BController%2522%26start%3D40%26hl%3Den%26client%3Dopera%26rls%3Den%26sa%3DN)
[http://translate.google.com/translate?hl=en&amp;sl=pl&amp;u=http://www.best4linux.net/pokaz.php%3Fid_recenzji%3D2&amp;ei=eEedSfe4EeTSjAfjpNW-BQ&amp;sa=X&amp;oi=translate&amp;resnum=7&amp;ct=result&amp;prev=/search%3Fq%3Dslmodem%2B%252200:1f.6%2BModem:%2BIntel%2BCorporation%2B82801DB/DBL/DBM%2B(ICH4/ICH4-L/ICH4-M)%2BAC%252797%2BModem%2BController%2522%26start%3D40%26hl%3Den%26client%3Dopera%26rls%3Den%26sa%3DN](http://translate.google.com/translate?hl=en&amp;sl=pl&amp;u=http://www.best4linux.net/pokaz.php%3Fid_recenzji%3D2&amp;ei=eEedSfe4EeTSjAfjpNW-BQ&amp;sa=X&amp;oi=translate&amp;resnum=7&amp;ct=result&amp;prev=/search%3Fq%3Dslmodem%2B%252200:1f.6%2BModem:%2BIntel%2BCorporation%2B82801DB/DBL/DBM%2B(ICH4/ICH4-L/ICH4-M)%2BAC%252797%2BModem%2BController%2522%26start%3D40%26hl%3Den%26client%3Dopera%26rls%3Den%26sa%3DN)
[http://duany2k.blogspot.com/2006/02/configuring-laptop-modem.html](http://duany2k.blogspot.com/2006/02/configuring-laptop-modem.html)

Thanks in advance!

---

