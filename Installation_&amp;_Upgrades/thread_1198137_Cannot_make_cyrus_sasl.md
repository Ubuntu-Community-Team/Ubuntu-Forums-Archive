---
title: "Cannot make cyrus sasl"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by zulkose on 2009-06-27
I'm trying to install cyrus-sasl version 2.1.23 in Ubuntu 8.04.1 for use with sendmail 8.14.2 user authentication. I ran configure which seemed to go okay, however making it ran into a few cryptic (to me) problems resulting in Errors 1 and 2. 

   # ./configure --enable-login  // if you know any other features I should include for use 
                                             // with sendmail they would be greatly appreciated : )

configure: loading cache ./config.cache
checking build system type... (cached) i686-pc-linux-gnu
checking host system type... (cached) i686-pc-linux-gnu
checking target system type... (cached) i686-pc-linux-gnu
checking for a BSD-compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... (cached) mawk
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... (cached) gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... (cached) o
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for style of include used by make... GNU
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... (cached) gcc -E
checking for gawk... (cached) mawk
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for __attribute__... (cached) no
checking for runpath switch... -Wl,-rpath,
checking for ranlib... (cached) ranlib
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
loading cache ./config.cache within ltconfig
checking for object suffix... o
checking for executable suffix... (cached) 
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking if gcc static flag -static works... -static
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... ok
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for objdir... .libs
creating libtool
updating cache ./config.cache
configure: loading cache ./config.cache
checking for connect... (cached) yes
checking for res_search... (cached) no
checking for dn_expand... (cached) yes
checking for dns_lookup... (cached) no
checking DB path to use... /etc/sasldb2
checking for egrep... (cached) grep -E
checking for ANSI C header files... (cached) yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for memory.h... (cached) yes
checking for strings.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for unistd.h... (cached) yes
checking for db.h... (cached) no
checking for ndbm.h... (cached) no
checking for gdbm.h... (cached) no
checking DB library to use... no
configure: WARNING: Disabling SASL authentication database support
checking if Berkeley DB handle is kept open in SASLDB... no
checking for dlopen in -ldl... (cached) yes
checking /dev/random to use... /dev/random
checking for nm... (cached) /usr/bin/nm -B
checking for underscore before symbols... (cached) no
checking for syslog... (cached) yes
checking for security/pam_appl.h... (cached) no
checking for pam/pam_appl.h... (cached) no
checking for pam_start... (cached) no
checking if I should include saslauthd... /var/state/saslauthd
checking to include Courier authdaemond support... /dev/null
checking if I should include pwcheck... no
checking if I should include the alwaystrue verifier... no
checking if we should enable sasl_checkapop... enabled
checking CRAM-MD5... enabled
checking for long... (cached) yes
checking size of long... (cached) 4
checking what directory libraries are found in... (cached) lib
checking for RSAPublicEncrypt in -lrsaref... (cached) no
checking for openssl/evp.h... (cached) no
checking for OpenSSL... no
checking DIGEST-MD5... enabled
configure: WARNING: OpenSSL not found -- OTP will be disabled
checking OTP... disabled
configure: WARNING: OpenSSL not found -- SRP will be disabled
checking SRP... disabled
checking KERBEROS_V4... disabled
checking for crypt... (cached) no
checking for crypt in -lcrypt... (cached) yes
checking for gssapi.h... (cached) no
checking for gssapi/gssapi.h... (cached) no
configure: WARNING: Disabling GSSAPI - no include files found
checking GSSAPI... disabled
checking PLAIN... enabled
checking ANONYMOUS... enabled
checking LOGIN... enabled
configure: WARNING: OpenSSL not found -- NTLM will be disabled
checking NTLM... disabled
configure: WARNING: OpenSSL not found -- PASSDSS will be disabled
checking PASSDSS... disabled
checking SQL... disabled
checking LDAPDB... disabled
checking for dmalloc library... no
checking for sfio library... no
checking for getsubopt... (cached) yes
checking for snprintf... (cached) yes
checking for vsnprintf... (cached) yes
checking for inet_aton in -lresolv... (cached) yes
checking for getaddrinfo... (cached) yes
checking for gai_strerror... (cached) yes
checking for getnameinfo... (cached) yes
checking for an ANSI C-conforming const... (cached) yes
checking for inline... (cached) inline
checking for mode_t... (cached) yes
checking for pid_t... (cached) yes
checking return type of signal handlers... (cached) void
checking whether time.h and sys/time.h may both be included... (cached) yes
checking for ANSI C header files... (cached) yes
checking for dirent.h that defines DIR... (cached) yes
checking for library containing opendir... (cached) none required
checking for sys/wait.h that is POSIX.1 compatible... (cached) yes
checking for des.h... (cached) no
checking for dlfcn.h... (cached) yes
checking for fcntl.h... (cached) yes
checking for limits.h... (cached) yes
checking for malloc.h... (cached) yes
checking for paths.h... (cached) yes
checking for strings.h... (cached) yes
checking for sys/file.h... (cached) yes
checking for sys/time.h... (cached) yes
checking for syslog.h... (cached) yes
checking for unistd.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for sys/uio.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for sysexits.h... (cached) yes
checking for stdarg.h... (cached) yes
checking for varargs.h... (cached) no
checking whether you have ss_family in struct sockaddr_storage... (cached) yes
checking whether you have sa_len in struct sockaddr... (cached) no
checking for socklen_t... (cached) yes
checking for gethostname... (cached) yes
checking for getdomainname... (cached) yes
checking for getpwnam... (cached) yes
checking for getspnam... (cached) yes
checking for gettimeofday... (cached) yes
checking for inet_aton... (cached) yes
checking for memcpy... (cached) yes
checking for mkdir... (cached) yes
checking for select... (cached) yes
checking for socket... (cached) yes
checking for strchr... (cached) yes
checking for strdup... (cached) yes
checking for strerror... (cached) yes
checking for strspn... (cached) yes
checking for strstr... (cached) yes
checking for strtol... (cached) yes
checking for jrand48... (cached) yes
updating cache ./config.cache
configure: creating ./config.status
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating sasldb/Makefile
config.status: creating plugins/Makefile
config.status: creating lib/Makefile
config.status: creating utils/Makefile
config.status: creating doc/Makefile
config.status: creating sample/Makefile
config.status: creating java/Makefile
config.status: creating java/CyrusSasl/Makefile
config.status: creating java/Test/Makefile
config.status: creating java/javax/Makefile
config.status: creating java/javax/security/Makefile
config.status: creating java/javax/security/auth/Makefile
config.status: creating java/javax/security/auth/callback/Makefile
config.status: creating pwcheck/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
configure: configuring in saslauthd
configure: running /bin/bash './configure' --prefix=/usr/local  '--enable-login' --cache-file=.././config.cache --srcdir=.
configure: loading cache .././config.cache
checking build system type... (cached) i686-pc-linux-gnu
checking host system type... (cached) i686-pc-linux-gnu
checking for a BSD-compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... (cached) mawk
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... (cached) gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... (cached) o
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for style of include used by make... GNU
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... (cached) gcc -E
checking for gawk... (cached) mawk
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for __attribute__... (cached) no
checking for runpath switch... -Wl,-rpath,
checking for connect... (cached) yes
checking for res_search... (cached) no
checking for dn_expand... (cached) yes
checking for dns_lookup... (cached) no
checking for egrep... (cached) grep -E
checking for ANSI C header files... (cached) yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for memory.h... (cached) yes
checking for strings.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for unistd.h... (cached) yes
checking for long... (cached) yes
checking size of long... (cached) 4
checking what directory libraries are found in... (cached) lib
checking for RSAPublicEncrypt in -lrsaref... (cached) no
checking for openssl/evp.h... (cached) no
checking for OpenSSL... no
checking KERBEROS_V4... disabled
checking for crypt... (cached) no
checking for crypt in -lcrypt... (cached) yes
checking for gssapi.h... (cached) no
checking for gssapi/gssapi.h... (cached) no
configure: WARNING: Disabling GSSAPI - no include files found
checking GSSAPI... disabled
checking for crypt... (cached) no
checking for crypt in -lcrypt... (cached) yes
checking for pam_start in -lpam... (cached) no
checking for PAM support... no
checking for inet_aton in -lresolv... (cached) yes
checking to include LDAP support... no
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... (cached) yes
checking whether time.h and sys/time.h may both be included... (cached) yes
checking for crypt.h... (cached) yes
checking for fcntl.h... (cached) yes
checking for krb5.h... (cached) no
checking for strings.h... (cached) yes
checking for syslog.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/time.h... (cached) yes
checking for sys/uio.h... (cached) yes
checking for an ANSI C-conforming const... (cached) yes
checking for pid_t... (cached) yes
checking whether gcc implements __func__... yes
checking return type of signal handlers... (cached) void
checking for gethostname... (cached) yes
checking for mkdir... (cached) yes
checking for socket... (cached) yes
checking for strdup... (cached) yes
checking for getspnam... (cached) yes
checking for strlcat... (cached) no
checking for strlcpy... (cached) no
checking if getpwnam_r/getspnam_r take 5 arguments... yes
checking for getaddrinfo... (cached) yes
checking for getnameinfo... (cached) yes
checking whether you have ss_family in struct sockaddr_storage... (cached) yes
checking whether you have sa_len in struct sockaddr... (cached) no
checking for socklen_t... (cached) yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating saslauthd.h
config.status: saslauthd.h is unchanged
config.status: executing depfiles commands
Configuration complete. Type make to build.

    #make
