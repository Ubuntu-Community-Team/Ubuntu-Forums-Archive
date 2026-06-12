---
title: "full command line in text readable mode please???"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-04-17
hey guys,

I need to have the output of the command

> sudo info coreutil

into a .txt or .doc or any text format to have it read later and learn from it. Can anyone help me please. I am not acquainted with "info" command so i don't know how to output it to a text document. 

somebody recommended this

> info --subnodes -O info.txt core

which i did and got an endless info.txt file with this

> &#26984;&#24931;&#27756;&#8313;&#25971;&#30051;&#25970;&#28704;&#25971;&#25717;&#29295;&#28257;&#28516;&#8301;&#30062;&#25197;&#29285;&#26400;&#28261;&#29285;&#29793;&#29295;&#2606;&#8202;†&#12128;&#25956;&#12150;&#29301;&#28257;&#28516;&#10093;&#29472;&#26229;&#26982;&#25955;&#8307;&#28518;&#8306;&#28525;&#29811;&#28704;&#24946;&#29795;&#25449;&#27745;&#29984;&#25971;&#11379;&#25120;&#29813;&#24864;&#28784;&#26988;&#24931;&#26996;&#28271;&#2675;&#25970;&#30065;&#29289;&#28265;&#8295;&#26984;&#26727;&#30253;&#27745;&#25973;&#28448;&#8306;&#28524;&#26478;&#29741;&#29285;&#8301;&#29296;&#29807;&#25445;&#26996;&#28271;&#28448;&#8294;&#29296;&#30313;&#29793;&#8293;&#24932;&#24948;&#27936;&#31073;&#29194;&#29029;&#26997;&#25970;&#24864;&#8302;&#27745;&#25972;&#28274;&#29793;&#8293;&#24932;&#24948;&#29472;&#30063;&#25458;&#8293;&#26988;&#25963;&#24608;&#25647;&#30309;&#29231;&#28257;&#28516;&#10093;&#28448;&#8306;&#12128;&#25956;&#12150;&#29281;&#28257;&#28516;&#10093;&#2606;&#26708;&#8293;&#25971;&#8308;&#26223;&#24864;&#24950;&#27753;&#25185;&#25964;&#29472;&#30063;&#25458;&#29541;&#25632;&#28773;&#28261;&#29540;&#28448;&#8302;&#28537;&#29301;&#28448;&#25968;&#24946;&#26996;&#26478;&#29472;&#29561;&#25972;&#11885;&#2570;†&#21536;&#8303;&#29557;&#8293;&#30067;&#26723;&#24864;&#29472;&#30063;&#25458;&#11365;&#29472;&#25968;&#26979;&#31078;&#29728;&#25960;&#24608;&#11565;&#24946;&#25710;&#28015;&#29485;&#30063;&#25458;&#15717;&#18758;&#17740;&#8231;&#28783;&#26996;&#28271;&#2604;&#11877;&#11879;&#8236;&#29536;&#30056;&#8294;&#11565;&#24946;&#25710;&#28015;&#29485;&#30063;&#25458;&#15717;&#25647;&#30309;&#29231;&#28257;&#28516;&#10093;*&#21536;&#25960;&#25376;&#28271;&#25972;&#29806;&#8307;&#26223;&#17952;&#19529;&#8261;&#26739;&#30063;&#25708;&#25098;&#8293;&#29537;&#29216;&#28257;&#28516;&#8301;&#29537;&#28704;&#29551;&#26995;&#27746;&#11877;†&#28225;&#25888;&#29298;&#29295;&#26912;&#8307;&#25970;&#28528;&#29810;&#25701;&#26912;&#8294;&#18758;&#17740;&#25632;&#25967;&#8307;&#28526;&#2676;&#28515;&#29806;&#26977;&#8302;&#28261;&#30063;&#26727;&#25120;&#29817;&#29541;&#29728;&#8303;&#24946;&#25710;&#28015;&#31337;&#8293;&#26740;&#8293;&#28265;&#30064;&#8308;&#25697;&#29029;&#24949;&#25972;&#31084;&#2606;&#8202;†&#28500;&#29216;&#28773;&#28530;&#30052;&#25955;&#29728;&#25960;&#29216;&#29541;&#27765;&#29556;&#28448;&#8294;&#28257;&#25888;&#29281;&#26988;&#29285;&#26912;&#30318;&#25455;&#29793;&#28521;&#8302;&#26223;&#24864;&#25376;&#28015;&#24941;&#25710;&#8236;&#28537;&#2677;&#24931;&#8302;&#24947;&#25974;&#29472;&#28015;&#8293;&#24946;&#25710;&#28015;&#25632;&#29793;&#8289;&#28265;&#28532;&#24864;&#26144;&#27753;&#8293;&#28257;&#8292;&#26740;&#28261;&#29984;&#25971;&#29728;&#24936;&#8308;&#26982;&#25964;&#24864;&#8307;&#26740;&#2661;&#24946;&#25710;&#28015;&#29472;&#30063;&#25458;&#8293;&#28265;&#25888;&#29281;&#26988;&#29285;&#24864;&#25710;&#27680;&#29793;&#29285;&#26912;&#30318;&#25455;&#29793;&#28521;&#29550;&#28448;&#8294;&#26740;&#8293;&#28515;&#28013;&#28257;&#11876;&#2570;†&#21280;&#28015;&#8293;&#27759;&#11620;&#24934;&#26739;&#28521;&#25966;&#8292;&#29295;&#29472;&#29300;&#28777;&#25968;&#11620;&#28516;&#28279;&#28448;&#25968;&#24946;&#26996;&#26478;&#29472;&#29561;&#25972;&#29549;&#27680;&#25441;&#8299;&#30067;

