---
title: "Formatting drives to be used by *anyone*"
date: 2008-10-09
forum: Hardware
---

### Post by optimal on 2008-10-09
Hey!

I'm having continual trouble with my swappable (USB) drives, a (seemingly) random event will cause it to change somehow - becoming read-only, or not writing the data properly (while claiming to be writeable), adding non-deletable files, filling up folders with gobbledy-gook files, ie:

```
root@cogbox:/media/DRK/stuff/levels# dir
¼&#8976;&#9577;æ:uuè.`&#960;&#9552;		êîl__&#9566;&#9571;e.LSV	       q&#8992;z&#8729;î&#9524;iv.&#9619;=&#8319;
½u&#9617;`&#949;\024m¬.r&#8776;n		g&#8976;¼&#9573;ô\031]¡.&#9575;&#8976;&#920;        µ&#9474;\br&#9560;&#9619;>p.±&#9612;&#9617;
\031&#9612;\03717wfx./Åº	&#9500;h&#9559;&#9559;*.}+{	       ¡ß\f&#9568;£\022&#9552;£.ƒz&#9516;
1M&#9567;\035\177\nrz.\004ca	ì<*æ&#9565;9$\020.s&#9632;m        s&#9632;{w&#9500;ß*.è}v
1{\017\bzjzy.&#8730;=&#9568;	&#8359;ïcp&#9484;îF².µü6	       &#8776;\016£t7>&#9600;°.uá¥
3è°\026&#9524;`&#9600;\033.&#9559;H6	I&#8805;&#9474;J\r&#8805;\\&#963;.»|d	       tl&#8976;&#9569;&#9558;&#8730;\023[.&#9573;]*
&#9566;6&#8359;ñW&#931;&#9580;Æ.µ&#9553;?		&#9484;ir\034±vm\036.½í&#9500;     UN&#8734;&#8992;M\bæ\024.&#9555;&#9532;&#9555;
9**h56&#9558;h.S&#9575;û		ì&#963;à\036&#8992;&#8729;%e.&#9580;2°        ü&#8804;&#9560;rö&#9571;xß.`&#9524;÷
ä[\023d&#9560;\006&#8319;7.öJî	j&#9568;&#9572;7±gƒ\\.wm\025       ^v>º!~&#949;ñ.&#9570;&#8734;¬
µ}¢áew&#963;&#9612;.<Kà		j&#8805;ì&#8730;\035&#8729;|l.&#9496;&#945;&#8805;        &#9569;v&#9566;&#9617;v&#9576;&#8992;\037.\t&#8729;f
â]&#9578;l¬q»\032.rAE		j&#9577;&#8734;&#963;ö.&#949;&#9580;.&#937;&#9579;&#9524;	       zú&#9573;<%g}\f.\037g\026
AÖN\030à_&#9553;k.h&#937;&#8734;		&#9578;\016Kz&#964;&#9573;&#9571;[.&#9575;\024(     &#945;0%k&#8734;&#920;ly.,&#9572;
&#9556;&#9571;]&#9496;åy&#9566;k.&#9572;&#9574;\025		m&#9575;\002«ä»&w._í<        &#9516;&#9600;&#9571;\002&#945;&#964;\037ñ.\1770)
]&#9557;\n\aa^%\177.&#915;&#8359;&#949;	&#9580;¡Nmî&#8976;Q&#937;.&#9580;&#9577;x	       )&#915;ynª&#9553;òd.`&#8805;é
<c&#9532;&#9632;:&#9560;&#9569;\b.fkf		»Ö¡&#9568;K&#9574;\033¥.j&#9555;k        &#949;&#9557;&#9474;&#8993;&#948;mé4.\021£`
\v\033\034çw5ö%.&#9554;&#9619;^	ô!Kw«&#9608;Q&#9617;.X&#9508;á	       &#960;&#9500;&#9552;+í&#960;\a&#9580;.J"¬
&#9563;%d&#9580;uf&#9604;s.&#9532;sÜ		Oo\001ñp&#9608;&#9508;\022.L&#966;\023  >&#8804;&#9508;&#966;|m\036&#9554;.&#9574;&#9574;±
é&#9472;&#8805;{b&#9564;[m.&#9564;h&#9488;		&#9532;*ò»&#9617;º\037t.µ.º        *.B&#9573;\022
&#9579;\026&#8805;¥*E&#9557;\n.i\031\\	qp\025\021æ&#9472;&#963;&#9474;.&#8359;\0054
```

Basically something new and annoying every now and then that stops me from doing what I'm supposed to be doing! My work!

OK, I'm fine at basic linux stuff, but this problem crops up time and time again, and it's becoming enough of an issue that I'm seriously considering going back to windows simply so that my drives play nice. I really don't want to, but it's looking likely!

Now, I don't particularly want a debate about security or anything like that (I'm not stupid enough to not backup my work or run a delete all command), but is there a simple way of making USB drives ALWAYS have read / write permissions whoever you are? Regardless of the machine or system?

If anyone can help me on this, I'll be ever appreciative!

---

### Post by az on 2008-10-09
I suggest you are having hardware problems.  I doubt Ubuntu or any other operating system has snything to do with that.

See here:
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by cariboo on 2008-10-09
I had a similar problem, I was getting the same output from a 1Gb flash drive, after I used gparted to reformat the drive as vfat. The fix was to plug it into a windows computer and use the disk management plugin to reformat the drive. I haven't had the problem since.

Jim

---

### Post by vanadium on 2008-10-09
Linux can also reformat fine. Also to me, this issue looks like a hardware problem.

---

