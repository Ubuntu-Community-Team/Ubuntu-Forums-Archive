---
title: "permission problems."
date: 2008-08-18
forum: General Help
---

### Post by shamusl on 2008-08-18
sudo nautilus wont work, and I can't change the permissions on a folder.
I have no idea what I have to do beyond this point. the folder is classified as unreadable, and all of the files in it cant be changed there permissions.

---

### Post by Loaded.len on 2008-08-18
try 
```
gksu nautilus
```

---

### Post by shamusl on 2008-08-18
> **Loaded.len said:**
> try 
```
gksu nautilus
```

This won't work. It won't let me change permissions to anything but root.

---

### Post by p_quarles on 2008-08-18
What is the name of this folder?

---

### Post by Loaded.len on 2008-08-18
ahh, sorry.  I guess I misunderstood the question.  

What about sudo su?

---

### Post by shamusl on 2008-08-18
> **p_quarles said:**
> What is the name of this folder?

recup_dir.1 recup_dir.2 recup_dir.3 recup_dir.4

they were created by the photorec program. They are in:

/home/shamus/
and I need them:
/home/shamus/desktop
and I also need to burn them out to disc.

---

### Post by p_quarles on 2008-08-18
All right, let's see what one of them looks like. Run this command in a terminal:
```
ls -l ~/recup_dir.1
```
Then post the output back here.

---

### Post by shamusl on 2008-08-18
> **p_quarles said:**
> All right, let's see what one of them looks like. Run this command in a terminal:
```
ls -l ~/recup_dir.1
```
Then post the output back here.

