---
title: "see my soundcard ....compaq presario b1900"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by hjbolide on 2008-02-16
i've installed ubuntu since 7.2007 , but i still cannot make my soundcard work -.-||
    i followed the page [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)  
    all seems right , and alsamixer also works , but no sound heard , even with headphone .
    after i tried sudo module-assistant a-i alsa-source
    comes the error msg.
     /usr/bin/make -C /lib/modules/2.6.20-16-generic/build                      &#9618; 
 &#9474; SUBDIRS=/usr/src/modules/alsa-driver                                       &#9618; 
 &#9474; O=/lib/modules/2.6.20-16-generic/build CPP="gcc-4.1 -E" CC="gcc-4.1"       &#9618; 
 &#9474; modules                                                                    &#9618; 
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'     &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o                    &#9618; 
 &#9474; In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:     &#9618; 
 &#9474; /usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error:               &#9618; 
 &#9474; linux/config.h: No such file or directory                                  &#9646; 
 &#9474; In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,  &#9618; 
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1:     
  /usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition    &#8593; 
 &#9474; of &#8216;jiffies_to_msecs&#8217;                                                      &#9618; 
 &#9474; include/linux/jiffies.h:268: error: previous definition of                 &#9618; 
 &#9474; &#8216;jiffies_to_msecs&#8217; was here                                                &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition    &#9618; 
 &#9474; of &#8216;msecs_to_jiffies&#8217;                                                      &#9618; 
 &#9474; include/linux/jiffies.h:290: error: previous definition of                 &#9618; 
 &#9474; &#8216;msecs_to_jiffies&#8217; was here                                                &#9618; 
 &#9474; In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,  &#9618; 
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1:     &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h: In function                &#9618; 
 &#9474; &#8216;snd_pci_orig_save_state&#8217;:                                                 &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many       &#9646; 
 &#9474; arguments to function &#8216;pci_save_state&#8217;                                     &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h: In function                &#8595; 
  &#8216;snd_pci_orig_restore_state&#8217;:                                              &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many       &#9618; 
 &#9474; arguments to function &#8216;pci_restore_state&#8217;                                  &#9618; 
 &#9474; make[6]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1       &#9618; 
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2                  &#9618; 
 &#9474; make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2                &#9618; 
 &#9474; make[3]: *** [modules] Error 2                                             &#9618; 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'      &#9618; 
 &#9474; make[2]: *** [compile] Error 2                                             &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618; 
 &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9646; 
 &#9474; make: *** [kdist_image] Error 2                                            &#8595;


any ideas?

sorry my sound card is realtek alc260     
intel sb450

---

### Post by jet200 on 2008-03-21
I'm also having the same problem and cant seem to find a definitive solution, can some shed some light on how to enable sound on a laptop with realtek rlc260. I followed the "comprehensive audio guide" and my laptop recognizes the sound card but thats all. Any help would be greatly appreciated.

---

### Post by Yellow Pasque on 2008-03-21
Try these scripts to upgrade ALSA, and also see the link on configuring alsa-base
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by jet200 on 2008-03-21
Hmmm nope didnt fix my prob ubuntu sees the sound card but I cant hear anything Im starting   to think they dont support my soundcard.

---

### Post by superprash2003 on 2008-03-21
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by jet200 on 2008-03-21
Thanks superprash2003 but that was one of the links I came across when searching the sound problem, unfortunately it didnt work. :(

---

