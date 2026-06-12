---
title: "pidgin crash on jaunty"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by DustofDust on 2009-04-23
hi,

after i start pidgin it shows up and crashes.

any help is appreciated!

---

### Post by mwacky on 2009-04-23
start pidgin using the command line and post the message, someone will be able to help if you post that.

---

### Post by DustofDust on 2009-04-23
strange i installed it again and rebooted and it still crashed but now it works.

dont know why...

---

### Post by Pisi-Deff on 2009-04-24
Same problem :/
```
eerik@eerik:~$ pidgin
*** stack smashing detected ***: pidgin terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7676da8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7676d60]
/usr/lib/purple-2/libxfire.so[0xb5a27064]
/usr/lib/purple-2/libxfire.so(gfire_packet_131+0x579)[0xb5a1f09b]
/usr/lib/purple-2/libxfire.so(gfire_parse_packet+0x2ce)[0xb5a1d0a8]
/usr/lib/purple-2/libxfire.so(gfire_input_cb+0x47f)[0xb5a1cdd2]
pidgin[0x80a8e93]
/usr/lib/libglib-2.0.so.0[0xb7843dad]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb780cb88]
/usr/lib/libglib-2.0.so.0[0xb78100eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb78105ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7aff7d9]
pidgin(main+0x89a)[0x80c31ea]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb758f775]
pidgin[0x806db61]
======= Memory map: ========
08048000-0810e000 r-xp 00000000 08:08 1061116    /usr/bin/pidgin
0810e000-0810f000 r--p 000c5000 08:08 1061116    /usr/bin/pidgin
0810f000-08112000 rw-p 000c6000 08:08 1061116    /usr/bin/pidgin
09237000-09f5b000 rw-p 09237000 00:00 0          [heap]
b4942000-b4943000 r-xp 00000000 08:08 1099892    /usr/lib/pango/1.6.0/modules/pango-arabic-lang.so
b4943000-b4944000 r--p 00000000 08:08 1099892    /usr/lib/pango/1.6.0/modules/pango-arabic-lang.so
b4944000-b4945000 rw-p 00001000 08:08 1099892    /usr/lib/pango/1.6.0/modules/pango-arabic-lang.so
b4945000-b49a5000 rw-s 00000000 00:09 2785320    /SYSV00000000 (deleted)
b49a5000-b4a07000 rw-p b49a5000 00:00 0 
b4a28000-b4a88000 rw-s 00000000 00:09 2752543    /SYSV00000000 (deleted)
b4a88000-b4b14000 r--p 00000000 08:08 8435       /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b4b14000-b4b15000 r-xp 00000000 08:08 763568     /usr/lib/gconv/ISO8859-1.so
b4b15000-b4b16000 r--p 00001000 08:08 763568     /usr/lib/gconv/ISO8859-1.so
b4b16000-b4b17000 rw-p 00002000 08:08 763568     /usr/lib/gconv/ISO8859-1.so
b4b17000-b4be6000 rw-p b4b17000 00:00 0 
b4be6000-b4c25000 r-xp 00000000 08:08 1059273    /usr/lib/libhunspell-1.2.so.0.0.0
b4c25000-b4c26000 r--p 0003e000 08:08 1059273    /usr/lib/libhunspell-1.2.so.0.0.0
b4c26000-b4c2a000 rw-p 0003f000 08:08 1059273    /usr/lib/libhunspell-1.2.so.0.0.0
b4c37000-b4c39000 r-xp 00000000 08:08 1099891    /usr/lib/pango/1.6.0/modules/pango-arabic-fc.so
b4c39000-b4c3a000 r--p 00001000 08:08 1099891    /usr/lib/pango/1.6.0/modules/pango-arabic-fc.so
b4c3a000-b4c3b000 rw-p 00002000 08:08 1099891    /usr/lib/pango/1.6.0/modules/pango-arabic-fc.so
b4c3b000-b4c3f000 r-xp 00000000 08:08 1075763    /usr/lib/enchant/libenchant_myspell.so
b4c3f000-b4c40000 r--p 00003000 08:08 1075763    /usr/lib/enchant/libenchant_myspell.so
b4c40000-b4c41000 rw-p 00004000 08:08 1075763    /usr/lib/enchant/libenchant_myspell.so
b4c41000-b4c4c000 r-xp 00000000 08:08 1075762    /usr/lib/enchant/libenchant_ispell.so
b4c4c000-b4c4d000 r--p 0000a000 08:08 1075762    /usr/lib/enchant/libenchant_ispell.so
b4c4d000-b4c4e000 rw-p 0000b000 08:08 1075762    /usr/lib/enchant/libenchant_ispell.so
b4c4e000-b4c5b000 r-xp 00000000 08:08 467989     /lib/libgcc_s.so.1
b4c5b000-b4c5c000 r--p 0000c000 08:08 467989     /lib/libgcc_s.so.1
b4c5c000-b4c5d000 rw-p 0000d000 08:08 467989     /lib/libgcc_s.so.1
b4c5d000-b4d41000 r-xp 00000000 08:08 1059579    /usr/lib/libstdc++.so.6.0.10
b4d41000-b4d45000 r--p 000e3000 08:08 1059579    /usr/lib/libstdc++.so.6.0.10
b4d45000-b4d46000 rw-p 000e7000 08:08 1059579    /usr/lib/libstdc++.so.6.0.10
b4d46000-b4d4c000 rw-p b4d46000 00:00 0 
b4d4c000-b4de0000 r-xp 00000000 08:08 1060499    /usr/lib/libaspell.so.15.1.4
b4de0000-b4de3000 r--p 00093000 08:08 1060499    /usr/lib/libaspell.so.15.1.4
b4de3000-b4de4000 rw-p 00096000 08:08 1060499    /usr/lib/libaspell.so.15.1.4
b4de4000-b4de8000 rw-p b4de4000 00:00 0 
b4dea000-b4df2000 r-xp 00000000 08:08 1075761    /usr/lib/enchant/libenchant_hspell.so
b4df2000-b4df3000 r--p 00007000 08:08 1075761    /usr/lib/enchant/libenchant_hspell.so
b4df3000-b4df5000 rw-p 00008000 08:08 1075761    /usr/lib/enchant/libenchant_hspell.so
b4df5000-b4df7000 r-xp 00000000 08:08 1075764    /usr/lib/enchant/libenchant_zemberek.so
b4df7000-b4df8000 r--p 00001000 08:08 1075764    /usr/lib/enchant/libenchant_zemberek.so
b4df8000-b4df9000 rw-p 00002000 08:08 1075764    /usr/lib/enchant/libenchant_zemberek.so
b4df9000-b4dfb000 r-xp 00000000 08:08 1075760    /usr/lib/enchant/libenchant_aspell.so
b4dfb000-b4dfc000 r--p 00001000 08:08 1075760    /usr/lib/enchant/libenchant_aspell.so
b4dfc000-b4dfd000 rw-p 00002000 08:08 1075760    /usr/lib/enchant/libenchant_aspell.so
b4dfd000-b4dff000 r-xp 00000000 08:08 1099893    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4dff000-b4e00000 r--p 00001000 08:08 1099893    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4e00000-b4e01000 rw-p 00002000 08:08 1099893    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4e01000-b4e99000 r--p 00000000 08:08 8434       /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4e99000-b4e9f000 r--s 00000000 08:08 681912     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b4e9f000-b4ea2000 r--s 00000000 08:08 681839     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b4ea2000-b4ea5000 r--s 00000000 08:08 681915     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b4ea5000-b4ea6000 r--s 00000000 08:08 681673     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b4ea6000-b4ea9000 r--s 00000000 08:08 681840     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b4ea9000-b4eac000 r--s 00000000 08:08 681835     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4eac000-b4eaf000 r--s 00000000 08:08 681838     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4eaf000-b4eb7000 r--s 00000000 08:08 681834     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b4eb7000-b4ec2000 r--s 00000000 08:08 681914     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4ec2000-b4ec4000 r--s 00000000 08:08 683971     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b4ec4000-b4ec5000 r--s 00000000 08:08 681844     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4ec5000-b4ee7000 r--s 00000000 08:08 681843     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b4ee7000-b4eea000 r--s 00000000 08:08 683976     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4eea000-b4ef1000 r--s 00000000 08:08 681842     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4ef1000-b4ef7000 r--s 00000000 08:08 683960     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4ef7000-b4efe000 r--s 00000000 08:08 683955     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b4efe000-b4f00000 r--s 00000000 08:08 683970     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b4f00000-b4f18000 r--s 00000000 08:08 1149495    /usr/share/mime/mime.cache
b4f18000-b4f2a000 r-xp 00000000 08:08 1060414    /usr/lib/libgvfscommon.so.0.0.0
b4f2a000-b4f2b000 r--p 00012000 08:08 1060414    /usr/lib/libgvfscommon.so.0.0.0
b4f2b000-b4f2c000 rw-p 00013000 08:08 1060414    /usr/lib/libgvfscommon.so.0.0.0
b4f2c000-b4f3b000 r-xp 00000000 08:08 1092139    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b4f3b000-b4f3c000 r--p 0000e000 08:08 1092139    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b4f3c000-b4f3d000 rw-p 0000f000 08:08 1092139    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b4f3d000-b4f57000 r-xp 00000000 08:08 1092140    /usr/lib/gio/modules/libgvfsdbus.so
b4f57000-b4f58000 r--p 00019000 08:08 1092140    /usr/lib/gio/modules/libgvfsdbus.so
b4f58000-b4f59000 rw-p 0001a000 08:08 1092140    /usr/lib/gio/modules/libgvfsdbus.so
b4f59000-b4f5a000 ---p b4f59000 00:00 0 
b4f5a000-b575a000 rw-p b4f5a000 00:00 0 
b575a000-b575e000 r-xp 00000000 08:08 1091827    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b575e000-b575f000 r--p 00003000 08:08 1091827    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b575f000-b5760000 rw-p 00004000 08:08 1091827    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5760000-b57a6000 r-xp 00000000 08:08 1075507    /usr/lib/nss/libnssckbi.so
b57a6000-b57ae000 r--p 00045000 08:08 1075507    /usr/lib/nss/libnssckbi.so
b57ae000-b57b2000 rw-p 0004d000 08:08 1075507    /usr/lib/nss/libnssckbi.so
b57b2000-b57f6000 r-xp 00000000 08:08 1075504    /usr/lib/nss/libfreebl3.so
b57f6000-b57f7000 r--p 00043000 08:08 1075504    /usr/lib/nss/libfreebl3.so
b57f7000-b57f8000 rw-p 00044000 08:08 1075504    /usr/lib/nss/libfreebl3.so
b57f8000-b582c000 r-xp 00000000 08:08 1075505    /usr/lib/nss/libsoftokn3.so
b582c000-b582d000 r--p 00034000 08:08 1075505    /usr/lib/nss/libsoftokn3.so
b582d000-b582e000 rw-p 00035000 08:08 1075505    /usr/lib/nss/libsoftokn3.so
b582e000-b5864000 r-xp 00000000 08:08 1076313    /usr/lib/purple-2/libqq.so
b5864000-b5865000 ---p 00036000 Aborted
eerik@eerik:~$ 

```

