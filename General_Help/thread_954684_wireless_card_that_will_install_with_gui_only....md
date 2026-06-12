---
title: "wireless card that will install with gui only..."
date: 2008-10-21
forum: General Help
---

### Post by kenley on 2008-10-21
no command line.
i have installed wubi on a laptop.  works great.  except wireless.  is there a wireless pc card or usb that will install and load drivers with gui only?  no need for command line involvement.  the 2 wireless adapters have frustrated me trying to get them to work that i am willing to buy one that has gui instructions how to install and set up.

i know that there are lists of wireless cards that have worked for some people.  and there are procedures that have worked for some people.  i would like a wireless card that will work from use with gui only.

if the use of command line to install stuff is eliminated that would be great.  i am not as intuitive as i once was.

Kenley

---

### Post by ago on 2008-10-21
There is no such thing as a network card driver installer. In linux things either are supported, in which case there is nothing to install, and the card will show up, or not supported. In the latter case, hope is not lost as you might still have some luck by using ndiswrapper which can reuse the windows drivers in linux. You can use ndisgtk as a GUI frontend for ndiswrapper to fetch the appropriate drivers. 

In any case use 8.10 as that has the most updated drivers and wider compatibility. [http://wubi-installer.org/devel/minefield/Wubi-8.10-rev513.exe](http://wubi-installer.org/devel/minefield/Wubi-8.10-rev513.exe)

So in short:

1) Try 8.10 and check whether your cards are "visible"
2) If the above does not work, install and try ndisgtk (plug in an ethernet cable to simplify the installation)
3) If the above does not work, buy a network card that is known to work well with linux.

In 8.10 click on the top right network icon to configure your network settings. As for the terminal is not generally required these days, but it more CONVENIENT than a GUI, so you are quite likely to stumble over it again and again even if not strictly necessary. For instance, to install ndisgtk I could tell you to go into the system menu, then admin, then synaptic, then searching for ndisgtk, then checking the box, then clicking ok.... OR I could tell you to type: "sudo apt-get install ndisgtk". Which one is simpler?

---

### Post by ago on 2008-10-21
There is no such thing as a network card driver installer. In linux things either are supported, in which case there is nothing to install, and the card will show up, or not supported. In the latter case, hope is not lost as you might still have some luck by using ndiswrapper which can reuse the windows drivers in linux. You can use ndisgtk as a GUI frontend for ndiswrapper to fetch the appropriate drivers. 

In any case use 8.10 as that has the most updated drivers and wider compatibility. [http://wubi-installer.org/devel/minefield/Wubi-8.10-rev513.exe](http://wubi-installer.org/devel/minefield/Wubi-8.10-rev513.exe)

So in short:

1) Try 8.10 and check whether your cards are "visible"
2) If the above does not work, install and try ndisgtk (plug in an ethernet cable to simplify the installation)
3) If the above does not work, buy a network card that is known to work well with linux.

In 8.10 click on the top right network icon to configure your network settings. As for the terminal is not generally required these days, but it more CONVENIENT than a GUI, so you are quite likely to stumble over it again and again even if not strictly necessary. For instance, to install ndisgtk I could tell you to go into the system menu, then admin, then synaptic, then searching for ndisgtk, then checking the box, then clicking ok.... OR I could tell you to type: "sudo apt-get install ndisgtk". Which one is simpler?

---

### Post by sethvath on 2008-10-21
This is how ndisgtk looks, is this the gui you're looking for?

---

