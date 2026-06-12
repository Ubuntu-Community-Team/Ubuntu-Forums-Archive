---
title: "Errors in OSSEC-HIDS Install"
date: 2008-08-29
forum: General Help
---

### Post by ShinHadoken on 2008-08-29
Hey guys,

I don't know if any of you are [OSSEC-HIDS]("http://www.ossec.com/") users, but I've found it to be an effective HIDS. However, while trying to install, I got all of this junk:

```
gzio.c:580: error: ‘gz_stream’ has no member named ‘outbuf’
gzio.c:581: warning: incompatible implicit declaration of built-in function ‘fwrite’
gzio.c:581: error: ‘gz_stream’ has no member named ‘outbuf’
gzio.c:581: error: ‘gz_stream’ has no member named ‘file’
gzio.c:587: error: ‘gz_stream’ has no member named ‘in’
gzio.c:588: error: ‘gz_stream’ has no member named ‘out’
gzio.c:590: error: ‘gz_stream’ has no member named ‘in’
gzio.c:591: error: ‘gz_stream’ has no member named ‘out’
gzio.c:594: error: ‘gz_stream’ has no member named ‘crc’
gzio.c:594: error: ‘gz_stream’ has no member named ‘crc’
gzio.c: In function ‘gzprintf’:
gzio.c:632: warning: implicit declaration of function ‘vsnprintf’
gzio.c: In function ‘gzputs’:
gzio.c:702: warning: incompatible implicit declaration of built-in function ‘strlen’
gzio.c: In function ‘do_flush’:
gzio.c:718: error: ‘gz_stream’ has no member named ‘mode’
gzio.c:726: warning: incompatible implicit declaration of built-in function ‘fwrite’
gzio.c:726: error: ‘gz_stream’ has no member named ‘outbuf’
gzio.c:726: error: ‘gz_stream’ has no member named ‘file’
gzio.c:730: error: ‘gz_stream’ has no member named ‘outbuf’
gzio.c:734: error: ‘gz_stream’ has no member named ‘out’
gzio.c:736: error: ‘gz_stream’ has no member named ‘out’
gzio.c: In function ‘gzflush’:
gzio.c:759: warning: implicit declaration of function ‘fflush’
gzio.c:759: error: ‘gz_stream’ has no member named ‘file’
gzio.c: In function ‘gzseek’:
gzio.c:784: error: ‘gz_stream’ has no member named ‘mode’
gzio.c:789: error: ‘gz_stream’ has no member named ‘in’
gzio.c:794: error: ‘gz_stream’ has no member named ‘inbuf’
gzio.c:795: error: ‘gz_stream’ has no member named ‘inbuf’
gzio.c:795: warning: incompatible implicit declaration of built-in function ‘malloc’
gzio.c:796: error: ‘gz_stream’ has no member named ‘inbuf’
gzio.c:797: warning: implicit declaration of function ‘memset’
gzio.c:797: warning: incompatible implicit declaration of built-in function ‘memset’
gzio.c:797: error: ‘gz_stream’ has no member named ‘inbuf’
gzio.c:803: error: ‘gz_stream’ has no member named ‘inbuf’
gzio.c:808: error: ‘gz_stream’ has no member named ‘in’
gzio.c:815: error: ‘gz_stream’ has no member named ‘out’
gzio.c:819: error: ‘gz_stream’ has no member named ‘transparent’
gzio.c:821: error: ‘gz_stream’ has no member named ‘back’
gzio.c:821: error: ‘EOF’ undeclared (first use in this function)
gzio.c:823: error: ‘gz_stream’ has no member named ‘inbuf’
gzio.c:824: warning: implicit declaration of function ‘fseek’
gzio.c:824: error: ‘gz_stream’ has no member named ‘file’
gzio.c:826: error: ‘gz_stream’ has no member named ‘in’
gzio.c:826: error: ‘gz_stream’ has no member named ‘out’
gzio.c:831: error: ‘gz_stream’ has no member named ‘out’
gzio.c:832: error: ‘gz_stream’ has no member named ‘out’
gzio.c:838: error: ‘gz_stream’ has no member named ‘outbuf’
gzio.c:839: error: ‘gz_stream’ has no member named ‘outbuf’
gzio.c:839: warning: incompatible implicit declaration of built-in function ‘malloc’
gzio.c:840: error: ‘gz_stream’ has no member named ‘outbuf’
gzio.c:842: error: ‘gz_stream’ has no member named ‘back’
gzio.c:843: error: ‘gz_stream’ has no member named ‘back’
gzio.c:844: error: ‘gz_stream’ has no member named ‘out’
gzio.c:846: error: ‘gz_stream’ has no member named ‘last’
gzio.c:852: error: ‘gz_stream’ has no member named ‘outbuf’
gzio.c:856: error: ‘gz_stream’ has no member named ‘out’
gzio.c:857: warning: control reaches end of non-void function
gzio.c: In function ‘gzrewind’:
gzio.c:867: error: ‘gz_stream’ has no member named ‘mode’
gzio.c:871: error: ‘gz_stream’ has no member named ‘back’
gzio.c:871: error: ‘EOF’ undeclared (first use in this function)
gzio.c:873: error: ‘gz_stream’ has no member named ‘inbuf’
gzio.c:874: error: ‘gz_stream’ has no member named ‘crc’
gzio.c:875: error: ‘gz_stream’ has no member named ‘transparent’
gzio.c:876: error: ‘gz_stream’ has no member named ‘in’
gzio.c:877: error: ‘gz_stream’ has no member named ‘out’
gzio.c:878: error: ‘gz_stream’ has no member named ‘file’
gzio.c:878: error: ‘gz_stream’ has no member named ‘start’
gzio.c: In function ‘gzeof’:
gzio.c:905: error: ‘gz_stream’ has no member named ‘mode’
gzio.c: In function ‘gzdirect’:
gzio.c:918: error: ‘gz_stream’ has no member named ‘mode’
gzio.c:919: error: ‘gz_stream’ has no member named ‘transparent’
gzio.c:920: warning: control reaches end of non-void function
gzio.c: In function ‘putLong’:
gzio.c:926: error: expected declaration specifiers before ‘FILE’
gzio.c:931: warning: implicit declaration of function ‘fputc’
gzio.c: In function ‘getLong’:
gzio.c:949: error: ‘EOF’ undeclared (first use in this function)
gzio.c: In function ‘gzclose’:
gzio.c:965: error: ‘gz_stream’ has no member named ‘mode’
gzio.c:972: error: ‘gz_stream’ has no member named ‘file’
gzio.c:972: error: ‘gz_stream’ has no member named ‘crc’
gzio.c:973: error: ‘gz_stream’ has no member named ‘file’
gzio.c:973: error: ‘gz_stream’ has no member named ‘in’
gzio.c: In function ‘gzerror’:
gzio.c:1007: warning: implicit declaration of function ‘strerror’
gzio.c:1007: error: ‘errno’ undeclared (first use in this function)
gzio.c:1007: warning: pointer/integer type mismatch in conditional expression
gzio.c:1011: error: ‘gz_stream’ has no member named ‘msg’
gzio.c:1011: error: ‘gz_stream’ has no member named ‘msg’
gzio.c:1012: warning: incompatible implicit declaration of built-in function ‘strlen’
gzio.c:1012: error: ‘gz_stream’ has no member named ‘path’
gzio.c:1014: error: ‘gz_stream’ has no member named ‘msg’
gzio.c:1014: warning: incompatible implicit declaration of built-in function ‘malloc’
gzio.c:1015: error: ‘gz_stream’ has no member named ‘msg’
gzio.c:1017: error: ‘gz_stream’ has no member named ‘msg’
gzio.c:1018: warning: incompatible implicit declaration of built-in function ‘snprintf’
gzio.c:1018: error: ‘gz_stream’ has no member named ‘msg’
gzio.c:1018: error: ‘gz_stream’ has no member named ‘path’
gzio.c:1019: error: ‘gz_stream’ has no member named ‘msg’
gzio.c:1020: warning: control reaches end of non-void function
gzio.c: In function ‘gzclearerr’:
gzio.c:1033: warning: implicit declaration of function ‘clearerr’
gzio.c:1033: error: ‘gz_stream’ has no member named ‘file’
In file included from infback.c:13:
zutil.h:23:22: error: string.h: No such file or directory
zutil.h:24:22: error: stdlib.h: No such file or directory
zutil.h:38:23: error: errno.h: No such file or directory
infback.c: In function ‘inflateBack’:
infback.c:338: warning: implicit declaration of function ‘memcpy’
infback.c:338: warning: incompatible implicit declaration of built-in function ‘memcpy’
In file included from inffast.c:6:
zutil.h:23:22: error: string.h: No such file or directory
zutil.h:24:22: error: stdlib.h: No such file or directory
zutil.h:38:23: error: errno.h: No such file or directory
In file included from inflate.c:83:
zutil.h:23:22: error: string.h: No such file or directory
zutil.h:24:22: error: stdlib.h: No such file or directory
zutil.h:38:23: error: errno.h: No such file or directory
inflate.c: In function ‘updatewindow’:
inflate.c:350: warning: implicit declaration of function ‘memcpy’
inflate.c:350: warning: incompatible implicit declaration of built-in function ‘memcpy’
inflate.c:357: warning: incompatible implicit declaration of built-in function ‘memcpy’
inflate.c: In function ‘inflate’:
inflate.c:688: warning: incompatible implicit declaration of built-in function ‘memcpy’
inflate.c:826: warning: incompatible implicit declaration of built-in function ‘memcpy’
inflate.c: In function ‘inflateSetDictionary’:
inflate.c:1197: warning: incompatible implicit declaration of built-in function ‘memcpy’
inflate.c:1202: warning: incompatible implicit declaration of built-in function ‘memcpy’
inflate.c: In function ‘inflateCopy’:
inflate.c:1353: warning: incompatible implicit declaration of built-in function ‘memcpy’
In file included from inftrees.c:6:
zutil.h:23:22: error: string.h: No such file or directory
zutil.h:24:22: error: stdlib.h: No such file or directory
zutil.h:38:23: error: errno.h: No such file or directory
In file included from deflate.h:16,
                 from trees.c:36:
zutil.h:23:22: error: string.h: No such file or directory
zutil.h:24:22: error: stdlib.h: No such file or directory
zutil.h:38:23: error: errno.h: No such file or directory
In file included from zutil.c:8:
zutil.h:23:22: error: string.h: No such file or directory
zutil.h:24:22: error: stdlib.h: No such file or directory
zutil.h:38:23: error: errno.h: No such file or directory
zutil.c: In function ‘zcalloc’:
zutil.c:306: warning: implicit declaration of function ‘malloc’
zutil.c:306: warning: incompatible implicit declaration of built-in function ‘malloc’
zutil.c:307: warning: implicit declaration of function ‘calloc’
zutil.c:307: warning: incompatible implicit declaration of built-in function ‘calloc’
zutil.c: In function ‘zcfree’:
zutil.c:314: warning: implicit declaration of function ‘free’
make[1]: *** [shared] Error 1
make[1]: Leaving directory `/home/james/Downloads/ossec-hids-1.5/src/external/zlib-1.2.3'
make[1]: Entering directory `/home/james/Downloads/ossec-hids-1.5/src/external/zlib-1.2.3'
cp -pr zlib.h zconf.h ../../headers/
cp -pr libz.a ../
cp: cannot stat `libz.a': No such file or directory
make[1]: *** [ossec] Error 1
make[1]: Leaving directory `/home/james/Downloads/ossec-hids-1.5/src/external/zlib-1.2.3'



 *** Making os_xml *** 

make[1]: Entering directory `/home/james/Downloads/ossec-hids-1.5/src/os_xml'
gcc -DXML_VAR=\"var\" -g -Wall -I../ -I../headers  -DDEFAULTDIR=\"/var/ossec\" -DLOCAL      -DARGV0=\"os_xml\" -DXML_VAR=\"var\" -DOSSECHIDS -c os_xml.c os_xml_access.c os_xml_node_access.c os_xml_variables.c os_xml_writer.c
In file included from os_xml.c:17:
../headers/shared.h:46:23: error: sys/types.h: No such file or directory
../headers/shared.h:47:22: error: sys/stat.h: No such file or directory
../headers/shared.h:48:22: error: sys/time.h: No such file or directory
../headers/shared.h:49:23: error: sys/param.h: No such file or directory
../headers/shared.h:54:22: error: sys/wait.h: No such file or directory
../headers/shared.h:58:24: error: sys/select.h: No such file or directory
../headers/shared.h:61:25: error: sys/utsname.h: No such file or directory
../headers/shared.h:63:19: error: stdio.h: No such file or directory
../headers/shared.h:64:20: error: unistd.h: No such file or directory
../headers/shared.h:65:20: error: stdlib.h: No such file or directory
../headers/shared.h:66:20: error: string.h: No such file or directory
../headers/shared.h:68:19: error: fcntl.h: No such file or directory
../headers/shared.h:69:20: error: dirent.h: No such file or directory
../headers/shared.h:70:19: error: ctype.h: No such file or directory
../headers/shared.h:71:20: error: signal.h: No such file or directory
../headers/shared.h:75:18: error: glob.h: No such file or directory
../headers/shared.h:76:19: error: netdb.h: No such file or directory
../headers/shared.h:77:24: error: netinet/in.h: No such file or directory
../headers/shared.h:78:23: error: arpa/inet.h: No such file or directory
../headers/shared.h:79:24: error: sys/socket.h: No such file or directory
../headers/shared.h:80:20: error: sys/un.h: No such file or directory
../headers/shared.h:86:18: error: time.h: No such file or directory
../headers/shared.h:87:19: error: errno.h: No such file or directory
In file included from ../headers/shared.h:197,
                 from os_xml.c:17:
