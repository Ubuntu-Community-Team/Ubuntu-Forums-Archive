---
title: "new laptop.. :/"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by Aesir09 on 2007-12-06
i have a toshiba laptop with an amd64, i am lazy and a noob so i just wubi -ed it. im pretty sure it installed the 32 bit version, which i would eventually wanna change.


1. i can't find out how to connect to my wireless router.

2. i get a quick almost unnoticable weird message at the boot but nothing wrong seems to happen.

3. it looks crappy and i checked the resolution and stuff.


help??

please please

im sick of vista :)

---

### Post by camccall on 2007-12-06
First off, can you tell us the model of the laptop you have.  Also how comfortable are you with the command line?  Can you post the information from the command dmesg.  That information would be a great starting point to help you get Ubuntu up and running.

---

### Post by Aesir09 on 2007-12-06
yes mine is a toshiba satellite A215


and also, i am running vista right now, so should i just record down what the msg says and then tell you??

because this is my first time every installing ubuntu on a notebook. but i couldn't find out how to connect to my wlan

and also, im eh ok with the command line. definitley not pro though lolz

:lolflag:

---

### Post by camccall on 2007-12-06
So do you have Ubuntu installed or are you just having problems with the LiveCD?

---

### Post by Aesir09 on 2007-12-06
i installed it with wubi, and it is 7.04 btw b/c they haven't release wubi 7.10, but i will just upgrade inside 7.04

and yeah...

so i will reboot right now with your cmd and see what i can do.

---

### Post by camccall on 2007-12-06
Ahh, sorry I missed that part.  I don't have any experience with Wubi so it may be that I'm not much help.  

If you run ```
dmesg > tmp.txt
``` and copy that file to your windows directory, you should be able to view the output and paste it into the forum.  Also can you connect your laptop directly to the router and get Internet connectivity in Ubuntu?

---

### Post by Aesir09 on 2007-12-06
yeah i could do that, and i did try saving it as a .txt in my windows directory.. cant find it!