```

-rw-r--r-- 1 root root  2048138 2008-08-18 00:53 f101794.mp3
-rw-r--r-- 1 root root  5406720 2008-08-18 00:53 f102295.mp4
-rw-r--r-- 1 root root  2547712 2008-08-18 00:53 f103615.mp4
-rw-r--r-- 1 root root  2539520 2008-08-18 00:53 f104237.mp4
-rw-r--r-- 1 root root  2719744 2008-08-18 00:53 f104857.mp4
-rw-r--r-- 1 root root  2617344 2008-08-18 00:53 f105521.mp4
-rw-r--r-- 1 root root  2629632 2008-08-18 00:53 f106160.mp4
-rw-r--r-- 1 root root  3379200 2008-08-18 00:53 f106802.mp4
-rw-r--r-- 1 root root  1986560 2008-08-18 00:53 f107627.mp4
-rw-r--r-- 1 root root  1282048 2008-08-18 00:53 f108112.mp4
-rw-r--r-- 1 root root  3485696 2008-08-18 00:53 f108425.mp4
-rw-r--r-- 1 root root  7817599 2008-08-18 00:52 f10886.mp3
-rw-r--r-- 1 root root  2555904 2008-08-18 00:53 f109276.mp4
-rw-r--r-- 1 root root  2658304 2008-08-18 00:53 f109900.mp4
-rw-r--r-- 1 root root  5091328 2008-08-18 00:53 f110549.mp4
-rw-r--r-- 1 root root 14936626 2008-08-18 00:53 f111792.mp3
-rw-r--r-- 1 root root  6273901 2008-08-18 00:53 f115439.mp3
-rw-r--r-- 1 root root  4326395 2008-08-18 00:53 f116977.mp3
-rw-r--r-- 1 root root  3469105 2008-08-18 00:53 f118040.mp3
-rw-r--r-- 1 root root  5944155 2008-08-18 00:53 f118887.mp3
-rw-r--r-- 1 root root  6715986 2008-08-18 00:53 f120339.mp3
-rw-r--r-- 1 root root  4382858 2008-08-18 00:53 f121979.mp3
-rw-r--r-- 1 root root 10946560 2008-08-18 00:53 f123050.mp3
-rw-r--r-- 1 root root  5703053 2008-08-18 00:53 f125729.mp3
-rw-r--r-- 1 root root  6269805 2008-08-18 00:53 f127122.mp3
-rw-r--r-- 1 root root  4259840 2008-08-18 00:52 f12805.mp4
-rw-r--r-- 1 root root  5009102 2008-08-18 00:53 f128658.mp3
-rw-r--r-- 1 root root  6957321 2008-08-18 00:53 f129881.mp3
-rw-r--r-- 1 root root  6590464 2008-08-18 00:53 f131586.mp4
-rw-r--r-- 1 root root     5527 2008-08-18 00:53 f133195.jpg
-rw-r--r-- 1 root root  7111518 2008-08-18 00:53 f133202.mp3
-rw-r--r-- 1 root root    66351 2008-08-18 00:53 f134945.mp3
-rw-r--r-- 1 root root  2387955 2008-08-18 00:53 f134986.mp3
-rw-r--r-- 1 root root  3153128 2008-08-18 00:53 f135601.mp3
-rw-r--r-- 1 root root  5005312 2008-08-18 00:53 f136371.mp4
-rw-r--r-- 1 root root  1720125 2008-08-18 00:53 f137593.mp3
-rw-r--r-- 1 root root  3720212 2008-08-18 00:53 f138301.mp3
-rw-r--r-- 1 root root  3137536 2008-08-18 00:53 f13845.mp4
-rw-r--r-- 1 root root  4904838 2008-08-18 00:53 f139210.mp3
-rw-r--r-- 1 root root  6136476 2008-08-18 00:53 f140408.mp3
-rw-r--r-- 1 root root 13499676 2008-08-18 00:53 f141907.mp3
-rw-r--r-- 1 root root  3773359 2008-08-18 00:53 f145203.mp3
-rw-r--r-- 1 root root  3534848 2008-08-18 00:53 f14611.mp4
-rw-r--r-- 1 root root  3773359 2008-08-18 00:53 f146125.mp3
-rw-r--r-- 1 root root  3301376 2008-08-18 00:53 f147093.mp4
-rw-r--r-- 1 root root  3170304 2008-08-18 00:53 f147899.mp4
-rw-r--r-- 1 root root  3289088 2008-08-18 00:53 f148673.mp4
-rw-r--r-- 1 root root  3354624 2008-08-18 00:53 f149476.mp4
-rw-r--r-- 1 root root  3170304 2008-08-18 00:53 f150295.mp4
-rw-r--r-- 1 root root  2408448 2008-08-18 00:53 f151069.mp4
-rw-r--r-- 1 root root  4341760 2008-08-18 00:53 f151657.mp4
-rw-r--r-- 1 root root  3690496 2008-08-18 00:53 f152717.mp4
-rw-r--r-- 1 root root  3330048 2008-08-18 00:53 f153618.mp4
-rw-r--r-- 1 root root  4587520 2008-08-18 00:53 f154431.mp4
-rw-r--r-- 1 root root  4489216 2008-08-18 00:53 f15474.mp4
-rw-r--r-- 1 root root  4153344 2008-08-18 00:53 f155551.mp4
-rw-r--r-- 1 root root  3866624 2008-08-18 00:53 f156565.mp4
-rw-r--r-- 1 root root  4573184 2008-08-18 00:53 f157509.mp3
-rw-r--r-- 1 root root  6064740 2008-08-18 00:53 f158626.mp3
-rw-r--r-- 1 root root  5864210 2008-08-18 00:53 f160107.mp3
-rw-r--r-- 1 root root  1660492 2008-08-18 00:53 f162068.mp3
-rw-r--r-- 1 root root  3475757 2008-08-18 00:53 f162474.mp3
-rw-r--r-- 1 root root   259469 2008-08-18 00:53 f163323.mp3
-rw-r--r-- 1 root root  3816847 2008-08-18 00:53 f163387.mp3
-rw-r--r-- 1 root root  3292724 2008-08-18 00:53 f164319.mp3
-rw-r--r-- 1 root root  4974759 2008-08-18 00:53 f165123.mp3
-rw-r--r-- 1 root root  4153344 2008-08-18 00:53 f16570.mp4
-rw-r--r-- 1 root root  5568889 2008-08-18 00:53 f166340.mp3
-rw-r--r-- 1 root root  3413473 2008-08-18 00:53 f167702.mp3
-rw-r--r-- 1 root root  3994435 2008-08-18 00:53 f168541.mp3
-rw-r--r-- 1 root root  4112825 2008-08-18 00:53 f169517.mp3
-rw-r--r-- 1 root root  5118916 2008-08-18 00:53 f170527.mp3
-rw-r--r-- 1 root root  3629056 2008-08-18 00:53 f171781.mp4
-rw-r--r-- 1 root root  3854336 2008-08-18 00:54 f172667.mp4
-rw-r--r-- 1 root root  2863104 2008-08-18 00:54 f173608.mp4
-rw-r--r-- 1 root root  4419584 2008-08-18 00:54 f174307.mp4
-rw-r--r-- 1 root root  2543616 2008-08-18 00:54 f175386.mp4
-rw-r--r-- 1 root root  3215360 2008-08-18 00:53 f17584.mp4
-rw-r--r-- 1 root root  2940928 2008-08-18 00:54 f176007.mp4
-rw-r--r-- 1 root root  3371008 2008-08-18 00:54 f176725.mp4
-rw-r--r-- 1 root root  3612672 2008-08-18 00:54 f177548.mp4
-rw-r--r-- 1 root root  3366912 2008-08-18 00:54 f178430.mp4
-rw-r--r-- 1 root root  2723840 2008-08-18 00:54 f179252.mp4
-rw-r--r-- 1 root root  1769472 2008-08-18 00:54 f179917.mp4
-rw-r--r-- 1 root root  3661824 2008-08-18 00:54 f180349.mp4
-rw-r--r-- 1 root root  3166208 2008-08-18 00:54 f181243.mp4
-rw-r--r-- 1 root root  4100096 2008-08-18 00:54 f182016.mp4
-rw-r--r-- 1 root root  3182592 2008-08-18 00:54 f183017.mp4
-rw-r--r-- 1 root root  4878336 2008-08-18 00:53 f18370.mp4
-rw-r--r-- 1 root root  6127616 2008-08-18 00:54 f183794.mp4
-rw-r--r-- 1 root root  3600384 2008-08-18 00:54 f185290.mp4
-rw-r--r-- 1 root root  3600384 2008-08-18 00:54 f186169.mp4
-rw-r--r-- 1 root root  5586944 2008-08-18 00:54 f187048.mp4
-rw-r--r-- 1 root root  7282688 2008-08-18 00:54 f188412.mp4
-rw-r--r-- 1 root root  1502991 2008-08-18 00:54 f190190.mp3
-rw-r--r-- 1 root root  6987567 2008-08-18 00:54 f191824.mp3
-rw-r--r-- 1 root root 16691200 2008-08-18 00:54 f193535.mp4
-rw-r--r-- 1 root root  2871296 2008-08-18 00:53 f19562.mp4
-rw-r--r-- 1 root root 11173888 2008-08-18 00:54 f197610.mp4
-rw-r--r-- 1 root root    11575 2008-08-18 00:54 f200338.jpg
-rw-r--r-- 1 root root  1421312 2008-08-18 00:54 f200428.mp4
-rw-r--r-- 1 root root    11575 2008-08-18 00:54 f200775.jpg
-rw-r--r-- 1 root root  1396736 2008-08-18 00:54 f200778.mp4
-rw-r--r-- 1 root root    11575 2008-08-18 00:54 f201119.jpg
-rw-r--r-- 1 root root  5328896 2008-08-18 00:54 f201122.mp4
-rw-r--r-- 1 root root    10064 2008-08-18 00:54 f202423.jpg
-rw-r--r-- 1 root root  8683520 2008-08-18 00:54 f202426.mp4
-rw-r--r-- 1 root root  4911104 2008-08-18 00:53 f20264.mp4
-rw-r--r-- 1 root root    10064 2008-08-18 00:54 f204546.jpg
-rw-r--r-- 1 root root  9584640 2008-08-18 00:54 f204549.mp4
-rw-r--r-- 1 root root    10064 2008-08-18 00:54 f206889.jpg
-rw-r--r-- 1 root root  6086656 2008-08-18 00:54 f206892.mp4
-rw-r--r-- 1 root root    10064 2008-08-18 00:54 f208378.jpg
-rw-r--r-- 1 root root  7000064 2008-08-18 00:54 f208381.mp4
-rw-r--r-- 1 root root    10064 2008-08-18 00:54 f210090.jpg
-rw-r--r-- 1 root root  5124096 2008-08-18 00:54 f210093.mp4
-rw-r--r-- 1 root root    10064 2008-08-18 00:54 f211344.jpg
-rw-r--r-- 1 root root  7155712 2008-08-18 00:54 f211347.mp4
-rw-r--r-- 1 root root    10064 2008-08-18 00:54 f213094.jpg
-rw-r--r-- 1 root root  4681728 2008-08-18 00:54 f213097.mp4
-rw-r--r-- 1 root root    10064 2008-08-18 00:54 f214240.jpg
-rw-r--r-- 1 root root  3366912 2008-08-18 00:54 f214243.mp4
-rw-r--r-- 1 root root  3184766 2008-08-18 00:53 f21470.mp3
-rw-r--r-- 1 root root     4667 2008-08-18 00:54 f215065.jpg
-rw-r--r-- 1 root root  3768320 2008-08-18 00:54 f215067.mp4
-rw-r--r-- 1 root root     4667 2008-08-18 00:54 f215987.jpg
-rw-r--r-- 1 root root  2019328 2008-08-18 00:54 f215989.mp4
-rw-r--r-- 1 root root     4667 2008-08-18 00:54 f216482.jpg
-rw-r--r-- 1 root root  6381568 2008-08-18 00:54 f216484.mp4
-rw-r--r-- 1 root root     4667 2008-08-18 00:54 f218042.jpg
-rw-r--r-- 1 root root  3485696 2008-08-18 00:54 f218044.mp4
-rw-r--r-- 1 root root     4667 2008-08-18 00:54 f218895.jpg
-rw-r--r-- 1 root root  3928064 2008-08-18 00:54 f218897.mp4
-rw-r--r-- 1 root root     4667 2008-08-18 00:54 f219856.jpg
-rw-r--r-- 1 root root  4632576 2008-08-18 00:54 f219858.mp4
-rw-r--r-- 1 root root     4667 2008-08-18 00:54 f220989.jpg
-rw-r--r-- 1 root root  6938624 2008-08-18 00:54 f220992.mp4
-rw-r--r-- 1 root root  2773125 2008-08-18 00:53 f22255.mp3
-rw-r--r-- 1 root root     4667 2008-08-18 00:54 f222686.jpg
-rw-r--r-- 1 root root  7512064 2008-08-18 00:54 f222693.mp4
-rw-r--r-- 1 root root  3543168 2008-08-18 00:54 f224527.mp3
-rw-r--r-- 1 root root  3780986 2008-08-18 00:54 f225393.mp3
-rw-r--r-- 1 root root  1237705 2008-08-18 00:54 f226317.mp3
-rw-r--r-- 1 root root  1237723 2008-08-18 00:54 f226620.mp3
-rw-r--r-- 1 root root  3543186 2008-08-18 00:54 f226923.mp3
-rw-r--r-- 1 root root  3781005 2008-08-18 00:54 f227789.mp3
-rw-r--r-- 1 root root  6562136 2008-08-18 00:54 f228713.mp3
-rw-r--r-- 1 root root  4820393 2008-08-18 00:53 f22940.mp3
-rw-r--r-- 1 root root  4203543 2008-08-18 00:54 f230321.mp3
-rw-r--r-- 1 root root  5384696 2008-08-18 00:54 f231348.mp3
-rw-r--r-- 1 root root  2695964 2008-08-18 00:54 f232663.mp3
-rw-r--r-- 1 root root  1033323 2008-08-18 00:54 f233322.mp3
-rw-r--r-- 1 root root  4525372 2008-08-18 00:54 f233575.mp3
-rw-r--r-- 1 root root  3174945 2008-08-18 00:54 f234684.mp3
-rw-r--r-- 1 root root  3174945 2008-08-18 00:54 f235460.mp3
-rw-r--r-- 1 root root  4108248 2008-08-18 00:54 f236236.mp3
-rw-r--r-- 1 root root  2565561 2008-08-18 00:54 f237239.mp3
-rw-r--r-- 1 root root  5322838 2008-08-18 00:54 f237866.mp3
-rw-r--r-- 1 root root  3281525 2008-08-18 00:54 f239166.mp3
-rw-r--r-- 1 root root  1502273 2008-08-18 00:54 f239968.mp3
-rw-r--r-- 1 root root  1644797 2008-08-18 00:54 f240335.mp3
-rw-r--r-- 1 root root  4205633 2008-08-18 00:54 f240737.mp3
-rw-r--r-- 1 root root  4145152 2008-08-18 00:53 f24123.mp4
-rw-r--r-- 1 root root   559775 2008-08-18 00:54 f241764.mp3
-rw-r--r-- 1 root root  1294129 2008-08-18 00:54 f241901.mp3
-rw-r--r-- 1 root root  1550756 2008-08-18 00:54 f242217.mp3
-rw-r--r-- 1 root root  2379569 2008-08-18 00:54 f242596.mp3
-rw-r--r-- 1 root root  3787256 2008-08-18 00:54 f243177.mp3
-rw-r--r-- 1 root root  1973731 2008-08-18 00:54 f244102.mp3
-rw-r--r-- 1 root root  3389440 2008-08-18 00:54 f244584.mp3
-rw-r--r-- 1 root root  3473408 2008-08-18 00:54 f245417.mp4
-rw-r--r-- 1 root root  5189904 2008-08-18 00:54 f246265.mp3
-rw-r--r-- 1 root root 19596711 2008-08-18 00:54 f247533.mp3
-rw-r--r-- 1 root root  3426825 2008-08-18 00:53 f25135.mp3
-rw-r--r-- 1 root root 14856320 2008-08-18 00:54 f252318.mp3
-rw-r--r-- 1 root root  7241728 2008-08-18 00:54 f255946.mp4
-rw-r--r-- 1 root root  5075471 2008-08-18 00:54 f257714.mp3
-rw-r--r-- 1 root root    65561 2008-08-18 00:54 f258996.mp3
-rw-r--r-- 1 root root  5735781 2008-08-18 00:54 f259127.mp3
-rw-r--r-- 1 root root  3981736 2008-08-18 00:53 f25979.mp3
-rw-r--r-- 1 root root  6564396 2008-08-18 00:54 f260596.mp3
-rw-r--r-- 1 root root  6190103 2008-08-18 00:54 f262207.mp3
-rw-r--r-- 1 root root  4968177 2008-08-18 00:54 f263727.mp3
-rw-r--r-- 1 root root  4653202 2008-08-18 00:54 f264948.mp3
-rw-r--r-- 1 root root  3514943 2008-08-18 00:54 f266154.mp3
-rw-r--r-- 1 root root  2773393 2008-08-18 00:54 f267117.mp3
-rw-r--r-- 1 root root   163500 2008-08-18 00:54 f267807.mp3
-rw-r--r-- 1 root root  4259880 2008-08-18 00:54 f267860.mp3
-rw-r--r-- 1 root root  5675037 2008-08-18 00:54 f269252.mp3
-rw-r--r-- 1 root root  3263601 2008-08-18 00:53 f26958.mp3
-rw-r--r-- 1 root root  7817599 2008-08-18 00:54 f272186.mp3
-rw-r--r-- 1 root root  4007810 2008-08-18 00:53 f27760.mp3
-rw-r--r-- 1 root root  4474253 2008-08-18 00:53 f28744.mp3
-rw-r--r-- 1 root root  5144885 2008-08-18 00:53 f29845.mp3
-rw-r--r-- 1 root root  3502286 2008-08-18 00:53 f31108.mp3
-rw-r--r-- 1 root root    71646 2008-08-18 00:54 f316096.html
-rw-r--r-- 1 root root   371500 2008-08-18 00:54 f316114.txt
-rw-r--r-- 1 root root    22838 2008-08-18 00:54 f316588.jpg
-rw-r--r-- 1 root root   434418 2008-08-18 00:54 f317872.txt
-rw-r--r-- 1 root root     6841 2008-08-18 00:54 f317979.txt
-rw-r--r-- 1 root root     5808 2008-08-18 00:54 f318078.txt
-rw-r--r-- 1 root root     6276 2008-08-18 00:54 f318169.txt
-rw-r--r-- 1 root root     6488 2008-08-18 00:54 f318261.txt
-rw-r--r-- 1 root root     6761 2008-08-18 00:54 f318353.txt
-rw-r--r-- 1 root root     6238 2008-08-18 00:54 f318440.txt
-rw-r--r-- 1 root root     6621 2008-08-18 00:54 f318532.txt
-rw-r--r-- 1 root root     5532 2008-08-18 00:54 f318629.txt
-rw-r--r-- 1 root root     7114 2008-08-18 00:54 f318724.txt
-rw-r--r-- 1 root root     5051 2008-08-18 00:54 f318799.txt
-rw-r--r-- 1 root root     7416 2008-08-18 00:54 f318867.txt
-rw-r--r-- 1 root root     5222 2008-08-18 00:54 f318961.txt
-rw-r--r-- 1 root root     7618 2008-08-18 00:54 f319048.txt
-rw-r--r-- 1 root root     6719 2008-08-18 00:54 f319141.txt
-rw-r--r-- 1 root root     6637 2008-08-18 00:54 f319229.txt
-rw-r--r-- 1 root root     5979 2008-08-18 00:54 f319321.txt
-rw-r--r-- 1 root root     6222 2008-08-18 00:54 f319392.txt
-rw-r--r-- 1 root root     4314 2008-08-18 00:54 f319485.txt
-rw-r--r-- 1 root root     6725 2008-08-18 00:54 f319539.txt
-rw-r--r-- 1 root root     5158 2008-08-18 00:54 f319601.txt
-rw-r--r-- 1 root root     6353 2008-08-18 00:54 f319663.txt
-rw-r--r-- 1 root root     6751 2008-08-18 00:54 f319725.txt
-rw-r--r-- 1 root root  9739580 2008-08-18 00:53 f31972.mp3
-rw-r--r-- 1 root root     6515 2008-08-18 00:54 f319803.txt
-rw-r--r-- 1 root root     6478 2008-08-18 00:54 f320038.txt
-rw-r--r-- 1 root root     7789 2008-08-18 00:54 f320103.txt
-rw-r--r-- 1 root root     6477 2008-08-18 00:54 f320162.txt
-rw-r--r-- 1 root root     7536 2008-08-18 00:54 f320218.txt
-rw-r--r-- 1 root root     7417 2008-08-18 00:54 f320272.txt
-rw-r--r-- 1 root root     6957 2008-08-18 00:54 f320327.txt
-rw-r--r-- 1 root root     4400 2008-08-18 00:54 f320381.txt
-rw-r--r-- 1 root root     6885 2008-08-18 00:54 f320436.txt
-rw-r--r-- 1 root root     4930 2008-08-18 00:54 f320492.txt
-rw-r--r-- 1 root root     6879 2008-08-18 00:54 f320548.txt
-rw-r--r-- 1 root root     6109 2008-08-18 00:54 f320603.txt
-rw-r--r-- 1 root root     5877 2008-08-18 00:54 f320661.txt
-rw-r--r-- 1 root root     7376 2008-08-18 00:54 f320713.txt
-rw-r--r-- 1 root root     5539 2008-08-18 00:54 f320766.txt
-rw-r--r-- 1 root root     5682 2008-08-18 00:54 f320822.txt
-rw-r--r-- 1 root root     6929 2008-08-18 00:54 f320878.txt
-rw-r--r-- 1 root root     7864 2008-08-18 00:54 f320931.txt
-rw-r--r-- 1 root root     7646 2008-08-18 00:54 f320984.txt
-rw-r--r-- 1 root root     6797 2008-08-18 00:54 f321036.txt
-rw-r--r-- 1 root root     7844 2008-08-18 00:54 f321089.txt
-rw-r--r-- 1 root root     6799 2008-08-18 00:54 f321143.txt
-rw-r--r-- 1 root root     5147 2008-08-18 00:54 f321195.txt
-rw-r--r-- 1 root root     6028 2008-08-18 00:54 f321249.txt
-rw-r--r-- 1 root root     6684 2008-08-18 00:54 f321304.txt
-rw-r--r-- 1 root root     5025 2008-08-18 00:54 f321360.txt
-rw-r--r-- 1 root root     7423 2008-08-18 00:54 f321414.txt
-rw-r--r-- 1 root root     6015 2008-08-18 00:54 f321470.txt
-rw-r--r-- 1 root root     7635 2008-08-18 00:54 f321525.txt
-rw-r--r-- 1 root root     6501 2008-08-18 00:54 f321585.txt
-rw-r--r-- 1 root root     5547 2008-08-18 00:54 f321642.txt
-rw-r--r-- 1 root root     4320 2008-08-18 00:54 f321701.txt
-rw-r--r-- 1 root root     7081 2008-08-18 00:54 f321758.txt
-rw-r--r-- 1 root root     6551 2008-08-18 00:54 f321817.txt
-rw-r--r-- 1 root root     7673 2008-08-18 00:54 f321858.txt
-rw-r--r-- 1 root root     4322 2008-08-18 00:54 f321919.txt
-rw-r--r-- 1 root root     6606 2008-08-18 00:54 f321983.txt
-rw-r--r-- 1 root root      130 2008-08-18 00:54 f322045.txt
-rw-r--r-- 1 root root     7882 2008-08-18 00:54 f322104.txt
-rw-r--r-- 1 root root     6019 2008-08-18 00:54 f322165.txt
-rw-r--r-- 1 root root     7033 2008-08-18 00:54 f322222.txt
-rw-r--r-- 1 root root     7913 2008-08-18 00:54 f322287.txt
-rw-r--r-- 1 root root     6887 2008-08-18 00:54 f322353.txt
-rw-r--r-- 1 root root     5619 2008-08-18 00:54 f322420.txt
-rw-r--r-- 1 root root     6858 2008-08-18 00:54 f322543.txt
-rw-r--r-- 1 root root     6814 2008-08-18 00:54 f322602.txt
-rw-r--r-- 1 root root     5104 2008-08-18 00:54 f322665.txt
-rw-r--r-- 1 root root     4735 2008-08-18 00:54 f322736.txt
-rw-r--r-- 1 root root     7524 2008-08-18 00:54 f322804.txt
-rw-r--r-- 1 root root     6266 2008-08-18 00:54 f322865.txt
-rw-r--r-- 1 root root     7785 2008-08-18 00:54 f322920.txt
-rw-r--r-- 1 root root     5841 2008-08-18 00:54 f322981.txt
-rw-r--r-- 1 root root     5628 2008-08-18 00:54 f323033.txt
-rw-r--r-- 1 root root     5295 2008-08-18 00:54 f323082.txt
-rw-r--r-- 1 root root     7194 2008-08-18 00:54 f323137.txt
-rw-r--r-- 1 root root     4776 2008-08-18 00:54 f323196.txt
-rw-r--r-- 1 root root     5467 2008-08-18 00:54 f323255.txt
-rw-r--r-- 1 root root     7346 2008-08-18 00:54 f323321.txt
-rw-r--r-- 1 root root     7415 2008-08-18 00:54 f323445.txt
-rw-r--r-- 1 root root     6892 2008-08-18 00:54 f323499.txt
-rw-r--r-- 1 root root     7284 2008-08-18 00:54 f323557.txt
-rw-r--r-- 1 root root     5736 2008-08-18 00:54 f323619.txt
-rw-r--r-- 1 root root     5494 2008-08-18 00:54 f323678.txt
-rw-r--r-- 1 root root     5421 2008-08-18 00:54 f323740.txt
-rw-r--r-- 1 root root     6205 2008-08-18 00:54 f323795.txt
-rw-r--r-- 1 root root     6422 2008-08-18 00:54 f323846.txt
-rw-r--r-- 1 root root     5700 2008-08-18 00:54 f323897.txt
-rw-r--r-- 1 root root     4493 2008-08-18 00:54 f323954.txt
-rw-r--r-- 1 root root     6593 2008-08-18 00:54 f324009.txt
-rw-r--r-- 1 root root     7541 2008-08-18 00:54 f324062.txt
-rw-r--r-- 1 root root     4596 2008-08-18 00:54 f324111.txt
-rw-r--r-- 1 root root     7622 2008-08-18 00:54 f324164.txt
-rw-r--r-- 1 root root     6719 2008-08-18 00:54 f324227.txt
-rw-r--r-- 1 root root      192 2008-08-18 00:54 f324339.txt
-rw-r--r-- 1 root root     6999 2008-08-18 00:54 f324403.txt
-rw-r--r-- 1 root root     6036 2008-08-18 00:54 f324469.txt
-rw-r--r-- 1 root root     6905 2008-08-18 00:54 f324534.txt
-rw-r--r-- 1 root root     6476 2008-08-18 00:54 f324596.txt
-rw-r--r-- 1 root root     5777 2008-08-18 00:54 f324655.txt
-rw-r--r-- 1 root root     6120 2008-08-18 00:54 f324717.txt
-rw-r--r-- 1 root root     5971 2008-08-18 00:54 f324779.txt
-rw-r--r-- 1 root root     6534 2008-08-18 00:54 f324839.txt
-rw-r--r-- 1 root root     7184 2008-08-18 00:54 f324906.txt
-rw-r--r-- 1 root root     5750 2008-08-18 00:54 f324969.txt
-rw-r--r-- 1 root root     7298 2008-08-18 00:54 f325041.txt
-rw-r--r-- 1 root root     7743 2008-08-18 00:54 f325096.txt
-rw-r--r-- 1 root root     4804 2008-08-18 00:54 f325159.txt
-rw-r--r-- 1 root root     7963 2008-08-18 00:54 f325219.txt
-rw-r--r-- 1 root root     7900 2008-08-18 00:54 f325345.txt
-rw-r--r-- 1 root root     5973 2008-08-18 00:54 f325413.txt
-rw-r--r-- 1 root root     6589 2008-08-18 00:54 f325472.txt
-rw-r--r-- 1 root root     7125 2008-08-18 00:54 f325531.txt
-rw-r--r-- 1 root root     7475 2008-08-18 00:54 f325592.txt
-rw-r--r-- 1 root root     7593 2008-08-18 00:54 f325650.txt
-rw-r--r-- 1 root root     4672 2008-08-18 00:54 f325714.txt
-rw-r--r-- 1 root root     5230 2008-08-18 00:54 f325773.txt
-rw-r--r-- 1 root root      190 2008-08-18 00:54 f325838.txt
-rw-r--r-- 1 root root     6196 2008-08-18 00:54 f325900.txt
-rw-r--r-- 1 root root     4557 2008-08-18 00:54 f325950.txt
-rw-r--r-- 1 root root     7341 2008-08-18 00:54 f325993.txt
-rw-r--r-- 1 root root     4767 2008-08-18 00:54 f326040.txt
-rw-r--r-- 1 root root      111 2008-08-18 00:54 f326086.txt
-rw-r--r-- 1 root root     7888 2008-08-18 00:54 f326130.txt
-rw-r--r-- 1 root root     7476 2008-08-18 00:54 f326177.txt
-rw-r--r-- 1 root root     7772 2008-08-18 00:54 f326228.txt
-rw-r--r-- 1 root root     6710 2008-08-18 00:54 f326275.txt
-rw-r--r-- 1 root root     7149 2008-08-18 00:54 f326320.txt
-rw-r--r-- 1 root root     4566 2008-08-18 00:54 f326371.txt
-rw-r--r-- 1 root root     5273 2008-08-18 00:54 f326417.txt
-rw-r--r-- 1 root root     5376 2008-08-18 00:54 f326458.txt
-rw-r--r-- 1 root root     4604 2008-08-18 00:54 f326504.txt
-rw-r--r-- 1 root root     4930 2008-08-18 00:54 f326551.txt
-rw-r--r-- 1 root root     5499 2008-08-18 00:54 f326591.txt
-rw-r--r-- 1 root root     4341 2008-08-18 00:54 f326635.txt
-rw-r--r-- 1 root root     7927 2008-08-18 00:54 f326682.txt
-rw-r--r-- 1 root root     5052 2008-08-18 00:54 f326729.txt
-rw-r--r-- 1 root root     6686 2008-08-18 00:54 f326775.txt
-rw-r--r-- 1 root root     6797 2008-08-18 00:54 f326826.txt
-rw-r--r-- 1 root root     5855 2008-08-18 00:54 f326873.txt
-rw-r--r-- 1 root root     5835 2008-08-18 00:54 f326915.txt
-rw-r--r-- 1 root root     4580 2008-08-18 00:54 f326960.txt
-rw-r--r-- 1 root root     5152 2008-08-18 00:54 f327011.txt
-rw-r--r-- 1 root root     4450 2008-08-18 00:54 f327060.txt
-rw-r--r-- 1 root root     7541 2008-08-18 00:54 f327123.txt
-rw-r--r-- 1 root root     5803 2008-08-18 00:54 f327186.txt
-rw-r--r-- 1 root root     7116 2008-08-18 00:54 f327315.txt
-rw-r--r-- 1 root root     8052 2008-08-18 00:54 f327377.txt
-rw-r--r-- 1 root root     6894 2008-08-18 00:54 f327501.txt
-rw-r--r-- 1 root root     7702 2008-08-18 00:54 f327563.txt
-rw-r--r-- 1 root root     5339 2008-08-18 00:54 f327630.txt
-rw-r--r-- 1 root root     6104 2008-08-18 00:54 f327690.txt
-rw-r--r-- 1 root root     7416 2008-08-18 00:54 f327750.txt
-rw-r--r-- 1 root root     5976 2008-08-18 00:54 f327810.txt
-rw-r--r-- 1 root root     6904 2008-08-18 00:54 f327879.txt
-rw-r--r-- 1 root root     7251 2008-08-18 00:54 f327944.txt
-rw-r--r-- 1 root root     4685 2008-08-18 00:54 f328001.txt
-rw-r--r-- 1 root root     5062 2008-08-18 00:54 f328065.txt
-rw-r--r-- 1 root root     6711 2008-08-18 00:54 f328126.txt
-rw-r--r-- 1 root root     5787 2008-08-18 00:54 f328188.txt
-rw-r--r-- 1 root root     6407 2008-08-18 00:54 f328254.txt
-rw-r--r-- 1 root root     5467 2008-08-18 00:54 f328326.txt
-rw-r--r-- 1 root root     5288 2008-08-18 00:54 f328401.txt
-rw-r--r-- 1 root root     4453 2008-08-18 00:54 f328457.txt
-rw-r--r-- 1 root root     4377 2008-08-18 00:54 f328515.txt
-rw-r--r-- 1 root root     5843 2008-08-18 00:54 f328568.txt
-rw-r--r-- 1 root root     5389 2008-08-18 00:54 f328626.txt
-rw-r--r-- 1 root root     6720 2008-08-18 00:54 f328703.txt
-rw-r--r-- 1 root root     8002 2008-08-18 00:54 f328776.txt
-rw-r--r-- 1 root root     7264 2008-08-18 00:54 f328846.txt
-rw-r--r-- 1 root root     6773 2008-08-18 00:54 f328919.txt
-rw-r--r-- 1 root root     5360 2008-08-18 00:54 f328981.txt
-rw-r--r-- 1 root root     6535 2008-08-18 00:54 f329043.txt
-rw-r--r-- 1 root root     5148 2008-08-18 00:54 f329113.txt
-rw-r--r-- 1 root root     6374 2008-08-18 00:54 f329184.txt
-rw-r--r-- 1 root root     6855 2008-08-18 00:54 f329259.txt
-rw-r--r-- 1 root root     6803 2008-08-18 00:54 f329334.txt
-rw-r--r-- 1 root root     6575 2008-08-18 00:54 f329402.txt
-rw-r--r-- 1 root root     7864 2008-08-18 00:54 f329554.txt
-rw-r--r-- 1 root root     4947 2008-08-18 00:54 f329629.txt
-rw-r--r-- 1 root root     5204 2008-08-18 00:54 f329701.txt
-rw-r--r-- 1 root root     6439 2008-08-18 00:54 f329775.txt
-rw-r--r-- 1 root root     4454 2008-08-18 00:54 f329846.txt
-rw-r--r-- 1 root root     6424 2008-08-18 00:54 f329909.txt
-rw-r--r-- 1 root root     6919 2008-08-18 00:54 f329972.txt
-rw-r--r-- 1 root root     6643 2008-08-18 00:54 f330040.txt
-rw-r--r-- 1 root root     6420 2008-08-18 00:54 f330108.txt
-rw-r--r-- 1 root root     6863 2008-08-18 00:54 f330178.txt
-rw-r--r-- 1 root root     7593 2008-08-18 00:54 f330322.txt
-rw-r--r-- 1 root root  3592275 2008-08-18 00:53 f34356.mp3
-rw-r--r-- 1 root root 10614227 2008-08-18 00:53 f35234.mp3
-rw-r--r-- 1 root root  1133377 2008-08-18 00:55 f370050.zip
-rw-r--r-- 1 root root      634 2008-08-18 00:55 f370330.txt
-rw-r--r-- 1 root root  6777709 2008-08-18 00:53 f37832.mp3
-rw-r--r-- 1 root root     4096 2008-08-18 00:52 f3828.xml
-rw-r--r-- 1 root root     4096 2008-08-18 00:52 f3832.txt
-rw-r--r-- 1 root root   226916 2008-08-18 00:55 f386371.jpg
-rw-r--r-- 1 root root     5540 2008-08-18 00:55 f393273.jpg
-rw-r--r-- 1 root root     2932 2008-08-18 00:55 f393279.jpg
-rw-r--r-- 1 root root     3047 2008-08-18 00:55 f393293.jpg
-rw-r--r-- 1 root root  4678228 2008-08-18 00:53 f39487.mp3
-rw-r--r-- 1 root root  3188702 2008-08-18 00:53 f40630.mp3
-rw-r--r-- 1 root root  4338688 2008-08-18 00:53 f41409.mp3
-rw-r--r-- 1 root root  7342080 2008-08-18 00:53 f42469.mp3
-rw-r--r-- 1 root root  5278952 2008-08-18 00:53 f44262.mp3
-rw-r--r-- 1 root root  6465314 2008-08-18 00:53 f45551.mp3
-rw-r--r-- 1 root root  2140831 2008-08-18 00:53 f47135.mp3
-rw-r--r-- 1 root root  5966843 2008-08-18 00:53 f47664.mp3
-rw-r--r-- 1 root root    20182 2008-08-18 00:56 f486125.jpg
-rw-r--r-- 1 root root  6198041 2008-08-18 00:53 f49172.mp3
-rw-r--r-- 1 root root  2680074 2008-08-18 00:53 f50691.mp3
-rw-r--r-- 1 root root      129 2008-08-18 00:53 f51351.txt
-rw-r--r-- 1 root root  8129517 2008-08-18 00:53 f51352.mp3
-rw-r--r-- 1 root root      107 2008-08-18 00:53 f53341.txt
-rw-r--r-- 1 root root  4548073 2008-08-18 00:53 f53343.mp3
-rw-r--r-- 1 root root  6230832 2008-08-18 00:53 f54460.mp3
-rw-r--r-- 1 root root  4416768 2008-08-18 00:53 f55987.mp3
-rw-r--r-- 1 root root  4725490 2008-08-18 00:53 f57072.mp3
-rw-r--r-- 1 root root  3788800 2008-08-18 00:53 f58226.mp3
-rw-r--r-- 1 root root  3390402 2008-08-18 00:53 f59151.mp3
-rw-r--r-- 1 root root  4465270 2008-08-18 00:53 f59979.mp3
-rw-r--r-- 1 root root  3536523 2008-08-18 00:53 f61070.mp3
-rw-r--r-- 1 root root  6768493 2008-08-18 00:53 f61934.mp3
-rw-r--r-- 1 root root  5625372 2008-08-18 00:53 f63587.mp3
-rw-r--r-- 1 root root  6840952 2008-08-18 00:53 f64961.mp3
-rw-r--r-- 1 root root  3876989 2008-08-18 00:53 f66632.mp3
-rw-r--r-- 1 root root 10140821 2008-08-18 00:53 f67585.mp3
-rw-r--r-- 1 root root  9739580 2008-08-18 00:53 f70061.mp3
-rw-r--r-- 1 root root 26606323 2008-08-18 00:53 f72439.mp3
-rw-r--r-- 1 root root 20522927 2008-08-18 00:53 f78935.mp3
-rw-r--r-- 1 root root 13489719 2008-08-18 00:53 f83946.mp3
-rw-r--r-- 1 root root     3215 2008-08-18 00:58 f847917.txt
-rw-r--r-- 1 root root     2263 2008-08-18 00:58 f848496.txt
-rw-r--r-- 1 root root      120 2008-08-18 00:58 f849983.txt
-rw-r--r-- 1 root root      115 2008-08-18 00:58 f851463.txt
-rw-r--r-- 1 root root    13034 2008-08-18 00:58 f851848.txt
-rw-r--r-- 1 root root     3627 2008-08-18 00:58 f851894.txt
-rw-r--r-- 1 root root    14596 2008-08-18 00:58 f851906.txt
-rw-r--r-- 1 root root      764 2008-08-18 00:58 f851916.txt
-rw-r--r-- 1 root root     7866 2008-08-18 00:58 f852003.txt
-rw-r--r-- 1 root root     7808 2008-08-18 00:58 f852006.txt
-rw-r--r-- 1 root root     7582 2008-08-18 00:58 f852009.txt
-rw-r--r-- 1 root root     7401 2008-08-18 00:58 f852012.txt
-rw-r--r-- 1 root root     7206 2008-08-18 00:58 f852015.txt
-rw-r--r-- 1 root root     6982 2008-08-18 00:58 f852018.txt
-rw-r--r-- 1 root root    11022 2008-08-18 00:58 f852020.txt
-rw-r--r-- 1 root root    11369 2008-08-18 00:58 f852023.txt
-rw-r--r-- 1 root root     4364 2008-08-18 00:58 f852029.txt
-rw-r--r-- 1 root root     2703 2008-08-18 00:58 f852110.txt
-rw-r--r-- 1 root root    13472 2008-08-18 00:58 f852138.txt
-rw-r--r-- 1 root root      676 2008-08-18 00:58 f852145.txt
-rw-r--r-- 1 root root     1803 2008-08-18 00:58 f852147.txt
-rw-r--r-- 1 root root      550 2008-08-18 00:58 f852150.txt
-rw-r--r-- 1 root root      136 2008-08-18 00:58 f852151.txt
-rw-r--r-- 1 root root      319 2008-08-18 00:58 f852152.txt
-rw-r--r-- 1 root root     1604 2008-08-18 00:58 f852154.txt
-rw-r--r-- 1 root root      996 2008-08-18 00:58 f852158.txt
-rw-r--r-- 1 root root      426 2008-08-18 00:58 f852162.txt
-rw-r--r-- 1 root root      533 2008-08-18 00:58 f852163.txt
-rw-r--r-- 1 root root    11120 2008-08-18 00:58 f852432.txt
-rw-r--r-- 1 root root    11062 2008-08-18 00:58 f852435.txt
-rw-r--r-- 1 root root    10836 2008-08-18 00:58 f852438.txt
-rw-r--r-- 1 root root    10655 2008-08-18 00:58 f852441.txt
-rw-r--r-- 1 root root    10460 2008-08-18 00:58 f852444.txt
-rw-r--r-- 1 root root    10236 2008-08-18 00:58 f852447.txt
-rw-r--r-- 1 root root    10180 2008-08-18 00:58 f852450.txt
-rw-r--r-- 1 root root    10527 2008-08-18 00:58 f852453.txt
-rw-r--r-- 1 root root     1181 2008-08-18 00:58 f852456.txt
-rw-r--r-- 1 root root     3110 2008-08-18 00:58 f852459.txt
-rw-r--r-- 1 root root     1221 2008-08-18 00:58 f852460.txt
-rw-r--r-- 1 root root      611 2008-08-18 00:58 f852461.txt
-rw-r--r-- 1 root root     2280 2008-08-18 00:58 f852462.txt
-rw-r--r-- 1 root root      387 2008-08-18 00:58 f852463.txt
-rw-r--r-- 1 root root     1939 2008-08-18 00:58 f852464.txt
-rw-r--r-- 1 root root     1315 2008-08-18 00:58 f852465.txt
-rw-r--r-- 1 root root     2865 2008-08-18 00:58 f852466.txt
-rw-r--r-- 1 root root     1053 2008-08-18 00:58 f852467.txt
-rw-r--r-- 1 root root      405 2008-08-18 00:58 f852468.txt
-rw-r--r-- 1 root root     4134 2008-08-18 00:58 f852469.txt
-rw-r--r-- 1 root root      136 2008-08-18 00:58 f852865.txt
-rw-r--r-- 1 root root      119 2008-08-18 00:58 f853462.txt
-rw-r--r-- 1 root root     3810 2008-08-18 00:58 f854306.txt
-rw-r--r-- 1 root root 13418666 2008-08-18 00:53 f87240.mp3
-rw-r--r-- 1 root root      245 2008-08-18 00:52 f8973.xml
-rw-r--r-- 1 root root     3930 2008-08-18 00:52 f8974.txt
-rw-r--r-- 1 root root    12122 2008-08-18 00:52 f8975.xml
-rw-r--r-- 1 root root  3472879 2008-08-18 00:53 f90517.mp3
-rw-r--r-- 1 root root  4500166 2008-08-18 00:53 f91368.mp3
-rw-r--r-- 1 root root  5191121 2008-08-18 00:53 f92472.mp3
-rw-r--r-- 1 root root  3890155 2008-08-18 00:53 f93746.mp3
-rw-r--r-- 1 root root  2879639 2008-08-18 00:53 f94702.mp3
-rw-r--r-- 1 root root      164 2008-08-18 00:53 f95411.txt
-rw-r--r-- 1 root root  3335324 2008-08-18 00:53 f95437.mp3
-rw-r--r-- 1 root root  4747054 2008-08-18 00:53 f96252.mp3
-rw-r--r-- 1 root root  5294009 2008-08-18 00:53 f97416.mp3
-rw-r--r-- 1 root root  4287145 2008-08-18 00:53 f98715.mp3
-rw-r--r-- 1 root root   575122 2008-08-18 00:53 f99768.mp3
-rw-r--r-- 1 root root  3723224 2008-08-18 00:53 f99909.mp3


```

