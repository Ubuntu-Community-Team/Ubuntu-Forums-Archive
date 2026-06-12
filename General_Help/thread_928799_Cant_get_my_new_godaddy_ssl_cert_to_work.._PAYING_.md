---
title: "Cant get my new godaddy ssl cert to work.. PAYING JOB $$$"
date: 2008-09-24
forum: General Help
---

### Post by svnslnlo on 2008-09-24
After following [THIS TUTORIAL]("http://caldergroup.com/security/apt-get-apache2-ssl-cert.html") I try to start up apache2 and get this error.. It asks for the pass phrase (For the ssl key file I guess, I'm a noob) so I enter it correctly and it just says FAIL, if I enter a false password it tells me its wrong and gives me 4 more chances.. Just add me to msn [email]silentkillerjoe@hotmail.com[/email] or xfire silentkillerjoe and I will pay you $7.00 on paypal or $14.00 on alertpay, I am willing to pay more I just need ssl on my website... Ill be standing by, please add me on msn or xfire..

EDIT: No control panel just so you know, I do everything via putty ssh and sftp in filezilla

root@LSN-D1915:~# /etc/init.d/apache2 start                                      * Starting web server apache2                                                  [Wed Sep 24 10:02:47 2008] [warn] module ssl_module is already loaded, skipping
[Wed Sep 24 10:02:47 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Wed Sep 24 10:02:47 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed Sep 24 10:02:47 2008] [warn] NameVirtualHost *:443 has no VirtualHosts
[Wed Sep 24 10:02:47 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
Apache/2.2.8 mod_ssl/2.2.8 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide the pass phrases.

Server LSN-D1915.pxe.limestonenetworks.com:443 (RSA)
Enter pass phrase:
                                                                         [fail]

---

