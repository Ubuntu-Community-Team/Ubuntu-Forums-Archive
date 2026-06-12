---
title: "no PC rtc found"
date: 2008-11-13
forum: General Help
---

### Post by kaoticsnow on 2008-11-13
Hello!,
   I am attempting to install Ubuntu 6.06 on an old Sunblade 100 but after booting to the CD I receive the following error

> [   76.880374] rtc_init: no PC rtc found

I have no idea what this error message means or how to troubleshoot this issue, I have searched but all other instances of this error seam to be when installing a 2nd hard disk I have one blank disk I want to install Ubuntu on.

---

### Post by Delta_Farce on 2008-11-13
Hi,

Try a full cold boot (turn the machine off completely for 20 secs) and then install using the parameter:

```
ok> SILO> Linux ide=nodma
```

If that solves you're problem, you'll need to add the same string to the silo.conf file to allow the machine to boot post install:

[Editing Silo to boot post install]("http://ubuntuforums.org/showpost.php?p=1402761&postcount=1")

It might also be worth upgrading the OBP to the latest Sun Firmware for the machine too. Have a search through the forum if you get stuck as there's lots of info on installing 6.06 on Sunblade 100's and 150's.

---

### Post by 081105jk on 2008-11-16
&#12289;[**&#26469;&#30005;&#36890;&#30693;&#30418;**](http://www.rp-cti.com/Chinese/224.html)&#32500;&#25252;&#37327;&#26497;&#23567;&#65292;[**&#24405;&#38899;&#20202;**](http://www.rp-cti.com/Chinese/411.html)&#23458;&#25143;&#29992;&#24471;&#30465;&#24515;&#12289;&#25918;&#24515;&#12290;&#20351;&#29992;&#28070;&#26222;&#30005;&#35805;[**&#24405;&#38899;&#31649;&#29702;**](http://www.rp-cti.com/Chinese/404.html)&#31995;&#32479;&#30340;&#22909;&#22788;&#65306; &#25919;&#24220;&#37096;&#38376;----&#25552;&#21319;&#25919;&#24220;&#24418;&#35937;&#65292;&#21327;&#21516;&#21150;&#20844;&#65292;[**&#24405;&#38899;&#20202;**](http://www.rp-cti.com/Chinese/411.html)&#20943;&#36731;&#20154;&#21592;&#24037;&#20316;&#24378;&#24230;&#65307;&#25253;&#35686;&#30005;&#35805;----[**&#24405;&#38899;&#30418;**](http://www.rp-cti.com/Chinese/289.html)&#35821;&#38899;&#35760;&#24405;&#65292;&#26377;&#25454;&#21487;&#26597;&#65307;

---

### Post by lyjg1113 on 2008-11-18
&#21271;&#20140;[**?k?C**](http://www.shunfengbj.cn/) &#26381;&#21153;&#33539;&#22260;    &#21271;&#20140;[**?k?C**](http://www.shunfengbj.cn/) &#39034;&#39118;&#20449;&#24687;&#21672;&#35810;&#26377;&#38480;&#20844;&#21496;&#25552;&#20379;&#33829;&#19994;&#25191;&#29031;&#12289;&#26410;&#23130;&#12289;&#32467;&#23130;&#35777;&#12289;&#20934;&#29983;&#12289;&#29983;&#32946;&#12289;&#20986;&#29983;&#12289;&#32467;&#25166;&#35777;&#12289;&#30005;&#28938;&#24037;&#25216;&#26415;&#31561;&#32423;&#35777;&#12289;&#39550;&#39542;[**?k?C**](http://www.shunfengbj.cn/) &#12289;&#21449;&#36710;[**?k?C**](http://www.shunfengbj.cn/) &#12289;&#38130;&#36710;[**?k?C**](http://www.shunfengbj.cn/) &#12289;&#36864;&#20237;&#21150;&#35777;&#12289;&#24037;&#31243;&#24072;&#12289;&#21416;&#24072;&#36164;&#26684;

---

### Post by LRTIMKEN on 2008-12-30
You wrote's nice and I support you![FAG](http://www.fag0.cn) [fag](http://www.fag0.cn) [FAG](http://www.fag0.cn) [fag](http://www.fag0.cn)

---