---

### Post by DustofDust on 2009-04-24
do you have problems with tracker search tool? kill tracker and try it again, maybe that was the reason it didnt crash here.

---

### Post by Pisi-Deff on 2009-04-24
Back from school.
Killed all tracker processes -> still crashed
reinstalled pidgin package -> still crashed
reinstalled all packages i have installed with pidgin in their name -> still crashes.
*sigh*
(15 minutes later)
Updated G-Fire from 0.8.0 to 0.8.1 -> no crashes, yay ^^

---

### Post by KindredCharles on 2009-04-25
> **Pisi-Deff said:**
> Back from school.
Killed all tracker processes -> still crashed
reinstalled pidgin package -> still crashed
reinstalled all packages i have installed with pidgin in their name -> still crashes.
*sigh*
(15 minutes later)
Updated G-Fire from 0.8.0 to 0.8.1 -> no crashes, yay ^^

Thank you having the same problem just updated G-Fire fixed my problem

---

### Post by DustofDust on 2009-04-25
thanks for the gfire hint. reinstalled it and now it works again.

seems we are a lot of players using linux with pidgin and gfire.

---

### Post by KindredCharles on 2009-04-30
Did some software updates with update manager and now it's crashing again with same error

*** stack smashing detected ***: pidgin terminated


Gfire is the correct version anyone else having this issue again?

