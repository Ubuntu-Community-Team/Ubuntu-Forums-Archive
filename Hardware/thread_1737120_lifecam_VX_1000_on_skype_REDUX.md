---
title: "lifecam VX 1000 on skype REDUX"
date: 2011-04-23
forum: Hardware
---

### Post by renoirbleu on 2011-04-23
Hello

 Unlike  others, I can see the video image on Cheese without installing the  patch. but I don't see any "sound preference" tab in my Cheese so I  cannot check if the mic works. 
Though, my mic seems working even when the cam is plugged in. I can still talk online on skype. 
The other problems on skype and  pidgin are same to what people have explained: simply video is not activated.

I tried to install the patch  anyway following the direction in this forum. 
but I am not sure if it worked fine or  not. I didn't get the final message line that it was successful. 
Just in  case, I attached the dialogue I had below.

I had to reboot anyway and started Cheese again but nothing seemed to be changed so far.
could you please help me ? 
I'm so frustrated that I cannot see any solutions here.

FYI, i can see that my computer detects my webcam on "video for linux2 (V4L2)". the test works fine.
i also selected this in the pidgin's option. but it's not working there. 

Thank you for your help in advance...!

------------------------------------------------------------------------------------------
> alice7m@bbJ-ordi:~$ cd Desktop/gspca-2.9.51-vx1000-patch-20100712/
bash: cd: Desktop/gspca-2.9.51-vx1000-patch-20100712/: Aucun fichier ou dossier de ce type
alice7m@bbJ-ordi:~$ make
make -C /lib/modules/2.6.32-31-generic/build M=/home/alice7m/build modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.32-31-generic »
  CC [M]  /home/alice7m/build/benq.o
  CC [M]  /home/alice7m/build/conex.o
  CC [M]  /home/alice7m/build/cpia1.o
  CC [M]  /home/alice7m/build/etoms.o
  CC [M]  /home/alice7m/build/finepix.o
  CC [M]  /home/alice7m/build/gl860.o
  CC [M]  /home/alice7m/build/gl860-mi1320.o
  CC [M]  /home/alice7m/build/gl860-ov2640.o
  CC [M]  /home/alice7m/build/gl860-ov9655.o
  CC [M]  /home/alice7m/build/gl860-mi2020.o
  CC [M]  /home/alice7m/build/jeilinj.o
  CC [M]  /home/alice7m/build/m5602_core.o
  CC [M]  /home/alice7m/build/m5602_ov9650.o
  CC [M]  /home/alice7m/build/m5602_ov7660.o
  CC [M]  /home/alice7m/build/m5602_mt9m111.o
  CC [M]  /home/alice7m/build/m5602_po1030.o
  CC [M]  /home/alice7m/build/m5602_s5k83a.o
  CC [M]  /home/alice7m/build/m5602_s5k4aa.o
  CC [M]  /home/alice7m/build/gspca.o
  CC [M]  /home/alice7m/build/mars.o
  CC [M]  /home/alice7m/build/mr97310a.o
  CC [M]  /home/alice7m/build/ov519.o
  CC [M]  /home/alice7m/build/ov534.o
  CC [M]  /home/alice7m/build/ov534_9.o
  CC [M]  /home/alice7m/build/pac207.o
  CC [M]  /home/alice7m/build/pac7302.o
  CC [M]  /home/alice7m/build/pac7311.o
  CC [M]  /home/alice7m/build/sn9c2028.o
  CC [M]  /home/alice7m/build/sn9c20x.o
  CC [M]  /home/alice7m/build/sonixb.o
  CC [M]  /home/alice7m/build/sonixj.o
  CC [M]  /home/alice7m/build/spca1528.o
  CC [M]  /home/alice7m/build/spca500.o
  CC [M]  /home/alice7m/build/spca501.o
  CC [M]  /home/alice7m/build/spca505.o
  CC [M]  /home/alice7m/build/spca506.o
  CC [M]  /home/alice7m/build/spca508.o
  CC [M]  /home/alice7m/build/spca561.o
  CC [M]  /home/alice7m/build/sq905.o
  CC [M]  /home/alice7m/build/sq905c.o
  CC [M]  /home/alice7m/build/sq930x.o