---

### Post by Loaded.len on 2008-08-18
I had the same problem with photorec recovery files.

```
rm -rf recup_dir.*
``` fixed it.

(forces the removal and all subdirs)

---

### Post by p_quarles on 2008-08-18
So what error message are getting when you try to move these files and folders after running 
```
gksu nautilus
```
?

In any case, there is any easy command to transfer ownership of those files to yourself:
```
sudo chown -R your_username ~/recup_dir.?
```
But if there is something else wrong (and form the sound of things, there may be), this may not resolve the issue.

---

### Post by p_quarles on 2008-08-18
> **Loaded.len said:**
> I had the same problem with photorec recovery files.

```
rm -rf recup_dir.*
``` fixed it.

(forces the removal and all subdirs)
He doesn't want to delete the files though. 

OP: Don't run that command unless you want to delete those files. :)

---

### Post by Loaded.len on 2008-08-18
I would actually recommend NOT using Nautilus as root to delete root files.  Or your ~/.local/share/Trash folder may start giving you grief (happened to me the first time I used photorec)

---

### Post by Loaded.len on 2008-08-18
> **p_quarles said:**
> He doesn't want to delete the files though. 

OP: Don't run that command unless you want to delete those files. :)


[COLOR="DarkRed"]**OHHHH  MY BAD... DO NOT DELETE!!!**[/COLOR]   Sorry, sorry, sorry