Also anyway to roll back my updates to fix this for now?

---

### Post by DustofDust on 2009-04-30
i suggest that you reinstall the latest 0.8.1

since i did this i have no problems

---

### Post by KindredCharles on 2009-04-30
> **DustofDust said:**
> i suggest that you reinstall the latest 0.8.1

since i did this i have no problems

I had this problem before, installed 0.8.1 it fixed it but now the problem has come back with some software updates.

---

### Post by DustofDust on 2009-04-30
i just talked with a gfire dev and a patch is in the work.

don't know when it is ready for download, so best you check [http://gfire.site40.net/](http://gfire.site40.net/) regularly.

---

### Post by KindredCharles on 2009-04-30
> **DustofDust said:**
> i just talked with a gfire dev and a patch is in the work.

don't know when it is ready for download, so best you check [http://gfire.site40.net/](http://gfire.site40.net/) regularly.

Thank you very much,

Anyone know a temp fix I can do while I wait for this patch?

---

### Post by KindredCharles on 2009-05-01
> **KindredCharles said:**
> Thank you very much,

Anyone know a temp fix I can do while I wait for this patch?

As the bug only effects you if your available I've changed my status to say away with the message that I'm there. anyone else have any better ideas I'd like to hear them. Hope this helps other people using gfire.