../headers/privsep_op.h:24: error: expected ‘)’ before ‘uid’
../headers/privsep_op.h:26: error: expected ‘)’ before ‘gid’
In file included from ../headers/shared.h:208,
                 from os_xml.c:17:
../headers/file-queue.h:31: error: expected specifier-qualifier-list before ‘FILE’
In file included from ../headers/file-queue.h:37,
                 from ../headers/shared.h:208,
                 from os_xml.c:17:
../headers/read-alert.h:35: error: expected declaration specifiers or ‘...’ before ‘FILE’
In file included from ../headers/shared.h:208,
                 from os_xml.c:17:
../headers/file-queue.h:38: warning: ‘struct tm’ declared inside parameter list
../headers/file-queue.h:38: warning: its scope is only this definition or declaration, which is probably not what you want
../headers/file-queue.h:40: warning: ‘struct tm’ declared inside parameter list
os_xml.c:33: error: expected ‘)’ before ‘*’ token
os_xml.c:38: error: expected ‘)’ before ‘*’ token
os_xml.c:39: error: expected ‘)’ before ‘*’ token
os_xml.c:47: error: expected ‘)’ before ‘*’ token
os_xml.c: In function ‘xml_error’:
os_xml.c:79: warning: implicit declaration of function ‘memset’
os_xml.c:79: warning: incompatible implicit declaration of built-in function ‘memset’
os_xml.c:80: warning: implicit declaration of function ‘vsnprintf’
os_xml.c: In function ‘OS_ClearXML’:
os_xml.c:96: warning: implicit declaration of function ‘free’
os_xml.c:108: warning: incompatible implicit declaration of built-in function ‘memset’
os_xml.c: In function ‘OS_ReadXML’:
os_xml.c:121: error: ‘FILE’ undeclared (first use in this function)
os_xml.c:121: error: (Each undeclared identifier is reported only once
os_xml.c:121: error: for each function it appears in.)
os_xml.c:121: error: ‘fp’ undeclared (first use in this function)
os_xml.c:123: warning: implicit declaration of function ‘fopen’
os_xml.c:132: error: ‘NULL’ undeclared (first use in this function)
os_xml.c:140: warning: incompatible implicit declaration of built-in function ‘memset’
os_xml.c:145: warning: implicit declaration of function ‘_ReadElem’
os_xml.c:149: warning: implicit declaration of function ‘fclose’
os_xml.c: At top level:
os_xml.c:169: error: expected ‘)’ before ‘*’ token
os_xml.c:203: error: expected ‘)’ before ‘*’ token
os_xml.c: In function ‘_writememory’:
os_xml.c:364: warning: implicit declaration of function ‘realloc’
os_xml.c:365: warning: implicit declaration of function ‘calloc’
os_xml.c:365: warning: incompatible implicit declaration of built-in function ‘calloc’
os_xml.c:366: warning: implicit declaration of function ‘strncpy’
os_xml.c:366: warning: incompatible implicit declaration of built-in function ‘strncpy’
os_xml.c:372: warning: assignment makes pointer from integer without a cast
os_xml.c:376: warning: assignment makes pointer from integer without a cast
os_xml.c:380: warning: assignment makes pointer from integer without a cast
os_xml.c:384: warning: assignment makes pointer from integer without a cast
os_xml.c:392: warning: implicit declaration of function ‘strcasecmp’
os_xml.c: In function ‘_writecontent’:
os_xml.c:403: warning: incompatible implicit declaration of built-in function ‘calloc’
os_xml.c:404: warning: incompatible implicit declaration of built-in function ‘strncpy’
os_xml.c: In function ‘_checkmemory’:
os_xml.c:417: warning: implicit declaration of function ‘strcmp’
os_xml.c: At top level:
os_xml.c:432: error: expected ‘)’ before ‘*’ token
os_xml_access.c:16:19: error: stdio.h: No such file or directory
os_xml_access.c:17:20: error: string.h: No such file or directory
os_xml_access.c:18:20: error: stdlib.h: No such file or directory
os_xml_access.c: In function ‘OS_ElementExist’:
os_xml_access.c:36: error: ‘NULL’ undeclared (first use in this function)
os_xml_access.c:36: error: (Each undeclared identifier is reported only once
os_xml_access.c:36: error: for each function it appears in.)
os_xml_access.c:45: warning: implicit declaration of function ‘strcmp’
os_xml_access.c: In function ‘OS_RootElementExist’:
os_xml_access.c:73: error: ‘NULL’ undeclared (first use in this function)
os_xml_access.c: In function ‘_GetElements’:
os_xml_access.c:106: error: ‘NULL’ undeclared (first use in this function)
os_xml_access.c:113: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:127: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:129: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:131: warning: implicit declaration of function ‘strlen’
os_xml_access.c:131: warning: incompatible implicit declaration of built-in function ‘strlen’
os_xml_access.c:133: warning: implicit declaration of function ‘realloc’
os_xml_access.c:136: warning: implicit declaration of function ‘calloc’
os_xml_access.c:136: warning: incompatible implicit declaration of built-in function ‘calloc’
os_xml_access.c:137: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:139: warning: implicit declaration of function ‘free’
os_xml_access.c:142: warning: implicit declaration of function ‘strncpy’
os_xml_access.c:142: warning: incompatible implicit declaration of built-in function ‘strncpy’
os_xml_access.c:148: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:178: warning: assignment from incompatible pointer type
os_xml_access.c: In function ‘OS_GetOneContentforElement’:
os_xml_access.c:190: error: ‘NULL’ undeclared (first use in this function)
os_xml_access.c:190: warning: initialization from incompatible pointer type
os_xml_access.c:194: warning: passing argument 3 of ‘_GetElementContent’ from incompatible pointer type
os_xml_access.c:197: warning: return from incompatible pointer type
os_xml_access.c:200: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:209: warning: assignment from incompatible pointer type
os_xml_access.c: In function ‘OS_GetElementContent’:
os_xml_access.c:224: error: ‘NULL’ undeclared (first use in this function)
os_xml_access.c:224: warning: passing argument 3 of ‘_GetElementContent’ from incompatible pointer type
os_xml_access.c: In function ‘OS_GetContents’:
os_xml_access.c:234: error: ‘NULL’ undeclared (first use in this function)
os_xml_access.c:239: warning: passing argument 3 of ‘_GetElementContent’ from incompatible pointer type
os_xml_access.c: In function ‘OS_GetAttributeContent’:
os_xml_access.c:251: error: ‘NULL’ undeclared (first use in this function)
os_xml_access.c:251: warning: initialization from incompatible pointer type
os_xml_access.c:259: warning: return from incompatible pointer type
os_xml_access.c:261: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:263: warning: incompatible implicit declaration of built-in function ‘strlen’
os_xml_access.c:266: warning: incompatible implicit declaration of built-in function ‘calloc’
os_xml_access.c:267: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:269: warning: incompatible implicit declaration of built-in function ‘strncpy’
os_xml_access.c:276: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:283: warning: return from incompatible pointer type
os_xml_access.c: In function ‘_GetElementContent’:
os_xml_access.c:293: error: ‘NULL’ undeclared (first use in this function)
os_xml_access.c:324: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:363: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:366: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:384: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:394: warning: implicit declaration of function ‘strdup’
os_xml_access.c:394: warning: incompatible implicit declaration of built-in function ‘strdup’
os_xml_access.c:395: warning: assignment from incompatible pointer type
os_xml_access.c:396: warning: comparison of distinct pointer types lacks a cast
os_xml_access.c:405: warning: comparison of distinct pointer types lacks a cast
os_xml_node_access.c:17:19: error: stdio.h: No such file or directory
os_xml_node_access.c:18:20: error: string.h: No such file or directory
os_xml_node_access.c:19:20: error: stdlib.h: No such file or directory
os_xml_node_access.c: In function ‘OS_ClearNode’:
os_xml_node_access.c:35: warning: implicit declaration of function ‘free’
os_xml_node_access.c:59: error: ‘NULL’ undeclared (first use in this function)
os_xml_node_access.c:59: error: (Each undeclared identifier is reported only once
os_xml_node_access.c:59: error: for each function it appears in.)
os_xml_node_access.c: In function ‘OS_GetElementsbyNode’:
os_xml_node_access.c:79: error: ‘NULL’ undeclared (first use in this function)
os_xml_node_access.c:101: warning: implicit declaration of function ‘realloc’
os_xml_node_access.c:106: warning: implicit declaration of function ‘calloc’
os_xml_node_access.c:106: warning: incompatible implicit declaration of built-in function ‘calloc’
os_xml_node_access.c:116: warning: implicit declaration of function ‘strdup’
os_xml_node_access.c:116: warning: incompatible implicit declaration of built-in function ‘strdup’
os_xml_variables.c:17:19: error: stdio.h: No such file or directory
os_xml_variables.c:18:20: error: string.h: No such file or directory
os_xml_variables.c:19:20: error: stdlib.h: No such file or directory
os_xml_variables.c: In function ‘OS_ApplyVariables’:
os_xml_variables.c:26: error: ‘NULL’ undeclared (first use in this function)
os_xml_variables.c:26: error: (Each undeclared identifier is reported only once
os_xml_variables.c:26: error: for each function it appears in.)
os_xml_variables.c:45: warning: implicit declaration of function ‘strcasecmp’
os_xml_variables.c:51: warning: implicit declaration of function ‘snprintf’
os_xml_variables.c:51: warning: incompatible implicit declaration of built-in function ‘snprintf’
os_xml_variables.c:53: warning: implicit declaration of function ‘realloc’
os_xml_variables.c:57: warning: implicit declaration of function ‘strdup’
os_xml_variables.c:57: warning: incompatible implicit declaration of built-in function ‘strdup’
os_xml_variables.c:62: warning: implicit declaration of function ‘strncpy’
os_xml_variables.c:62: warning: incompatible implicit declaration of built-in function ‘strncpy’
os_xml_variables.c:69: warning: incompatible implicit declaration of built-in function ‘snprintf’
os_xml_variables.c:80: warning: incompatible implicit declaration of built-in function ‘snprintf’
os_xml_variables.c:86: warning: incompatible implicit declaration of built-in function ‘snprintf’
os_xml_variables.c:92: warning: incompatible implicit declaration of built-in function ‘strdup’
os_xml_variables.c:96: warning: incompatible implicit declaration of built-in function ‘strncpy’
os_xml_variables.c:120: warning: implicit declaration of function ‘strlen’
os_xml_variables.c:120: warning: incompatible implicit declaration of built-in function ‘strlen’
os_xml_variables.c:125: warning: incompatible implicit declaration of built-in function ‘strdup’
os_xml_variables.c:130: warning: incompatible implicit declaration of built-in function ‘snprintf’
os_xml_variables.c:142: warning: implicit declaration of function ‘memset’
os_xml_variables.c:142: warning: incompatible implicit declaration of built-in function ‘memset’
os_xml_variables.c:180: warning: implicit declaration of function ‘free’
os_xml_variables.c:182: warning: implicit declaration of function ‘calloc’
os_xml_variables.c:182: warning: incompatible implicit declaration of built-in function ‘calloc’
os_xml_variables.c:187: warning: incompatible implicit declaration of built-in function ‘snprintf’
os_xml_variables.c:193: warning: incompatible implicit declaration of built-in function ‘strncpy’
os_xml_variables.c:197: warning: implicit declaration of function ‘strncat’
os_xml_variables.c:197: warning: incompatible implicit declaration of built-in function ‘strncat’
os_xml_variables.c:213: warning: incompatible implicit declaration of built-in function ‘snprintf’
os_xml_variables.c:229: warning: incompatible implicit declaration of built-in function ‘snprintf’
In file included from os_xml_writer.c:18:
../headers/shared.h:46:23: error: sys/types.h: No such file or directory
../headers/shared.h:47:22: error: sys/stat.h: No such file or directory
../headers/shared.h:48:22: error: sys/time.h: No such file or directory
../headers/shared.h:49:23: error: sys/param.h: No such file or directory
../headers/shared.h:54:22: error: sys/wait.h: No such file or directory
../headers/shared.h:58:24: error: sys/select.h: No such file or directory
../headers/shared.h:61:25: error: sys/utsname.h: No such file or directory
../headers/shared.h:63:19: error: stdio.h: No such file or directory
../headers/shared.h:64:20: error: unistd.h: No such file or directory
../headers/shared.h:65:20: error: stdlib.h: No such file or directory
../headers/shared.h:66:20: error: string.h: No such file or directory
../headers/shared.h:68:19: error: fcntl.h: No such file or directory
../headers/shared.h:69:20: error: dirent.h: No such file or directory
../headers/shared.h:70:19: error: ctype.h: No such file or directory
../headers/shared.h:71:20: error: signal.h: No such file or directory
../headers/shared.h:75:18: error: glob.h: No such file or directory
../headers/shared.h:76:19: error: netdb.h: No such file or directory
../headers/shared.h:77:24: error: netinet/in.h: No such file or directory
../headers/shared.h:78:23: error: arpa/inet.h: No such file or directory
../headers/shared.h:79:24: error: sys/socket.h: No such file or directory
../headers/shared.h:80:20: error: sys/un.h: No such file or directory
../headers/shared.h:86:18: error: time.h: No such file or directory
../headers/shared.h:87:19: error: errno.h: No such file or directory
In file included from ../headers/shared.h:197,
                 from os_xml_writer.c:18:
