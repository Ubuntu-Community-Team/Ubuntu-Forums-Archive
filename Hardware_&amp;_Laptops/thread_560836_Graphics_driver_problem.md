---
title: "Graphics driver problem?"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by Linux_noob1 on 2007-09-26
I have Kubuntu 7.04 and graphics don't seem to be working very good.
I have VIA km400 intergrated. 
Some things don't work, and when I play bzflag it crashes all the time and I get this in the terminal:


0000:   42028b68  44160000  3f000000  ffffffff
0010:   42b19b5c  43efb447  3f000000  ffffffff
0020:   42b19b5c  43efb447  3f000000  ffffffff
0030:   42b19b5c  43efb447  3f000000  ffffffff
0040:   42b19b5c  43efb447  3f000000  ffffffff
0050:   42b19b5c  43efb447  3f000000  ffffffff
0060:   42b19b5c  43efb447  3f000000  ffffffff
0070:   42028ab0  44160000  3f000000  ffffffff
0080:   42028a90  44160000  3f000000  ffffffff
0090:   42b19b00  43efb43c  3f000000  ffffffff
00a0:   42b19b00  43efb43c  3f000000  ffffffff
00b0:   42b19b00  43efb43c  3f000000  ffffffff
00c0:   42b19b00  43efb43c  3f000000  ffffffff
00d0:   42b19b00  43efb43c  3f000000  ffffffff
00e0:   42b19b00  43efb43c  3f000000  ffffffff
00f0:   420289c8  44160000  3f000000  ffffffff
0100:   420289a8  44160000  3f000000  ffffffff
0110:   42b19a9c  43efb432  3f000000  ffffffff
0120:   42b19a9c  43efb432  3f000000  ffffffff
0130:   42b19a9c  43efb432  3f000000  ffffffff
0140:   42b19a9c  43efb432  3f000000  ffffffff
0150:   42b19a9c  43efb432  3f000000  ffffffff
0160:   42b19a9c  43efb432  3f000000  ffffffff
0170:   420288d0  44160000  3f000000  ffffffff
0180:   420288b0  44160000  3f000000  ffffffff
0190:   42b19a38  43efb425  3f000000  ffffffff
01a0:   f210f110  00010000  00030400  43ffffff
01b0:   44000cff  109f2e00  11000001  12230ca0
01c0:   15010000  23000000  24000000  7b000000
01d0:   f210f110  00010000  701b224b  7100d0a6
01e0:   40819700  41000001  7c000000  42090ca0
01f0:   f210f110  00010000  cccccccc  dddddddd
0200:   f210f110  00000000  ec007400  ee020c00
0210:   42b99914  43f1558e  3f000000  ffffff00
0220:   42b99914  43ef0c1e  3f000000  ffffff00
0230:   42b07354  43f1558e  3f000000  ffffff00
0240:   42b99914  43ef0c1e  3f000000  ffffff00
0250:   42b07354  43ef0c1e  3f000000  ffffff00
0260:   42b07354  43f1558e  3f000000  ffffff00
0270:   ee120f00  f210f110  00010000  cccccccc
0280:   dddddddd  f210f110  00000000  ec017420
0290:   ee010860  42b50634  43f1558e  3f000000
02a0:   ffffff00  42b99914  43f030d6  3f000000
02b0:   ffffff00  42b50634  43ef0c1e  3f000000
02c0:   ffffff00  42b07354  43f030d6  3f000000
02d0:   ffffff00  42b50634  43f1558e  3f000000
02e0:   ffffff00  ee110b60  f210f110  00010000
02f0:   00030400  43ffffff  44000cff  109f2e00
0300:   11000001  12230ca0  15010000  23000000
0310:   24000000  7b000000  f210f110  00010000
0320:   cccccccc  dddddddd  f210f110  00000000
0330:   ec017400  ee010800  40877680  4415186e
0340:   3f000000  ffffffff  40231180  44160000
0350:   3f000000  ffffffff  40231180  44160000
0360:   3f000000  ffffffff  40877680  4415186e
0370:   3f000000  ffffffff  3e7d0800  4415756a
0380:   3f000000  ffffffff  409cae40  44160000
0390:   3f000000  ffffffff  409cae40  44160000
03a0:   3f000000  ffffffff  3e7d0800  4415756a
03b0:   3f000000  ffffffff  ee110b00  f210f110
03c0:   00010000  cccccccc  dddddddd  f210f110
03d0:   00000000  ec017400  ee010800  424cf130
03e0:   43e9eec2  3f000000  ffffffff  4242cf18
03f0:   43eca6f3  3f000000  ffffffff  4242cf18
0400:   43eca6f3  3f000000  ffffffff  424cf130
0410:   43e9eec2  3f000000  ffffffff  423cff68
0420:   43eaa8ba  3f000000  ffffffff  4252c0e8
0430:   43ebecfc  3f000000  ffffffff  4252c0e8
0440:   43ebecfc  3f000000  ffffffff  423cff68
0450:   43eaa8ba  3f000000  ffffffff  3f08a000
0460:   44124081  3f000000  ffffffff  00000000
0470:   441289d7  3f000000  ffffffff  00000000
0480:   441289d7  3f000000  ffffffff  3f08a000
0490:   44124081  3f000000  ffffffff  00000000
04a0:   44130466  3f000000  ffffffff  3ffe4700
04b0:   44133f9e  3f000000  ffffffff  3ffe4700
04c0:   44133f9e  3f000000  ffffffff  00000000
04d0:   44130466  3f000000  ffffffff  40207580
04e0:   43fc5690  3f000000  ffffffff  00000000
04f0:   43ff0792  3f000000  ffffffff  00000000
0500:   43ff0792  3f000000  ffffffff  40207580
0510:   43fc5690  3f000000  ffffffff  00000000
0520:   43fd68b3  3f000000  ffffffff  407d7100
0530:   43fe54ca  3f000000  ffffffff  407d7100
0540:   43fe54ca  3f000000  ffffffff  00000000
0550:   43fd68b3  3f000000  ffffffff  41cef0a0
0560:   440510cc  3f000000  ffffffff  41baac60
0570:   44066ce4  3f000000  ffffffff  41baac60
0580:   44066ce4  3f000000  ffffffff  41cef0a0
0590:   440510cc  3f000000  ffffffff  41af0d00
05a0:   44056dc7  3f000000  ffffffff  41da9000
05b0:   44060fe8  3f000000  ffffffff  41da9000
05c0:   44060fe8  3f000000  ffffffff  41af0d00
05d0:   44056dc7  3f000000  ffffffff  41b076e0
05e0:   43e469eb  3f000000  ffffffff  419c32b0
05f0:   43e7221c  3f000000  ffffffff  419c32b0
0600:   43e7221c  3f000000  ffffffff  41b076e0
0610:   43e469eb  3f000000  ffffffff  41909340
0620:   43e523e2  3f000000  ffffffff  41bc1650
0630:   43e66825  3f000000  ffffffff  41bc1650
0640:   43e66825  3f000000  ffffffff  41909340
0650:   43e523e2  3f000000  ffffffff  3fd5ea00
0660:   43ff3dcb  3f000000  ffffffff  00000000
0670:   44008488  3f000000  ffffffff  00000000
0680:   44008488  3f000000  ffffffff  3fd5ea00
0690:   43ff3dcb  3f000000  ffffffff  00000000
06a0:   440040e3  3f000000  ffffffff  4047f000
06b0:   44009e02  3f000000  ffffffff  4047f000
06c0:   44009e02  3f000000  ffffffff  00000000
06d0:   440040e3  3f000000  ffffffff  3e278800
06e0:   43fefa85  3f000000  ffffffff  00000000
06f0:   43ff277c  3f000000  ffffffff  00000000
0700:   43ff277c  3f000000  ffffffff  3e278800
0710:   43fefa85  3f000000  ffffffff  00000000
0720:   44004c30  3f000000  ffffffff  3fcee800
0730:   44007c60  3f000000  ffffffff  3fcee800
0740:   44007c60  3f000000  ffffffff  00000000
0750:   44004c30  3f000000  ffffffff  4236aa90
0760:   43f22ea2  3f000000  ffffffff  422c8878
0770:   43f4e6d2  3f000000  ffffffff  422c8878
0780:   43f4e6d2  3f000000  ffffffff  4236aa90
0790:   43f22ea2  3f000000  ffffffff  4226b8c8
07a0:   43f2e898  3f000000  ffffffff  423c7a48
07b0:   43f42cdb  3f000000  ffffffff  423c7a48
07c0:   43f42cdb  3f000000  ffffffff  4226b8c8
07d0:   43f2e898  3f000000  ffffffff  ee110b00
07e0:   f210f110  00010000  cccccccc  dddddddd
07f0:   f210f110  00000000  ec017400  ee010800
0800:   42336f80  43f8608a  3f000000  ffff0000
0810:   42294d68  43fb18ba  3f000000  ffff0000
0820:   42294d68  43fb18ba  3f000000  ffff0000
0830:   42336f80  43f8608a  3f000000  ffff0000
0840:   42237db8  43f91a81  3f000000  ffff0000
0850:   42393f38  43fa5ec4  3f000000  ffff0000
0860:   42393f38  43fa5ec4  3f000000  ffff0000
0870:   42237db8  43f91a81  3f000000  ffff0000
0880:   ee110b00  f210f110  00010000  00030400
0890:   43ffffff  44000cff  109f2e00  11000001
08a0:   12230ca0  15010000  23000000  24000000
08b0:   7b000000  cccccccc  f210f110  00010000
08c0:   cccccccc  dddddddd  f210f110  00000000
08d0:   ec017420  ee010860  43160f50  44059f2f
08e0:   3f000000  ffffffff  431cfe98  44066de7
08f0:   3f000000  ffffffff  4312d472  44075b01
0900:   3f000000  ffffffff  4319c3ba  440829b9
0910:   3f000000  ffffffff  ee110b60  f210f110
0920:   00010000  00030400  43ffffff  44000cff
0930:   109f2e00  11000001  12230ca0  15010000
0940:   23000000  24000000  7b000000  cccccccc
0950:   f210f110  00010000  cccccccc  dddddddd
0960:   f210f110  00000000  ec017400  ee010800
0970:   42b30000  43d98000  3f000000  ffffffff
0980:   42b30000  43db0000  3f000000  ffffffff
0990:   ee110b00  f210f110  00010000  00030400
09a0:   43ffffff  44000cff  109f2e00  11000001
09b0:   12230ca0  15010000  23000000  24000000
09c0:   7b000000  cccccccc  f210f110  00010000
09d0:   cccccccc  dddddddd  f210f110  00000000
09e0:   ec017400  ee010800  42b30000  4400a000
09f0:   3f000000  ffffffff  42b30000  43fd4000
0a00:   3f000000  ffffffff  42b30000  43fd4000
0a10:   3f000000  ffffffff  42b30000  4400a000
0a20:   3f000000  ffffffff  42bb0000  43ff4000
0a30:   3f000000  ffffffff  42ab0000  43ff4000
0a40:   3f000000  ffffffff  42ab0000  43ff4000
0a50:   3f000000  ffffffff  42bb0000  43ff4000
0a60:   3f000000  ffffffff  ee110b00  f210f110
0a70:   00010000  00030400  43ffffff  44000cff
0a80:   109f2e00  11000001  12230ca0  15010000
0a90:   23000000  24000000  7b000000  cccccccc
0aa0:   f210f110  00010000  cccccccc  dddddddd
0ab0:   f210f110  00000000  ec007400  ee020c00
0ac0:   42b792e0  4400325c  3f000000  ffffffff
0ad0:   42b792e0  43fe1b48  3f000000  ffffffff
0ae0:   42ae6d20  4400325c  3f000000  ffffffff
0af0:   42b792e0  43fe1b48  3f000000  ffffffff
0b00:   42ae6d20  43fe1b48  3f000000  ffffffff
0b10:   42ae6d20  4400325c  3f000000  ffffffff
0b20:   ee120f00  f210f110  00010000  cccccccc
0b30:   dddddddd  f210f110  00000000  ec017420
0b40:   ee010860  42b30000  4400325c  3f000000
0b50:   ffffffff  42b792e0  43ff4000  3f000000
0b60:   ffffffff  42b30000  43fe1b48  3f000000
0b70:   ffffffff  42ae6d20  43ff4000  3f000000
0b80:   ffffffff  42b30000  4400325c  3f000000
0b90:   ffffffff  ee110b60  f210f110  00010000
0ba0:   cccccccc  cccccccc  cccccccc  cccccccc
0bb0:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
Aborted (core dumped)


