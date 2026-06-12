---
title: "Postfix/SASL/MySQL &quot;SASL LOGIN authentication failed&quot;"
date: 2008-10-04
forum: General Help
---

### Post by Temujin_12 on 2008-10-04
Okay, here we go...

I'm trying to get SMTP to work using postfix/sasl/mysql on an Ubuntu 6.06.2 LTS server.  I followed [a really good guide]("http://flurdy.com/docs/postfix/edition5.html") in setting this up.

I've turned off TLS so I can test things in basic LOGIN mode.  I've turned up logging as much as I can figure out how to do.  Here's what I'm seeing:

Client:
```

$telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 mydomain.com ESMTP Postfix
EHLO mydomain.com
250-mydomain.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5 PLAIN LOGIN
250-AUTH=DIGEST-MD5 CRAM-MD5 PLAIN LOGIN
250 8BITMIME
AUTH LOGIN
334 VXNlcm5hbWU6
[BASE_64_ENCODED_USERNAME]
334 UGFzc3dvcmQ6
[BASE_64_ENCODED_PASSWORD]
535 Error: authentication failed

```

Here's what I see in my mail.log:
```

Oct  4 00:52:38 mydomain postfix/smtpd[4942]: > localhost.localdomain[127.0.0.1]: 220 mydomain.com ESMTP Postfix
Oct  4 00:52:44 mydomain postfix/smtpd[4942]: < localhost.localdomain[127.0.0.1]: EHLO localhost
Oct  4 00:52:44 mydomain postfix/smtpd[4942]: > localhost.localdomain[127.0.0.1]: 250-mydomain.com
Oct  4 00:52:44 mydomain postfix/smtpd[4942]: > localhost.localdomain[127.0.0.1]: 250-PIPELINING
Oct  4 00:52:44 mydomain postfix/smtpd[4942]: > localhost.localdomain[127.0.0.1]: 250-SIZE 10240000
Oct  4 00:52:44 mydomain postfix/smtpd[4942]: > localhost.localdomain[127.0.0.1]: 250-ETRN
Oct  4 00:52:44 mydomain postfix/smtpd[4942]: > localhost.localdomain[127.0.0.1]: 250-AUTH DIGEST-MD5 CRAM-MD5 PLAIN LOGIN
Oct  4 00:52:44 mydomain postfix/smtpd[4942]: match_list_match: localhost.localdomain: no match
Oct  4 00:52:44 mydomain postfix/smtpd[4942]: match_list_match: 127.0.0.1: no match
Oct  4 00:52:44 mydomain postfix/smtpd[4942]: > localhost.localdomain[127.0.0.1]: 250-AUTH=DIGEST-MD5 CRAM-MD5 PLAIN LOGIN
Oct  4 00:52:44 mydomain postfix/smtpd[4942]: > localhost.localdomain[127.0.0.1]: 250 8BITMIME
Oct  4 00:52:48 mydomain postfix/smtpd[4942]: < localhost.localdomain[127.0.0.1]: AUTH LOGIN
Oct  4 00:52:48 mydomain postfix/smtpd[4942]: smtpd_sasl_authenticate: sasl_method LOGIN
Oct  4 00:52:48 mydomain postfix/smtpd[4942]: smtpd_sasl_authenticate: uncoded challenge: Username:
Oct  4 00:52:48 mydomain postfix/smtpd[4942]: > localhost.localdomain[127.0.0.1]: 334 VXNlcm5hbWU6
Oct  4 00:52:58 mydomain postfix/smtpd[4942]: < localhost.localdomain[127.0.0.1]: [BASE64_ENCODED_USERNAME]
Oct  4 00:52:58 mydomain postfix/smtpd[4942]: smtpd_sasl_authenticate: decoded response: myusername@mydomain.com
Oct  4 00:52:58 mydomain postfix/smtpd[4942]: smtpd_sasl_authenticate: uncoded challenge: Password:
Oct  4 00:52:58 mydomain postfix/smtpd[4942]: > localhost.localdomain[127.0.0.1]: 334 UGFzc3dvcmQ6
Oct  4 00:53:05 mydomain postfix/smtpd[4942]: < localhost.localdomain[127.0.0.1]: [BASE64_ENCODED_PASSWORD]
Oct  4 00:53:05 mydomain postfix/smtpd[4942]: smtpd_sasl_authenticate: decoded response: [MY_PASSWORD]
Oct  4 00:53:06 mydomain postfix/smtpd[4942]: warning: localhost.localdomain[127.0.0.1]: SASL LOGIN authentication failed
Oct  4 00:53:06 mydomain postfix/smtpd[4942]: > localhost.localdomain[127.0.0.1]: 535 Error: authentication failed

```

My biggest frustration is the seeming "SASL LOGIN authentication failed" dead end.  I've turned on MySQL logging and it is making the queries as specified in my postfix configuration files.

My question is how can I figure out what exactly is causing the SASL authentication failure?  Most SASL errors I've seen other people having with this have a bit more information about what caused the SASL authentication failure.  Is there a way to turn the SASL logging up?

---

