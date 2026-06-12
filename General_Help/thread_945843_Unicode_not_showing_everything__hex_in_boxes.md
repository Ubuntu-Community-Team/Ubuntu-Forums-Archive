---
title: "Unicode not showing everything / hex in boxes"
date: 2008-10-12
forum: General Help
---

### Post by Exakun on 2008-10-12
I've always been bothered by the fact that I'm using UTF-8 Unicode, the supposed "everything" encoding, but all the time I see boxes where characters should be (example: &#5031; looks like a box with 1 3/A 7 in it in Firefox, or just an empty box in Amarok).

I've tried installing every kind of TTF I could find in the Ubuntu repos, but that didn't seem to change anything (I wasn't too hopeful about that approach). Is there any way to make these characters appear properly? Much thanks in advance.

---

### Post by Band B on 2009-06-03
I know it's more than a year ago, but it has a high pagerank, so i found it.

Anyway: the solution
```
sudo apt-get install unifont
```
If you are planning the read/write a lot in an other language it's better the install a specific font, though.

> Complex fonts (such as Indic or Semitic scripts, where letters change shape depending on their position in a word, or such as Mongolian, which is written vertically) will not render perfectly. The philosophy behind this font, though, is that anything meaningful is better than an empty box for a unknown glyph.

---

### Post by brallan on 2009-07-20
wow, thanks bandB, that's something I've been wondering about for years, especially when the language names in wikipedia didn't render properly:

  * Afrikaans     * Alemannisch     * &#4768;&#4635;&#4653;&#4763;     * Anglo-Saxon     * &#1575;&#1604;&#1593;&#1585;&#1576;&#1610;&#1577;     * Aragonés     * &#1808;&#1834;&#1825;&#1821;&#1808;     * Armãneashce     * Arpetan     * Asturianu     * Az&#601;rbaycan     * &#2476;&#2494;&#2434;&#2482;&#2494;     * Bân-lâm-gú     * &#1041;&#1072;&#1096;&#1185;&#1086;&#1088;&#1090;     * &#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103;     * &#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103; (&#1090;&#1072;&#1088;&#1072;&#1096;&#1082;&#1077;&#1074;&#1110;&#1094;&#1072;)     * Bikol Central     * Boarisch     * Bosanski     * Brezhoneg     * &#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1089;&#1082;&#1080;     * Català     * &#1063;&#1233;&#1074;&#1072;&#1096;&#1083;&#1072;     * Cebuano     * &#268;esky     * Chavacano de Zamboanga     * Corsu     * Cymraeg     * Dansk     * Deitsch     * Deutsch     * Dolnoserbski     * Eesti     * &#917;&#955;&#955;&#951;&#957;&#953;&#954;&#940;     * Español     * Esperanto     * Euskara     * &#1601;&#1575;&#1585;&#1587;&#1740;     * Fiji Hindi     * Føroyskt     * Français     * Frysk     * Gaeilge     * Gaelg     * Gàidhlig     * Galego     * &#36123;&#35486;     * &#2711;&#2753;&#2716;&#2736;&#2750;&#2724;&#2752;     * &#54620;&#44397;&#50612;     * Hawai`i     * &#1344;&#1377;&#1397;&#1381;&#1408;&#1381;&#1398;     * &#2361;&#2367;&#2344;&#2381;&#2342;&#2368;     * Hrvatski     * Ido     * Bahasa Indonesia     * Interlingua     * &#1048;&#1088;&#1086;&#1085;&#1072;&#1091;     * Íslenska     * Italiano     * &#1506;&#1489;&#1512;&#1497;&#1514;     * Basa Jawa     * &#3221;&#3240;&#3277;&#3240;&#3233;     * &#4325;&#4304;&#4320;&#4311;&#4323;&#4314;&#4312;     * Kernewek     * Kiswahili     * &#1050;&#1086;&#1084;&#1080;     * Kreyòl ayisyen     * Kurdî / &#1603;&#1608;&#1585;&#1583;&#1740;     * Latina     * Latvie&#353;u     * Lëtzebuergesch     * Lietuvi&#371;     * Líguru     * Limburgs     * Lingála     * Lumbaart     * Magyar     * &#1052;&#1072;&#1082;&#1077;&#1076;&#1086;&#1085;&#1089;&#1082;&#1080;     * &#3374;&#3378;&#3375;&#3390;&#3379;&#3330;     * &#2350;&#2352;&#2366;&#2336;&#2368;     * &#1605;&#1589;&#1585;&#1609;     * Bahasa Melayu     * &#1052;&#1086;&#1085;&#1075;&#1086;&#1083;     * &#4121;&#4156;&#4116;&#4154;&#4121;&#4140;&#4120;&#4140;&#4126;&#4140;     * N&#257;huatl     * Nederlands     * Nedersaksisch     * &#2344;&#2375;&#2346;&#2366;&#2354;&#2368;     * &#2344;&#2375;&#2346;&#2366;&#2354; &#2349;&#2366;&#2359;&#2366;     * &#26085;&#26412;&#35486;     * &#8234;Norsk (bokmål)&#8236;     * &#8234;Norsk (nynorsk)&#8236;     * Nouormand     * Novial     * Occitan     * O'zbek     * Piemontèis     * Tok Pisin     * Plattdüütsch     * Polski     * Português     * Q&#305;r&#305;mtatarca     * Român&#259;     * Rumantsch     * Runa Simi     * &#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;     * &#1057;&#1072;&#1093;&#1072; &#1090;&#1099;&#1083;&#1072;     * Sámegiella     * Sardu     * Scots     * Seeltersk     * Shqip     * Sicilianu     * Simple English     * Sloven&#269;ina     * &#1057;&#1083;&#1086;&#1074;&#1123;&#769;&#1085;&#1100;&#1089;&#1082;&#1098; / &#11284;&#11278;&#11281;&#11266;&#11297;&#11280;&#11296;&#11284;&#11277;&#11295;     * Sloven&#353;&#269;ina     * &#346;l&#367;nski     * Soomaaliga     * &#1057;&#1088;&#1087;&#1089;&#1082;&#1080; / Srpski     * Srpskohrvatski / &#1057;&#1088;&#1087;&#1089;&#1082;&#1086;&#1093;&#1088;&#1074;&#1072;&#1090;&#1089;&#1082;&#1080;     * Suomi     * Svenska     * Tagalog     * &#2980;&#2990;&#3007;&#2996;&#3021;     * Taqbaylit     * Tatarça/&#1058;&#1072;&#1090;&#1072;&#1088;&#1095;&#1072;     * &#3108;&#3142;&#3122;&#3137;&#3095;&#3137;     * Tetun     * &#3652;&#3607;&#3618;     * &#1058;&#1086;&#1207;&#1080;&#1082;&#1251;     * Türkçe     * &#1059;&#1082;&#1088;&#1072;&#1111;&#1085;&#1089;&#1100;&#1082;&#1072;     * &#1575;&#1585;&#1583;&#1608;     * Uyghurche&#8206; / &#1574;&#1735;&#1610;&#1594;&#1735;&#1585;&#1670;&#1749;     * Vèneto     * Ti&#7871;ng Vi&#7879;t     * Volapük     * Võro     * &#25991;&#35328;     * West-Vlams     * Winaray     * Wolof     * &#21556;&#35821;     * &#1497;&#1497;&#1460;&#1491;&#1497;&#1513;     * &#31925;&#35486;     * Zazaki     * &#381;emait&#279;&#353;ka     * &#20013;&#25991; 
    
Now they DO!

---