---

### Post by garylinux on 2009-05-08
rm -rf ~/.purple/icons/ worked for me
I seems the icons dir gets too large 
(this just worked for me)  the error I was getting was
"Gtk:ERROR:/build/buildd/gtk+2.0-2.16.1/gtk/gtktreestore.c:532:gtk_tree_store_get_path: assertion failed: (G_NODE (iter->user_data)->parent != NULL)
Aborted"

---

### Post by Intrinsic on 2009-05-21
Ok, I am brand new to Ubuntu.  I installed the latest versions of both pidgin, and gfire and this is the error that I get:

intrinsic@ubuntu:~$ pidgin
*** stack smashing detected ***: pidgin terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb76fdda8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb76fdd60]
/usr/lib/purple-2/libxfire.so[0xb5ea90e4]
/usr/lib/purple-2/libxfire.so[0xb5e98401]
pidgin(pidgin_blist_get_name_markup+0x11f)[0x808227f]
pidgin[0x80829fd]
pidgin[0x80838d4]
pidgin[0x8082e50]
pidgin[0x8082f66]
/usr/lib/libpurple.so.0(purple_blist_update_buddy_status+0xdc)[0xb77af0bc]
/usr/lib/libpurple.so.0(purple_prpl_got_user_status+0xc8)[0xb77e4ea8]
/usr/lib/purple-2/libxfire.so(gfire_update_buddy_status+0x2af)[0xb5e9a7d9]
/usr/lib/purple-2/libxfire.so(gfire_parse_packet+0x8b2)[0xb5e9f6b0]
/usr/lib/purple-2/libxfire.so(gfire_input_cb+0x47f)[0xb5e9edf6]
pidgin[0x80a8e93]
/usr/lib/libglib-2.0.so.0[0xb78cadad]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb7893b88]
/usr/lib/libglib-2.0.so.0[0xb78970eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb78975ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7b867d9]
pidgin(main+0x89a)[0x80c31ea]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7616775]
pidgin[0x806db61]
======= Memory map: ========
08048000-0810e000 r-xp 00000000 07:00 1532594    /usr/bin/pidgin
0810e000-0810f000 r--p 000c5000 07:00 1532594    /usr/bin/pidgin
0810f000-08112000 rw-p 000c6000 07:00 1532594    /usr/bin/pidgin
088cf000-0930a000 rw-p 088cf000 00:00 0          [heap]
b5756000-b57b6000 rw-s 00000000 00:09 6651933    /SYSV00000000 (deleted)
b57b6000-b5842000 r--p 00000000 07:00 1342669    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b5842000-b5911000 rw-p b5842000 00:00 0 
b5911000-b59a5000 r-xp 00000000 07:00 1195356    /usr/lib/libaspell.so.15.1.4
b59a5000-b59a8000 r--p 00093000 07:00 1195356    /usr/lib/libaspell.so.15.1.4
b59a8000-b59a9000 rw-p 00096000 07:00 1195356    /usr/lib/libaspell.so.15.1.4
b59a9000-b59ad000 rw-p b59a9000 00:00 0 
b59ad000-b59ec000 r-xp 00000000 07:00 1195828    /usr/lib/libhunspell-1.2.so.0.0.0
b59ec000-b59ed000 r--p 0003e000 07:00 1195828    /usr/lib/libhunspell-1.2.so.0.0.0
b59ed000-b59f1000 rw-p 0003f000 07:00 1195828    /usr/lib/libhunspell-1.2.so.0.0.0
b5a08000-b5a09000 r-xp 00000000 07:00 1422768    /usr/lib/gconv/ISO8859-1.so
b5a09000-b5a0a000 r--p 00001000 07:00 1422768    /usr/lib/gconv/ISO8859-1.so
b5a0a000-b5a0b000 rw-p 00002000 07:00 1422768    /usr/lib/gconv/ISO8859-1.so
b5a0b000-b5a18000 r-xp 00000000 07:00 1250993    /lib/libgcc_s.so.1
b5a18000-b5a19000 r--p 0000c000 07:00 1250993    /lib/libgcc_s.so.1
b5a19000-b5a1a000 rw-p 0000d000 07:00 1250993    /lib/libgcc_s.so.1
b5a1a000-b5afe000 r-xp 00000000 07:00 1196165    /usr/lib/libstdc++.so.6.0.10
b5afe000-b5b02000 r--p 000e3000 07:00 1196165    /usr/lib/libstdc++.so.6.0.10
b5b02000-b5b03000 rw-p 000e7000 07:00 1196165    /usr/lib/libstdc++.so.6.0.10
b5b03000-b5b09000 rw-p b5b03000 00:00 0 
b5b0a000-b5b0c000 r-xp 00000000 07:00 1211705    /usr/lib/enchant/libenchant_aspell.so
b5b0c000-b5b0d000 r--p 00001000 07:00 1211705    /usr/lib/enchant/libenchant_aspell.so
b5b0d000-b5b0e000 rw-p 00002000 07:00 1211705    /usr/lib/enchant/libenchant_aspell.so
b5b0e000-b5b10000 r-xp 00000000 07:00 1211709    /usr/lib/enchant/libenchant_zemberek.so
b5b10000-b5b11000 r--p 00001000 07:00 1211709    /usr/lib/enchant/libenchant_zemberek.so
b5b11000-b5b12000 rw-p 00002000 07:00 1211709    /usr/lib/enchant/libenchant_zemberek.so
b5b12000-b5b1a000 r-xp 00000000 07:00 1211706    /usr/lib/enchant/libenchant_hspell.so
b5b1a000-b5b1b000 r--p 00007000 07:00 1211706    /usr/lib/enchant/libenchant_hspell.so
b5b1b000-b5b1d000 rw-p 00008000 07:00 1211706    /usr/lib/enchant/libenchant_hspell.so
b5b1d000-b5b21000 r-xp 00000000 07:00 1211708    /usr/lib/enchant/libenchant_myspell.so
b5b21000-b5b22000 r--p 00003000 07:00 1211708    /usr/lib/enchant/libenchant_myspell.so
b5b22000-b5b23000 rw-p 00004000 07:00 1211708    /usr/lib/enchant/libenchant_myspell.so
b5b23000-b5b2e000 r-xp 00000000 07:00 1211707    /usr/lib/enchant/libenchant_ispell.so
b5b2e000-b5b2f000 r--p 0000a000 07:00 1211707    /usr/lib/enchant/libenchant_ispell.so
b5b2f000-b5b30000 rw-p 0000b000 07:00 1211707    /usr/lib/enchant/libenchant_ispell.so
b5b30000-b5b32000 r-xp 00000000 07:00 1276851    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5b32000-b5b33000 r--p 00001000 07:00 1276851    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5b33000-b5b34000 rw-p 00002000 07:00 1276851    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5b34000-b5bcc000 r--p 00000000 07:00 1342670    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5bcc000-b5bd2000 r--s 00000000 07:00 572383     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5bd2000-b5bd5000 r--s 00000000 07:00 572392     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b5bd5000-b5bd8000 r--s 00000000 07:00 572384     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b5bd8000-b5bdf000 r--s 00000000 07:00 573147     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5bdf000-b5be2000 r--s 00000000 07:00 572390     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5be2000-b5bea000 r--s 00000000 07:00 572393     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5bea000-b5bf5000 r--s 00000000 07:00 572373     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5bf5000-b5c17000 r--s 00000000 07:00 572784     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b5c17000-b5c1e000 r--s 00000000 07:00 572387     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5c1e000-b5c23000 r--s 00000000 07:00 573138     /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b5c23000-b5c29000 r--s 00000000 07:00 572372     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b5c29000-b5c43000 r-xp 00000000 07:00 1226404    /usr/lib/gio/modules/libgvfsdbus.so
b5c43000-b5c44000 r--p 00019000 07:00 1226404    /usr/lib/gio/modules/libgvfsdbus.so
b5c44000-b5c45000 rw-p 0001a000 07:00 1226404    /usr/lib/gio/modules/libgvfsdbus.so
b5c45000-b5c57000 r-xp 00000000 07:00 1195815    /usr/lib/libgvfscommon.so.0.0.0
b5c57000-b5c58000 r--p 00012000 07:00 1195815    /usr/lib/libgvfscommon.so.0.0.0
b5c58000-b5c59000 rw-p 00013000 07:00 1195815    /usr/lib/libgvfscommon.so.0.0.0
b5c59000-b5c73000 r--s 00000000 07:00 1292607    /usr/share/mime/mime.cache
b5c73000-b5cd3000 rw-s 00000000 00:09 6619164    /SYSV00000000 (deleted)
b5cd3000-b5d19000 r-xp 00000000 07:00 57235      /usr/lib/nss/libnssckbi.so
b5d19000-b5d21000 r--p 00045000 07:00 57235      /usr/lib/nss/libnssckbi.so
b5d21000-b5d25000 rw-p 0004d000 07:00 57235      /usr/lib/nss/libnssckbi.so
b5d25000-b5d69000 r-xp 00000000 07:00 57234      /usr/lib/nss/libfreebl3.so
b5d69000-b5d6a000 r--p 00043000 07:00 57234      /usr/lib/nss/libfreebl3.so
b5d6a000-b5d6b000 rw-p 00044000 07:00 57234      /usr/lib/nss/libfreebl3.so
b5d6b000-b5d9f000 r-xp 00000000 07:00 57238      /usr/lib/nss/libsoftokn3.so
b5d9f000-b5da0000 r--p 00034000 07:00 57238      /usr/lib/nss/libsoftokn3.so
b5da0000-b5da1000 rw-p 00035000 07:00 57238      /usr/lib/nss/libsoftokn3.so
b5da1000-b5dd0000 r-xp 00000000 07:00 1251008    /lib/libncurses.so.5.7
b5dd0000-b5dd2000 r--p 0002e000 07:00 1251008    /lib/libncurses.so.5.7
b5dd2000-b5dd3000 rw-p 00030000 07:00 1251008    /lib/libncurses.so.5.7
b5dd3000-b5dff000 r-xp 00000000 07:00 1251052    /lib/libreadline.so.5.2
b5dff000-b5e00000 ---p 0002c000 07:00 1251052    /lib/libreadline.so.5.2
b5e00000-b5e01000 r--p 0002c000 07:00 1251052    /lib/libreadline.so.5.2
b5e01000-b5e04000 rw-p 0002d000 07:00 1251052    /lib/libreadline.so.5.2
b5e04000-b5e05000 rw-p b5e04000 00:00 0 
b5e05000-b5e0e000 r-xp 00000000 07:00 1196258    /usr/lib/libzephyr.so.3.0.0
b5e0e000-b5e0f000 ---p 00009000 07:00 1196258    /usr/lib/libzephyr.so.3.0.0
b5e0f000-b5e10000 r--p 00009000 07:00 1196258    /usr/lib/libzephyr.so.3.0.0
b5e10000-b5e11000 rw-p 0000a000 07:00 1196258    /usr/lib/libzephyr.so.3.0.0
b5e11000-b5e14000 rw-p b5e11000 00:00 0 
b5e16000-b5e1d000 r--s 00000000 07:00 572968     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b5e1d000-b5e2c000 r-xp 00000000 07:00 1226403    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5e2c000-b5e2d000 r--p 0000e000 07:00 1226403    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5e2d000-b5e2e000 rw-p 0000f000 07:00 1226403    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5e2e000-b5e38000 r-xp 00000000 07:00 1562275    /usr/lib/purple-2/libsimple.so
b5e38000-b5e39000 r--p 00009000 07:00 1562275    /usr/lib/purple-2/libsimple.so
b5e39000-b5e3a000 rw-p 0000a000 07:00 1562275    /usr/lib/purple-2/libsimple.so
b5e3a000-b5e4a000 rw-p b5e3a000 00:00 0 
b5e4a000-b5e59000 r-xp 00000000 07:00 1195366    /usr/lib/libavahi-client.so.3.2.4
b5e59000-b5e5a000 r--p 0000e000 07:00 1195366    /usr/lib/libavahi-client.so.3.2.4
b5e5a000-b5e5b000 rw-p 0000f000 07:00 1195366    /usr/lib/libavahi-client.so.3.2.4
b5e5b000-b5e65000 r-xp 00000000 07:00 1195368    /usr/lib/libavahi-common.so.3.5.0
b5e65000-b5e66000 r--p 00009000 07:00 1195368    /usr/lib/libavahi-common.so.3.5.0
b5e66000-b5e67000 rw-p 0000a000 07:00 1195368    /usr/lib/libavahi-common.so.3.5.0
b5e67000-b5e68000 r--s 0000Aborted
intrinsic@ubuntu:~$ 