and also i think my wireless card is uncompatible :(:confused:

---

### Post by jrharvey on 2007-12-06
Wubi 7.10 alpha is out right now. I know it is just an alpha but i used it on 2 computers and it works fine. I did have to tweak a few things in windows and do a chkdisk but overall it has much better driver support than 7.04


[http://ubuntuforums.org/showthread.php?t=572147&highlight=wubi+alpha](http://ubuntuforums.org/showthread.php?t=572147&highlight=wubi+alpha)

---

### Post by jrharvey on 2007-12-06
Oh yes, and I am also sick of vista. I do have to use it with rendering software and autocad and sketchup but I hate every time i have to boot into it.

---

### Post by Aesir09 on 2007-12-06
ok thanks and one time, on my family computer, i tried to install wubi 7.10 and all it did was like almost install the .iso it didnt actually install the OS.

PS** which one do i choose from all the alphas?!?!**

amd64 btw

---

### Post by jrharvey on 2007-12-06
hmm good question!!!! I would choose the newest release. I havnt tried the newest alpha but hopefully its better than the previous versions.

---

### Post by Aesir09 on 2007-12-06
dmesg reads as follows in 7.10 install, while unplugged from router

```

[   43.954377] hda_codec: invalid dep_range_val 0:7fff
[   43.954460] hda_codec: invalid dep_range_val 0:7fff
[   43.954463] hda_codec: invalid dep_range_val 0:7fff
[   43.954546] hda_codec: invalid dep_range_val 0:7fff
[   43.954548] hda_codec: invalid dep_range_val 0:7fff
[   43.954631] hda_codec: invalid dep_range_val 0:7fff
[   43.954633] hda_codec: invalid dep_range_val 0:7fff
[   43.954702] hda_codec: invalid dep_range_val 0:7fff
[   43.954704] hda_codec: invalid dep_range_val 0:7fff
[   43.954766] hda_codec: invalid dep_range_val 0:7fff
[   43.954768] hda_codec: invalid dep_range_val 0:7fff
[   43.954829] hda_codec: invalid dep_range_val 0:7fff
[   43.954831] hda_codec: invalid dep_range_val 0:7fff
[   43.954892] hda_codec: invalid dep_range_val 0:7fff
[   43.954894] hda_codec: invalid dep_range_val 0:7fff
[   43.954955] hda_codec: invalid dep_range_val 0:7fff
[   43.954957] hda_codec: invalid dep_range_val 0:7fff
[   43.955018] hda_codec: invalid dep_range_val 0:7fff
[   43.955020] hda_codec: invalid dep_range_val 0:7fff
[   43.955084] hda_codec: invalid dep_range_val 0:7fff
[   43.955086] hda_codec: invalid dep_range_val 0:7fff
[   43.955147] hda_codec: invalid dep_range_val 0:7fff
[   43.955149] hda_codec: invalid dep_range_val 0:7fff
[   43.955211] hda_codec: invalid dep_range_val 0:7fff
[   43.955213] hda_codec: invalid dep_range_val 0:7fff
[   43.955274] hda_codec: invalid dep_range_val 0:7fff
[   43.955276] hda_codec: invalid dep_range_val 0:7fff
[   43.955337] hda_codec: invalid dep_range_val 0:7fff
[   43.955339] hda_codec: invalid dep_range_val 0:7fff
[   43.955401] hda_codec: invalid dep_range_val 0:7fff
[   43.955404] hda_codec: invalid dep_range_val 0:7fff
[   43.955468] hda_codec: invalid dep_range_val 0:7fff
[   43.955471] hda_codec: invalid dep_range_val 0:7fff
[   43.955533] hda_codec: invalid dep_range_val 0:7fff
[   43.955535] hda_codec: invalid dep_range_val 0:7fff
[   43.955595] hda_codec: invalid dep_range_val 0:7fff
[   43.955598] hda_codec: invalid dep_range_val 0:7fff
[   43.955660] hda_codec: invalid dep_range_val 0:7fff
[   43.955662] hda_codec: invalid dep_range_val 0:7fff
[   43.955724] hda_codec: invalid dep_range_val 0:7fff
[   43.955726] hda_codec: invalid dep_range_val 0:7fff
[   43.955787] hda_codec: invalid dep_range_val 0:7fff
[   43.955789] hda_codec: invalid dep_range_val 0:7fff
[   43.955850] hda_codec: invalid dep_range_val 0:7fff
[   43.955852] hda_codec: invalid dep_range_val 0:7fff
[   43.955913] hda_codec: invalid dep_range_val 0:7fff
[   43.955915] hda_codec: invalid dep_range_val 0:7fff
[   43.955977] hda_codec: invalid dep_range_val 0:7fff
[   43.955979] hda_codec: invalid dep_range_val 0:7fff
[   43.956040] hda_codec: invalid dep_range_val 0:7fff
[   43.956042] hda_codec: invalid dep_range_val 0:7fff
[   43.956103] hda_codec: invalid dep_range_val 0:7fff
[   43.956105] hda_codec: invalid dep_range_val 0:7fff
[   43.956167] hda_codec: invalid dep_range_val 0:7fff
[   43.956169] hda_codec: invalid dep_range_val 0:7fff
[   43.956230] hda_codec: invalid dep_range_val 0:7fff
[   43.956232] hda_codec: invalid dep_range_val 0:7fff
[   43.956293] hda_codec: invalid dep_range_val 0:7fff
[   43.956295] hda_codec: invalid dep_range_val 0:7fff
[   43.956356] hda_codec: invalid dep_range_val 0:7fff
[   43.956358] hda_codec: invalid dep_range_val 0:7fff
[   43.956419] hda_codec: invalid dep_range_val 0:7fff
[   43.956421] hda_codec: invalid dep_range_val 0:7fff
[   43.956482] hda_codec: invalid dep_range_val 0:7fff
[   43.956484] hda_codec: invalid dep_range_val 0:7fff
[   43.956546] hda_codec: invalid dep_range_val 0:7fff
[   43.956548] hda_codec: invalid dep_range_val 0:7fff
[   43.956609] hda_codec: invalid dep_range_val 0:7fff
[   43.956611] hda_codec: invalid dep_range_val 0:7fff
[   43.956672] hda_codec: invalid dep_range_val 0:7fff
[   43.956674] hda_codec: invalid dep_range_val 0:7fff
[   43.956735] hda_codec: invalid dep_range_val 0:7fff
[   43.956737] hda_codec: invalid dep_range_val 0:7fff
[   43.956798] hda_codec: invalid dep_range_val 0:7fff
[   43.956800] hda_codec: invalid dep_range_val 0:7fff
[   43.956861] hda_codec: invalid dep_range_val 0:7fff
[   43.956863] hda_codec: invalid dep_range_val 0:7fff
[   43.956924] hda_codec: invalid dep_range_val 0:7fff
[   43.956926] hda_codec: invalid dep_range_val 0:7fff
[   43.956987] hda_codec: invalid dep_range_val 0:7fff
[   43.957223] hda_codec: invalid dep_range_val 0:7fff
[   43.957225] hda_codec: invalid dep_range_val 0:7fff
[   43.957286] hda_codec: invalid dep_range_val 0:7fff
[   43.957288] hda_codec: invalid dep_range_val 0:7fff
[   43.957349] hda_codec: invalid dep_range_val 0:7fff
[   43.957351] hda_codec: invalid dep_range_val 0:7fff
[   43.957412] hda_codec: invalid dep_range_val 0:7fff
[   43.957414] hda_codec: invalid dep_range_val 0:7fff
[   43.957475] hda_codec: invalid dep_range_val 0:7fff
[   43.957477] hda_codec: invalid dep_range_val 0:7fff
[   43.957538] hda_codec: invalid dep_range_val 0:7fff
[   43.957540] hda_codec: invalid dep_range_val 0:7fff
[   43.957601] hda_codec: invalid dep_range_val 0:7fff
[   43.957603] hda_codec: invalid dep_range_val 0:7fff
[   43.957664] hda_codec: invalid dep_range_val 0:7fff
[   43.957666] hda_codec: invalid dep_range_val 0:7fff
[   43.957727] hda_codec: invalid dep_range_val 0:7fff
[   43.957729] hda_codec: invalid dep_range_val 0:7fff
[   43.957789] hda_codec: invalid dep_range_val 0:7fff
[   43.957792] hda_codec: invalid dep_range_val 0:7fff
[   43.957852] hda_codec: invalid dep_range_val 0:7fff
[   43.957855] hda_codec: invalid dep_range_val 0:7fff
[   43.957915] hda_codec: invalid dep_range_val 0:7fff
[   43.957917] hda_codec: invalid dep_range_val 0:7fff
[   43.957978] hda_codec: invalid dep_range_val 0:7fff
[   43.957980] hda_codec: invalid dep_range_val 0:7fff
[   43.958041] hda_codec: invalid dep_range_val 0:7fff
[   43.958043] hda_codec: invalid dep_range_val 0:7fff
[   43.958104] hda_codec: invalid dep_range_val 0:7fff
[   43.958106] hda_codec: invalid dep_range_val 0:7fff
[   43.958167] hda_codec: invalid dep_range_val 0:7fff
[   43.958169] hda_codec: invalid dep_range_val 0:7fff
[   43.958231] hda_codec: invalid dep_range_val 0:7fff
[   43.958233] hda_codec: invalid dep_range_val 0:7fff
[   43.958294] hda_codec: invalid dep_range_val 0:7fff
[   43.958296] hda_codec: invalid dep_range_val 0:7fff
[   43.958358] hda_codec: invalid dep_range_val 0:7fff
[   43.958360] hda_codec: invalid dep_range_val 0:7fff
[   43.958421] hda_codec: invalid dep_range_val 0:7fff
[   43.958423] hda_codec: invalid dep_range_val 0:7fff
[   43.958485] hda_codec: invalid dep_range_val 0:7fff
[   43.958487] hda_codec: invalid dep_range_val 0:7fff
[   43.958548] hda_codec: invalid dep_range_val 0:7fff
[   43.958550] hda_codec: invalid dep_range_val 0:7fff
[   43.958612] hda_codec: invalid dep_range_val 0:7fff
[   43.958614] hda_codec: invalid dep_range_val 0:7fff
[   43.958675] hda_codec: invalid dep_range_val 0:7fff
[   43.958677] hda_codec: invalid dep_range_val 0:7fff
[   43.958739] hda_codec: invalid dep_range_val 0:7fff
[   43.958741] hda_codec: invalid dep_range_val 0:7fff
[   43.958802] hda_codec: invalid dep_range_val 0:7fff
[   43.958804] hda_codec: invalid dep_range_val 0:7fff
[   43.958865] hda_codec: invalid dep_range_val 0:7fff
[   43.958867] hda_codec: invalid dep_range_val 0:7fff
[   43.958929] hda_codec: invalid dep_range_val 0:7fff
[   43.958931] hda_codec: invalid dep_range_val 0:7fff
[   43.958992] hda_codec: invalid dep_range_val 0:7fff
[   43.958994] hda_codec: invalid dep_range_val 0:7fff
[   43.959057] hda_codec: invalid dep_range_val 0:7fff
[   43.959059] hda_codec: invalid dep_range_val 0:7fff
[   43.959121] hda_codec: invalid dep_range_val 0:7fff
[   43.959123] hda_codec: invalid dep_range_val 0:7fff
[   43.959184] hda_codec: invalid dep_range_val 0:7fff
[   43.959187] hda_codec: invalid dep_range_val 0:7fff
[   43.959249] hda_codec: invalid dep_range_val 0:7fff
[   43.959251] hda_codec: invalid dep_range_val 0:7fff
[   43.959322] hda_codec: invalid dep_range_val 0:7fff
[   43.959324] hda_codec: invalid dep_range_val 0:7fff
[   43.959409] hda_codec: invalid dep_range_val 0:7fff
[   43.959411] hda_codec: invalid dep_range_val 0:7fff
[   43.959497] hda_codec: invalid dep_range_val 0:7fff
[   43.959499] hda_codec: invalid dep_range_val 0:7fff
[   43.959582] hda_codec: invalid dep_range_val 0:7fff
[   43.959585] hda_codec: invalid dep_range_val 0:7fff
[   43.959668] hda_codec: invalid dep_range_val 0:7fff
[   43.959670] hda_codec: invalid dep_range_val 0:7fff
[   43.959753] hda_codec: invalid dep_range_val 0:7fff
[   43.959755] hda_codec: invalid dep_range_val 0:7fff
[   43.959838] hda_codec: invalid dep_range_val 0:7fff
[   43.959840] hda_codec: invalid dep_range_val 0:7fff
[   43.959924] hda_codec: invalid dep_range_val 0:7fff
[   43.959926] hda_codec: invalid dep_range_val 0:7fff
[   43.960010] hda_codec: invalid dep_range_val 0:7fff
[   43.960012] hda_codec: invalid dep_range_val 0:7fff
[   43.960095] hda_codec: invalid dep_range_val 0:7fff
[   43.960098] hda_codec: invalid dep_range_val 0:7fff
[   43.960181] hda_codec: invalid dep_range_val 0:7fff
[   43.960183] hda_codec: invalid dep_range_val 0:7fff
[   43.960266] hda_codec: invalid dep_range_val 0:7fff
[   43.960268] hda_codec: invalid dep_range_val 0:7fff
[   43.960351] hda_codec: invalid dep_range_val 0:7fff
[   43.960353] hda_codec: invalid dep_range_val 0:7fff
[   43.960437] hda_codec: invalid dep_range_val 0:7fff
[   43.960439] hda_codec: invalid dep_range_val 0:7fff
[   43.960523] hda_codec: invalid dep_range_val 0:7fff
[   43.960526] hda_codec: invalid dep_range_val 0:7fff
[   43.960610] hda_codec: invalid dep_range_val 0:7fff
[   43.960612] hda_codec: invalid dep_range_val 0:7fff
[   43.960695] hda_codec: invalid dep_range_val 0:7fff
[   43.960698] hda_codec: invalid dep_range_val 0:7fff
[   43.960782] hda_codec: invalid dep_range_val 0:7fff
[   43.960784] hda_codec: invalid dep_range_val 0:7fff
[   43.960868] hda_codec: invalid dep_range_val 0:7fff
[   43.960870] hda_codec: invalid dep_range_val 0:7fff
[   43.960954] hda_codec: invalid dep_range_val 0:7fff
[   43.960957] hda_codec: invalid dep_range_val 0:7fff
[   43.961041] hda_codec: invalid dep_range_val 0:7fff
[   43.961043] hda_codec: invalid dep_range_val 0:7fff
[   43.961127] hda_codec: invalid dep_range_val 0:7fff
[   43.961129] hda_codec: invalid dep_range_val 0:7fff
[   43.961212] hda_codec: invalid dep_range_val 0:7fff
[   43.961214] hda_codec: invalid dep_range_val 0:7fff
[   43.961298] hda_codec: invalid dep_range_val 0:7fff
[   43.961300] hda_codec: invalid dep_range_val 0:7fff
[   43.961384] hda_codec: invalid dep_range_val 0:7fff
[   43.961386] hda_codec: invalid dep_range_val 0:7fff
[   43.961469] hda_codec: invalid dep_range_val 0:7fff
[   43.961471] hda_codec: invalid dep_range_val 0:7fff
[   43.961555] hda_codec: invalid dep_range_val 0:7fff
[   43.961557] hda_codec: invalid dep_range_val 0:7fff
[   43.961640] hda_codec: invalid dep_range_val 0:7fff
[   43.961643] hda_codec: invalid dep_range_val 0:7fff
[   43.961726] hda_codec: invalid dep_range_val 0:7fff
[   43.961728] hda_codec: invalid dep_range_val 0:7fff
[   43.961811] hda_codec: invalid dep_range_val 0:7fff
[   43.961814] hda_codec: invalid dep_range_val 0:7fff
[   43.961897] hda_codec: invalid dep_range_val 0:7fff
[   43.962227] hda_codec: invalid dep_range_val 0:7fff
[   43.962229] hda_codec: invalid dep_range_val 0:7fff
[   43.962312] hda_codec: invalid dep_range_val 0:7fff
[   43.962314] hda_codec: invalid dep_range_val 0:7fff
[   43.962397] hda_codec: invalid dep_range_val 0:7fff
[   43.962399] hda_codec: invalid dep_range_val 0:7fff
[   43.962482] hda_codec: invalid dep_range_val 0:7fff
[   43.962485] hda_codec: invalid dep_range_val 0:7fff
[   43.962568] hda_codec: invalid dep_range_val 0:7fff
[   43.962570] hda_codec: invalid dep_range_val 0:7fff
[   43.962653] hda_codec: invalid dep_range_val 0:7fff
[   43.962655] hda_codec: invalid dep_range_val 0:7fff
[   43.962739] hda_codec: invalid dep_range_val 0:7fff
[   43.962741] hda_codec: invalid dep_range_val 0:7fff
[   43.962825] hda_codec: invalid dep_range_val 0:7fff
[   43.962827] hda_codec: invalid dep_range_val 0:7fff
[   43.962912] hda_codec: invalid dep_range_val 0:7fff
[   43.962914] hda_codec: invalid dep_range_val 0:7fff
[   43.962998] hda_codec: invalid dep_range_val 0:7fff
[   43.963000] hda_codec: invalid dep_range_val 0:7fff
[   43.963085] hda_codec: invalid dep_range_val 0:7fff
[   43.963087] hda_codec: invalid dep_range_val 0:7fff
[   43.963172] hda_codec: invalid dep_range_val 0:7fff
[   43.963174] hda_codec: invalid dep_range_val 0:7fff
[   43.963258] hda_codec: invalid dep_range_val 0:7fff
[   43.963260] hda_codec: invalid dep_range_val 0:7fff
[   43.963345] hda_codec: invalid dep_range_val 0:7fff
[   43.963347] hda_codec: invalid dep_range_val 0:7fff
[   43.963434] hda_codec: invalid dep_range_val 0:7fff
[   43.963436] hda_codec: invalid dep_range_val 0:7fff
[   43.963520] hda_codec: invalid dep_range_val 0:7fff
[   43.963522] hda_codec: invalid dep_range_val 0:7fff
[   43.963606] hda_codec: invalid dep_range_val 0:7fff
[   43.963608] hda_codec: invalid dep_range_val 0:7fff
[   43.963691] hda_codec: invalid dep_range_val 0:7fff
[   43.963693] hda_codec: invalid dep_range_val 0:7fff
[   43.963777] hda_codec: invalid dep_range_val 0:7fff
[   43.963779] hda_codec: invalid dep_range_val 0:7fff
[   43.963862] hda_codec: invalid dep_range_val 0:7fff
[   43.963865] hda_codec: invalid dep_range_val 0:7fff
[   43.963948] hda_codec: invalid dep_range_val 0:7fff
[   43.963950] hda_codec: invalid dep_range_val 0:7fff
[   43.964034] hda_codec: invalid dep_range_val 0:7fff
[   43.964036] hda_codec: invalid dep_range_val 0:7fff
[   43.964119] hda_codec: invalid dep_range_val 0:7fff
[   43.964122] hda_codec: invalid dep_range_val 0:7fff
[   43.964205] hda_codec: invalid dep_range_val 0:7fff
[   43.964207] hda_codec: invalid dep_range_val 0:7fff
[   43.964291] hda_codec: invalid dep_range_val 0:7fff
[   43.964293] hda_codec: invalid dep_range_val 0:7fff
[   43.964376] hda_codec: invalid dep_range_val 0:7fff
[   43.964379] hda_codec: invalid dep_range_val 0:7fff
[   43.964462] hda_codec: invalid dep_range_val 0:7fff
[   43.964464] hda_codec: invalid dep_range_val 0:7fff
[   43.964548] hda_codec: invalid dep_range_val 0:7fff
[   43.964550] hda_codec: invalid dep_range_val 0:7fff
[   43.964635] hda_codec: invalid dep_range_val 0:7fff
[   43.964637] hda_codec: invalid dep_range_val 0:7fff
[   43.964720] hda_codec: invalid dep_range_val 0:7fff
[   43.964723] hda_codec: invalid dep_range_val 0:7fff
[   43.964807] hda_codec: invalid dep_range_val 0:7fff
[   43.964809] hda_codec: invalid dep_range_val 0:7fff
[   43.964893] hda_codec: invalid dep_range_val 0:7fff
[   43.964896] hda_codec: invalid dep_range_val 0:7fff
[   43.964980] hda_codec: invalid dep_range_val 0:7fff
[   43.964982] hda_codec: invalid dep_range_val 0:7fff
[   43.965066] hda_codec: invalid dep_range_val 0:7fff
[   43.965068] hda_codec: invalid dep_range_val 0:7fff
[   43.965152] hda_codec: invalid dep_range_val 0:7fff
[   43.965154] hda_codec: invalid dep_range_val 0:7fff
[   43.965239] hda_codec: invalid dep_range_val 0:7fff
[   43.965241] hda_codec: invalid dep_range_val 0:7fff
[   43.965325] hda_codec: invalid dep_range_val 0:7fff
[   43.965327] hda_codec: invalid dep_range_val 0:7fff
[   43.965412] hda_codec: invalid dep_range_val 0:7fff
[   43.965414] hda_codec: invalid dep_range_val 0:7fff
[   43.965498] hda_codec: invalid dep_range_val 0:7fff
[   43.965500] hda_codec: invalid dep_range_val 0:7fff
[   43.965584] hda_codec: invalid dep_range_val 0:7fff
[   43.965586] hda_codec: invalid dep_range_val 0:7fff
[   43.965671] hda_codec: invalid dep_range_val 0:7fff
[   43.965673] hda_codec: invalid dep_range_val 0:7fff
[   43.965757] hda_codec: invalid dep_range_val 0:7fff
[   43.965759] hda_codec: invalid dep_range_val 0:7fff
[   43.965843] hda_codec: invalid dep_range_val 0:7fff
[   43.965846] hda_codec: invalid dep_range_val 0:7fff
[   43.965930] hda_codec: invalid dep_range_val 0:7fff
[   43.965932] hda_codec: invalid dep_range_val 0:7fff
[   43.966015] hda_codec: invalid dep_range_val 0:7fff
[   43.966017] hda_codec: invalid dep_range_val 0:7fff
[   43.966101] hda_codec: invalid dep_range_val 0:7fff
[   43.966103] hda_codec: invalid dep_range_val 0:7fff
[   43.966186] hda_codec: invalid dep_range_val 0:7fff
[   43.966188] hda_codec: invalid dep_range_val 0:7fff
[   43.966272] hda_codec: invalid dep_range_val 0:7fff
[   43.966274] hda_codec: invalid dep_range_val 0:7fff
[   43.966357] hda_codec: invalid dep_range_val 0:7fff
[   43.966359] hda_codec: invalid dep_range_val 0:7fff
[   43.966443] hda_codec: invalid dep_range_val 0:7fff
[   43.966445] hda_codec: invalid dep_range_val 0:7fff
[   43.966528] hda_codec: invalid dep_range_val 0:7fff
[   43.966530] hda_codec: invalid dep_range_val 0:7fff
[   43.966612] hda_codec: invalid dep_range_val 0:7fff
[   43.966614] hda_codec: invalid dep_range_val 0:7fff
[   43.966698] hda_codec: invalid dep_range_val 0:7fff
[   43.966700] hda_codec: invalid dep_range_val 0:7fff
[   43.966784] hda_codec: invalid dep_range_val 0:7fff
[   43.966787] hda_codec: invalid dep_range_val 0:7fff
[   43.966871] hda_codec: invalid dep_range_val 0:7fff
[   43.966874] hda_codec: invalid dep_range_val 0:7fff
[   43.966958] hda_codec: invalid dep_range_val 0:7fff
[   43.966960] hda_codec: invalid dep_range_val 0:7fff
[   43.967045] hda_codec: invalid dep_range_val 0:7fff
[   43.967047] hda_codec: invalid dep_range_val 0:7fff
[   43.967131] hda_codec: invalid dep_range_val 0:7fff
[   43.967134] hda_codec: invalid dep_range_val 0:7fff
[   43.967218] hda_codec: invalid dep_range_val 0:7fff
[   43.967220] hda_codec: invalid dep_range_val 0:7fff
[   43.967305] hda_codec: invalid dep_range_val 0:7fff
[   43.967307] hda_codec: invalid dep_range_val 0:7fff
[   43.967391] hda_codec: invalid dep_range_val 0:7fff
[   43.967393] hda_codec: invalid dep_range_val 0:7fff
[   43.967482] hda_codec: invalid dep_range_val 0:7fff
[   43.967484] hda_codec: invalid dep_range_val 0:7fff
[   43.967567] hda_codec: invalid dep_range_val 0:7fff
[   43.967569] hda_codec: invalid dep_range_val 0:7fff
[   43.967653] hda_codec: invalid dep_range_val 0:7fff
[   43.967982] hda_codec: invalid dep_range_val 0:7fff
[   43.967984] hda_codec: invalid dep_range_val 0:7fff
[   43.968068] hda_codec: invalid dep_range_val 0:7fff
[   43.968070] hda_codec: invalid dep_range_val 0:7fff
[   43.968154] hda_codec: invalid dep_range_val 0:7fff
[   43.968156] hda_codec: invalid dep_range_val 0:7fff
[   43.968241] hda_codec: invalid dep_range_val 0:7fff
[   43.968243] hda_codec: invalid dep_range_val 0:7fff
[   43.968326] hda_codec: invalid dep_range_val 0:7fff
[   43.968328] hda_codec: invalid dep_range_val 0:7fff
[   43.968411] hda_codec: invalid dep_range_val 0:7fff
[   43.968413] hda_codec: invalid dep_range_val 0:7fff
[   43.968496] hda_codec: invalid dep_range_val 0:7fff
[   43.968499] hda_codec: invalid dep_range_val 0:7fff
[   43.968583] hda_codec: invalid dep_range_val 0:7fff
[   43.968585] hda_codec: invalid dep_range_val 0:7fff
[   43.968662] hda_codec: invalid dep_range_val 0:7fff
[   43.968664] hda_codec: invalid dep_range_val 0:7fff
[   43.968726] hda_codec: invalid dep_range_val 0:7fff
[   43.968729] hda_codec: invalid dep_range_val 0:7fff
[   43.968789] hda_codec: invalid dep_range_val 0:7fff
[   43.968791] hda_codec: invalid dep_range_val 0:7fff
[   43.968852] hda_codec: invalid dep_range_val 0:7fff
[   43.968854] hda_codec: invalid dep_range_val 0:7fff
[   43.968916] hda_codec: invalid dep_range_val 0:7fff
[   43.968919] hda_codec: invalid dep_range_val 0:7fff
[   43.968980] hda_codec: invalid dep_range_val 0:7fff
[   43.968982] hda_codec: invalid dep_range_val 0:7fff
[   43.969043] hda_codec: invalid dep_range_val 0:7fff
[   43.969045] hda_codec: invalid dep_range_val 0:7fff
[   43.969106] hda_codec: invalid dep_range_val 0:7fff
[   43.969108] hda_codec: invalid dep_range_val 0:7fff
[   43.969170] hda_codec: invalid dep_range_val 0:7fff
[   43.969172] hda_codec: invalid dep_range_val 0:7fff
[   43.969233] hda_codec: invalid dep_range_val 0:7fff
[   43.969235] hda_codec: invalid dep_range_val 0:7fff
[   43.969295] hda_codec: invalid dep_range_val 0:7fff
[   43.969298] hda_codec: invalid dep_range_val 0:7fff
[   43.969360] hda_codec: invalid dep_range_val 0:7fff
[   43.969362] hda_codec: invalid dep_range_val 0:7fff
[   43.969423] hda_codec: invalid dep_range_val 0:7fff
[   43.969426] hda_codec: invalid dep_range_val 0:7fff
[   43.969486] hda_codec: invalid dep_range_val 0:7fff
[   43.969489] hda_codec: invalid dep_range_val 0:7fff
[   43.969551] hda_codec: invalid dep_range_val 0:7fff
[   43.969553] hda_codec: invalid dep_range_val 0:7fff
[   43.969615] hda_codec: invalid dep_range_val 0:7fff
[   43.969617] hda_codec: invalid dep_range_val 0:7fff
[   43.969678] hda_codec: invalid dep_range_val 0:7fff
[   43.969680] hda_codec: invalid dep_range_val 0:7fff
[   43.969742] hda_codec: invalid dep_range_val 0:7fff
[   43.969744] hda_codec: invalid dep_range_val 0:7fff
[   43.969806] hda_codec: invalid dep_range_val 0:7fff
[   43.969808] hda_codec: invalid dep_range_val 0:7fff
[   43.969868] hda_codec: invalid dep_range_val 0:7fff
[   43.969871] hda_codec: invalid dep_range_val 0:7fff
[   43.969933] hda_codec: invalid dep_range_val 0:7fff
[   43.969935] hda_codec: invalid dep_range_val 0:7fff
[   43.969996] hda_codec: invalid dep_range_val 0:7fff
[   43.969998] hda_codec: invalid dep_range_val 0:7fff
[   43.970063] hda_codec: invalid dep_range_val 0:7fff
[   43.970065] hda_codec: invalid dep_range_val 0:7fff
[   43.970150] hda_codec: invalid dep_range_val 0:7fff
[   43.970152] hda_codec: invalid dep_range_val 0:7fff
[   43.970235] hda_codec: invalid dep_range_val 0:7fff
[   43.970237] hda_codec: invalid dep_range_val 0:7fff
[   43.970321] hda_codec: invalid dep_range_val 0:7fff
[   43.970323] hda_codec: invalid dep_range_val 0:7fff
[   43.970407] hda_codec: invalid dep_range_val 0:7fff
[   43.970409] hda_codec: invalid dep_range_val 0:7fff
[   43.970492] hda_codec: invalid dep_range_val 0:7fff
[   43.970495] hda_codec: invalid dep_range_val 0:7fff
[   43.970578] hda_codec: invalid dep_range_val 0:7fff
[   43.970580] hda_codec: invalid dep_range_val 0:7fff
[   43.970664] hda_codec: invalid dep_range_val 0:7fff
[   43.970666] hda_codec: invalid dep_range_val 0:7fff
[   43.970749] hda_codec: invalid dep_range_val 0:7fff
[   43.970751] hda_codec: invalid dep_range_val 0:7fff
[   43.970835] hda_codec: invalid dep_range_val 0:7fff
[   43.970837] hda_codec: invalid dep_range_val 0:7fff
[   43.970920] hda_codec: invalid dep_range_val 0:7fff
[   43.970923] hda_codec: invalid dep_range_val 0:7fff
[   43.971006] hda_codec: invalid dep_range_val 0:7fff
[   43.971008] hda_codec: invalid dep_range_val 0:7fff
[   43.971092] hda_codec: invalid dep_range_val 0:7fff
[   43.971094] hda_codec: invalid dep_range_val 0:7fff
[   43.971177] hda_codec: invalid dep_range_val 0:7fff
[   43.971180] hda_codec: invalid dep_range_val 0:7fff
[   43.971263] hda_codec: invalid dep_range_val 0:7fff
[   43.971265] hda_codec: invalid dep_range_val 0:7fff
[   43.971349] hda_codec: invalid dep_range_val 0:7fff
[   43.971351] hda_codec: invalid dep_range_val 0:7fff
[   43.971437] hda_codec: invalid dep_range_val 0:7fff
[   43.971439] hda_codec: invalid dep_range_val 0:7fff
[   43.971523] hda_codec: invalid dep_range_val 0:7fff
[   43.971525] hda_codec: invalid dep_range_val 0:7fff
[   43.971609] hda_codec: invalid dep_range_val 0:7fff
[   43.971612] hda_codec: invalid dep_range_val 0:7fff
[   43.971696] hda_codec: invalid dep_range_val 0:7fff
[   43.971698] hda_codec: invalid dep_range_val 0:7fff
[   43.971782] hda_codec: invalid dep_range_val 0:7fff
[   43.971784] hda_codec: invalid dep_range_val 0:7fff
[   43.971868] hda_codec: invalid dep_range_val 0:7fff
[   43.971870] hda_codec: invalid dep_range_val 0:7fff
[   43.971955] hda_codec: invalid dep_range_val 0:7fff
[   43.971957] hda_codec: invalid dep_range_val 0:7fff
[   43.972041] hda_codec: invalid dep_range_val 0:7fff
[   43.972043] hda_codec: invalid dep_range_val 0:7fff
[   43.972110] hda_codec: invalid dep_range_val 0:7fff
[   43.972113] hda_codec: invalid dep_range_val 0:7fff
[   43.972174] hda_codec: invalid dep_range_val 0:7fff
[   43.972177] hda_codec: invalid dep_range_val 0:7fff
[   43.972239] hda_codec: invalid dep_range_val 0:7fff
[   43.972241] hda_codec: invalid dep_range_val 0:7fff
[   43.972302] hda_codec: invalid dep_range_val 0:7fff
[   43.972304] hda_codec: invalid dep_range_val 0:7fff
[   43.972365] hda_codec: invalid dep_range_val 0:7fff
[   43.972367] hda_codec: invalid dep_range_val 0:7fff
[   43.972429] hda_codec: invalid dep_range_val 0:7fff
[   43.972431] hda_codec: invalid dep_range_val 0:7fff
[   43.972515] hda_codec: invalid dep_range_val 0:7fff
[   43.972517] hda_codec: invalid dep_range_val 0:7fff
[   43.972600] hda_codec: invalid dep_range_val 0:7fff
[   43.972603] hda_codec: invalid dep_range_val 0:7fff
[   43.972671] hda_codec: invalid dep_range_val 0:7fff
[   43.972673] hda_codec: invalid dep_range_val 0:7fff
[   43.972735] hda_codec: invalid dep_range_val 0:7fff
[   44.078941] si3054: cannot initialize. EXT MID = 0000
[   44.431167] lp: driver loaded but no devices found
[   44.964892] EXT3 FS on loop0, internal journal
[   45.462944] kjournald starting.  Commit interval 5 seconds
[   45.463132] EXT3 FS on loop1, internal journal
[   45.463138] EXT3-fs: mounted filesystem with ordered data mode.
[   53.356135] Adding 872060k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:872060k
[   54.070985] ACPI: Battery Slot [BAT0] (battery present)
[   54.326844] No dock devices found.
[   54.365725] input: Power Button (FF) as /class/input/input6
[   54.366099] ACPI: Power Button (FF) [PWRF]
[   54.396186] input: Power Button (CM) as /class/input/input7
[   54.396246] ACPI: Power Button (CM) [PWRB]
[   54.396346] input: Lid Switch as /class/input/input8
[   54.396360] ACPI: Lid Switch [LID]
[   54.458811] ACPI: AC Adapter [ADP0] (on-line)
[   54.482649] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   54.825321] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 processors (version 2.00.00)
[   54.840647] powernow-k8:    0 : fid 0x9 (1700 MHz), vid 0x13
[   54.840653] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   54.840656] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a
[   56.784509] r8169: eth0: link down
[   56.866633] ppdev: user-space parallel port driver
[   57.056288] audit(1196995837.901:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5097 profile="/usr/sbin/cupsd"
[   57.501194] Failure registering capabilities with primary security module.
[   57.707780] Bluetooth: Core ver 2.11
[   57.707904] NET: Registered protocol family 31
[   57.707907] Bluetooth: HCI device and connection manager initialized
[   57.707912] Bluetooth: HCI socket layer initialized
[   57.725445] Bluetooth: L2CAP ver 2.8
[   57.725452] Bluetooth: L2CAP socket layer initialized
[   57.804482] Bluetooth: RFCOMM socket layer initialized
[   57.804506] Bluetooth: RFCOMM TTY layer initialized
[   57.804510] Bluetooth: RFCOMM ver 1.8

```

---

