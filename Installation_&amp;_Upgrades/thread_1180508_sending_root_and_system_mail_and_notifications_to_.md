---
title: "sending root and system mail and notifications to an external account"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by ouchmyhand on 2009-06-06
I am trying to get my system and root email to be retrieved by a mail client on my OSX machine.
I have tried to install postfix and i think it is installed right but cant get my mail.

Any help form someone who has done this before would be great.
Also any tips on what sorts of system notifications etc. i need to set up on a new server would be great too.

---

### Post by ouchmyhand on 2009-06-08
Anyone???

---

### Post by ouchmyhand on 2009-06-09
Can anyone redirect me to somewhere that could help? I'm so new i don't know where to look. I thought the Ubuntu forums would be a good start but so far no assistance.

---

### Post by lensman3 on 2009-06-09
If the mail client is sendmail go to the file /etc/aliases and add a line for the user you want to forward.  It can be a fully qualified email account line "userabc@google.com".  Restart sendmail by "/etc/init.d/sendmail restart".  Sendmail may have to be setup so it will forward to a smart host.

Contact me through my profile and I'll send you my working copy of a sendmail smart host setup.  

To rebuild the alias data base use the command "newaliases".

There is one other piece you need.  Once everything is setup you need to send the existing email to your external account.  Use the following command for that:

formail -Y -s sendmail [email]person@new_address.com[/email] </var/spool/mail/mail-file

Then rename the /var/spool/mail/mail-file or delete it.  Again the mail client is sendmail so you need a smart host version of sendmail.  The reason you need a smart host version is "spam".

---

### Post by BarryDocks on 2009-10-05
Having similar problems, I have setup postfix uning smarthost and followed this guide:
[http://ubuntuforums.org/showthread.php?t=203577]("http://ubuntuforums.org/showthread.php?t=203577")

When I check my mail from my ISP  I get and undeliverable message which says:
> This is the mail system at host fileserver.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can delete your own text from the attached returned message.

                   The mail system

<adrian@myISP.co.uk> (expanded from <root>): host
    smtpin.myISP.co.uk[81.103.221.10] said: 553
    fileserver.ispmail.ntl.com does not exist (in reply to MAIL FROM command)

This is the content of my ~/etc/postfix/main.cf:
> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = fileserver
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = fileserver, localhost.localdomain, , localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all

I must be missing something simple in the postfix config, can anyone point me in the right direction?

Thanks

---