make  all-recursive
make[1]: Entering directory `/root/cyrus-sasl-2.1.23'
Making all in include
make[2]: Entering directory `/root/cyrus-sasl-2.1.23/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/cyrus-sasl-2.1.23/include'
Making all in sasldb
make[2]: Entering directory `/root/cyrus-sasl-2.1.23/sasldb'
ar cru .libs/libsasldb.a db_none.o
make[2]: Leaving directory `/root/cyrus-sasl-2.1.23/sasldb'
Making all in plugins
make[2]: Entering directory `/root/cyrus-sasl-2.1.23/plugins'
if /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include -I../lib -I../sasldb -I../include    -Wall -W -g -O2 -MT digestmd5.lo -MD -MP -MF ".deps/digestmd5.Tpo" \
      -c -o digestmd5.lo `test -f 'digestmd5.c' || echo './'`digestmd5.c; \
    then mv -f ".deps/digestmd5.Tpo" ".deps/digestmd5.Plo"; \
    else rm -f ".deps/digestmd5.Tpo"; exit 1; \
    fi
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include -I../lib -I../sasldb -I../include -Wall -W -g -O2 -MT digestmd5.lo -MD -MP -MF .deps/digestmd5.Tpo -c digestmd5.c  -fPIC -DPIC -o digestmd5.lo
digestmd5.c:279: warning: pointer targets in initialization differ in signedness
digestmd5.c: In function 'DigestCalcResponse':
digestmd5.c:366: warning: pointer targets in passing argument 2 of 'utils->MD5Update' differ in signedness
digestmd5.c: At top level:
digestmd5.c:812: error: expected specifier-qualifier-list before 'des_key_schedule'
digestmd5.c: In function 'dec_3des':
digestmd5.c:849: warning: implicit declaration of function 'des_ede2_cbc_encrypt'
digestmd5.c:852: error: 'des_context_t' has no member named 'keysched'
digestmd5.c:853: error: 'des_context_t' has no member named 'keysched2'
digestmd5.c:854: error: 'des_context_t' has no member named 'ivec'
digestmd5.c:855: error: 'DES_DECRYPT' undeclared (first use in this function)
digestmd5.c:855: error: (Each undeclared identifier is reported only once
digestmd5.c:855: error: for each function it appears in.)
digestmd5.c:842: warning: unused parameter 'digest'
digestmd5.c: In function 'enc_3des':
digestmd5.c:900: error: 'des_context_t' has no member named 'keysched'
digestmd5.c:901: error: 'des_context_t' has no member named 'keysched2'
digestmd5.c:902: error: 'des_context_t' has no member named 'ivec'
digestmd5.c:903: error: 'DES_ENCRYPT' undeclared (first use in this function)
digestmd5.c: In function 'init_3des':
digestmd5.c:923: warning: implicit declaration of function 'des_key_sched'
digestmd5.c:923: error: 'des_cblock' undeclared (first use in this function)
digestmd5.c:923: error: expected expression before ')' token
digestmd5.c:927: error: expected expression before ')' token
digestmd5.c:929: error: 'des_context_t' has no member named 'ivec'
digestmd5.c:936: error: expected expression before ')' token
digestmd5.c:940: error: expected expression before ')' token
digestmd5.c:943: error: 'des_context_t' has no member named 'ivec'
digestmd5.c: In function 'dec_des':
digestmd5.c:967: warning: implicit declaration of function 'des_cbc_encrypt'
digestmd5.c:970: error: 'des_context_t' has no member named 'keysched'
digestmd5.c:971: error: 'des_context_t' has no member named 'ivec'
digestmd5.c:972: error: 'DES_DECRYPT' undeclared (first use in this function)
digestmd5.c:976: error: 'des_context_t' has no member named 'ivec'
digestmd5.c:960: warning: unused parameter 'digest'
digestmd5.c: In function 'enc_des':
digestmd5.c:1021: error: 'des_context_t' has no member named 'keysched'
digestmd5.c:1022: error: 'des_context_t' has no member named 'ivec'
digestmd5.c:1023: error: 'DES_ENCRYPT' undeclared (first use in this function)
digestmd5.c:1027: error: 'des_context_t' has no member named 'ivec'
digestmd5.c: In function 'init_des':
digestmd5.c:1047: error: 'des_cblock' undeclared (first use in this function)
digestmd5.c:1047: error: expected expression before ')' token
digestmd5.c:1049: error: 'des_context_t' has no member named 'ivec'
digestmd5.c:1056: error: expected expression before ')' token
digestmd5.c:1058: error: 'des_context_t' has no member named 'ivec'
digestmd5.c: In function 'dec_rc4':
digestmd5.c:1211: warning: unused parameter 'digest'
digestmd5.c: In function 'digestmd5_encode':
digestmd5.c:1401: warning: pointer targets in passing argument 5 of 'text->utils->hmac_md5' differ in signedness
digestmd5.c: In function 'digestmd5_decode_packet':
digestmd5.c:1497: warning: pointer targets in assignment differ in signedness
digestmd5.c: In function 'digestmd5_server_mech_new':
digestmd5.c:1797: warning: unused parameter 'challenge'
digestmd5.c:1798: warning: unused parameter 'challen'
digestmd5.c: In function 'digestmd5_server_mech_step1':
digestmd5.c:1947: warning: pointer targets in passing argument 6 of 'add_to_challenge' differ in signedness
digestmd5.c:1820: warning: unused parameter 'clientin'
digestmd5.c:1821: warning: unused parameter 'clientinlen'
digestmd5.c:1824: warning: unused parameter 'oparams'
digestmd5.c: In function 'digestmd5_server_mech_step2':
digestmd5.c:2100: warning: dereferencing type-punned pointer will break strict-aliasing rules
digestmd5.c:2117: warning: dereferencing type-punned pointer will break strict-aliasing rules
digestmd5.c:2235: warning: dereferencing type-punned pointer will break strict-aliasing rules
digestmd5.c:2235: warning: pointer targets in passing argument 2 of '_plug_strdup' differ in signedness
digestmd5.c:2238: warning: dereferencing type-punned pointer will break strict-aliasing rules
digestmd5.c:2238: warning: pointer targets in passing argument 2 of '_plug_strdup' differ in signedness
digestmd5.c:2274: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
digestmd5.c:2274: warning: pointer targets in passing argument 1 of '__builtin_strcmp' differ in signedness
digestmd5.c:2274: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
digestmd5.c:2274: warning: pointer targets in passing argument 1 of '__builtin_strcmp' differ in signedness
digestmd5.c:2274: warning: pointer targets in passing argument 1 of '__builtin_strcmp' differ in signedness
digestmd5.c:2274: warning: pointer targets in passing argument 1 of '__builtin_strcmp' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 1 of '__builtin_strcmp' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 1 of '__builtin_strcmp' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 1 of '__builtin_strcmp' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 1 of '__builtin_strcmp' differ in signedness
digestmd5.c:2286: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
digestmd5.c:2351: warning: pointer targets in passing argument 1 of '__builtin_strncpy' differ in signedness
digestmd5.c:2369: warning: pointer targets in passing argument 2 of 'DigestCalcSecret' differ in signedness
digestmd5.c:2369: warning: pointer targets in passing argument 3 of 'DigestCalcSecret' differ in signedness
digestmd5.c:2514: warning: pointer targets in passing argument 2 of 'text->cipher_init' differ in signedness
digestmd5.c:2514: warning: pointer targets in passing argument 3 of 'text->cipher_init' differ in signedness
digestmd5.c: In function 'make_client_response':
digestmd5.c:3010: warning: pointer targets in passing argument 3 of 'calculate_response' differ in signedness
digestmd5.c:3010: warning: pointer targets in passing argument 11 of 'calculate_response' differ in signedness
digestmd5.c:3034: warning: pointer targets in passing argument 6 of 'add_to_challenge' differ in signedness
digestmd5.c:3145: warning: pointer targets in passing argument 2 of 'text->cipher_init' differ in signedness
digestmd5.c:3145: warning: pointer targets in passing argument 3 of 'text->cipher_init' differ in signedness
digestmd5.c: In function 'parse_server_challenge':
digestmd5.c:3229: warning: dereferencing type-punned pointer will break strict-aliasing rules
digestmd5.c: In function 'digestmd5_client_mech_step1':
digestmd5.c:3732: warning: dereferencing type-punned pointer will break strict-aliasing rules
digestmd5.c:3732: warning: pointer targets in passing argument 2 of '_plug_strdup' differ in signedness
digestmd5.c:3735: warning: dereferencing type-punned pointer will break strict-aliasing rules
digestmd5.c:3735: warning: pointer targets in passing argument 2 of '_plug_strdup' differ in signedness
digestmd5.c:3703: warning: unused parameter 'serverin'
digestmd5.c:3704: warning: unused parameter 'serverinlen'
digestmd5.c: In function 'digestmd5_client_mech_step3':
digestmd5.c:3838: warning: unused parameter 'prompt_need'
digestmd5.c:3839: warning: unused parameter 'clientout'
digestmd5.c:3840: warning: unused parameter 'clientoutlen'
digestmd5.c: In function 'digestmd5_client_mech_step':
digestmd5.c:4000: warning: pointer targets in assignment differ in signedness
make[2]: *** [digestmd5.lo] Error 1
make[2]: Leaving directory `/root/cyrus-sasl-2.1.23/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/cyrus-sasl-2.1.23'
make: *** [all] Error 2

