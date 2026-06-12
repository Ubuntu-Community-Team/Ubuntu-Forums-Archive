---
title: "Can't compile Ndiswrapper 1.53"
date: 2008-10-11
forum: General Help
---

### Post by TheSwede86 on 2008-10-11
Hi!

Got Ubuntu 8.04 with kernel 2.6.24-19-generic and ndiswrapper 1.53 and can't compile it. I have a few translations at the end of this post. Please tell me if you need any translations or clarifications.

Try to "sudo make uninstall" and get:

NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.

and then run "sudo make" and get this:

ubuntu@ubuntu-laptop:~/Skrivbord/ndiswrapper-1.53$ sudo make
make -C driver
make[1]: Går till katalogen "/home/ubuntu/Skrivbord/ndiswrapper-1.53/driver"
make -C /usr/src/linux-headers-2.6.24-19-generic M=/home/ubuntu/Skrivbord/ndiswrapper-1.53/driver
make[2]: Går till katalogen "/usr/src/linux-headers-2.6.24-19-generic"
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Lämnar katalogen "/usr/src/linux-headers-2.6.24-19-generic"
make[1]: Lämnar katalogen "/home/ubuntu/Skrivbord/ndiswrapper-1.53/driver"
make -C utils
make[1]: Går till katalogen "/home/ubuntu/Skrivbord/ndiswrapper-1.53/utils"
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: fel: stdlib.h: Filen eller katalogen finns inte
loadndisdriver.c:16:19: fel: stdio.h: Filen eller katalogen finns inte
loadndisdriver.c:17:19: fel: errno.h: Filen eller katalogen finns inte
loadndisdriver.c:18:20: fel: string.h: Filen eller katalogen finns inte
loadndisdriver.c:19:20: fel: libgen.h: Filen eller katalogen finns inte
loadndisdriver.c:21:22: fel: sys/mman.h: Filen eller katalogen finns inte
loadndisdriver.c:23:23: fel: sys/types.h: Filen eller katalogen finns inte
loadndisdriver.c:24:23: fel: sys/ioctl.h: Filen eller katalogen finns inte
loadndisdriver.c:25:22: fel: sys/stat.h: Filen eller katalogen finns inte
loadndisdriver.c:26:20: fel: unistd.h: Filen eller katalogen finns inte
loadndisdriver.c:27:19: fel: fcntl.h: Filen eller katalogen finns inte
I fil inkluderad från /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 från /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 från loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: fel: limits.h: Filen eller katalogen finns inte
loadndisdriver.c:29:19: fel: ctype.h: Filen eller katalogen finns inte
loadndisdriver.c:30:20: fel: dirent.h: Filen eller katalogen finns inte
loadndisdriver.c:31:20: fel: syslog.h: Filen eller katalogen finns inte
loadndisdriver.c:34:25: fel: linux/major.h: Filen eller katalogen finns inte
loadndisdriver.c:35:25: fel: linux/ioctl.h: Filen eller katalogen finns inte
In file included from loadndisdriver.c:37:
../driver/loader.h:28: fel: expected specifier-qualifier-list before "size_t"
loadndisdriver.c: I funktion "load_file":
loadndisdriver.c:67: fel: "size_t" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:67: fel: (Varje odeklarerad identifierare rapporteras bara en gång
loadndisdriver.c:67: fel: för varje funktion den finns i.)
loadndisdriver.c:67: fel: expected ";" before "size"
loadndisdriver.c:68: fel: "NULL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:69: fel: lagringsstorlek på "statbuf" är okänd
loadndisdriver.c:71: varning: implicit deklaration av funktionen "basename"
loadndisdriver.c:71: varning: initiering skapar pekare från heltal utan typkonvertering
loadndisdriver.c:73: varning: implicit deklaration av funktionen "open"
loadndisdriver.c:73: fel: "O_RDONLY" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:75: varning: implicit deklaration av funktionen "syslog"
loadndisdriver.c:75: fel: "LOG_KERN" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:75: fel: "LOG_INFO" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:75: varning: implicit deklaration av funktionen "strerror"
loadndisdriver.c:75: fel: "errno" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:76: fel: "EINVAL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:79: varning: implicit deklaration av funktionen "fstat"
loadndisdriver.c:81: varning: implicit deklaration av funktionen "close"
loadndisdriver.c:84: fel: "size" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:86: varning: implicit deklaration av funktionen "mmap"
loadndisdriver.c:86: fel: "PROT_READ" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:86: fel: "MAP_PRIVATE" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:86: varning: tilldelning skapar pekare av heltal utan typkonvertering
loadndisdriver.c:87: fel: "MAP_FAILED" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:93: varning: implicit deklaration av funktionen "strncpy"
loadndisdriver.c:93: varning: inkompatibel implicit deklaration av inbyggd funktion "strncpy"
loadndisdriver.c:95: fel: "struct load_driver_file" har ingen medlem med namnet "size"
loadndisdriver.c:96: fel: "struct load_driver_file" har ingen medlem med namnet "data"
loadndisdriver.c:69: varning: oanvänd variabel "statbuf"
loadndisdriver.c: I funktion "parse_setting_line":
loadndisdriver.c:109: varning: implicit deklaration av funktionen "isspace"
loadndisdriver.c:115: varning: implicit deklaration av funktionen "strchr"
loadndisdriver.c:115: varning: inkompatibel implicit deklaration av inbyggd funktion "strchr"
loadndisdriver.c:115: fel: "NULL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:117: fel: "LOG_KERN" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:117: fel: "LOG_INFO" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:118: fel: "EINVAL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:138: varning: implicit deklaration av funktionen "strlen"
loadndisdriver.c:138: varning: inkompatibel implicit deklaration av inbyggd funktion "strlen"
loadndisdriver.c: I funktion "read_conf_file":
loadndisdriver.c:150: fel: lagringsstorlek på "statbuf" är okänd
loadndisdriver.c:151: fel: "FILE" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:151: fel: "config" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:157: varning: implicit deklaration av funktionen "lstat"
loadndisdriver.c:158: fel: "LOG_KERN" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:158: fel: "LOG_INFO" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:158: fel: "errno" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:160: fel: "EINVAL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:163: varning: implicit deklaration av funktionen "sscanf"
loadndisdriver.c:163: varning: inkompatibel implicit deklaration av inbyggd funktion "sscanf"
loadndisdriver.c:178: varning: implicit deklaration av funktionen "fopen"
loadndisdriver.c:178: fel: "NULL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:182: varning: implicit deklaration av funktionen "fgets"
loadndisdriver.c:194: varning: inkompatibel implicit deklaration av inbyggd funktion "strncpy"
loadndisdriver.c:205: varning: implicit deklaration av funktionen "fclose"
loadndisdriver.c:150: varning: oanvänd variabel "statbuf"
loadndisdriver.c: I funktion "load_bin_file":
loadndisdriver.c:217: fel: "LOG_KERN" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:217: fel: "LOG_INFO" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:219: varning: implicit deklaration av funktionen "tolower"
loadndisdriver.c:221: varning: implicit deklaration av funktionen "chdir"
loadndisdriver.c:222: fel: "errno" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:224: fel: "EINVAL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:230: varning: inkompatibel implicit deklaration av inbyggd funktion "strncpy"
loadndisdriver.c:232: varning: implicit deklaration av funktionen "ioctl"
loadndisdriver.c:232: varning: implicit deklaration av funktionen "_IOW"
loadndisdriver.c:232: fel: expected expression before "struct"
loadndisdriver.c: I funktion "load_driver":
loadndisdriver.c:249: fel: "DIR" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:249: fel: "driver_dir" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:251: fel: "NULL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:255: fel: "LOG_KERN" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:255: fel: "LOG_INFO" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:257: fel: "errno" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:259: fel: "EINVAL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:261: varning: implicit deklaration av funktionen "opendir"
loadndisdriver.c:267: varning: implicit deklaration av funktionen "malloc"
loadndisdriver.c:267: varning: inkompatibel implicit deklaration av inbyggd funktion "malloc"
loadndisdriver.c:271: varning: implicit deklaration av funktionen "memset"
loadndisdriver.c:271: varning: inkompatibel implicit deklaration av inbyggd funktion "memset"
loadndisdriver.c:272: varning: inkompatibel implicit deklaration av inbyggd funktion "strncpy"
loadndisdriver.c:280: varning: implicit deklaration av funktionen "readdir"
loadndisdriver.c:280: varning: tilldelning skapar pekare av heltal utan typkonvertering
loadndisdriver.c:282: fel: lagringsstorlek på "statbuf" är okänd
loadndisdriver.c:284: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:287: varning: implicit deklaration av funktionen "stat"
loadndisdriver.c:287: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:288: varning: implicit deklaration av funktionen "S_ISREG"
loadndisdriver.c:289: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:294: varning: inkompatibel implicit deklaration av inbyggd funktion "strlen"
loadndisdriver.c:294: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:296: varning: implicit deklaration av funktionen "strcasecmp"
loadndisdriver.c:296: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:299: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:302: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:303: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:305: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:311: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:312: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:313: varning: implicit deklaration av funktionen "strcpy"
loadndisdriver.c:313: varning: inkompatibel implicit deklaration av inbyggd funktion "strcpy"
loadndisdriver.c:314: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:317: fel: "struct load_driver_file" har ingen medlem med namnet "size"
loadndisdriver.c:318: fel: "struct load_driver_file" har ingen medlem med namnet "data"
loadndisdriver.c:321: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:282: varning: oanvänd variabel "statbuf"
loadndisdriver.c:344: fel: expected expression before "struct"
loadndisdriver.c:346: varning: implicit deklaration av funktionen "closedir"
loadndisdriver.c:348: varning: implicit deklaration av funktionen "free"
loadndisdriver.c:355: varning: implicit deklaration av funktionen "munmap"
loadndisdriver.c:355: fel: "struct load_driver_file" har ingen medlem med namnet "data"
loadndisdriver.c:355: fel: "struct load_driver_file" har ingen medlem med namnet "size"
loadndisdriver.c:357: fel: "struct load_driver_file" har ingen medlem med namnet "data"
loadndisdriver.c:357: fel: "struct load_driver_file" har ingen medlem med namnet "size"
loadndisdriver.c: I funktion "get_device":
loadndisdriver.c:367: fel: lagringsstorlek på "statbuf" är okänd
loadndisdriver.c:370: fel: "LOG_KERN" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:370: fel: "LOG_INFO" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:373: fel: "errno" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:374: fel: "EINVAL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:376: varning: implicit deklaration av funktionen "snprintf"
loadndisdriver.c:376: varning: inkompatibel implicit deklaration av inbyggd funktion "snprintf"
loadndisdriver.c:407: varning: inkompatibel implicit deklaration av inbyggd funktion "strncpy"
loadndisdriver.c:367: varning: oanvänd variabel "statbuf"
loadndisdriver.c: I funktion "load_device":
loadndisdriver.c:419: fel: "DIR" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:419: fel: "dir" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:423: fel: "LOG_KERN" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:423: fel: "LOG_INFO" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:424: varning: inkompatibel implicit deklaration av inbyggd funktion "memset"
loadndisdriver.c:426: fel: "errno" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:427: fel: "EINVAL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:429: fel: "NULL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:434: varning: tilldelning skapar pekare av heltal utan typkonvertering
loadndisdriver.c:435: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:436: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:439: fel: derefererar pekare till ofullständig typ
loadndisdriver.c:447: fel: expected expression before "struct"
loadndisdriver.c: I funktion "get_ioctl_device":
loadndisdriver.c:464: fel: "FILE" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:464: fel: "proc_misc" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:472: varning: implicit deklaration av funktionen "strstr"
loadndisdriver.c:472: varning: inkompatibel implicit deklaration av inbyggd funktion "strstr"
loadndisdriver.c:473: varning: implicit deklaration av funktionen "strtol"
loadndisdriver.c:473: fel: "NULL" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:483: fel: "LOG_KERN" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:483: fel: "LOG_INFO" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:488: varning: implicit deklaration av funktionen "unlink"
loadndisdriver.c:489: varning: implicit deklaration av funktionen "mknod"
loadndisdriver.c:489: fel: "S_IFCHR" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:489: fel: "MISC_MAJOR" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:490: fel: "errno" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:495: fel: "O_RDONLY" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c: I funktion "main":
loadndisdriver.c:511: varning: implicit deklaration av funktionen "openlog"
loadndisdriver.c:511: fel: "LOG_PERROR" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:511: fel: "LOG_CONS" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:511: fel: "LOG_KERN" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:511: fel: "LOG_DEBUG" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:513: fel: "LOG_INFO" är odeklarerad (första förekomsten i denna funktion)
loadndisdriver.c:515: varning: implicit deklaration av funktionen "strncmp"
loadndisdriver.c:517: varning: implicit deklaration av funktionen "printf"
loadndisdriver.c:517: varning: inkompatibel implicit deklaration av inbyggd funktion "printf"
loadndisdriver.c:527: varning: implicit deklaration av funktionen "atoi"
loadndisdriver.c:542: varning: implicit deklaration av funktionen "atof"
loadndisdriver.c:549: varning: implicit deklaration av funktionen "strcmp"
loadndisdriver.c:556: varning: inkompatibel implicit deklaration av inbyggd funktion "sscanf"
loadndisdriver.c:590: varning: implicit deklaration av funktionen "closelog"
make[1]: *** [loadndisdriver] Fel 1
make[1]: Lämnar katalogen "/home/ubuntu/Skrivbord/ndiswrapper-1.53/utils"
make: *** [all] Fel 2

Sorry for its in swedish, a little help here:

Fel = Error
odeklarerad = undecleared (or something like that)
"Filen eller katalogen finns inte" = File or folder does not exist
derefererar pekare till ofullständig typ = dereferer points to uncomplete type

What files do I lack if I am lacking any dependencies or/and what do I need to do to install ndiswrapper?

Thanks in advance & Best Regards - TheSwede86

---

