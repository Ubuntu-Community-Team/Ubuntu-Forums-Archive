---
title: "Ubuntu much slower on Ultra 1 than expected"
date: 2008-08-10
forum: General Help
---

### Post by Spark19 on 2008-08-10
Oh wise people ...

Help me understand this very simple issue.

Q: Ubuntu installed on an Ultra 1 runs much slower than OpenBSD on the same machine. Whats going on?

Executing a simple command like "man ls" will scroll and fill your screen in command line mode much much faster in OpenBSD than on Ubuntu. Any ideas why? And what can be done to speed it up?

Well IMHO ubuntu is running slower. My previous experience on SparcStation10 running RedHat made me suspicious as it had seemed faster.

:confused: Any clues?

---

### Post by kerry_s on 2008-08-10
spec's?
ubuntu is not built for speed. there priority is ease of use.

---

### Post by Spark19 on 2008-08-10
The Ultra 1 is a 140Mhz, 9 Gig Scsi HDD, 256MB RAM.

Ubuntu 6.06LTS
OpenBSD 4.3

Ease of use? 

My X window installation activity on Ubuntu has taken a life of its own.

OpenBSD X window ran on the very first shot - out of the boxen/CD.

Essentially, the X window is not running coz it does not pick up any numbers after probing the address space. Maybe the issue is not with X but the kernel routines that provide the probed results.

Many of the "no clue" X failures on this forum seem to have this issue, ie no numbers on address probing. 

I could appreciate some help on this.

--

---

