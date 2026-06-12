---
title: "Dual monitors gdm login screens and terminal blank screen problems"
date: 2008-10-10
forum: General Help
---

### Post by linuxvacuum on 2008-10-10
I have 2 monitors plugged in the same Nvidia card. Each have their own resolution. 

What I want is to see the login screen on BOTH monitors and if I Ctrl+Alt+Fx to see the terminal on BOTH screens so I can open either monitor without complications.

As of now I have to open the primary monitor just to login and then close it after I logged in...

What works now is to manually plug and unplug each monitor on the primary vga port with autodetection of the resolution. But I would like to leave each monitor plugged in and that would only be possible with seeing the login screen and fullscreen terminal on both screens.

---

### Post by tm002ly on 2008-10-10
&#23567;&#30333;&#33258;&#20174;&#37027;&#27425;&#8220;&#39321;&#28207;&#20845;&#21512;&#24425;&#8221;&#20107;&#20214;&#21518;&#65292;&#27599;&#22825;&#37117;&#38506;&#30528;&#25105;&#65292;&#32780;&#19988;&#26102;&#38388;&#36234;&#26469;&#36234;&#38271;&#65292;&#19981;&#36807;&#24120;&#24120;&#22312;&#19981;&#33258;&#35273;&#38388;&#23601;&#20250;&#39078;&#30528;&#30473;&#24551;&#37057;&#22320;&#30475;&#30528;&#25105;&#12290;&#25105;&#35828;&#31505;&#35805;&#36887;&#20182;&#20063;&#26410;&#33021;&#20351;&#20182;&#24320;&#24576;&#65292;&#34429;&#26159;&#36731;&#26366;&#36947;&#20154;&#21644;&#30333;&#23567;&#22992;&#30473;&#23431;&#38388;&#30340;&#31070;&#20260;&#65292;&#31505;&#24847;&#20877;&#20063;&#19981;&#33021;&#21040;&#36798;&#30524;&#24213;[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gz.cn)[&#20845;&#21512;&#24425;](http://www.tm203.sc.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gx.cn)[&#20845;&#21512;&#24425;](http://www.tm203.gd.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.hn.cn)

---

### Post by linuxvacuum on 2008-10-10
Somthing to add in xorg.conf or with the nvidia settings?

---

### Post by bodhi.zazen on 2008-10-10
You set your monitor settings with nvidia-settings ;

```
gksu nvidia-settings
```

I can not tell from you post is you are wanting mirrored monitors ? 

At any rate, one issue IMO is that gnome is not very good in terms of dual monitor awareness. This is reflected in GDM for example. As far as I know you can only get a log in screen on each monitor with mirrored monitors. This is a limitation of GDM and I do not think you can fix it by setting nvidia or xorg.

For example, if you look at xfce or kde both are more dual monitor aware then gnome.

Again I get the feeling I am not understanding what you are wanting exactly.

---

### Post by linuxvacuum on 2008-10-10
That is exactly what I want. I want mirrored monitors when I login. Then right after login, each monitor has its own resolution.

---

### Post by bodhi.zazen on 2008-10-10
> **linuxvacuum said:**
> That is exactly what I want. I want mirrored monitors when I login. Then right after login, each monitor has its own resolution.

I do not think you can do this automatically. You can set your monitors to mirror, but the same settings will be used when you log in.

The closest thing you can do is disable GDM and boot to the command line. Your monitors will be mirrored. Log in and then manually start gnome with :

```
startx
```

---

