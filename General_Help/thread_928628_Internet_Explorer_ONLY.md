---
title: "Internet Explorer ONLY"
date: 2008-09-24
forum: General Help
---

### Post by mashcaster on 2008-09-24
A website I use regularly is only viewable (properly) in Internet Explorer 7.  It will not even work on other browsers on Window XP, let alone FireFox 3.0 or Opera on Ubuntu.

I have a very low spec laptop which just about runs Ubuntu and I cannot afford to go out and buy Windows XP/Vista just to run this website.

Currently the only way I get to use this website is in a library or on a work computer which uses Windows XP.

What is the best way for me to get this to run on my low spec laptop?  I don't think virtual machines are the way to go because of the spec of my machine.

Please help.

---

### Post by tarps87 on 2008-09-24
You can try running it under wine, wine is available from the Ubuntu repositories. Wine in a implementation of the windows api, not a virtual machine, it is also free and open source
This site has a how to on installing it:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4195](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4195)
(I don't know if it is any good a I have not tried it)

---

### Post by RaZe42 on 2008-09-24
There's also this plugin to firefox which allows you to render pages with the IE engine
[https://addons.mozilla.org/en-US/firefox/addon/1419]("https://addons.mozilla.org/en-US/firefox/addon/1419")

---

### Post by mashcaster on 2008-09-24
> **tarps87 said:**
> You can try running it under wine, wine is available from the Ubuntu repositories. Wine in a implementation of the windows api, not a virtual machine, it is also free and open source
This site has a how to on installing it:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4195](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4195)
(I don't know if it is any good a I have not tried it)

I will try this out.  Thanks

> **RaZe42 said:**
> There's also this plugin to firefox which allows you to render pages with the IE engine
[https://addons.mozilla.org/en-US/firefox/addon/1419]("https://addons.mozilla.org/en-US/firefox/addon/1419")

I don't think IE Tabs works on Linux.

---

### Post by eentonig on 2008-09-24
Best thing to do, is sent a nice and polite comment to the webmaster and his boss, stating that you don't like the fact that you're being blocked from using their services. And that any decent webdevelopper these days should be capable to construct a website that is useable by at least the three most commonly used different brands of webbrowsers.

I know I've been sending those kind of mails regularly when I experience the same issue.

Next best thing, is get wine on you box.

---

### Post by mashcaster on 2008-09-24
> **eentonig said:**
> Best thing to do, is sent a nice and polite comment to the webmaster and his boss, stating that you don't like the fact that you're being blocked from using their services. And that any decent webdevelopper these days should be capable to construct a website that is useable by at least the three most commonly used different brands of webbrowsers.

I know I've been sending those kind of mails regularly when I experience the same issue.

Next best thing, is get wine on you box.

Basically, I need IE7 for 2 reasons.

1. For the reason mentioned above
2. I am a web developer and I need to test sites on IE7

Apparently on their website, it says their site will be compatible with firefox soon.  How soon, I have no idea.  I have been waiting for a few months already.

---

### Post by kokkus on 2008-09-24
Can you plz post the website url here?
Maybe someone can help you find a solution or an alternative way.
Forexample if it's because of ActivX it's possiblw to use IEs4linux.
[http://apt.thegnuguru.org/pool/main/i/ies4linux/](http://apt.thegnuguru.org/pool/main/i/ies4linux/)
You have to install Wine to use internet explorer for linux 

IEs4Linux is not very stabile, so do not expact too much.

---

### Post by dodle on 2008-09-24
> **ace214 said:**
> In most cases you can use the User Agent Switcher add-on for Firefox. If the website supports Firefox on Windows, this will generally work. The only time it won't is if the website specifically requires Internet Explorer or Windows Media Player.

Here's a link to the add-on page. [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Try this addon for firefox.  Don't know if will help, but I hope so.

---

### Post by rossjman1 on 2008-09-24
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
IE 6, not 7.

---

### Post by mashcaster on 2008-09-25
> **kokkus said:**
> Can you plz post the website url here?
Maybe someone can help you find a solution or an alternative way.
Forexample if it's because of ActivX it's possiblw to use IEs4linux.
[http://apt.thegnuguru.org/pool/main/i/ies4linux/](http://apt.thegnuguru.org/pool/main/i/ies4linux/)
You have to install Wine to use internet explorer for linux 

IEs4Linux is not very stabile, so do not expact too much.

I will give it a try.  Thanks

> **dodle said:**
> Try this addon for firefox.  Don't know if will help, but I hope so.

I have that addon installed "very useful" however, it does not make any difference to the site I am interested in.

> **rossjman1 said:**
> [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
IE 6, not 7.

Ah, I tried that site on IE6 and it will not work properly.  It only seems to work on IE7.  I could be wrong though, so I will have a double check.

---

### Post by tonybaqain on 2008-09-25
a short way to have it all : 

[LIST]
[*]sudo bash or sudo -i or su -, and enter your password
[*]apt-get install wine
[*]wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
[*]tar zxvf ies4linux-latest.tar.gz
[*]cd ies4linux-*
[*]./ies4linux
[*]when it asks you for IE7, click on yes.
[/LIST]

then you'll have IE5.5 , IE6 , IE7 on your linux.

have fun :)

---

### Post by rossjman1 on 2008-09-25
> **tonybaqain said:**
> a short way to have it all : 

[LIST]
[*]sudo bash or sudo -i or su -, and enter your password
[*]apt-get install wine
[*]wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
[*]tar zxvf ies4linux-latest.tar.gz
[*]cd ies4linux-*
[*]./ies4linux
[*]when it asks you for IE7, click on yes.
[/LIST]

then you'll have IE5.5 , IE6 , IE7 on your linux.

have fun :)

They need to update their webpage if this is true, it says ie 5, 5.5, and 6 only.

---

### Post by patrickballeux on 2008-09-25
Have you tried installing ie4Linux.  It works quite well if you do not use too much stuff in your pages.

Flash is working and some success with Java applets.


Here is the link :[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

This is what I use at work to do some testing...

---

### Post by mashcaster on 2008-09-26
It is illegal to use ies4linux if you do not have a valid Microsoft Windows licence.  I have an old Microsoft Windows 95 license and maybe even a Microsoft Windows 3.1 license somewhere.  So can I use ies4linux legally with these old licenses?

---

### Post by rossjman1 on 2008-09-26
If you're installing for personal use then don't worry about it dude.

---

### Post by mashcaster on 2008-09-28
The website works better with using ies4linux, but it is still not totally readable.  I ended up deleting ies4linux in the end.  Looks like VM is the only way to go.

---

### Post by zhuohua on 2008-10-11
Hi, i still get this following errors when i typed : ./ies4linux What should i do.. please help me.. thanx alot
btw, i am on kubuntu hardy (wine 1.0)
 
 
 IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).
 
 No user interface available. Use command-line ies4linux or install pygtk. Details: [http://www.tatanka.com.br/ies4linux/page/No_GUI](http://www.tatanka.com.br/ies4linux/page/No_GUI)
 
 IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).
 
 
 Usage: ./ies4linux [OPTIONS]
 
 This script downloads and automagically installs multiple versions of
 Microsoft Internet Explorer on Wine.
 
 Without any option, IEs4Linux will:
 - install IE6
 - install Adobe Flash 9
 - create icons on Desktop and Menu
 - use folder: /home/zhuohua/.ies4linux
 
 You can configure other things:
 
 --install-ie55 Install IE5.5 in BASEDIR/ie55/
 --install-ie5 Install IE5 in BASEDIR/ie5/
 
 --install-corefonts Install MS Core Fonts (corefonts.sf.net)
 
 --no-flash Don't install Adobe Flash Player 9
 --no-ie6 Don't install IE 6
 
 --no-desktop-icon Don't create an icon in Desktop
 --no-menu-icon Don't insert icon on Menu
 
 --full-help Display all possible options

---

### Post by twowheeler on 2008-11-12
> **zhuohua said:**
> Hi, i still get this following errors when i typed : ./ies4linux What should i do.. please help me.. thanx alot
btw, i am on kubuntu hardy (wine 1.0)
 
 
 IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).
 
 No user interface available. Use command-line ies4linux or install pygtk. Details: [http://www.tatanka.com.br/ies4linux/page/No_GUI](http://www.tatanka.com.br/ies4linux/page/No_GUI)
 
 

Yeah, me too.  Does anyone have a solution for this?

Edit: and by the way it is not related to using wine 1.x vs. 0.9.x.  I installed an old wine version 0.9.59 using Package --> Force Version in Synaptic and still get the above error with ies3linux.

---

