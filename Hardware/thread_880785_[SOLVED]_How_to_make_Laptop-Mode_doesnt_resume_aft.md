---
title: "[SOLVED] How to make Laptop-Mode doesnt resume after suspend"
date: 2008-08-05
forum: Hardware
---

### Post by AbtZ on 2008-08-05
I would like to create a script similar to what is suggested in this [thread]("http://bbs.archlinux.org/viewtopic.php?pid=402532").

Does anyone know what it should look like, and where I should put it?

To address excessive load cycling I followed the guide on the [Ubuntu Wiki]("https://wiki.ubuntu.com/PowerManagement#head-ab94c99627b86e9fbb29a09d3316178269c3e764").

---

### Post by AbtZ on 2008-08-11
Well, that's what you get for posting when you really should be sleeping. The thread title is stupid and totally misleading; the "doesnt" shouldn't be in it.

In any case, I managed to solve the problem myself. I created a script ```
sudo gedit /etc/pm/sleep.d/10laptopmoderestart
``` 

with the code

```
#!/bin/bash
case $1 in
    hibernate)
        /etc/init.d/laptop-mode stop
        ;;
    suspend)
        /etc/init.d/laptop-mode stop
        ;;
    thaw)
        /etc/init.d/laptop-mode start
        ;;
    resume)
        /etc/init.d/laptop-mode start
        ;;
    *)
        echo Something is not right.
        ;;
esac
```

Then I made it executable with
```
sudo chmod +x /etc/pm/sleep.d/10laptopmoderestart
```

Done! laptop mode works as intended, and restarts after resuming from suspend/hibernate :D

---

### Post by kaurman on 2008-09-17
Hi!

I don't know much about writing scripts. Could someone explain what is the purpose of "case $1" and "esac" in this script? 

Kaur

---

### Post by AbtZ on 2008-09-17
It is a way to avoid nested "if" statements. "case" is the beginning of such a switch, "esac" signifies its end.

For more info: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_03.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_03.html)

---

### Post by kaurman on 2008-09-18
Hi!

Ok, thanks for the information.

K

---

### Post by salsa95 on 2008-11-09
Nope.  Thanks for the tip, but on my HP laptop, this does not work...

---

### Post by AbtZ on 2008-11-10
I did this on Hardy. Maybe it works differently in Intrepid?

---

