---
title: "Audio CD not mounting (DVD + blank discs fine)"
date: 2008-10-29
forum: Hardware
---

### Post by iheartmuseums on 2008-10-29
Hi all. I recently updated to Hardy, and since then i've been having troubles with my CD/DVD drive. It will still recognise and mount DVDs and blank discs, and give them icons on the desktop when they mount. However (and i've tried a number of different discs) audio CDs just will not mount automatically, and when I try to mount /cdrom I get:

[mntent]: warning: no final newline at the end of /etc/fstab
mount: No medium found

I can't figure out why it's not working just for audio CDs - any ideas?

---

### Post by bubbleskitties on 2008-10-29
I have a simaler problem , My dvd drive will recognize every thing but a audio CD. when you look for it in the files its not there. k3b will recognize it but nothing else will. Please let me know if any one else has had this problem.

---

### Post by JMorg on 2008-10-29
Do you have numerous audio players installed? It is a possibility that the programs are fighting to mount the audio CD in one or the other and are not allowing it to fully mount. The reason I say this is because you stated that the error message given involves, "Medium Not Found". Try removing the audio players you aren't using and keep the one and see what happens then. I know it might not be the exact advice you were looking for, but I think it is definitely a possibility. Hope this helps ya out in some way :)

---

### Post by iheartmuseums on 2008-10-29
I don't have any more now than before I updated to Hardy though (still only got Amarok, Rythmbox which I never use, and the audio CD extractor) - and i've now got my media preferences set to 'do nothing' for audio CDs. I was trying to mount the cd manually which shouldn't have anything to do with programs (unless i'm quite mistaken) - this is what is frustrating to me. I'd happily remove Rythmbox, but the two others are my mainstays unfortunately.

---

### Post by 080801jk on 2008-10-30
&#22522;&#30784;&#26550;&#26500;&#31649;&#29702; &#12288;&#12288;Mocha BSM&#39318;&#20808;&#26159;&#25552;&#20379;&#20102;&#22914;&#19979;&#30417;&#25511;&#21644;&#31649;&#29702;&#30340;[**&#32593;&#31649;&#36719;&#20214;**](http://www.mochabsm.com/)&#65306;?&#12288; - &#20027;&#26426;?&#12288; - &#32593;&#32476;&#35774;&#22791;&#19982;&#25299;&#25169;?&#12288; - IT&#36164;&#20135;&#12288;&#12288;&#25903;&#25345;&#30340;&#32593;&#32476;&#35774;&#22791;&#30340;&#21378;&#23478;&#21253;&#25324;&#65306;Cisco&#12289;&#21326;&#20026;&#12289;&#38463;&#23572;&#21345;&#29305;&#12289;&#20013;&#20852;&#12289;Nortel&#12289;Juniper&#12289;Netscreen&#12289;F5&#12289;AVAYA&#12289;Lucent&#12289;Foundary&#12289;D-link&#12289;&#36808;&#26222;&#31561;&#65292;&#35774;&#22791;&#31867;&#22411;&#21253;&#25324;&#36335;&#30001;&#22120;&#12289;&#20132;&#25442;&#26426;&#12289;&#38450;&#28779;&#22681;&#12289;&#23433;&#20840;&#35774;&#22791;&#31561;&#12290;  &#24212;&#29992;&#31649;&#29702; &#12288;&#12288;Mocha BSM&#20063;&#26159;&#25903;&#25345;&#24212;&#29992;&#31649;&#29702;&#30340;[**&#32593;&#31649;&#36719;&#20214;**](http://www.mochabsm.com/)&#65306;&#12288;? - J2EE&#24212;&#29992;&#26381;&#21153;&#22120; ?C WebSphere, Weblogic, SunOne?&#12288; - Lotus Domino?&#12288; - Portal ?C WebSphere, Weblogic, SunOne?&#12288; - &#25968;&#25454;&#24211; ?C Oracle, DB2, MySQL, MS SQL?&#12288; - LDAP ?C IBM, SunOne?&#12288; - Web Server ?C Apache, IIS, SunOne?&#12288; - URL & Ports?&#12288; - Mail ?C MS Exchange, Lotus Mail  &#31471;&#21040;&#31471;&#21709;&#24212;&#26102;&#38388;&#31649;&#29702; &#12288;&#12288;&#30417;&#25511;&#21709;&#24212;&#26102;&#38388;&#30340;[**&#32593;&#31649;&#36719;&#20214;**](http://www.mochabsm.com/)&#65306;?&#12288; - &#24405;&#21046;&#19982;&#27169;&#25311;&#29992;&#25143;&#20351;&#29992;&#32593;&#31449;&#30340;&#20851;&#38190;&#25805;&#20316;&#19982;&#27493;&#39588;&#65292;&#24182;&#19988;&#21487;&#20197;&#23450;&#26102;&#22238;&#25918;&#65292;&#33719;&#24471;&#30456;&#20851;&#21709;&#24212;&#26102;&#38388;&#19982;HTTP&#29366;&#24577;&#12290;?&#12288; - &#23450;&#20301;&#22797;&#26434;&#30340;&#19994;&#21153;&#31995;&#32479;&#30340;&#29942;&#39048;&#12290; &#12288;&#19994;&#21153;&#26381;&#21153;&#31649;&#29702; &#12288;&#12288;&#20197;&#26381;&#21153;&#30340;&#35270;&#35282;&#26469;&#31649;&#29702;&#20225;&#19994;&#30340;&#32593;&#31649;&#36719;&#20214;&#65292;&#25552;&#20379;&#20102;&#20197;&#19979;&#21151;&#33021;&#65306;?&#12288; - &#21487;&#35270;&#21270;&#26381;&#21153;&#23450;&#20041;?&#12288; - &#26381;&#21153;&#20202;&#34920;&#30424; ?&#12288; - &#26381;&#21153;&#27700;&#24179;&#31649;&#29702; [**IT&#36816;&#32500;&#31649;&#29702;**](http://www.mochabsm.com/buy/index.htm) &#12288;&#12288;&#36890;&#36807;[**IT&#36816;&#32500;&#31649;&#29702;**](http://www.mochabsm.com/buy/index.htm)&#65292;&#20197;ITIL&#30340;&#27969;&#31243;&#26694;&#26550;&#65292;&#32532;&#36896;&#19968;&#20010;&#33258;&#21160;&#21270;&#65292;&#27969;&#31243;&#21270;&#21644;&#35268;&#33539;&#21270;&#30340;IT&#36816;&#32500;&#31995;&#32479;&#12290;