Any suggestions?

---

### Post by zulkose on 2009-06-28
bump

---

### Post by eugenevdm on 2010-02-03
> **zulkose said:**
> bump

I need help too. This might be the clue:

> digestmd5.c: In function 'digestmd5_client_mech_step':
digestmd5.c:4000: warning: pointer targets in assignment differ in signedness
make[2]: *** [digestmd5.lo] Error 1
make[2]: Leaving directory `/home/eugene/cyrus-sasl2_2.1.23.dfsg1/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/eugene/cyrus-sasl2_2.1.23.dfsg1'
make: *** [all] Error 2

I tried three different version from here:
[http://security.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/](http://security.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/)

2.1.19, 2.1.22, 2.1.23 and all three are failing.

EDIT:

The problem is with GCC and elif statement documented here:
[http://www.cyrius.com/journal/gcc#gcc-4.4-preprocessor-errors](http://www.cyrius.com/journal/gcc#gcc-4.4-preprocessor-errors)

Follow this:

--- plugins/digestmd5.c~        2008-11-08 18:28:21.000000000 +0000
+++ plugins/digestmd5.c 2008-11-08 18:28:50.000000000 +0000
@@ -2715,7 +2715,7 @@
        "DIGEST-MD5",                   /* mech_name */
 #ifdef WITH_RC4
        128,                            /* max_ssf */
-#elif WITH_DES
**+#elif defined(WITH_DES)**
        112,
 #else 
        1,
@@ -4034,7 +4034,7 @@
        "DIGEST-MD5",
 #ifdef WITH_RC4                                /* mech_name */
        128,                            /* max ssf */
-#elif WITH_DES
**+#elif defined(WITH_DES)**
        112,
 #else
        1,

---

### Post by ptmcg on 2010-07-07
I resolved this by running ./configure with --with-des=no, instead of patching the source.

---

### Post by Brent Bice on 2010-08-10
cyrus-sasl-2.1.24rc1 appears to have fixed this. It compiled fine on my ubuntu 10.04 laptop...

---

