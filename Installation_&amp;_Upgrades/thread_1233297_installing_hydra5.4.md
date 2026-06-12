---
title: "installing hydra5.4"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by martinvanputten on 2009-08-06
I'm having a difficult time installing hydra5.4. I managed to get most of the drivers needed to run the tool on my machine but I'm still receiving this error that says its ignored... but I'm still unable to use hydra... the command itself is understood in bash but does absolutely nothing. I have written the config and install to separate files if someone could help me find out what this error is and how to fix it?

-------------------------------------------------------------------------------------------------------------------------
./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from [http://www.sap.com/solutions/netweaver/linux/eval/index.asp](http://www.sap.com/solutions/netweaver/linux/eval/index.asp)
Checking for libssh (libssh/libssh.h) ...
                                      ... found
NOTE: ensure that you have libssh v0.11 installed!! Get it from [http://0xbadc0de.be](http://0xbadc0de.be) !

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"



-------------------------------------------------------------------------------------------------------------------------
make

gcc -I. -Wall -O2 -o pw-inspector pw-inspector.c
gcc -I. -Wall -O2 -c hydra-vnc.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pcnfs.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-rexec.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-nntp.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-socks5.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-telnet.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-cisco.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-ftp.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-imap.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pop3.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smb.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-icq.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-cisco-enable.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-ldap.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-mysql.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http-proxy.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smbnt.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-mssql.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-snmp.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-cvs.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smtpauth.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-sapr3.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-ssh2.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-teamspeak.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-postgres.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-rsh.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-rlogin.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-oracle-listener.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-svn.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pcanywhere.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-sip.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-vmauthd.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http-proxy-auth-ntlm.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-imap-ntlm.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pop3-ntlm.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smtpauth-ntlm.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http-form.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c crc32.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c d3des.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c md4.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-mod.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c ntlm.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -lm -o hydra hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-mysql.o hydra-http-proxy.o hydra-smbnt.o hydra-mssql.o hydra-snmp.o hydra-cvs.o hydra-smtpauth.o hydra-sapr3.o hydra-ssh2.o hydra-teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o hydra-oracle-listener.o hydra-svn.o hydra-pcanywhere.o hydra-sip.o hydra-vmauthd.o hydra-http-proxy-auth-ntlm.o hydra-imap-ntlm.o hydra-pop3-ntlm.o hydra-smtpauth-ntlm.o hydra-http-form.o crc32.o d3des.o md4.o hydra-mod.o ntlm.o hydra.o -lm -lssl -lpq -lssh -lcrypto -L/usr/lib -L/usr/local/lib -L/lib -L/lib -L/usr/lib || echo -e "\nIF YOU RECEIVED THE ERROR MESSAGE \"cannot find -lpq\" DO THE FOLLOWING:\n  make clean; ./configure\n  vi Makefile    <- and remove the \"-lpq\" and \"-DLIBPOSTGRES\" statements\n  make\n"
-e 
IF YOU RECEIVED THE ERROR MESSAGE "cannot find -lpq" DO THE FOLLOWING:
  make clean; ./configure
  vi Makefile    <- and remove the "-lpq" and "-DLIBPOSTGRES" statements
  make


If men could get pregnant, abortion would be a sacrament

cd hydra-gtk && ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
Error: could not compile. Analyse this:
callbacks.c: In function ‘popen_re_unbuffered’:
callbacks.c:532: warning: format not a string literal and no format arguments
callbacks.c: In function ‘on_btnSave_clicked’:
callbacks.c:668: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
In function ‘open’,
    inlined from ‘on_btnSave_clicked’ at callbacks.c:666:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
In function ‘snprintf’,
    inlined from ‘hydra_get_options’ at callbacks.c:247:
/usr/include/bits/stdio2.h:65: warning: call to __builtin___snprintf_chk will always overflow destination buffer
make[3]: *** [callbacks.o] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive-am] Error 2

Do not worry, as I said, xhydra is really optional. ./hydra is ready to go!

Now type make install


 -------------------------------------------------------------------------------------------------------------------------
make install

gcc -I. -Wall -O2 -lm -o hydra hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-mysql.o hydra-http-proxy.o hydra-smbnt.o hydra-mssql.o hydra-snmp.o hydra-cvs.o hydra-smtpauth.o hydra-sapr3.o hydra-ssh2.o hydra-teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o hydra-oracle-listener.o hydra-svn.o hydra-pcanywhere.o hydra-sip.o hydra-vmauthd.o hydra-http-proxy-auth-ntlm.o hydra-imap-ntlm.o hydra-pop3-ntlm.o hydra-smtpauth-ntlm.o hydra-http-form.o crc32.o d3des.o md4.o hydra-mod.o ntlm.o hydra.o -lm -lssl -lpq -lssh -lcrypto -L/usr/lib -L/usr/local/lib -L/lib -L/lib -L/usr/lib || echo -e "\nIF YOU RECEIVED THE ERROR MESSAGE \"cannot find -lpq\" DO THE FOLLOWING:\n  make clean; ./configure\n  vi Makefile    <- and remove the \"-lpq\" and \"-DLIBPOSTGRES\" statements\n  make\n"
-e 
IF YOU RECEIVED THE ERROR MESSAGE "cannot find -lpq" DO THE FOLLOWING:
  make clean; ./configure
  vi Makefile    <- and remove the "-lpq" and "-DLIBPOSTGRES" statements
  make


If men could get pregnant, abortion would be a sacrament

test -e hydra.exe && touch Makefile || strip hydra pw-inspector
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra

---

