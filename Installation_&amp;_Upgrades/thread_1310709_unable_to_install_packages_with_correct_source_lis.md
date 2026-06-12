---
title: "unable to install packages with correct source list, packages missing?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by BaiLee on 2009-11-02
packages missing?
how can i fix this?

the following is the error messages.


eric@wd-laptop:~$ sudo apt-get update
&#33719;&#21462;&#65306;1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
&#24573;&#30053; [http://dl.google.com](http://dl.google.com) stable/main Translation-zh_CN   
&#33719;&#21462;&#65306;2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]      
&#33719;&#21462;&#65306;3 [http://dl.google.com](http://dl.google.com) stable/main Packages [665B]
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-zh_CN
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-zh_CN
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-zh_CN
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
&#24573;&#30053; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-zh_CN
&#24573;&#30053; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-zh_CN     
&#24573;&#30053; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-zh_CN       
&#24573;&#30053; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-zh_CN     
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg                     
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-zh_CN                   
&#24573;&#30053; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-zh_CN          
&#24573;&#30053; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-zh_CN    
&#24573;&#30053; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-zh_CN      
&#24573;&#30053; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-zh_CN    
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
&#21629;&#20013; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
&#19979;&#36733; 3,394B&#65292;&#32791;&#26102; 34 &#31186; (98B/s)
&#27491;&#22312;&#35835;&#21462;&#36719;&#20214;&#21253;&#21015;&#34920;... &#23436;&#25104;


eric@wd-laptop:~$ sudo apt-get install sqlitebrowser
[sudo] password for eric: 
&#27491;&#22312;&#35835;&#21462;&#36719;&#20214;&#21253;&#21015;&#34920;... &#23436;&#25104;
&#27491;&#22312;&#20998;&#26512;&#36719;&#20214;&#21253;&#30340;&#20381;&#36182;&#20851;&#31995;&#26641;       
&#27491;&#22312;&#35835;&#21462;&#29366;&#24577;&#20449;&#24687;... &#23436;&#25104;       
&#23558;&#20250;&#23433;&#35013;&#19979;&#21015;&#39069;&#22806;&#30340;&#36719;&#20214;&#21253;&#65306;
  libqt3-mt
&#24314;&#35758;&#23433;&#35013;&#30340;&#36719;&#20214;&#21253;&#65306;
  libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc
&#19979;&#21015;&#12304;&#26032;&#12305;&#36719;&#20214;&#21253;&#23558;&#34987;&#23433;&#35013;&#65306;
  libqt3-mt sqlitebrowser
&#20849;&#21319;&#32423;&#20102; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26032;&#23433;&#35013;&#20102; 2 &#20010;&#36719;&#20214;&#21253;&#65292;&#35201;&#21368;&#36733; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26377; 1 &#20010;&#36719;&#20214;&#26410;&#34987;&#21319;&#32423;&#12290;
&#38656;&#35201;&#19979;&#36733; 3,500kB/3,633kB &#30340;&#36719;&#20214;&#21253;&#12290;
&#35299;&#21387;&#32553;&#21518;&#20250;&#28040;&#32791;&#25481; 9,372kB &#30340;&#39069;&#22806;&#31354;&#38388;&#12290;
&#24744;&#24076;&#26395;&#32487;&#32493;&#25191;&#34892;&#21527;&#65311;[Y/n]Y
&#38169;&#35823; [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main libqt3-mt 3:3.3.8-b-5ubuntu2
  404  Not Found [IP: 91.189.88.40 80]
&#26080;&#27861;&#19979;&#36733; [http://archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-5ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-5ubuntu2_i386.deb)  404  Not Found [IP: 91.189.88.40 80]
E: &#26377;&#20960;&#20010;&#36719;&#20214;&#21253;&#26080;&#27861;&#19979;&#36733;&#65292;&#24744;&#21487;&#20197;&#36816;&#34892; apt-get update &#25110;&#32773;&#21152;&#19978; --fix-missing &#30340;&#36873;&#39033;&#20877;&#35797;&#35797;&#65311;

---

### Post by BaiLee on 2009-11-02
additionally.
vga instruction failed to work.
alt-F1-F6 with low resolution.

---

### Post by BaiLee on 2009-11-02
repository has different version file but the requested file is missing.
why?

---