### Post by Temujin_12 on 2008-10-04
I've since run saslfinger and here's the output:
*saslfinger -s:*
```
saslfinger - postfix Cyrus sasl configuration Sat Oct  4 10:54:33 CDT 2008
version: 1.0.2
mode: server-side SMTP AUTH

-- basics --
Postfix: 2.2.10
System: Ubuntu 6.06.2 LTS \n \l

-- smtpd is linked to --
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x00002aaaab4f1000)

-- active SMTP AUTH and TLS parameters for smtpd --
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = no


-- listing of /usr/lib64/sasl2 --
total 1088
[EXCLUDED]

-- listing of /usr/lib/sasl2 --
total 1088
[EXCLUDED]




-- content of /etc/postfix/sasl/smtpd.conf --
log_level: 7
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select password from mailbox where username='%u@%r' and active = 1


-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       -       -       -       smtpd      -v
          -o cleanup_service_name=pre-cleanup
smtps    inet  n       -       n       -       -       smtpd
        -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes
587     inet   n       -       n       -       -       smtpd
        -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
        -o mime_header_checks=
        -o nested_header_checks=
        -o body_checks=
        -o header_checks=
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       n       300     1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
        -o fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
amavis    unix  -       -       -       -       2       smtp
          -o smtp_data_done_timeout=1200
          -o smtp_send_xforward_command=yes
127.0.0.1:10025 inet n  -       -       -       -       smtpd
          -o content_filter=
          -o local_recipient_maps=
          -o relay_recipient_maps=
          -o smtpd_restriction_classes=
          -o smtpd_client_restrictions=
          -o smtpd_helo_restrictions=
          -o smtpd_sender_restrictions=
          -o smtpd_recipient_restrictions=permit_mynetworks,reject
          -o strict_rfc821_envelopes=yes
          -o mynetworks=127.0.0.0/8
          -o smtpd_error_sleep_time=0
          -o smtpd_soft_error_limit=1001
          -o smtpd_hard_error_limit=1001
pre-cleanup unix n      -       -       -       0       cleanup
          -o virtual_alias_maps=
          -o canonical_maps=
          -o sender_canonical_maps=
          -o recipient_canonical_maps=
          -o masquerade_domains=
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- mechanisms on localhost --
250-AUTH DIGEST-MD5 CRAM-MD5 PLAIN LOGIN
250-AUTH=DIGEST-MD5 CRAM-MD5 PLAIN LOGIN


-- end of saslfinger output --


```

*saslfinger -c:*
```
saslfinger - postfix Cyrus sasl configuration Sat Oct  4 10:52:43 CDT 2008
version: 1.0.2
mode: client-side SMTP AUTH

-- basics --
Postfix: 2.2.10
System: Ubuntu 6.06.2 LTS \n \l

-- smtp is linked to --
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x00002aaaab4f1000)

-- active SMTP AUTH and TLS parameters for smtp --
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes


-- listing of /usr/lib64/sasl2 --
total 1088
[EXCLUDED]

-- listing of /usr/lib/sasl2 --
total 1088
[EXCLUDED]


Cannot find the smtp_sasl_password_maps parameter in main.cf.
Client-side SMTP AUTH cannot work without this parameter!

```

I noticed that it says I needed the "smtp_sasl_password_maps" property in order for client side login.  Not knowing exactly what MySQL config is needed to do this, I borrowed config from [a how to for postfix/sasl/mysql]("http://www.happystoddards.com/neildocs/index.php/Fedora_Core_6_Postfix_Smart-hosting_with_SASL_and_MySQL#smtp_auth.cf").  Now when I run:
```
saslfinger -c
```

...it no longer shows that error.  Restarting postfix/sasl, however, I still get the same SASL authentication failure.  What's confusing is that I'm not seeing any additional MySQL queries in my query log, which leads me to believe that the authentication failure is happening before it involves the "smtp_sasl_password_maps" config.

Does anyone see anything else in my saslfinger outputs that indicates where the problem may be coming from? Or does anyone know how else to get more debugging information?

---

### Post by Temujin_12 on 2008-10-04
Thought I'd include MySQL logging to provide some more information:
```
                   2262 Connect     mail@localhost on maildb
                   2262 Query       START TRANSACTION
                   2262 Query       select password from mailbox where username='myusername@mydomain.com' and active = 1
                   2262 Query       COMMIT
                   2262 Quit

```

Here's my mailbox table:
```

mysql> select * from mailbox limit 1 \G
*************************** 1. row ***************************
username: myusername@mydomain.com
password: {SHA}3da541559918a808c2402bba5012f6c60b27661c
    name: My Name
 maildir: myusername@mydomain.com/
   quota: 0
  domain: mydomain.com
 created: 2008-10-01 23:36:57
modified: 2008-10-01 23:36:57
  active: 1
1 row in set (0.00 sec)

```

---

### Post by Temujin_12 on 2008-10-05
I figured it out.  It turns out that SASL cannot authenticate against encrypted or hashed passwords (lame!).  Changing the password field in my DB to be the plain text password now allows me to successfully authenticate.

---

