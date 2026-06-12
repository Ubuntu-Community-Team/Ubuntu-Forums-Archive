---
title: "nmap question"
date: 2008-08-25
forum: General Help
---

### Post by cssutto on 2008-08-25
nmap gives me the following and I have no idea what it means.

Can anyone explain?

1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at [http://www.insecure.org/cgi-bin/servicefp-submit.cgi](http://www.insecure.org/cgi-bin/servicefp-submit.cgi) :
SF-Port80-TCP:V=4.53%I=7%D=8/25%Time=48B35071%P=x86_64-unknown-linux-gnu%r
SF:(GetRequest,EE,"HTTP/1\.0\x20401\x20Unauthorized\r\nServer:\x20Embedded
SF:\x20HTTP\x20Server\x20RK1008\r\nWWW-Authenticate:\x20Basic\x20realm=\"K
SF:R1\x20\"\r\nConnection:\x20close\r\n\r\n<HTML><HEAD><TITLE>401\x20Unaut
SF:horized</TITLE></HEAD>\n<BODY\x20BGCOLOR=\"#ffffff\"><H4>401\x20Unautho
SF:rized</H4></BODY></HTML>\n")%r(HTTPOptions,D1,"HTTP/1\.0\x20501\x20Not\
SF:x20Implemented\r\nServer:\x20Embedded\x20HTTP\x20Server\x20RK1008\r\nCo
SF:nnection:\x20close\r\n\r\n<HTML><HEAD><TITLE>501\x20Not\x20Implemented<
SF:/TITLE></HEAD>\n<BODY\x20BGCOLOR=\"#ffffff\"><H4>501\x20Not\x20Implemen
SF:ted</H4></BODY></HTML>\n")%r(RTSPRequest,D1,"RTSP/1\.0\x20501\x20Not\x2
SF:0Implemented\r\nServer:\x20Embedded\x20HTTP\x20Server\x20RK1008\r\nConn
SF:ection:\x20close\r\n\r\n<HTML><HEAD><TITLE>501\x20Not\x20Implemented</T
SF:ITLE></HEAD>\n<BODY\x20BGCOLOR=\"#ffffff\"><H4>501\x20Not\x20Implemente
SF:d</H4></BODY></HTML>\n")%r(FourOhFourRequest,BF,"HTTP/1\.0\x20404\x20No
SF:t\x20Found\r\nServer:\x20Embedded\x20HTTP\x20Server\x20RK1008\r\nConnec
SF:tion:\x20close\r\n\r\n<HTML><HEAD><TITLE>404\x20Not\x20Found</TITLE></H
SF:EAD>\n<BODY\x20BGCOLOR=\"#ffffff\"><H4>404\x20Not\x20Found</H4></BODY><
SF:/HTML>\n")%r(SIPOptions,D0,"SIP/2\.0\x20501\x20Not\x20Implemented\r\nSe
SF:rver:\x20Embedded\x20HTTP\x20Server\x20RK1008\r\nConnection:\x20close\r
SF:\n\r\n<HTML><HEAD><TITLE>501\x20Not\x20Implemented</TITLE></HEAD>\n<BOD
SF:Y\x20BGCOLOR=\"#ffffff\"><H4>501\x20Not\x20Implemented</H4></BODY></HTM
SF:L>\n");

---

### Post by Taxman415a on 2008-08-26
It's in the manpage, check man nmap and hit a / and then fingerprint and enter which will get you to a relevant section. Basically nmap tried to do service or OS detection of some sort based on the options you gave to it and the results were unknown to it. So it prints out that fingerprint in case you know exactly what was running on the machine for sure so that the nmap database can be updated.

---

### Post by cssutto on 2008-08-26
Thanks for the info.

After digging through it all, I still don't know any more than I did.

I have a wireless router which is set up to stealth port 80 through the router's firewall.

I suspect that this is what nmap is reporting.

---

### Post by Taxman415a on 2008-08-27
Yes basically. You either ran the -A or -sV switches to nmap and it tried service and version detection and found one it didn't know in it's database. That fingerprint is just some details they can use to update the database so that next time it runs it could give the answer more authoritatively instead of the output you saw.

---