---

### Post by shamusl on 2008-08-18
> **Loaded.len said:**
> I had the same problem with photorec recovery files.

```
rm -rf recup_dir.*
``` fixed it.

(forces the removal and all subdirs)

I am under the impression that that is a bad command, and won't try it without confirmation first.

---

### Post by Loaded.len on 2008-08-18
Yes, I was worried that you were running it as we were trying to tell you not to. :)  So glad you didn't. But you may want to keep it in mind when your DONE with photorec. Sorry for that.

---

### Post by shamusl on 2008-08-18
> **p_quarles said:**
> He doesn't want to delete the files though. 

OP: Don't run that command unless you want to delete those files. :)

Any Ideas though? I'm really stuck here.

---

### Post by p_quarles on 2008-08-18
> **shamusl said:**
> Any Ideas though? I'm really stuck here.
Yeah, and that would be the questions I asked earlier to which you haven't replied yet. ;)

---

### Post by shamusl on 2008-08-18
> **p_quarles said:**
> Yeah, and that would be the questions I asked earlier to which you haven't replied yet. ;)

This is the exact file I need if any files at all (the most important):
/home/shamus/Desktop/recup_dir.4/f728219.rar , this file is 657.6mb, and is part of a multipart rar.

---

### Post by Loaded.len on 2008-08-18
So if you 