I have to say that I love being able to stay away from windows, but for noobs the lack of support/tuts is a bit frustrating.  I am trying to learn the language, but it is a lot tougher to learn because of the lack of help. I have posted in some forums and the replies that I get (if any) are sort of the superior/you-are-stupid-go-back-to-windows  kind of replies.

Any help in this would be appreciated. :)   I had heard that compiling from source can fix this problem, but when I tried to compile I recieved an error about not having pidgin installed, which I do, and I couldnt find a solution to that problem either.  Thanks a lot for any feedback.

---

### Post by sTpny on 2009-07-16
Hi all.. I had this problem too..  Nothing to do with G-fire for me.  I don't know what that is, nor could I find it in the Repos.  What did work was deleting the pidgin icons as suggested. Thanks lots.  I'm glad there are people here who are smarter than me. ;)

Anyhow... In regards to the lack of help.. well.. thats just part of open source.  Nobody should be calling anyone down.. newbies quite often get called down anyhow though.. because of their non-open-source attitude. People who write the software do not usually write the associated help files.. and the people who write the help files sometimes do not finish before the software itself gets updated.. In other words.. Things can change very fast.. and often... So until a piece of software is finished (are they ever?).. It is difficult to have a complete and accurate help file. 

Ok.. Thats my piece.. Also.. About the pidgin crash.. I had the plugin that archives all the icons for pidgin turned on (still do). Is this what caused the crash? Why would the Icon Directory being to full crash Pidgin? 

Last thing.. Umm.. For those of us who read this thread and don't have any idea about what G-fire is..  A quick explanation would be nice. 

Ok.. Thats really all.  

Thanks for the Great and Useful Info.. I really need my IM. ;)


----

sTpny

---