Stuff like this is all i got, a huge endless info.txt file. 
Any help??? 
Anything wrong??? 

Please explain for dummy, hehe

---

### Post by Tim Sharitt on 2009-04-17
You can try

```
zcat /usr/share/info/coreutils.info.gz >coreutils
```

It will have the package information printed at the top, so it's pretty, but past that is all the information contained in the info page.

---

### Post by Will4 on 2009-04-17
can anyone send me the full command line for Ubuntu, (debian)... 'cuz i can't get /usr/share/info/coreutils.info.gz output to a text document!! 

any idea how to manage the "info" command to output all the info to a .txt ???

Thanx in advance..

[email]william.wh23@gmail.com[/email]

---

### Post by Will4 on 2009-04-17
i don't get it!! Sorry.

where does the zcat command send the text to?? dir?? file???

---

### Post by Tim Sharitt on 2009-04-17
> **Will4 said:**
> i don't get it!! Sorry.

where does the zcat command send the text to?? dir?? file???

The command I gave you will create a file called coreutils in your current working directory.

If I wanted the file to be called coreutils-info and placed in my ~/Documents directory, the command would be

```
zcat /usr/share/info/coreutils.info.gz >~/Documents/coreutils-info
```

---

### Post by Will4 on 2009-04-17
the same Chinese characters in the whole document!! 

any idea?? Thank you so much for your help!! 

Any clue on how to have it readable??

---

### Post by Tim Sharitt on 2009-04-17
Just so it's clear, what do you see when you enter

```
info coreutils
```

---

### Post by Pettman on 2009-04-17
I'd use redirection to get a textfile. This can be done typing the following into a terminal:```
info coreutils > name_of_file
```Where name_of_file is the desired name of the output file. To learn more about redirection and other useful things use: ```
man bash
```

---

### Post by Will4 on 2009-04-21
hey guys, I did 
> 
info coreutils
and of course i get the whole thing in English but my point is. IS there any way i can output it to a text document out of coreutils, in order to keep it in a flash drive for example???

I did 

> info coreutils > (name_of_file) 

and still got these chinese words all over. aushhshh!! what a mess!!

---