/home/alice7m/build/jpeg.h:152: warning: ‘jpeg_set_qual’ defined but not used
  CC [M]  /home/alice7m/build/stk014.o
  CC [M]  /home/alice7m/build/stv0680.o
  CC [M]  /home/alice7m/build/stv06xx.o
  CC [M]  /home/alice7m/build/stv06xx_vv6410.o
  CC [M]  /home/alice7m/build/stv06xx_hdcs.o
  CC [M]  /home/alice7m/build/stv06xx_pb0100.o
  CC [M]  /home/alice7m/build/stv06xx_st6422.o
  CC [M]  /home/alice7m/build/sunplus.o
  CC [M]  /home/alice7m/build/t613.o
  CC [M]  /home/alice7m/build/tasc.o
  CC [M]  /home/alice7m/build/tp6800.o
  CC [M]  /home/alice7m/build/tv8532.o
  CC [M]  /home/alice7m/build/vc032x.o
  CC [M]  /home/alice7m/build/zc3xx.o
  LD [M]  /home/alice7m/build/gspca_main.o
  LD [M]  /home/alice7m/build/gspca_benq.o
  LD [M]  /home/alice7m/build/gspca_conex.o
  LD [M]  /home/alice7m/build/gspca_cpia1.o
  LD [M]  /home/alice7m/build/gspca_etoms.o
  LD [M]  /home/alice7m/build/gspca_finepix.o
  LD [M]  /home/alice7m/build/gspca_jeilinj.o
  LD [M]  /home/alice7m/build/gspca_mars.o
  LD [M]  /home/alice7m/build/gspca_mr97310a.o
  LD [M]  /home/alice7m/build/gspca_ov519.o
  LD [M]  /home/alice7m/build/gspca_ov534.o
  LD [M]  /home/alice7m/build/gspca_ov534_9.o
  LD [M]  /home/alice7m/build/gspca_pac207.o
  LD [M]  /home/alice7m/build/gspca_pac7302.o
  LD [M]  /home/alice7m/build/gspca_pac7311.o
  LD [M]  /home/alice7m/build/gspca_sn9c2028.o
  LD [M]  /home/alice7m/build/gspca_sn9c20x.o
  LD [M]  /home/alice7m/build/gspca_sonixb.o
  LD [M]  /home/alice7m/build/gspca_sonixj.o
  LD [M]  /home/alice7m/build/gspca_spca500.o
  LD [M]  /home/alice7m/build/gspca_spca501.o
  LD [M]  /home/alice7m/build/gspca_spca505.o
  LD [M]  /home/alice7m/build/gspca_spca506.o
  LD [M]  /home/alice7m/build/gspca_spca508.o
  LD [M]  /home/alice7m/build/gspca_spca561.o
  LD [M]  /home/alice7m/build/gspca_spca1528.o
  LD [M]  /home/alice7m/build/gspca_sq905.o
  LD [M]  /home/alice7m/build/gspca_sq905c.o
  LD [M]  /home/alice7m/build/gspca_sq930x.o
  LD [M]  /home/alice7m/build/gspca_sunplus.o
  LD [M]  /home/alice7m/build/gspca_stk014.o
  LD [M]  /home/alice7m/build/gspca_stv0680.o
  LD [M]  /home/alice7m/build/gspca_t613.o
  LD [M]  /home/alice7m/build/gspca_tasc.o
  LD [M]  /home/alice7m/build/gspca_tp6800.o
  LD [M]  /home/alice7m/build/gspca_tv8532.o
  LD [M]  /home/alice7m/build/gspca_vc032x.o
  LD [M]  /home/alice7m/build/gspca_zc3xx.o
  LD [M]  /home/alice7m/build/gspca_gl860.o
  LD [M]  /home/alice7m/build/gspca_m5602.o
  LD [M]  /home/alice7m/build/gspca_stv06xx.o
  Building modules, stage 2.
  MODPOST 41 modules
  CC      /home/alice7m/build/gspca_benq.mod.o
  LD [M]  /home/alice7m/build/gspca_benq.ko
  CC      /home/alice7m/build/gspca_conex.mod.o
  LD [M]  /home/alice7m/build/gspca_conex.ko
  CC      /home/alice7m/build/gspca_cpia1.mod.o
  LD [M]  /home/alice7m/build/gspca_cpia1.ko
  CC      /home/alice7m/build/gspca_etoms.mod.o
  LD [M]  /home/alice7m/build/gspca_etoms.ko
  CC      /home/alice7m/build/gspca_finepix.mod.o
  LD [M]  /home/alice7m/build/gspca_finepix.ko
  CC      /home/alice7m/build/gspca_gl860.mod.o
  LD [M]  /home/alice7m/build/gspca_gl860.ko
  CC      /home/alice7m/build/gspca_jeilinj.mod.o
  LD [M]  /home/alice7m/build/gspca_jeilinj.ko
  CC      /home/alice7m/build/gspca_m5602.mod.o
  LD [M]  /home/alice7m/build/gspca_m5602.ko
  CC      /home/alice7m/build/gspca_main.mod.o
  LD [M]  /home/alice7m/build/gspca_main.ko
  CC      /home/alice7m/build/gspca_mars.mod.o
  LD [M]  /home/alice7m/build/gspca_mars.ko
  CC      /home/alice7m/build/gspca_mr97310a.mod.o
  LD [M]  /home/alice7m/build/gspca_mr97310a.ko
  CC      /home/alice7m/build/gspca_ov519.mod.o
  LD [M]  /home/alice7m/build/gspca_ov519.ko
  CC      /home/alice7m/build/gspca_ov534.mod.o
  LD [M]  /home/alice7m/build/gspca_ov534.ko
  CC      /home/alice7m/build/gspca_ov534_9.mod.o
  LD [M]  /home/alice7m/build/gspca_ov534_9.ko
  CC      /home/alice7m/build/gspca_pac207.mod.o
  LD [M]  /home/alice7m/build/gspca_pac207.ko
  CC      /home/alice7m/build/gspca_pac7302.mod.o
  LD [M]  /home/alice7m/build/gspca_pac7302.ko
  CC      /home/alice7m/build/gspca_pac7311.mod.o
  LD [M]  /home/alice7m/build/gspca_pac7311.ko
  CC      /home/alice7m/build/gspca_sn9c2028.mod.o
  LD [M]  /home/alice7m/build/gspca_sn9c2028.ko
  CC      /home/alice7m/build/gspca_sn9c20x.mod.o
  LD [M]  /home/alice7m/build/gspca_sn9c20x.ko
  CC      /home/alice7m/build/gspca_sonixb.mod.o
  LD [M]  /home/alice7m/build/gspca_sonixb.ko
  CC      /home/alice7m/build/gspca_sonixj.mod.o
  LD [M]  /home/alice7m/build/gspca_sonixj.ko
  CC      /home/alice7m/build/gspca_spca1528.mod.o
  LD [M]  /home/alice7m/build/gspca_spca1528.ko
  CC      /home/alice7m/build/gspca_spca500.mod.o
  LD [M]  /home/alice7m/build/gspca_spca500.ko
  CC      /home/alice7m/build/gspca_spca501.mod.o
  LD [M]  /home/alice7m/build/gspca_spca501.ko
  CC      /home/alice7m/build/gspca_spca505.mod.o
  LD [M]  /home/alice7m/build/gspca_spca505.ko
  CC      /home/alice7m/build/gspca_spca506.mod.o
  LD [M]  /home/alice7m/build/gspca_spca506.ko
  CC      /home/alice7m/build/gspca_spca508.mod.o
  LD [M]  /home/alice7m/build/gspca_spca508.ko
  CC      /home/alice7m/build/gspca_spca561.mod.o
  LD [M]  /home/alice7m/build/gspca_spca561.ko
  CC      /home/alice7m/build/gspca_sq905.mod.o
  LD [M]  /home/alice7m/build/gspca_sq905.ko
  CC      /home/alice7m/build/gspca_sq905c.mod.o
  LD [M]  /home/alice7m/build/gspca_sq905c.ko
  CC      /home/alice7m/build/gspca_sq930x.mod.o
  LD [M]  /home/alice7m/build/gspca_sq930x.ko
  CC      /home/alice7m/build/gspca_stk014.mod.o
  LD [M]  /home/alice7m/build/gspca_stk014.ko
  CC      /home/alice7m/build/gspca_stv0680.mod.o
  LD [M]  /home/alice7m/build/gspca_stv0680.ko
  CC      /home/alice7m/build/gspca_stv06xx.mod.o
  LD [M]  /home/alice7m/build/gspca_stv06xx.ko
  CC      /home/alice7m/build/gspca_sunplus.mod.o
  LD [M]  /home/alice7m/build/gspca_sunplus.ko
  CC      /home/alice7m/build/gspca_t613.mod.o
  LD [M]  /home/alice7m/build/gspca_t613.ko
  CC      /home/alice7m/build/gspca_tasc.mod.o
  LD [M]  /home/alice7m/build/gspca_tasc.ko
  CC      /home/alice7m/build/gspca_tp6800.mod.o
  LD [M]  /home/alice7m/build/gspca_tp6800.ko
  CC      /home/alice7m/build/gspca_tv8532.mod.o
  LD [M]  /home/alice7m/build/gspca_tv8532.ko
  CC      /home/alice7m/build/gspca_vc032x.mod.o
  LD [M]  /home/alice7m/build/gspca_vc032x.ko
  CC      /home/alice7m/build/gspca_zc3xx.mod.o
  LD [M]  /home/alice7m/build/gspca_zc3xx.ko
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.32-31-generic »
alice7m@bbJ-ordi:~$ sudo make install
[sudo] password for alice7m: 
rm -f /lib/modules/2.6.32-31-generic/kernel/drivers/media/video/gspca/gspca*.ko /lib/modules/2.6.32-31-generic/kernel/drivers/media/video/gspca/*/gspca*.ko; \
    install -c -m 0644 build/*.ko /lib/modules/2.6.32-31-generic/kernel/drivers/media/video/gspca/; \
    depmod
alice7m@bbJ-ordi:~$ 
alice7m@bbJ-ordi:~$
---------------------------------------------------------------------------

---