sudo chown 777 /home/shamus/Desktop/recup_dir.4/f728219.rar

you still can't read/move it?

---

### Post by shamusl on 2008-08-18
> **Loaded.len said:**
> So if you 

sudo chown 777 /home/shamus/Desktop/recup_dir.4/f728219.rar

you still can't read/move it?

Nope. Permission denied.

---

### Post by p_quarles on 2008-08-18
> **shamusl said:**
> Nope. Permission denied.
* sigh *

Try the command I gave you. And answer my question about the error message you get from gksu nautilus.

---

### Post by Loaded.len on 2008-08-18
Well, I guess you could temporarily unlock the root account.

```
sudo passwd root
```

Then enter YOUR password, followed by the password you want to give root. (enter that twice to avoid typos)

Then you can su

when you're done, exit out of su mode and lock the root account again.

```
sudo passwd root -l
```

---

### Post by shamusl on 2008-08-18
> **Loaded.len said:**
> Well, I guess you could temporarily unlock the root account.

```
sudo passwd root
```

Then enter YOUR password, followed by the password you want to give root. (enter that twice to avoid typos)

Then you can su

when you're done, exit out of su mode and lock the root account again.

```
sudo passwd root -l
```

This worked. Thank you.

---

### Post by ilrudie on 2008-08-18
> **Loaded.len said:**
> Well, I guess you could temporarily unlock the root account.

```
sudo passwd root
```Then enter YOUR password, followed by the password you want to give root. (enter that twice to avoid typos)

Then you can su

when you're done, exit out of su mode and lock the root account again.

```
sudo passwd root -l
```

```
sudo su -
```
does the same thing without the need to set a root password.

---

