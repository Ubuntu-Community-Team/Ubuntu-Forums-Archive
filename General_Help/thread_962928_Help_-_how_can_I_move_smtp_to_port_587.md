---
title: "Help - how can I move smtp to port 587?"
date: 2008-10-29
forum: General Help
---

### Post by joel@parke.ods.org on 2008-10-29
I need to move my mail server (smtp) to a different port, such as 587.  I looked around for how to modify main.cf and didn't see how to do it.  Could someone let me know what changes to add to main.cf below?  I am certain that others need to do this.  Thanks!

*****main.cf*************

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# TLS parameters
smtp_tls_CAfile=/etc/apache2/certwork/ca.crt
smtp_tls_cert_file=/etc/apache2/certwork/parke.ods.org.crt
smtp_tls_key_file=/etc/apache2/certwork/server.key
smtpd_tls_CAfile=/etc/apache2/certwork/ca.crt
smtpd_tls_cert_file=/etc/apache2/certwork/parke.ods.org.crt
smtpd_tls_key_file=/etc/apache2/certwork/server.key
smtp_use_tls=yes
smtp_tls_note_starttls_offer = yes
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

myhostname = parke.ods.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = parke.ods.org, MinistryNewEngland.org, TheNarrow$

relayhost = [smtp.comcast.net]:587
#relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =

mynetworks = 127.0.0.0/8, 192.168.1.0/28,
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
header_size_limit = 10240000
message_size_limit = 1024000000
readme_directory = /usr/share/doc/postfix
html_directory = /usr/share/doc/postfix/html

---

### Post by joel@parke.ods.org on 2008-10-29
Hi,

I found that this was actually extremely easy to do.  For those of you also needing this, simply uncomment the submission line in
/etc/postfix/master.cf:
smtp      inet  n       -       n       -       -       smtpd
submission inet n      -       n       -       -       smtpd
Then restart postfix 
And all is good and smtp listens on both ports 25 and 587.
I hope this helps someone else out there.

... Joel

---

