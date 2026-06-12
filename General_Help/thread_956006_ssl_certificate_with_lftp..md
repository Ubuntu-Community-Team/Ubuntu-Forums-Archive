---
title: "ssl certificate with lftp."
date: 2008-10-22
forum: General Help
---

### Post by MrJaxon on 2008-10-22
Hi people!

I hope to get your help on this issue since I've been going crazy not finding the answer by google or by the info or manpages. I'm really new to linux so maybe I've seen the answer somewhere but haven't realized it.

Anyways, I got a friend who has a private server encrypted with auth ssl. In GUI ftp programs you get a certificate that you can save when connecting to this server.

I really want to learn how to do this via lftp. I got lftp version 3.6.1
and I connect to the server like this: lftp -d -u username,password -p portnumber xx.xxx.xx.xxx:xxxx

lftp connects to the server and shows me this:

<--- 220 FTP Server ready.
---> FEAT
<--- 500 'FEAT': Command not understood
---> AUTH TLS
<--- 234 AUTH TLS successful.
---> USER test
Certificate: CN=xx.xxx.xx.xxx
Issued by: CN=xx.xxx.xx.xxx
WARNING: Certificate verification: Not trusted

I can move around the server but when I try to dl something with: "get filename.txt" it says: Access failed: 550 filename.txt Access is denied.

I guess that I should have to get that certificate in some way and store it on my computer, however I don't know anything for sure. I would really like a walkthrough or help in any way to get this to work.

can anyone help me how to sort this issue out? I would be really thankful.

Bye for now!

---

### Post by MrJaxon on 2008-10-23
Ok, I got the answer from another forum. Thought that I would post it here if anyone is interested. It wasn't the certifikate, apparently I can just ignore the warning. Only thing I had to do was to put "set ftp:ssl-protect-data yes" in lftp.conf. After that I could dl from the server :D

---

