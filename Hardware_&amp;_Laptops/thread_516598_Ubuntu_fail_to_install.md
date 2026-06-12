---
title: "Ubuntu fail to install"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by rlubcke on 2007-08-03
I have been using ubuntu for the past 2 years in my desktop pc but now I just bought a dell laptop with the following descriptions:

  1 261-4874 I9400,CORE DUO T2350(1.86GHZ), SP
  1 310-5941 XLARGE CARRY CASE,NYLON,I9200/9300
  1 310-8052 DELL 2-BTN OPTCL USB MOUSE,BLK,INSP
  1 310-8627 VISTA BASIC STICKER,INSP
  1 311-5832 1GB,DDR2,533MHZ,2 DIMM,I9400/E1705,DLA
  1 312-0374 80 WHR,9-CELL,LION,PRIM BATT,I9400/E1705
  1 313-4217 INTEGRATED HD AUDIO,INSPIRON
  1 313-4910 DELL RESOURCE DVD,BACK-UP,INSP
  1 313-5030 8X DVD+/-RW DRIVE,I9400/E1705
  1 320-4558 LCD,17-INCH,WXGA+,I9400/E1705
  1 320-4561 256MB ATI MBLTY RADEON X1400,I9400/E1705
  1 341-4221 160GB HARD DRIVE,I9400/E1705
  1 410-0880 MCAFEE 8.0,30DAY,SPN,DIM/INSP
  1 412-0923 ADOBE ACROBAT READER 7.0.8,SPN,INS
  1 420-5769 ISP SEARCH ASST PORTAL,DIM/INSP
  1 420-6436 VISTA,PC-RESTORE, DIM/INSP
  1 420-6464 ROXIO CREATOR LE,V,DIM/INSP
  1 420-6555 WIN VISTA HOME BASIC,SPN,INS
  1 430-0493 INTEGRATED NIC AND MODEM
  1 430-1516 INTEL PRO/WRLS 3945,A/G,DC,I9400/E1705
  1 430-2245 INT 355 BLTH WRLS,VSTA,E1705/E1505/M1710
  1 915-2160 NBD,INSP,LDSP, INIT YR, LA
  1 412-0925 MSWORKS8.5,SPN,INS
  1 983-2207 INFO, SERVICES DELL
  1 499-9998 INTERNATIONAL PROCESSING
  1 900-9054 NO WARRANTY,YRS 2 AND 3,L1

and I was not able to install it because of the following problem (I am trying to install Ubuntu 7.04):

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly."

and the errors were the followings:

"(EE) Vesa (0): No matching modes
 (EE) Screen (s) found, but none have a usable configuration.
 Fatal server error:
 No screen found"

I have read that there are some problems with ATI but I have not find any solutions. Please someone help me, right now my laptop has windows vista and it really sucks!!

Thanks in advance!!

---

### Post by merlinus on 2007-08-03
When you get the failure message, you might try this:

Ctrl-Alt-F1 to get to prompt

sudo dpkg-reconfigure xserver-xorg

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

startx

-merlin

---