../headers/privsep_op.h:24: error: expected ‘)’ before ‘uid’
../headers/privsep_op.h:26: error: expected ‘)’ before ‘gid’
In file included from ../headers/shared.h:208,
                 from os_xml_writer.c:18:
../headers/file-queue.h:31: error: expected specifier-qualifier-list before ‘FILE’
In file included from ../headers/file-queue.h:37,
                 from ../headers/shared.h:208,
                 from os_xml_writer.c:18:
../headers/read-alert.h:35: error: expected declaration specifiers or ‘...’ before ‘FILE’
In file included from ../headers/shared.h:208,
                 from os_xml_writer.c:18:
../headers/file-queue.h:38: warning: ‘struct tm’ declared inside parameter list
../headers/file-queue.h:38: warning: its scope is only this definition or declaration, which is probably not what you want
../headers/file-queue.h:40: warning: ‘struct tm’ declared inside parameter list
os_xml_writer.c:35: error: expected ‘)’ before ‘*’ token
os_xml_writer.c:36: error: expected ‘)’ before ‘*’ token
os_xml_writer.c:45: error: expected ‘)’ before ‘*’ token
os_xml_writer.c: In function ‘OS_WriteXML’:
os_xml_writer.c:74: error: ‘FILE’ undeclared (first use in this function)
os_xml_writer.c:74: error: (Each undeclared identifier is reported only once
os_xml_writer.c:74: error: for each function it appears in.)
os_xml_writer.c:74: error: ‘fp_in’ undeclared (first use in this function)
os_xml_writer.c:75: error: ‘fp_out’ undeclared (first use in this function)
os_xml_writer.c:85: warning: implicit declaration of function ‘fopen’
os_xml_writer.c:96: warning: implicit declaration of function ‘fclose’
os_xml_writer.c:101: warning: implicit declaration of function ‘_WReadElem’
os_xml_writer.c:115: warning: implicit declaration of function ‘fseek’
os_xml_writer.c:115: error: ‘SEEK_END’ undeclared (first use in this function)
os_xml_writer.c:116: warning: implicit declaration of function ‘fprintf’
os_xml_writer.c:116: warning: incompatible implicit declaration of built-in function ‘fprintf’
os_xml_writer.c: At top level:
os_xml_writer.c:153: error: expected ‘)’ before ‘*’ token
os_xml_writer.c:204: error: expected ‘)’ before ‘*’ token
make[1]: *** [xml] Error 1
make[1]: Leaving directory `/home/james/Downloads/ossec-hids-1.5/src/os_xml'

Error Making os_xml
make: *** [all] Error 1

 Error 0x5.
 Building error. Unable to finish the installation.
```Can anyone help me out? Are there some dependencies I need to install, or what? 

Thanks a lot guys!

SH

---

### Post by ssaady on 2008-08-30
any suggestions for this?  I think it is some GCC incompat.

---

### Post by ssaady on 2008-08-30
I installed libc6-dev and it appears to be compiling now.

---

### Post by ShinHadoken on 2008-08-30
That did it! Thanks so much!

SH

---

