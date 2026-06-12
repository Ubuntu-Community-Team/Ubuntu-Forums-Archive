---
title: "fonts in open office - breezy"
date: 2005-11-27
forum: General Help
---

### Post by slava on 2005-11-27
I am having troubles displaying a russian doc in open office 1 and 2 on breezy. i have russian lang support packages installed: 
language-pack-ru 
language-pack-gnome-ru 
language-support-ru
openoffice.org2-help-ru
openoffice.org2-l10n-ru

screenshot of what i see when i open the file and the file itself are attached to this message. not sure what to do.. thanks for help 
slava

---

### Post by kovu-cat on 2005-11-27
maybe the russian language pack of openoffice is missing.

the next line shows the following packages as result:

  $ apt-cache search openoffice |grep ru

  openoffice.org2-help-ru - Russian help for OpenOffice.org
  openoffice.org2-l10n-be-by - Belarussian language package for OpenOffice.org
  openoffice.org2-l10n-ru - Russian language package for OpenOffice.org
  openoffice.org-l10n-ru - Russian language package for OpenOffice.org
  language-pack-gnome-ru-base - GNOME translations for language Russian
  language-pack-ru-base - translations for language Russian
  language-support-ru - metapackage for Russian language support

and some more packages.

kovu

---

### Post by slava on 2005-11-29
thanks for the post. it seems i already have openoffice support packages installed 

```
dpkg -l openoffice.org2* | grep ru
ii  openoffice.org2-help-ru            1.9.129-0.1ubuntu5 Russian help for OpenOffice.org
un  openoffice.org2-help-ru-1.9.129    <none>             (no description available)
ii  openoffice.org2-l10n-ru            1.9.129-0.1ubuntu3 Russian language package for OpenOffice.org
un  openoffice.org2-thesaurus          <none>             (no description available)
un  openoffice.org2-thesaurus-en-us    <none>             (no description available)
un  openoffice.org2-thesaurus-ru       <none>             (no description available)
$ sudo apt-get install openoffice.org2-thesaurus-ru
Reading package lists... Done
Building dependency tree... Done
Package openoffice.org2-thesaurus-ru is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openoffice.org2-thesaurus-ru has no installation candidate
```

---

### Post by slava on 2005-12-12
help please :) i don't know what else to try..

---

### Post by esperantisto on 2005-12-12
&#1057;&#1083;&#1072;&#1074;&#1072;, &#1086;&#1087;&#1080;&#1096;&#1080; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1091; &#1087;&#1086;&#1087;&#1086;&#1076;&#1088;&#1086;&#1073;&#1085;&#1077;&#1077;: &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1099; &#1074; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1093; &#1074; &#1092;&#1086;&#1088;&#1084;&#1072;&#1090;&#1077; &#1089;&#1072;&#1084;&#1086;&#1075;&#1086; OOo &#1080;&#1083;&#1080; &#1074; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1093; MS Word?

---

