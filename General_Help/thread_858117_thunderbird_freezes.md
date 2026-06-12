---
title: "thunderbird freezes"
date: 2008-07-13
forum: General Help
---

### Post by Adnanius on 2008-07-13
Hello, 
When I lunch thunderbird, It opens, tries to download my new messages, and then freezes, so I have to force quit it. 
It doesn't give error messages.
Here's the terminal's output:
```
:~$ thunderbird 
*** glibc detected *** /usr/lib/thunderbird/thunderbird-bin: double free or corruption (out): 0x0000000001dc1dc0 ***
======= Backtrace: =========
/lib/libc.so.6[0x2ac0dddd6b0a]
/lib/libc.so.6(cfree+0x8c)[0x2ac0dddda6fc]
/usr/lib/thunderbird/libmozjs.so[0x2ac0d900cec5]
/usr/lib/thunderbird/libmozjs.so[0x2ac0d8fc66e1]
/usr/lib/thunderbird/libmozjs.so(JS_GC+0x2a)[0x2ac0d8f9dfea]
/usr/lib/thunderbird/components/libgklayout.so[0x2aaab11fa369]
/usr/lib/thunderbird/components/libgklayout.so[0x2aaab11f9002]
/usr/lib/thunderbird/components/libgklayout.so[0x2aaab1208abb]
/usr/lib/thunderbird/components/libgklayout.so[0x2aaab1208b77]
/usr/lib/thunderbird/libxpcom_core.so[0x2ac0d94d07fe]
/usr/lib/thunderbird/libxpcom_core.so[0x2ac0d94d0eaa]
/usr/lib/thunderbird/libxpcom_core.so(PL_HandleEvent+0x19)[0x2ac0d94cc9b9]
/usr/lib/thunderbird/libxpcom_core.so(PL_ProcessPendingEvents+0x4b)[0x2ac0d94ccc5b]
/usr/lib/thunderbird/libxpcom_core.so[0x2ac0d94cea2b]
/usr/lib/thunderbird/components/libwidget_gtk2.so[0x2aaaaf347072]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1c3)[0x2ac0dd129fd3]
/usr/lib/libglib-2.0.so.0[0x2ac0dd12d2dd]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0x2ac0dd12d5ea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x2ac0da2f5883]
/usr/lib/thunderbird/components/libwidget_gtk2.so[0x2aaaaf347425]
/usr/lib/thunderbird/components/libtoolkitcomps.so[0x2aaab0249f2e]
/usr/lib/thunderbird/thunderbird-bin[0x4078d3]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2ac0ddd82b44]
/usr/lib/thunderbird/thunderbird-bin[0x403a59]
======= Memory map: ========
00400000-00415000 r-xp 00000000 03:01 656729                             /usr/lib/thunderbird/thunderbird-bin
00615000-00617000 rw-p 00015000 03:01 656729                             /usr/lib/thunderbird/thunderbird-bin
00617000-01df5000 rw-p 00617000 00:00 0                                  [heap]
40000000-40001000 ---p 40000000 00:00 0 
40001000-40801000 rw-p 40001000 00:00 0 
40801000-40802000 ---p 40801000 00:00 0 
40802000-41002000 rw-p 40802000 00:00 0 
41002000-41003000 ---p 41002000 00:00 0 
41003000-41803000 rw-p 41003000 00:00 0 
41803000-41804000 ---p 41803000 00:00 0 
41804000-42004000 rw-p 41804000 00:00 0 
42004000-42005000 ---p 42004000 00:00 0 
42005000-42805000 rw-p 42005000 00:00 0 
42805000-42806000 ---p 42805000 00:00 0 
42806000-43006000 rw-p 42806000 00:00 0 
43006000-43007000 ---p 43006000 00:00 0 
43007000-43807000 rw-p 43007000 00:00 0 
43807000-43808000 ---p 43807000 00:00 0 
43808000-44008000 rw-p 43808000 00:00 0 
2aaaaaaab000-2aaaaaaeb000 r-xp 00000000 03:01 656525                     /usr/lib/thunderbird/components/libi18n.so
2aaaaaaeb000-2aaaaacea000 ---p 00040000 03:01 656525                     /usr/lib/thunderbird/components/libi18n.so
2aaaaacea000-2aaaaacef000 rw-p 0003f000 03:01 656525                     /usr/lib/thunderbird/components/libi18n.so
2aaaaacef000-2aaaaad02000 r-xp 00000000 03:01 656631                     /usr/lib/thunderbird/components/libchrome.so
2aaaaad02000-2aaaaaf01000 ---p 00013000 03:01 656631                     /usr/lib/thunderbird/components/libchrome.so
2aaaaaf01000-2aaaaaf03000 rw-p 00012000 03:01 656631                     /usr/lib/thunderbird/components/libchrome.so
2aaaaaf03000-2aaaaaf1a000 r-xp 00000000 03:01 656548                     /usr/lib/thunderbird/components/libjar50.so
2aaaaaf1a000-2aaaab11a000 ---p 00017000 03:01 656548                     /usr/lib/thunderbird/components/libjar50.so
2aaaab11a000-2aaaab11c000 rw-p 00017000 03:01 656548                     /usr/lib/thunderbird/components/libjar50.so
2aaaab11c000-2aaaab14e000 r-xp 00000000 03:01 656558                     /usr/lib/thunderbird/components/librdf.so
2aaaab14e000-2aaaab34e000 ---p 00032000 03:01 656558                     /usr/lib/thunderbird/components/librdf.so
2aaaab34e000-2aaaab352000 rw-p 00032000 03:01 656558                     /usr/lib/thunderbird/components/librdf.so
2aaaab352000-2aaaab3c4000 r-xp 00000000 03:01 656561                     /usr/lib/thunderbird/components/libhtmlpars.so
2aaaab3c4000-2aaaab5c3000 ---p 00072000 03:01 656561                     /usr/lib/thunderbird/components/libhtmlpars.so
2aaaab5c3000-2aaaab5


```

---

### Post by mike2357 on 2008-07-13
Possible solution:

[http://ubuntuforums.org/showthread.php?t=798803]("http://ubuntuforums.org/showthread.php?t=798803")

---

### Post by Adnanius on 2008-07-13
it's the first thing I tried. I would be ashamed if this works, the thread you gave me was mine! 
maybe this is a significant info : I recently defined a number of filters. It was working with the filters on. And well, when the freezing problem got online, I disabled the filters, but it didnt work. I uninstalled thunderbird andd reinstall it & replaced my .mozilla thuderbird folder in my home folder, it still didnt work.
Any ideas ?

---

### Post by p110011 on 2008-10-30
I think mine does the same thing, I download messages and click one to read but tbird turns Grey and I have to force quit.:confused:

---