### Post by ghij712 on 2008-10-21
&#21407;&#26412;&#20197;&#20026;&#21487;&#20197;&#30041;&#20303;&#32511;&#33394;&#65292;&#30041;&#20303;&#28201;&#26262;&#12290;&#20294;&#26159;&#65292;&#19981;&#30693;&#35273;&#20043;&#20013;&#65292;&#22312;&#25105;&#25970;&#20987;&#38190;&#30424;&#30340;&#26102;&#20505;&#65292;&#25163;&#20919;&#20102;&#65292;&#25165;&#21457;&#29616;&#20908;&#24050;&#32463;&#24456;&#28145;&#20102;!  &#21448;&#26159;&#23506;&#20919;&#30340;&#23395;&#33410;&#12290;&#22235;&#24029;&#19996;&#37096;&#30340;&#20908;&#22825;&#26159;&#24178;&#23506;&#12289;&#24178;&#23506;&#30340;&#65292;&#19981;&#19979;&#38632;&#65292;&#19981;&#39128;&#38634;&#65292;&#34892;&#36208;&#22312;&#22823;&#34903;&#19978;&#25226;&#22260;&#24062;&#25166;&#30340;&#29282;&#29282;&#23454;&#23454;&#30340;&#65292;&#25163;&#25571;&#22312;&#21253;&#37324;&#65292;&#21702;&#21990;&#30528;&#22312;&#20154;&#27969;&#20013;&#28508;&#34892;&#12290;&#20840;&#19990;&#30028;&#21482;&#21097;&#19979;&#19968;&#31181;&#24863;&#35273;-----&#20919;&#12290;&#22825;&#20919;&#24515;&#26356;&#21152;&#20919;!  &#26641;&#26525;&#19978;&#36824;&#25671;&#26355;&#30528;&#37027;&#20123;&#26410;&#22312;&#31179;&#22825;&#25481;&#23613;&#30340;&#26543;&#21494;&#65292;&#23567;&#27827;&#37324;&#27700;&#24555;&#35201;&#26543;&#20102;&#12290;&#30707;&#25329;&#26725;&#23569;&#20102;&#32511;&#33394;&#30340;&#38506;&#34924;&#65292;&#27827;&#33609;&#20063;&#22240;&#20026;&#27700;&#30340;&#26543;&#31469;&#32823;&#28937;&#22312;&#27827;&#22564;&#19978;&#12290;&#26366;&#32463;&#38506;&#20276;&#25105;&#24230;&#36807;&#23401;&#25552;&#26102;&#20809;&#19968;&#30452;&#35748;&#20026;&#26368;&#32654;&#20029;&#30340;&#26223;&#33394;&#65292;&#31455;&#21464;&#24471;&#22914;&#27492;&#27169;&#26679;&#12290;&#31449;&#22312;&#30707;&#25329;&#26725;&#19978;&#65292;&#31070;&#20260;&#40687;&#28982;&#22914;&#21516;&#21320;&#30561;&#21518;&#37027;&#31181;&#26406;&#32999;&#30340;&#31354;&#31354;&#30340;&#33853;&#23518;&#12290;&#19978;&#28023;&#35774;&#22791;&#21378;&#38144;&#21806;[&#33261;&#27687;&#32769;&#21270;&#35797;&#39564;&#31665;](http://shebei.blog.ccidnet.com/),[&#27673;&#28783;&#32784;&#27668;&#20505;&#35797;&#39564;&#31665;](http://shebei.blog.ccidnet.com/),[&#39640;&#20302;&#28201;&#28287;&#28909;&#35797;&#39564;&#31665;](http://shebei.blog.ccidnet.com/),[&#32043;&#22806;&#28783;&#32784;&#27668;&#20505;&#35797;&#39564;&#31665;](http://shebei.blog.ccidnet.com/),[&#28888;&#31665;](http://shebei.blog.ccidnet.com/)&#31561;&#35774;&#22791;&#12290;&#35760;&#24471;&#26377;&#19968;&#20010;&#25991;&#23398;&#23478;&#35828;&#36807;&#65306;&#35835;&#19968;&#21477;&#35805;&#65292;&#26377;&#21315;&#19975;&#30340;&#24863;&#35302;&#30340;&#26102;&#20505;&#65292;&#36825;&#21477;&#35805;&#23601;&#26159;&#21453;&#26144;&#20182;&#30340;&#24515;&#24577;.&#21516;&#26679;&#65292;&#25105;&#20197;&#20026;&#30475;&#26223;&#33394;&#20063;&#26159;&#65307;&#27934;&#24713;&#19990;&#30028;&#19975;&#29289;&#20134;&#28982;&#12290;&#36825;&#20123;&#26085;&#23376;&#20197;&#26469;&#21457;&#29983;&#30340;&#20107;&#65292;&#35753;&#25105;&#35273;&#24471;&#19990;&#30028;&#21464;&#20102;&#39068;&#33394;&#12290;&#26366;&#32463;&#19968;&#30452;&#24188;&#31258;&#30340;&#35748;&#20026;&#65292;&#24444;&#27492;&#20449;&#20219;&#65292;&#23601;&#33021;&#27704;&#36828;&#30340;&#20445;&#30041;&#25105;&#20204;&#24444;&#27492;&#24515;&#20013;&#30340;&#24773;&#24875;&#65292;&#21487;&#20197;&#30041;&#30340;&#20303;&#26366;&#32463;&#35768;&#19979;&#30340;&#28023;&#35475;&#23665;&#30431;&#12290;&#23545;&#26041;&#30340;&#31361;&#28982;&#32972;&#21467;&#21364;&#35753;&#25105;&#20260;&#24576;&#12290;&#29992;&#30524;&#27882;&#22830;&#27714;&#12289;&#24680;&#12289;&#20877;&#27425;&#22830;&#27714;&#20351;&#22905;&#21487;&#20197;&#22238;&#24515;&#36716;&#24847;&#12290;&#25105;&#29992;&#23613;&#19968;&#20999;&#26041;&#27861;&#21435;&#20445;&#30041;&#37027;&#20221;&#24515;&#37324;&#26080;&#27861;&#26367;&#20195;&#30340;&#33394;&#24425;,&#26368;&#21518;&#21364;&#24466;&#21171;&#26080;&#21151;&#12290;&#20170;&#22825;&#25105;&#32456;&#20110;&#26126;&#30333;&#65292;&#32511;&#33394;&#30041;&#19981;&#20303;,&#28201;&#26262;&#30041;&#19981;&#20303;&#12290;&#20908;,&#22987;&#32456;&#37117;&#26159;&#35201;&#26469;&#30340;&#12290;&#26126;&#24180;&#26149;&#22825;&#65292;&#26641;&#26525;&#20877;&#20986;&#26032;&#21494;&#65292;&#32511;&#20877;&#20063;&#19981;&#26159;&#37027;&#29255;&#32511;&#65292;&#21487;&#33021;&#26525;&#20250;&#20026;&#27492;&#40687;&#28982;&#19968;&#29983;&#12290;&#21487;&#26159;&#30475;&#39118;&#26223;&#30340;&#20154;&#65292;&#35841;&#20250;&#22312;&#20046;&#26159;&#21542;&#26366;&#32463;&#30340;&#37027;&#29255;&#21602;?  &#22320;&#29699;&#20877;&#27425;&#36716;&#20837;&#22826;&#38451;&#36817;&#36712;&#30340;&#26102;&#20505;&#65292;&#20154;&#20204;&#33073;&#21435;&#21402;&#21402;&#30340;&#22841;&#34915;&#65292;&#22312;&#26149;&#26085;&#37324;&#23433;&#19968;&#25226;&#26885;&#23376;&#20139;&#21463;&#21644;&#29030;&#38451;&#20809;&#30340;&#26102;&#20505;&#65292;&#35841;&#20250;&#22312;&#20046;&#37027;&#20123;&#28201;&#26262;&#26159;&#19981;&#26159;&#26366;&#32463;&#30340;&#37027;&#20123;&#30340;&#21602;?  &#34429;&#28982;"&#26366;&#32463;&#27815;&#28023;&#38590;&#20026;&#27700;"&#65292;&#20294;&#20439;&#20154;&#30475;&#39118;&#26223;&#30340;&#26102;&#20505;&#65292;&#19981;&#20250;&#21435;&#36776;&#21035;&#20170;&#24180;&#30340;&#32511;&#19982;&#21435;&#24180;&#30340;&#32511;&#26377;&#20160;&#20040;&#19981;&#21516;&#12290;&#23545;&#20110;&#20182;&#20204;&#26469;&#35828;&#65292;&#20219;&#20309;&#19968;&#29255;&#37117;&#19968;&#26679;&#12290;&#25105;&#20204;&#37117;&#26159;&#20439;&#20154;&#12290; &#25152;&#20197;,&#25105;&#20204;&#30340;&#19968;&#20999;&#19981;&#38590;&#20813;&#33853;&#19968;&#20010;&#20439;&#22871;&#30340;&#32467;&#23616;&#65292;&#23569;&#28857;&#25379;&#25166;&#65292;&#23569;&#28857;&#30171;&#33510;&#12290;&#25152;&#20197;&#65292;&#26159;&#19981;&#26159;&#26366;&#32463;&#30340;&#37027;&#29255;&#32511;,&#24182;&#19981;&#37325;&#35201;&#12290;

---