---

### Post by JMorg on 2008-10-30
Hmm, well it just seems odd that it will mount a DVD but not a CD. It doesn't sound like the laser in the optical drive is bad because of that reason, which is why it leads me to believe there is a software issue. :( Now if the laser reads in data from a CD separately than a DVD then I am willing to believe that, but that is something I'm not 100% positive on and I don't want to give you misinformation!

---

### Post by SKUK on 2008-11-02
I have the same problem.To hear my audio cd's, I installed _*audio CD extractor*_. This is not a neat solution, but is working. I tried uninstalling players, added all the codecs. Nothing seems to work except audio CD extractor. It is not a hardware problem.

---

### Post by iheartmuseums on 2008-11-03
Unfortunately I already have that installed - it's not recognising Audio discs either. They just aren't auto-mounting for some really random reason. Still having no troubles with DVDs, data DVDs, blank DVDs and CDRs.

I can't think of why it's singling out audio CDs.

---

### Post by originalsurfmex on 2008-11-12
im having the same problem, tried a bunch of stuff from other forums...worked over my fstab file...but no dice...

...anyone solve this for themselves??


i can access the drive from amarok and soundkonverter, but every time i try and mount it i get this message:
```
-@-:/$ mount cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

btw im running an hp tx2000 tablet pc

---

### Post by gali98 on 2008-11-14
Well... you could always try intrepid...
Kory

---

### Post by iheartmuseums on 2008-11-17
I didn't like the Hardy upgrade in general, I had a lot of niggling problems. This is something i'm not sure upgrading will even help! I've thought about doing a clean reinstall to see if it helps but I figure it'll just end up being a waste of time. 

I just wish there were some logical explanation for this problem!

---

### Post by madverb on 2008-11-17
You can't mount blank discs.
Also I'm pretty sure you don't really "mount" audio discs either.

---

### Post by iheartmuseums on 2008-11-17
Blank discs are recognised by the drive, as are DVDs, audio discs are not. This is my problem. I've not had to manually mount anything for a long time, but I figure mount /cdrom/ should at least recognise that there's an audio disc in my drive.

---

### Post by iheartmuseums on 2009-01-05
Does anyone have a clue as to this problem's solution? I'm still not sure what could've gone wrong. My fstab is as follows:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4cba0cb1-bf06-4ec9-956e-3369b9e94e58 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5f1945fe-caa8-4dd6-a4ef-4653344de83f none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0


---