### Post by 081103jk on 2008-11-10
&#27599;&#20010;&#20225;&#19994;&#32593;&#31449;&#22343;&#21487;&#20197;&#25317;&#26377;&#33258;&#24049;&#30340;&#36164;&#28304;&#65292;&#36825;&#31181;&#36164;&#28304;&#21487;&#20197;&#34920;&#29616;&#20026;&#19968;&#23450;&#30340;&#35775;&#38382;&#37327;&#12289;&#27880;&#20876;&#29992;&#25143;&#20449;&#24687;&#12289;&#26377;&#20215;&#20540;&#30340;&#20869;&#23481;&#21644;&#21151;&#33021;&#12289;&#32593;&#32476;&#24191;&#21578;&#31354;&#38388;&#31561;&#65292;&#21033;&#29992;&#32593;&#31449;&#30340;&#36164;&#28304;&#19982;&#21512;&#20316;&#20249;&#20276;&#24320;&#23637;&#21512;&#20316;&#65292;&#23454;&#29616;&#36164;&#28304;&#20849;&#20139;&#65292;&#20849;&#21516;&#25193;&#22823;&#25910;&#30410;&#30340;&#30446;&#30340;&#12290;&#22312;&#36825;&#20123;&#36164;&#28304;&#21512;&#20316;&#24418;&#24335;&#20013;&#65292;&#20132;&#25442;&#38142;&#25509;&#26159;&#26368;&#31616;&#21333;&#30340;&#19968;&#31181;&#21512;&#20316;&#26041;&#24335;&#65292;&#35843;&#26597;&#34920;&#26126;&#20063;&#26159;&#26032;[**google&#25512;&#24191;**](http://www.jkw.name/googletuiguang.htm)&#30340;&#26377;&#25928;&#26041;&#24335;&#20043;&#19968;&#12290;&#20132;&#25442;&#38142;&#25509;&#25110;&#31216;&#20114;&#24800;&#38142;&#25509;&#65292;&#26159;&#20855;&#26377;&#19968;&#23450;&#20114;&#34917;&#20248;&#21183;&#30340;&#32593;&#31449;&#20043;&#38388;&#30340;&#31616;&#21333;&#21512;&#20316;&#24418;&#24335;&#65292;&#21363;&#20998;&#21035;&#22312;&#33258;&#24049;&#30340;&#32593;&#31449;&#19978;&#25918;&#32622;&#23545;&#26041;&#32593;&#31449;&#30340;LOGO&#25110;&#32593;&#31449;&#21517;&#31216;&#24182;&#35774;&#32622;&#23545;&#26041;&#32593;&#31449;&#30340;&#36229;&#32423;&#38142;&#25509;&#65292;&#20351;&#24471;&#29992;&#25143;&#21487;&#20197;&#20174;&#21512;&#20316;&#32593;&#31449;&#20013;&#21457;&#29616;&#33258;&#24049;&#30340;&#32593;&#31449;&#65292;&#36798;&#21040;&#20114;&#30456;&#25512;&#24191;&#30340;&#30446;&#12290;&#20132;&#25442;&#38142;&#25509;&#30340;&#20316;&#29992;&#20027;&#35201;&#34920;&#29616;&#22312;&#20960;&#20010;&#26041;&#38754;&#65306;&#33719;&#24471;&#35775;&#38382;&#37327;&#12289;&#22686;&#21152;&#29992;&#25143;&#27983;&#35272;&#26102;&#30340;&#21360;&#35937;&#12289;&#22312;[**google&#25512;&#24191;**](http://www.jkw.name/googletuiguang.htm)&#20013;&#22686;&#21152;&#20248;&#21183;&#12289;&#36890;&#36807;&#21512;&#20316;&#32593;&#31449;&#30340;&#25512;&#33616;&#22686;&#21152;&#35775;&#38382;&#32773;&#30340;&#21487;&#20449;&#24230;&#31561;&#12290;&#20132;&#25442;&#38142;&#25509;&#36824;&#26377;&#27604;&#26159;&#21542;&#21487;&#20197;&#21462;&#24471;&#30452;&#25509;&#25928;&#26524;&#26356;&#28145;&#19968;&#23618;&#30340;&#24847;&#20041;&#65292;&#19968;&#33324;&#26469;&#35828;&#65292;&#27599;&#20010;&#32593;&#31449;&#37117;&#20542;&#21521;&#20110;&#38142;&#25509;&#20215;&#20540;&#39640;&#30340;&#20854;&#20182;&#32593;&#31449;&#65292;&#22240;&#27492;&#33719;&#24471;&#20854;&#20182;&#32593;&#31449;&#30340;&#38142;&#25509;&#20063;&#23601;&#24847;&#21619;&#30528;&#33719;&#24471;&#20102;&#20110;&#21512;&#20316;&#20249;&#20276;&#21644;&#19968;&#20010;&#39046;&#22495;&#20869;&#21516;&#31867;&#32593;&#31449;&#30340;&#35748;&#21487;&#12290;

---

### Post by kaurman on 2008-11-10
shouldn't there be a - in the filename? Like this 10-laptopmoderestart.

---

### Post by AbtZ on 2008-11-10
Don't think it matters. The numbers in the names are just to make the scripts execute in a certain order.

---

### Post by kaurman on 2008-11-10
[quote="AbtZ"]Don't think it matters. The numbers in the names are just to make the scripts execute in a certain order. [/quote]

I know, but I thought that maybe the system gets confused if the number isn't separated in any way. You're probably right though, that it doesn't matter.

---