### Post by kerry_s on 2008-08-10
i40mhz! you have to do a custom build, no way is ubuntu going to run on that.
grab the debian net installer:
[http://cdimage.debian.org/debian-cd/4.0_r4a/sparc/iso-cd/debian-40r4a-sparc-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/sparc/iso-cd/debian-40r4a-sparc-businesscard.iso)

at the package selection uncheck everything, your going custom so you don't need any of that.

after that's all done and you reboot and the disk ejects.

log in as root

apt-get install xorg fluxbox menu

exit  <-to get out of root

log in as your user
startx

if it works, just keep building up from there. i have my doubts though, i don't think there's many, if any, modern linux that will work on 140mhz, plus it being a sparc is really going to limit your options.

there are specialized linux for low specs, but there all i386.

if bsd was working fine you might want to stick with that.

good luck.

---

### Post by ryry46d9 on 2008-10-04
> **Spark19 said:**
> The Ultra 1 is a 140Mhz, 9 Gig Scsi HDD, 256MB RAM.

Ubuntu 6.06LTS
OpenBSD 4.3

Ease of use? 

My X window installation activity on Ubuntu has taken a life of its own.

OpenBSD X window ran on the very first shot - out of the boxen/CD.

Essentially, the X window is not running coz it does not pick up any numbers after probing the address space. Maybe the issue is not with X but the kernel routines that provide the probed results.

Many of the "no clue" X failures on this forum seem to have this issue, ie no numbers on address probing. 

I could appreciate some help on this.

--

my question is  what do you want this box to do ?????  

I would recommend sticking with OpenBSD also due to the FACTS its light on RAM (seeings how you only got 256) and install  " blackbox" can be found in the ports  it super light weight granted you don't got the cool menus like Gnome or KDE has to offer,  but it will help Firefox load pages better I have a ultra2 with dual 400'z  1Gb ram 18GB 7200RPM SCA  and it screams

 todays project is a ultra10 @ 300Mhz with a gig of ram trying out ubuntu7 on it just to get a feel for Linux again on sparc since I have not tried Linux SPARC since redhat 6.4 

let me know how X works out for ya im running this box headless / keyboard but you never know when you need a back up X server:popcorn:

---

### Post by 081104jk on 2008-11-13
[**&#20013;&#22269;&#21009;&#20107;&#24459;&#24072;**](http://www.Fadalawyer.org/zgxsls.html)                        [**&#20013;&#22269;&#21009;&#20107;&#24459;&#24072;**](http://www.Fadalawyer.org/zgxsls.html)&#32593;&#19968;&#12289;&#27010;&#24565;&#21450;&#20854;&#26500;&#25104;&#35784;&#39575;&#32618;&#65292;&#26159;&#25351;&#20197;&#38750;&#27861;&#21344;&#26377;&#20026;&#30446;&#30340;&#65292;&#29992;&#34394;&#26500;&#20107;&#23454;&#25110;&#32773;&#38544;&#30610;&#30495;&#30456;&#30340;&#26041;&#27861;&#65292;&#39575;&#21462;&#25968;&#39069;&#36739;&#22823;&#30340;&#20844;&#31169;&#36130;&#29289;&#30340;&#34892;&#20026;&#12290;&#65288;&#19968;&#65289;&#23458;&#20307;&#35201;&#20214;&#26412;&#32618;&#20405;&#29359;&#30340;&#23458;&#20307;&#26159;&#20844;&#31169;&#36130;&#29289;&#25152;&#26377;&#26435;&#12290;&#26377;&#20123;&#29359;&#32618;&#27963;&#21160;&#65292;&#34429;&#28982;&#20063;&#20351;&#29992;&#26576;&#20123;&#27450;&#39575;&#25163;&#27573;&#65292;&#29978;&#33267;&#20063;&#36861;&#27714;&#26576;&#20123;&#38750;&#27861;&#32463;&#27982;&#21033;&#30410;&#65292;&#20294;&#22240;&#20854;&#20405;&#29359;&#30340;&#23458;&#20307;&#19981;&#26159;&#25110;&#32773;&#19981;&#38480;&#20110;&#20844;&#31169;&#36130;&#20135;&#25152;&#26377;&#26435;&#12290;&#25152;&#20197;&#65292;&#19981;&#26500;&#25104;&#35784;&#39575;&#32618;&#12290;&#20363;&#22914;&#65306;&#25296;&#21334;&#22919;&#22899;&#12289;&#20799;&#31461;&#30340;&#65292;&#23646;&#20110;&#20405;&#29359;&#20154;&#36523;&#26435;&#21033;&#32618;&#12290;&#35784;&#39575;&#32618;&#20405;&#29359;&#30340;&#23545;&#35937;&#65292;&#20165;&#38480;&#20110;&#22269;&#23478;&#12289;&#38598;&#20307;&#25110;&#20010;&#20154;&#30340;&#36130;&#29289;&#65292;&#32780;&#19981;&#26159;&#39575;&#21462;&#20854;&#20182;&#38750;&#27861;&#21033;&#30410;&#12290;&#20854;&#23545;&#35937;&#65292;&#20063;&#24212;&#25490;&#38500;&#37329;&#34701;&#26426;&#26500;&#30340;&#36151;&#27454;&#12290;&#22240;&#26412;&#27861;&#24050;&#20110;&#31532;193&#26465;&#29305;&#21035;&#35268;&#23450;&#20102;&#36151;&#27454;&#35784;&#39575;&#32618;&#12290;[**&#21009;&#20107;&#35785;&#35772;&#24459;&#24072;**](http://www.Fadalawyer.org/xsssls.html)&#20844;&#23433;&#26426;&#20851;&#25110;&#32773;&#20154;&#27665;&#26816;&#23519;&#38498;&#21457;&#29616;&#29359;&#32618;&#20107;&#23454;&#25110;&#32773;&#29359;&#32618;&#23244;&#30097;&#20154;&#65292;&#24212;&#24403;&#25353;&#29031;&#31649;&#36758;&#33539;&#22260;&#31435;&#26696;&#20390;&#26597;&#12290; &#20013;&#22269;[&#21009;&#20107;&#36777;&#25252;**&#24459;&#24072;&#32593;**](http://www.Fadalawyer.org/)&#25552;&#20379;&#20154;&#27665;&#26816;&#23519;&#38498;&#31649;&#36758;&#36138;&#27745;&#36159;&#36162;&#29359;&#32618;&#65292;&#22269;&#23478;&#24037;&#20316;&#20154;&#21592;&#30340;&#28174;&#32844;&#29359;&#32618;&#65292;&#22269;&#23478;&#26426;&#20851;&#24037;&#20316;&#20154;&#21592;&#21033;&#29992;&#32844;&#26435;&#23454;&#26045;&#30340;&#38750;&#27861;&#25304;&#31105;&#12289;&#21009;&#35759;&#36924;&#20379;&#12289;&#25253;&#22797;&#38519;&#23475;&#12289;&#38750;&#27861;&#25628;&#26597;&#30340;&#20405;&#29359;&#20844;&#27665;&#20154;&#36523;&#26435;&#21033;&#30340;&#29359;&#32618;&#20197;&#21450;&#20405;&#29359;&#20844;&#27665;&#27665;&#20027;&#26435;&#21033;&#30340;&#29359;&#32618;&#12290;

---

