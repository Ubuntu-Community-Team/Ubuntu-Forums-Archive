---
title: "[SOLVED] Howto install HP1018 on Feisty?"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by ttry72 on 2007-07-02
Hi all

My new printer does not work. The setup program identified the printer, but it cannot print out the test page (or any other). Please tell me, what is the right way to make it work on Feisty?

Issue is now solved. Just follow instructions of the link below:

[http://linuxdesktopsoftware.com/2007/04/how_to_install_a_hp1000_series.html](http://linuxdesktopsoftware.com/2007/04/how_to_install_a_hp1000_series.html)

---

### Post by linuxwizard on 2007-07-02
This might help look over notes make sure using recommended driver

[http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018](http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018)

---

### Post by ttry72 on 2007-07-02
> **linuxwizard said:**
> This might help look over notes make sure using recommended driver

[http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018](http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018)

I took the file foo2zjs and followed the instructions ([http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL)).

Unfortunately I got a long error message after the 'make' command:
----
sudo make
#
# Dependencies...
#
# ... OK!
#
cc -O2 -Wall   -c -o foo2zjs.o foo2zjs.c
foo2zjs.c:60:19: error: stdio.h: No such file or directory
foo2zjs.c:61:20: error: stdlib.h: No such file or directory
foo2zjs.c:62:19: error: ctype.h: No such file or directory
foo2zjs.c:63:20: error: string.h: No such file or directory
foo2zjs.c:64:20: error: unistd.h: No such file or directory
In file included from foo2zjs.c:67:
zjs.h:9:22: error: inttypes.h: No such file or directory
In file included from foo2zjs.c:67:
zjs.h:10: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘DWORD’
zjs.h:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WORD’
zjs.h:12: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘BYTE’
zjs.h:36: error: expected specifier-qualifier-list before ‘DWORD’
zjs.h:248: error: expected specifier-qualifier-list before ‘DWORD’
zjs.h:256: error: expected specifier-qualifier-list before ‘DWORD’
zjs.h:261: error: expected specifier-qualifier-list before ‘int32_t’
zjs.h:265: error: ‘uint32_t’ undeclared here (not in a function)
zjs.h:266: error: expected specifier-qualifier-list before ‘uint32_t’
zjs.h:270: error: ‘uint16_t’ undeclared here (not in a function)
zjs.h:271: error: expected specifier-qualifier-list before ‘uint16_t’
zjs.h:275: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘be32’
zjs.h:293: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘be16’
foo2zjs.c:114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
foo2zjs.c:117: error: expected specifier-qualifier-list before ‘off_t’
foo2zjs.c:121: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SeekMedia’
foo2zjs.c: In function ‘usage’:
foo2zjs.c:140: warning: implicit declaration of function ‘fprintf’
foo2zjs.c:140: warning: incompatible implicit declaration of built-in function ‘fprintf’
foo2zjs.c:140: error: ‘stderr’ undeclared (first use in this function)
foo2zjs.c:140: error: (Each undeclared identifier is reported only once
foo2zjs.c:140: error: for each function it appears in.)
foo2zjs.c:222: warning: implicit declaration of function ‘exit’
foo2zjs.c:222: warning: incompatible implicit declaration of built-in function ‘exit’
foo2zjs.c: In function ‘debug’:
foo2zjs.c:319: warning: implicit declaration of function ‘setvbuf’
foo2zjs.c:319: error: ‘stderr’ undeclared (first use in this function)
foo2zjs.c:319: error: ‘_IOLBF’ undeclared (first use in this function)
foo2zjs.c:319: error: ‘BUFSIZ’ undeclared (first use in this function)
foo2zjs.c:321: warning: implicit declaration of function ‘vfprintf’
foo2zjs.c: In function ‘error’:
foo2zjs.c:331: error: ‘stderr’ undeclared (first use in this function)
foo2zjs.c:335: warning: incompatible implicit declaration of built-in function ‘exit’
foo2zjs.c: At top level:
foo2zjs.c:340: error: expected declaration specifiers or ‘...’ before ‘FILE’
foo2zjs.c: In function ‘chunk_write_rsvd’:
foo2zjs.c:344: error: ‘ZJ_HEADER’ has no member named ‘type’
foo2zjs.c:344: warning: implicit declaration of function ‘be32’
foo2zjs.c:345: error: ‘ZJ_HEADER’ has no member named ‘items’
foo2zjs.c:346: error: ‘ZJ_HEADER’ has no member named ‘size’
foo2zjs.c:347: error: ‘ZJ_HEADER’ has no member named ‘reserved’
foo2zjs.c:347: warning: implicit declaration of function ‘be16’
foo2zjs.c:348: error: ‘ZJ_HEADER’ has no member named ‘signature’
foo2zjs.c:349: warning: implicit declaration of function ‘fwrite’
foo2zjs.c:349: warning: incompatible implicit declaration of built-in function ‘fwrite’
foo2zjs.c:349: error: ‘fp’ undeclared (first use in this function)
foo2zjs.c: At top level:
foo2zjs.c:354: error: expected declaration specifiers or ‘...’ before ‘FILE’
foo2zjs.c: In function ‘chunk_write’:
foo2zjs.c:356: error: ‘fp’ undeclared (first use in this function)
foo2zjs.c:356: error: too many arguments to function ‘chunk_write_rsvd’
foo2zjs.c: At top level:
foo2zjs.c:360: error: expected declaration specifiers or ‘...’ before ‘FILE’
foo2zjs.c: In function ‘item_uint32_write’:
foo2zjs.c:364: error: ‘ZJ_ITEM_HEADER’ has no member named ‘size’
foo2zjs.c:365: error: ‘ZJ_ITEM_HEADER’ has no member named ‘item’
foo2zjs.c:366: error: ‘ZJ_ITEM_HEADER’ has no member named ‘type’
foo2zjs.c:367: error: ‘ZJ_ITEM_HEADER’ has no member named ‘param’
foo2zjs.c:368: error: ‘ZJ_ITEM_UINT32’ has no member named ‘value’
foo2zjs.c:369: warning: incompatible implicit declaration of built-in function ‘fwrite’
foo2zjs.c:369: error: ‘fp’ undeclared (first use in this function)
foo2zjs.c: At top level:
foo2zjs.c:373: error: expected declaration specifiers or ‘...’ before ‘FILE’
foo2zjs.c: In function ‘item_str_write’:
foo2zjs.c:378: warning: implicit declaration of function ‘strlen’
foo2zjs.c:378: warning: incompatible implicit declaration of built-in function ‘strlen’
foo2zjs.c:380: error: ‘ZJ_ITEM_HEADER’ has no member named ‘size’
foo2zjs.c:381: error: ‘ZJ_ITEM_HEADER’ has no member named ‘item’
foo2zjs.c:382: error: ‘ZJ_ITEM_HEADER’ has no member named ‘type’
foo2zjs.c:383: error: ‘ZJ_ITEM_HEADER’ has no member named ‘param’
foo2zjs.c:384: error: ‘fp’ undeclared (first use in this function)
foo2zjs.c:386: warning: incompatible implicit declaration of built-in function ‘fwrite’
foo2zjs.c: In function ‘free_chain’:
foo2zjs.c:410: warning: implicit declaration of function ‘free’
foo2zjs.c: At top level:
foo2zjs.c:416: error: expected declaration specifiers or ‘...’ before ‘FILE’
foo2zjs.c: In function ‘write_plane’:
foo2zjs.c:435: error: ‘fp’ undeclared (first use in this function)
foo2zjs.c:435: error: too many arguments to function ‘chunk_write’
foo2zjs.c:436: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:443: error: too many arguments to function ‘chunk_write’
foo2zjs.c:444: warning: incompatible implicit declaration of built-in function ‘fwrite’
foo2zjs.c:454: error: too many arguments to function ‘chunk_write’
foo2zjs.c:455: warning: incompatible implicit declaration of built-in function ‘fwrite’
foo2zjs.c:457: warning: implicit declaration of function ‘putc’
foo2zjs.c:463: error: too many arguments to function ‘chunk_write’
foo2zjs.c:465: error: too many arguments to function ‘chunk_write’
foo2zjs.c: At top level:
foo2zjs.c:470: error: expected declaration specifiers or ‘...’ before ‘FILE’
foo2zjs.c: In function ‘start_page’:
foo2zjs.c:505: error: ‘ofp’ undeclared (first use in this function)
foo2zjs.c:505: error: too many arguments to function ‘chunk_write’
foo2zjs.c:508: error: too many arguments to function ‘chunk_write_rsvd’
foo2zjs.c:509: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:511: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:512: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:513: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:514: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:515: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:516: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:518: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:520: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:524: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:526: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:528: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:529: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:530: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:531: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:532: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:533: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:534: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c:535: error: ‘EvenPages’ undeclared (first use in this function)
foo2zjs.c:536: error: ‘SeekMedia’ undeclared (first use in this function)
foo2zjs.c:536: warning: implicit declaration of function ‘ftell’
foo2zjs.c:538: error: too many arguments to function ‘item_uint32_write’
foo2zjs.c: At top level:
foo2zjs.c:542: error: expected ‘)’ before ‘*’ token
foo2zjs.c:549: error: expected declaration specifiers or ‘...’ before ‘FILE’
foo2zjs.c: In function ‘write_page’:
foo2zjs.c:553: error: ‘ofp’ undeclared (first use in this function)
foo2zjs.c:553: error: too many arguments to function ‘start_page’
foo2zjs.c:556: error: too many arguments to function ‘write_plane’
foo2zjs.c:558: error: too many arguments to function ‘write_plane’
foo2zjs.c:562: error: too many arguments to function ‘write_plane’
foo2zjs.c:564: error: too many arguments to function ‘write_plane’
foo2zjs.c:567: error: too many arguments to function ‘write_plane’
foo2zjs.c:569: warning: implicit declaration of function ‘end_page’
foo2zjs.c: In function ‘output_jbig’:
foo2zjs.c:586: warning: implicit declaration of function ‘malloc’
foo2zjs.c:586: warning: incompatible implicit declaration of built-in function ‘malloc’
foo2zjs.c:608: warning: incompatible implicit declaration of built-in function ‘malloc’
foo2zjs.c:615: warning: implicit declaration of function ‘memcpy’
foo2zjs.c:615: warning: incompatible implicit declaration of built-in function ‘memcpy’
foo2zjs.c:622: warning: incompatible implicit declaration of built-in function ‘malloc’
foo2zjs.c: At top level:
foo2zjs.c:634: error: expected ‘)’ before ‘*’ token
foo2zjs.c:677: error: expected ‘)’ before ‘*’ token
foo2zjs.c:688: error: expected ‘)’ before ‘*’ token
foo2zjs.c: In function ‘cmyk_planes’:
foo2zjs.c:712: warning: implicit declaration of function ‘memset’
foo2zjs.c:712: warning: incompatible implicit declaration of built-in function ‘memset’
foo2zjs.c: At top level:
foo2zjs.c:782: error: expected declaration specifiers or ‘...’ before ‘FILE’
foo2zjs.c: In function ‘cmyk_page’:
foo2zjs.c:793: warning: incompatible implicit declaration of built-in function ‘malloc’
foo2zjs.c:803: error: ‘FILE’ undeclared (first use in this function)
foo2zjs.c:803: error: ‘dfp’ undeclared (first use in this function)
foo2zjs.c:805: warning: implicit declaration of function ‘sprintf’
foo2zjs.c:805: warning: incompatible implicit declaration of built-in function ‘sprintf’
foo2zjs.c:806: warning: implicit declaration of function ‘fopen’
foo2zjs.c:809: warning: incompatible implicit declaration of built-in function ‘fwrite’
foo2zjs.c:810: warning: implicit declaration of function ‘fclose’
foo2zjs.c:824: error: ‘ofp’ undeclared (first use in this function)
foo2zjs.c:824: error: too many arguments to function ‘write_page’
foo2zjs.c:826: error: too many arguments to function ‘write_page’
foo2zjs.c:828: error: too many arguments to function ‘write_page’
foo2zjs.c: At top level:
foo2zjs.c:836: error: expected declaration specifiers or ‘...’ before ‘FILE’
foo2zjs.c: In function ‘pksm_page’:
foo2zjs.c:859: error: ‘ofp’ undeclared (first use in this function)
foo2zjs.c:859: error: too many arguments to function ‘write_page’
foo2zjs.c:861: error: too many arguments to function ‘write_page’
foo2zjs.c:863: error: too many arguments to function ‘write_page’
foo2zjs.c: At top level:
foo2zjs.c:869: error: expected declaration specifiers or ‘...’ before ‘FILE’
foo2zjs.c: In function ‘pbm_page’:
foo2zjs.c:906: error: ‘ofp’ undeclared (first use in this function)
foo2zjs.c:906: error: too many arguments to function ‘write_page’
foo2zjs.c: At top level:
foo2zjs.c:914: error: expected declaration specifiers or ‘...’ before ‘FILE’
foo2zjs.c: In function ‘read_and_clip_image’:
foo2zjs.c:920: warning: incompatible implicit declaration of built-in function ‘malloc’
foo2zjs.c:929: warning: implicit declaration of function ‘fread’
foo2zjs.c:929: error: ‘ifp’ undeclared (first use in this function)
foo2zjs.c:952: warning: incompatible implicit declaration of built-in function ‘memset’
foo2zjs.c:984: error: ‘EOF’ undeclared (first use in this function)
foo2zjs.c: At top level:
foo2zjs.c:988: error: expected ‘)’ before ‘*’ token
foo2zjs.c:1056: error: expected ‘)’ before ‘*’ token
foo2zjs.c:1073: error: expected ‘)’ before ‘*’ token
foo2zjs.c:1087: error: expected ‘)’ before ‘*’ token
foo2zjs.c:1112: error: expected ‘)’ before ‘*’ token
foo2zjs.c:1240: error: expected ‘)’ before ‘*’ token
foo2zjs.c:1316: error: expected ‘)’ before ‘*’ token
foo2zjs.c: In function ‘parse_xy’:
foo2zjs.c:1348: warning: implicit declaration of function ‘strtoul’
foo2zjs.c: At top level:
foo2zjs.c:1360: error: expected ‘)’ before ‘*’ token
foo2zjs.c: In function ‘main’:
foo2zjs.c:1400: warning: implicit declaration of function ‘getopt’
foo2zjs.c:1401: error: ‘EOF’ undeclared (first use in this function)
foo2zjs.c:1405: warning: implicit declaration of function ‘atoi’
foo2zjs.c:1405: error: ‘optarg’ undeclared (first use in this function)
foo2zjs.c:1427: warning: implicit declaration of function ‘strcmp’
foo2zjs.c:1453: warning: implicit declaration of function ‘printf’
foo2zjs.c:1453: warning: incompatible implicit declaration of built-in function ‘printf’
foo2zjs.c:1453: warning: incompatible implicit declaration of built-in function ‘exit’
foo2zjs.c:1466: error: ‘optind’ undeclared (first use in this function)
foo2zjs.c:1484: error: ‘EvenPages’ undeclared (first use in this function)
foo2zjs.c:1484: warning: implicit declaration of function ‘tmpfile’
foo2zjs.c:1488: warning: implicit declaration of function ‘start_doc’
foo2zjs.c:1488: error: ‘stdout’ undeclared (first use in this function)
foo2zjs.c:1492: warning: implicit declaration of function ‘do_one’
foo2zjs.c:1492: error: ‘stdin’ undeclared (first use in this function)
foo2zjs.c:1498: error: ‘FILE’ undeclared (first use in this function)
foo2zjs.c:1498: error: ‘ifp’ undeclared (first use in this function)
foo2zjs.c:1513: error: ‘DWORD’ undeclared (first use in this function)
foo2zjs.c:1513: error: expected ‘;’ before ‘media’
foo2zjs.c:1518: error: ‘struct <anonymous>’ has no member named ‘b’
foo2zjs.c:1519: warning: implicit declaration of function ‘blank_page’
foo2zjs.c:1520: error: ‘struct <anonymous>’ has no member named ‘e’
foo2zjs.c:1522: error: ‘struct <anonymous>’ has no member named ‘b’
foo2zjs.c:1522: error: ‘struct <anonymous>’ has no member named ‘e’
foo2zjs.c:1530: warning: implicit declaration of function ‘load_tray2’
foo2zjs.c:1532: warning: implicit declaration of function ‘fseek’
foo2zjs.c:1532: error: ‘SeekMedia’ undeclared (first use in this function)
foo2zjs.c:1533: error: ‘media’ undeclared (first use in this function)
foo2zjs.c:1534: warning: incompatible implicit declaration of built-in function ‘fwrite’
foo2zjs.c:1540: error: ‘struct <anonymous>’ has no member named ‘b’
foo2zjs.c:1540: error: ‘struct <anonymous>’ has no member named ‘e’
foo2zjs.c:1541: error: ‘struct <anonymous>’ has no member named ‘b’
foo2zjs.c:1542: error: ‘struct <anonymous>’ has no member named ‘e’
foo2zjs.c:1542: error: ‘struct <anonymous>’ has no member named ‘b’
foo2zjs.c:1543: warning: implicit declaration of function ‘getc’
foo2zjs.c:1548: warning: implicit declaration of function ‘end_doc’
foo2zjs.c:1550: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [foo2zjs.o] Error 1
---


What does it mean and what is the reason for the errors?

---

