---
title: "Mailserver Postfix doesnt work after installing Webmin"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by deepakdeshp on 2009-10-20
**Postfix mail problem**             
                                                                Hi,

My mail server using Postfix Dovecot is not working after installing webmin. I installed webmin successfully through an install.sh script. I had to change the hostname also in this process. It has reconfigured the Postfix and Dovecot config files. So I need to get the basic mail server working.

I am running Jaunty 9.04 and had successfully configured mail server and was able to get and send mail in my Thunderbird client from my client machine using Postfix and Dovecot.
I am unable to send mails even from localhost now.

 The Postfix mail logs are 

[I]Oct 20 02:34:27 ubuntu postfix/master[30239]: daemon started -- version 2.5.5, configuration /etc/postfix
Oct 20 02:34:34 ubuntu postfix/master[30239]: reload configuration /etc/postfix
Oct 20 02:34:49 ubuntu postfix/pickup[30260]: 4569F16162A: uid=0 from=<root>
Oct 20 02:34:49 ubuntu postfix/cleanup[30271]: 4569F16162A: message-id=<20091020063449.4569F16162A@ubuntuserver>
Oct 20 02:34:49 ubuntu postfix/qmgr[30259]: 4569F16162A: from=<root@ns1.YOURDOMAINNAMEHERE.com>, size=348, nrcpt=1 (queue active)
Oct 20 02:34:49 ubuntu postfix/local[30273]: 4569F16162A: to=<deepak@ns1.YOURDOMAINNAMEHERE.com>, orig_to=<root@ns1.YOURDOMAINNAMEHERE.com>, relay=local, delay=0.06, delays=0.05/0/0/0.01, dsn=2.0.0, status=sent (delivered to maildir)
Oct 20 02:34:49 ubuntu postfix/qmgr[30259]: 4569F16162A: removed[/I]


Any help will be greatly appreciated.

---

