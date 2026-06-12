---
title: "Canon MF 5730 carps-cups driver compilation errors in Ubuntu 13.10"
date: 2014-02-18
forum: Hardware
---

### Post by vlkoff on 2014-02-18
Hi guys,

I'm new to Ubuntu, tryind to make my old printer working.

After some painfull research I have found this printer is not supported in Linux anywhere, finally I have found someone who has created the drivers:
[HTML]https://github.com/ondrej-zary/carps-cups/[/HTML]

I have downloaded the source files, checked the Makefile and found out it uses some executables which are missing on my system,
```

cups-config --datadir
cups-config --serverbin

```

so I installed 
```

sudo apt-get install libcups2-dev

```

The first compile attempt:
```

vlk@vlk-Latitude-E6410:~/Downloads/carps-cups-master$ sudo make
[sudo] password for vlk: 
gcc -Wall -Wextra --std=c99 -O2 carps-decode.c -o carps-decode
carps-decode.c: In function ‘decode_print_data’:
carps-decode.c:315:3: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 7 has type ‘long int’ [-Wformat=]
   printf("out_pos: 0x%x, line_num=%d, line_pos=%d (%d), len=%d, in_pos=0x%x ", out_bytes, line_num, line_pos, line_pos * 8, len, block_pos + data - start);
   ^
carps-decode.c: In function ‘get_block’:
carps-decode.c:63:8: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
   fread(data, 1, 1, f); /* discard the first 0x01 byte */
        ^
gcc -Wall -Wextra --std=c99 -O2 rastertocarps.c -o rastertocarps -lcupsimage
rastertocarps.c:11:25: fatal error: cups/raster.h: No such file or directory
 #include <cups/raster.h>
                         ^
compilation terminated.
make: *** [rastertocarps] Error 1

```

After some more research in
[HTML]http://ubuntuforums.org/showthread.php?t=1269926[/HTML]


I hgave installed:
```

sudo apt-get install libcupsimage2-dev
[COLOR=#000000][FONT=Courier][SIZE=3]sudo apt-get install build-essential[/SIZE][/FONT][/COLOR]

```

Second compilation attempt:
```

vlk@vlk-Latitude-E6410:~/Downloads/carps-cups-master$ sudo make
[sudo] password for vlk: 
gcc -Wall -Wextra --std=c99 -O2 rastertocarps.c -o rastertocarps -lcupsimage
rastertocarps.c: In function ‘encode_print_data’:
rastertocarps.c:289:9: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
    fread(cur_line, 1, line_len_file, f);
         ^
rastertocarps.c: In function ‘main’:
rastertocarps.c:550:8: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result [-Wunused-result]
   fgets(tmp, sizeof(tmp), f);
        ^
rastertocarps.c:556:9: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result [-Wunused-result]
    fgets(tmp, sizeof(tmp), f);
         ^
/usr/bin/ld: /tmp/ccYgFvmn.o: undefined reference to symbol 'cupsMarkOptions'
/usr/lib/x86_64-linux-gnu/libcups.so.2: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status
make: *** [rastertocarps] Error 1

```


I'm not a programmer, my abilities are at end here.
Any advice appreciated.
Thx Jiri

---

### Post by daniele-masciarelli on 2014-06-21
it seems there was an error in the make file and that it was fixed. is it working since then?

---

