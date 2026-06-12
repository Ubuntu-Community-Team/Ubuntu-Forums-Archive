---
title: "TeXMaker"
date: 2005-01-03
forum: General Help
---

### Post by Denis the P. on 2005-01-03
Does someone has managed to install the LateX editor TeXMaker on Ubuntu?
The website of TeXMaker tells that it need qt3 installed but doesn't say which libraries are needed. I have installed some of them with synaptic but I am still not able to install TeXmaker.

---

### Post by mirtux on 2005-01-23
[QUOTE=Denis the P.]Does someone has managed to install the LateX editor TeXMaker on Ubuntu?
The website of TeXMaker tells that it need qt3 installed but doesn't say which libraries are needed. I have installed some of them with synaptic but I am still not able to install TeXmaker.[/QUOTE]
 Hi,
  i would like to install [COLOR=Red]TeXmaker [/COLOR] too on my Ubuntu box! I was used to use (!) [COLOR=YellowGreen]Kile[/COLOR] on my Fedora Core 3 OS but now, on Ubuntu  KDE gives me a lot of strange errors when i try to install it. I searched for [COLOR=Red]TeXmaker[/COLOR] on the repositories but it's not present. I will try to install it and i will let you know if i had your problem too!

Regards,
MC

---

### Post by kleeman on 2005-01-23
I downloaded the suse 9.1 rpm and then used alien (sudo alien *.rpm) to convert it to a deb file. It then installed fine with sudo dpkg -i *.deb (* stands for the texmaker prefix don't use it literally ;-)) It works nicely and loads faster than kile the other tex frontend

---

### Post by mirtux on 2005-01-24
[QUOTE=kleeman]I downloaded the suse 9.1 rpm and then used alien (sudo alien *.rpm) to convert it to a deb file. It then installed fine with sudo dpkg -i *.deb (* stands for the texmaker prefix don't use it literally ;-)) It works nicely and loads faster than kile the other tex frontend[/QUOTE]
Thank you very much kleeman, now it's working nicely also for me! 
Do you know to who we might ask, in general, to add packages of general interest to some repositories?

Regards,
MC

---

### Post by Denis the P. on 2005-02-03
Works also fine with the SUSE 9.2 RPM from the TeXMaker web site.

---

### Post by neoflight on 2006-02-14
[QUOTE=kleeman]I downloaded the suse 9.1 rpm and then used alien (sudo alien *.rpm) to convert it to a deb file. It then installed fine with sudo dpkg -i *.deb (* stands for the texmaker prefix don't use it literally ;-)) It works nicely and loads faster than kile the other tex frontend[/QUOTE]

Hello.....

I know its from way back in the days of Warty. This concerns Breezy...
would you please help me with MY problem posted [here]("http://www.ubuntuforums.org/showthread.php?t=129010&page=2")
THanks

---

### Post by kleeman on 2006-02-14
I installed the static build from the webpage (very nice I must say) and opened a tex file I had laying around. I got your error message when I clicked on the quickbuild button. I solved it by going into the configuration and altering the postscript viewing program from gv to ggv. All the other commands (latex, dvips, dvi view etc) seemed to work fine. 

If this is not your problem could you provide more precise steps so I can reproduce what you are describing?

---

### Post by neoflight on 2006-02-16
[QUOTE=kleeman]I installed the static build from the webpage (very nice I must say) and opened a tex file I had laying around. I got your error message when I clicked on the quickbuild button. I solved it by going into the configuration and altering the postscript viewing program from gv to ggv. All the other commands (latex, dvips, dvi view etc) seemed to work fine. 

If this is not your problem could you provide more precise steps so I can reproduce what you are describing?[/QUOTE]


Thanks a lot. I solved it. the problem was something similar. This time it was due to xpdf. i had to install that before I could run F1(Quick build)..everything else seems ok now. it was not creating log file but now it can coz, i gave the full path 
**/usr/local/texlive/2005/bin/i386-linux/appropriate_command %.extexntion **

but just xpdf %.pdf ....
thanks a lot kleeman...

---