What is the problem and how can I fix this? :confused:

Thanks

---

### Post by Linux_noob1 on 2007-09-27
If I can't get this fixed can anyone recommend a cheap graphics card I can use to take its place? 
 If there is a way, does anyone know a good tutorial? 


Please help

---

### Post by dabl on 2007-09-27
OK, I can't make heads or tails of that hexadecimal output.

Let's try a couple of basic things. Open your console window, and type in these:

```
lscpi -v
```

```
glxgears
```

Post the output, and maybe it will reveal something. :)

---

### Post by Linux_noob1 on 2007-09-29
> OK, I can't make heads or tails of that hexadecimal output.

Let's try a couple of basic things. Open your console window, and type in these:

Code:

lscpi -v

Code:

glxgears

Post the output, and maybe it will reveal something. 

Thanks for the response!

I went to post the glxgears results here (while it was still running) I copied from the console. Then Kubuntu just went and shut down while I was in the middle of posting here. Could I be experiencing a overheating issue?
    The computer didn't just stop it just shutdown like it normally would.

I also noticed while playing bzflag whenever I got near a teleporter my FPS would go down to around 1-2fps
     
Maybe this whole problem is severe overheating? Does anyone know a heat monitor program to see if this is the problem?

I couldn't get   lscpi -v    to work becuase it said it wasn't a command. Am I doing something wrong?


Thanks for the help

---

