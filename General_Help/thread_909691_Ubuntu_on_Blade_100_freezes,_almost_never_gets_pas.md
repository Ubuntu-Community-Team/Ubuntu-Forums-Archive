---
title: "Ubuntu on Blade 100 freezes, almost never gets past boot"
date: 2008-09-03
forum: General Help
---

### Post by huffandy@hotmail.com on 2008-09-03
Hi, 

I am having problems with the boot.  Actually not just just that, it freezes booting from the install cd (having redo the install several times).  Freezes when booting when doing rescue, etc.  

I updated the PROM to the latest version also.

If anyone can help me, I would greatly appreciate it!  Thanks.

Oh, and its Ubuntu 7.10 also.

Andrew

---

### Post by cjawcrusher512 on 2008-09-09
What is a ball mill and how does it function?[http://wiki.answers.com/Q/What_is_a_ball_mill_and_how_does_it_function](http://wiki.answers.com/Q/What_is_a_ball_mill_and_how_does_it_function)

---

### Post by cjawcrusher512 on 2008-09-09
[[size=2][color=#006699]How to buy a ball mill with quality at reasonable price in China  ?[/color][/size]](http://answers.yahoo.com/question/index?qid=20080826203448AAVEOrl)

---

### Post by tahirdar on 2008-09-09
Try installing Ubuntu 7.10 server edition first, then once installed do

sudo apt-get install xubuntu-desktop

One other thing use the onboard graphics card, take out any Expert3D etc. from the system before you install.

---

### Post by huffandy@hotmail.com on 2008-09-10
Hi, I did originally install 7.10 Server first, and then did 

sudo aptitude install xubuntu-desktop

but things get a little wild after the SILO prompt, even while trying to run from the CD at boot time, many times, I am lucky to finish the install processes to do this.  The problems occur when the white screen flashes back to the black linux screen, and the freeze can occur randomly. (almost whenever it feels like it.)

Thanks,
Andrew

---

### Post by wowbuts5 on 2008-09-14
WoW  [wow gold](http://veryge.com/) in our special discounting zone of US servers is the most cheapest [world of warcraft gold](http://veryge.com/) in the world. On our 'buy now' page, you can buy wow gold of this special zone.And you will get gold within 5 minutes after ordered. Please click our "Fast gold order form" on the left hand . [ffxi gil](http://veryge.com/) Fast delivery within 5 minutes,7*24 services.

---

### Post by tahirdar on 2008-09-22
Can you see the UBUNTU spash screen when booting? And are you using the onboard ATI graphics adapter. If so try booting into rescue mode and edit /etc/X11/xorg.conf

sudo vi /etc/X11/xorg.conf

Then add the following text in Device section of frame buffer:

Option          "reference_clock"       "28.636 MHz"

---

### Post by huffandy@hotmail.com on 2008-09-23
Thanks tahidar,

I'm just realizing this to be a video card issue, (yeah, onboard dosen't cut it).  I scoured for another post and it was a little confusing, Will a ATI Radeon card work or does it have to be Sun "certified?"

Thanks in advance.

---

### Post by tahirdar on 2008-09-23
I guess any PCI graphic card should work, no need for Sun certification as you are using Ubuntu not Solaris.

---

### Post by huffandy@hotmail.com on 2008-09-23
Thanks for all your help, (although I think fixing this machine is costing me more than what it is worth!) :)

---

### Post by Hosting24hour on 2008-09-26
These all graphic system working here to support your task

---

### Post by 080818jk on 2008-10-30
[**&#38500;&#23576;&#35774;&#22791;**](http://www.hbjzcc.com.cn)&#20844;&#21496;&#22320;&#29702;&#20301;&#32622;&#20248;&#36234;&#65292;&#19996;&#38752;104&#22269;&#36947;&#65292;&#35199;&#37066;06&#22269;&#36947;&#65292;&#21344;&#22320;&#38754;&#31215;50000&#24179;&#31859;&#65292;&#24314;&#31569;&#38754;&#31215; 12000&#24179;&#31859;&#65292;&#22266;&#23450;&#36164;&#20135;2000&#19975;&#20803;&#65292;&#32844;&#24037;360&#20154;&#65292;&#25216;&#26415;&#24037;&#31243;&#20154;&#21592;30&#20154;&#65292;&#39640;&#32423;&#25216;&#26415;&#20154;&#21592;15&#20154;&#65292;&#24180;&#20135;&#37327;5000&#21544;&#20844;&#21496;&#20973;&#20511; &#30528;&#24378;&#22823;&#30340;&#32508;&#21512;&#23454;&#21147;&#12289;&#36807;&#30828;&#30340;&#20135;&#21697;&#36136;&#37327;&#36194;&#24471;&#20102;&#20840;&#22269;&#21508;&#22320;&#26032;&#32769;&#29992;&#25143;&#30340;&#25903;&#25345;&#19982;&#20449;&#36182;&#12290;[**&#38500;&#23576;&#22120;**](http://www.hbjzcc.com.cn)&#20844;&#21496;&#20135;&#21697;&#20998;&#20026;&#20845;&#22823;&#31867;&#31995;&#21015;&#65306;&#30005;&#38500;&#23576;&#31995;&#21015;&#12289;&#34955;&#24335;&#38500;&#23576;&#35774;&#22791;&#31995;&#21015;&#12289;&#26059;&#39118;&#38500;&#23576;&#22120;&#31995;&#21015;&#12289;&#28287;&#24335;&#38500;&#23576;&#22120;&#31995;&#21015;&#12289;&#38500;&#23576;&#22120;&#31995;&#21015;&#65292;&#37197;&#20214;&#20135;&#21697;&#12289;&#36755;&#36865;&#35774;&#22791;&#31995;&#21015;&#65292;&#20063;&#21487;&#26681;&#25454;&#29992;&#25143;&#38656;&#35201;&#36827;&#34892;&#38750;&#26631;&#35774;&#35745;&#21450;&#25913;&#36896;&#23433;&#35013;&#12290;[**&#38500;&#23576;&#22120;**](http://www.hbjzcc.com.cn/index.html)&#20844;&#21496;&#25317;&#26377;150&#20154;&#30340;&#23433;&#35013;&#35843;&#35797;&#38431;&#20237;&#65292;&#21487;&#25215;&#25597;&#22823;&#22411;&#29615;&#20445;&#31995;&#32479;&#30340;&#35774;&#22791;&#23433;&#35013;&#21450;&#35843;&#35797;&#12290;&#12288;**&#12288;**[**&#38500;&#23576;&#22120;**](http://www.hbjzcc.com.cn/index.html)&#20844;&#21496;&#23447;&#26088;&#65306;&#20135;&#21697;&#36136;&#37327;&#31532;&#19968;&#12289;&#20449;&#35465;&#33267;&#19978;&#21407;&#21017;&#65292;&#20197;&#26032;&#30340;&#26426;&#21046;&#12289;&#26032;&#30340;&#36215;&#28857;&#12289;&#32487;&#32493;&#33268;&#21147;&#20110;&#29615;&#22659;&#24037;&#31243;&#12289;&#29615;&#20445;&#35774;&#22791;&#30340;&#30740;&#31350;&#21644;&#24320;&#21457;&#65292;&#21162;&#21147;&#25552;&#39640;&#33258;&#36523;&#32032;&#36136;&#65292;&#22686;&#24378;&#24066;&#22330;&#31454;&#20105;&#21147;&#65292;&#22312;&#29615;&#20445;&#34892;&#19994;&#20013;&#31435;&#20110;&#19981;&#36133;&#20043;&#22320;&#12290;  &#12288;&#12288;&#33891;&#20107;&#38271;&#25658;&#20840;&#20307;&#21592;&#24037;&#30495;&#35802;&#26399;&#24453;&#25658;&#25163;&#19982;&#24744;&#21512;&#20316;&#65292;[**&#38500;&#23576;&#22120;**](http://www.hbjzcc.com.cn/index.html)&#20026;&#25105;&#22269;&#29615;&#20445;&#20107;&#19994;&#20316;&#20986;&#20010;&#22823;&#30340;&#36129;&#29486;&#65292;&#20026;&#25105;&#20204;&#30340;&#26126;&#22825;&#22859;&#26007;&#12290;

---

### Post by qrst472 on 2008-11-03
The real evils, indeed, of [wow gold](http://www.wowpowerleveling-wow.com/) Emma's situation were the power of having rather too much her own way, and a disposition to think a little [wow gold](http://www.wow-wowpowerleveling.com/) too well of herself; these were the disadvantages which threatened alloy to her many enjoyments. The danger, however, was at [wow power leveling](http://www.powerleveling-wowgold.com/wow-power-leveling.html) present so unperceived, that they did not by any means rank as misfortunes with her. Sorrow came--a gentle sorrow--but not at all in the shape of any disagreeable consciousness.--Miss Taylor married. It was Miss Taylor's loss which first brought grief. It was on the [wow powerleveling](http://www.wow-wowpowerleveling.com/) wedding-day of this beloved friend that Emma first sat in mournful thought of any continuance. The wedding over, and the bride-people gone, her father and herself were left to dine together, with no prospect of a third to cheer a long evening. Her father composed himself to sleep after dinner, as usual, and she had then only to sit and think of what she had lost.weiwei1978123

---