### Post by esperantisto on 2005-12-12
&#1042; &#1086;&#1073;&#1097;&#1077;&#1084;, &#1085;&#1072;&#1089;&#1082;&#1086;&#1083;&#1100;&#1082;&#1086; &#1103; &#1087;&#1086;&#1085;&#1080;&#1084;&#1072;&#1102;, &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1072; &#1080;&#1084;&#1077;&#1085;&#1085;&#1086; &#1089; &#1074;&#1086;&#1088;&#1076;&#1086;&#1074;&#1089;&#1082;&#1080;&#1084; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1086;&#1084;. &#1069;&#1090;&#1086; &#1087;&#1088;&#1086;&#1080;&#1089;&#1093;&#1086;&#1076;&#1080;&#1090;, &#1074; &#1086;&#1089;&#1085;&#1086;&#1074;&#1085;&#1086;&#1084;, &#1074; &#1076;&#1086;&#1082;&#1072;&#1093; &#1074;&#1086;&#1088;&#1076;&#1072; &#1076;&#1086; 97 &#1074;&#1077;&#1088;&#1089;&#1080;&#1080; (&#1080; &#1072;&#1085;&#1072;&#1083;&#1086;&#1075;&#1080;&#1095;&#1085;&#1099;&#1093; &#1101;&#1082;&#1089;&#1077;&#1083;&#1072;) &#1080;&#1079;-&#1079;&#1072; &#1090;&#1086;&#1075;&#1086;, &#1095;&#1090;&#1086; &#1090;&#1072;&#1084; &#1085;&#1077;&#1074;&#1077;&#1088;&#1085;&#1086; &#1091;&#1082;&#1072;&#1079;&#1072;&#1085; &#1103;&#1079;&#1099;&#1082; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;. &#1051;&#1077;&#1095;&#1080;&#1090;&#1089;&#1103; &#1089; &#1087;&#1086;&#1084;&#1086;&#1097;&#1100;&#1102; &#1074;&#1086;&#1090; &#1101;&#1090;&#1080;&#1093; &#1076;&#1074;&#1091;&#1093; &#1084;&#1072;&#1082;&#1088;&#1086;&#1089;&#1086;&#1074; (&#1086;&#1076;&#1080;&#1085; &#1076;&#1083;&#1103; writer, &#1076;&#1088;&#1091;&#1075;&#1086;&#1081; &#1076;&#1083;&#1103; calc &#8212; &#1076;&#1086;&#1075;&#1072;&#1076;&#1072;&#1081;&#1089;&#1103; &#1089;&#1072;&#1084; :-))
```
REM  *****  Recode from cp1252 to cp1251 for Word and Excel files without language set.
REM  *****  Authors Dmitry G. Mastrukov and A. Novodroskii 2002, code corrercted by Dmitri Gabinski
REM  ***** GPL license


Dim mCP1252(123) As String
Dim mCP1251(123) As String

Sub Init
mCP1252() = Array("&#8364;","&#8218;","¸","&#8222;","&#8230;","&#8224;","&#8225;","&#710;","&#8240;","&#352;","&#8249;","&#338;","&#381;", _
  					"&#8216;","&#8217;","&#8220;","&#8221;","&#8226;","&#8211;","&#8212;","&#8482;","&#353;","&#8250;","&#339;","¡","&#382;", _
  					"&#376;","*","¡","¢","£","¤","¥","¦","§","¨","©","ª","«", _
  					"¬","*","®","¯","°","±","²","³","´","µ","¶","·","¸", _
  					"¹","º","»","¼","½","¾","¿","À","Á","Â","Ã","Ä","Å", _
  					"Æ","Ç","È","É","Ê","Ë","Ì","Í","Î","Ï","Ð","Ñ","Ò", _
  					"Ó","Ô","Õ","Ö","×","Ø","Ù","Ú","Û","Ü","Ý","Þ","ß", _
  					"à","á","â","ã","ä","å","æ","ç","è","é","ê","ë","ì", _
  					"í","î","ï","ð","ñ","ò","ó","ô","õ","ö","÷","ø","ù", _
  					"ú","û","ü","ý","þ","ÿ")
mCP1251() = Array("&#1026;","&#8218;","&#1105;","&#8222;","&#8230;","&#8224;","&#8225;","&#8364;","&#8240;","&#1033;","&#8249;","&#1034;","&#1035;", _
  					"&#8216;","&#8217;","&#8220;","&#8221;","&#8226;","&#8211;","&#8212;","&#8482;","&#1113;","&#8250;","&#1114;","&#1116;","&#1115;", _
  					"&#1119;","*","&#1038;","&#1118;","&#1032;","¤","&#1168;","¦","§","&#1025;","©","&#1028;","«", _
  					"¬","*","®","&#1031;","°","±","&#1030;","&#1110;","&#1169;","µ","¶","·","&#1105;", _
  					"&#8470;","&#1108;","»","&#1112;","&#1029;","&#1109;","&#1111;","&#1040;","&#1041;","&#1042;","&#1043;","&#1044;","&#1045;", _
  					"&#1046;","&#1047;","&#1048;","&#1049;","&#1050;","&#1051;","&#1052;","&#1053;","&#1054;","&#1055;","&#1056;","&#1057;","&#1058;", _
  					"&#1059;","&#1060;","&#1061;","&#1062;","&#1063;","&#1064;","&#1065;","&#1066;","&#1067;","&#1068;","&#1069;","&#1070;","&#1071;", _
  					"&#1072;","&#1073;","&#1074;","&#1075;","&#1076;","&#1077;","&#1078;","&#1079;","&#1080;","&#1081;","&#1082;","&#1083;","&#1084;", _
  					"&#1085;","&#1086;","&#1087;","&#1088;","&#1089;","&#1090;","&#1091;","&#1092;","&#1093;","&#1094;","&#1095;","&#1096;","&#1097;", _
  					"&#1098;","&#1099;","&#1100;","&#1101;","&#1102;","&#1103;")
End Sub

Sub RecodeAllWriter
  Dim n As Long
  Dim oDocument As Object
  Dim oReplace As Object
  Init()	
  oDocument = ThisComponent
  oReplace = oDocument.createReplaceDescriptor
  For n = lbound(mCP1252()) To ubound(mCP1252())
    oReplace.SearchString = mCP1252(n)
    oReplace.ReplaceString = mCP1251(n)
    oReplace.SearchCaseSensitive = TRUE
    oDocument.replaceAll(oReplace)
   Next n
  MsgBox "&#1055;&#1088;&#1077;&#1086;&#1073;&#1088;&#1072;&#1079;&#1086;&#1074;&#1072;&#1085;&#1086;"
End Sub

Sub RecodeAllCalc
  Dim n As Long
  Dim m As Long
  Dim oDocument As Object
  Dim oReplace As Object
  Init()	
  On error goto ex
  oDocument = ThisComponent
  m = 0
  While 1 = 1 
  oReplace = oDocument.Sheets(m).createReplaceDescriptor
  For n = lbound(mCP1252()) To ubound(mCP1252())
    oReplace.SearchString = mCP1252(n)
    oReplace.ReplaceString = mCP1251(n)
    oReplace.SearchCaseSensitive = TRUE
    oDocument.Sheets(m).replaceAll(oReplace)
  Next n
  m = m + 1
  Wend
  ex:
  MsgBox "&#1055;&#1088;&#1077;&#1086;&#1073;&#1088;&#1072;&#1079;&#1086;&#1074;&#1072;&#1085;&#1086;"
End Sub
```

&#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1096;&#1100; &#1076;&#1086;&#1082;&#1091;, &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072;&#1077;&#1096;&#1100; &#1084;&#1072;&#1082;&#1088;&#1086;&#1089;. &#1042;&#1089;&#1105;. &#1050;&#1072;&#1078;&#1077;&#1090;&#1089;&#1103;, &#1086;&#1076;&#1085;&#1091; &#1073;&#1091;&#1082;&#1074;&#1091; &#1087;&#1088;&#1077;&#1086;&#1073;&#1088;&#1072;&#1079;&#1091;&#1077;&#1090; &#1085;&#1077;&#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1100;&#1085;&#1086;, &#1085;&#1086; &#1085;&#1077; &#1087;&#1086;&#1084;&#1085;&#1102;, &#1082;&#1072;&#1082;&#1091;&#1102;.

---

### Post by slava on 2005-12-17
to esperantisto:
&#1041;&#1086;&#1083;&#1100;&#1096;&#1086;&#1077; &#1089;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;, &#1101;&#1090;&#1086; &#1087;&#1086;&#1084;&#1086;&#1075;&#1083;&#1086; :)

---

