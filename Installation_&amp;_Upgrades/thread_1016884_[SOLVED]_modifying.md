---
title: "[SOLVED] modifying"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by abhilashm86 on 2008-12-20
There is a single configuration file to be altered: $HOME/.msmtprc. It can be created and permissions set as follows:

$ touch $HOME/.msmtprc
$ touch $HOME/.msmtp.log
$ chmod 0600 $HOME/.msmtprc

also while setting up mutt,
Below is the required configuration for a Gmail server:
account default              
host smtp.gmail.com          
port 587                     
from [email]full.gmail.address@gmail.com[/email]   
tls on                       
tls_starttls on              
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on                     
user gmail.username        
password mypassword        
logfile ~/.msmtp.log

where should i do the required configration for gmail server,it was given in this thread
[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)

---

### Post by Partyboi2 on 2008-12-20
After you have done this step
> $ touch $HOME/.msmtprc
$ touch $HOME/.msmtp.log
$ chmod 0600 $HOME/.msmtprc
 you will now have a hidden file called .msmtprc in your /home directory which you would  open using any text editor eg. ```
nano  ~/.msmtprc
``` and
add the following
```
account default              
host smtp.gmail.com          
port 587                     
from [COLOR=Red]full.gmail.address@gmail.com[/COLOR]   
tls on                       
tls_starttls on              
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on                     
user [COLOR=Red]gmail.username[/COLOR]        
password [COLOR=Red]mypassword [/COLOR]       
logfile ~/.msmtp.log
```then save the changes (Ctl+o enter Ctrl+x) and continue with the howto

*Remember to change the highlighted red parts to your actually information.

---

### Post by abhilashm86 on 2008-12-20
> **Partyboi2 said:**
> After you have done this step
 you will now have a hidden file called .msmtprc in your /home directory which you would  open using any text editor eg. ```
nano  ~/.msmtprc
``` and
add the following
```
account default              
host smtp.gmail.com          
port 587                     
from [COLOR=Red]full.gmail.address@gmail.com[/COLOR]   
tls on                       
tls_starttls on              
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on                     
user [COLOR=Red]gmail.username[/COLOR]        
password [COLOR=Red]mypassword [/COLOR]       
logfile ~/.msmtp.log
```then save the changes (Ctl+o enter Ctrl+x) and continue with the howto

*Remember to change the highlighted red parts to your actually information.


i changed the config file now,in mutt i am getting this error

From: root <root@abhilash-desktop>
      To: [email]abhilashm86@yahoo.com[/email]
      Cc:
     Bcc:
 Subject: hey
Reply-To:
     Fcc: ~/sent
     Mix: <no chain defined>
Security: Clear

-- Attachments
- I     1 /tmp/mutt-abhilash-desktop-0-6762-0[text/plain, 7bit, us-ascii, 0.1K]
-- Mutt: Compose  [Approx. msg size: 0.1K   Atts: 1]----------------------------
Error sending message, child exited 127 (Exec error.).

why is the from address not changed?

---

### Post by andrew.46 on 2008-12-21
Hi abhilashm86,

Sorry to see you are having a little trouble with the mutt and gmail guide:

> **abhilashm86 said:**
> i changed the config file now,in mutt i am getting this error

From: root <root@abhilash-desktop>
      To: [email]abhilashm86@yahoo.com[/email]

There is a setting in your $HOME/.muttrc which should be altered to something like the following:

```
# Boring details
set realname = "abhilashm86"
set from = "abhilashm86@gmail.com"
set use_from = yes
set envelope_from ="yes"

```

The settings in your $HOME/.msmtprc should reflect this naming scheme. Can you do me a favour and post the contents of this file to the forum? Using my fictitious address above this would make the $HOME/.msmtprc file something like this:

```
account default              
host smtp.gmail.com          
port 587                     
from abhilashm86@gmail.com  
tls on                       
tls_starttls on              
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on                     
user abhilashm86       
password mypassword        
logfile ~/.msmtp.log
```

With the obvious need to substitute your real details and your password.You appear to have another problem in that the mail is not leaving your system:

> Error sending message, child exited 127 (Exec error.).

This is usually a certificate error / msmtp problem. Can you repeat the step:

```
sudo apt-get install openssl ca-certificates
```

and post any error or success messages? Could you please then post the results of the following command:

```
sudo find /etc -iname 'ca-certificates.crt'
```

All the very best,

  Andrew

---

### Post by abhilashm86 on 2008-12-21
[QUOTE=andrew.46;6409600]Hi abhilashm86,
This is usually a certificate error / msmtp problem. Can you repeat the step:

```
sudo apt-get install openssl ca-certificates
```

yes i did once again,but its installed,0 upgraded was the result by terminal

HOME/.msmtprc details are

-rw-------  1 abhilash root       432 2008-12-21 18:56 .msmtprc
-rw-------  1 abhilash root       436 2008-12-21 18:52 .msmtprc~

contents of file .msmtprc are
account default              
host smtp.gmail.com          
port 587                     
from [email]abhilashm86@gmail.com[/email]   
tls on                       
tls_starttls on              
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on                     
user abhilashm86        
password *********

set realname = "abhilashm86"
set from = "abhilashm86@gmail.com"
set use_from = yes
set envelope_from = "yes"

logfile ~/.msmtp.log






and post any error or success messages? Could you please then post the results of the following command:

```
sudo find /etc -iname 'ca-certificates.crt'
```

root@abhilash-desktop:/# sudo find /etc -iname 'ca-certificates.crt'
/etc/ssl/certs/ca-certificates.crt
root@abhilash-desktop:/# 

and if u want details of file ca-certificates

-----BEGIN CERTIFICATE-----
MIIEuDCCA6CgAwIBAgIBBDANBgkqhkiG9w0BAQUFADCBtDELMAkGA1UEBhMCQlIx
EzARBgNVBAoTCklDUC1CcmFzaWwxPTA7BgNVBAsTNEluc3RpdHV0byBOYWNpb25h
bCBkZSBUZWNub2xvZ2lhIGRhIEluZm9ybWFjYW8gLSBJVEkxETAPBgNVBAcTCEJy
YXNpbGlhMQswCQYDVQQIEwJERjExMC8GA1UEAxMoQXV0b3JpZGFkZSBDZXJ0aWZp
Y2Fkb3JhIFJhaXogQnJhc2lsZWlyYTAeFw0wMTExMzAxMjU4MDBaFw0xMTExMzAy
MzU5MDBaMIG0MQswCQYDVQQGEwJCUjETMBEGA1UEChMKSUNQLUJyYXNpbDE9MDsG
A1UECxM0SW5zdGl0dXRvIE5hY2lvbmFsIGRlIFRlY25vbG9naWEgZGEgSW5mb3Jt
YWNhbyAtIElUSTERMA8GA1UEBxMIQnJhc2lsaWExCzAJBgNVBAgTAkRGMTEwLwYD
VQQDEyhBdXRvcmlkYWRlIENlcnRpZmljYWRvcmEgUmFpeiBCcmFzaWxlaXJhMIIB
IjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAwPMudwX/hvm+Uh2b/lQAcHVA
isamaLkWdkwP9/S/tOKIgRrL6Oy+ZIGlOUdd6uYtk9Ma/3pUpgcfNAj0vYm5gsyj
Qo9emsc+x6m4VWwk9iqMZSCK5EQkAq/Ut4n7KuLE1+gdftwdIgxfUsPt4CyNrY50
QV57KM2UT8x5rrmzEjr7TICGpSUAl2gVqe6xaii+bmYR1QrmWaBSAG59LrkrjrYt
bRhFboUDe1DK+6T8s5L6k8c8okpbHpa9veMztDVC9sPJ60MWXh6anVKo1UcLcbUR
yEeNvZneVRKAAU6ouwdjDvwlsaKydFKwed0ToQ47bmUKgcm+wV3eTRk36UOnTwID
AQABo4HSMIHPME4GA1UdIARHMEUwQwYFYEwBAQAwOjA4BggrBgEFBQcCARYsaHR0
cDovL2FjcmFpei5pY3BicmFzaWwuZ292LmJyL0RQQ2FjcmFpei5wZGYwPQYDVR0f
BDYwNDAyoDCgLoYsaHR0cDovL2FjcmFpei5pY3BicmFzaWwuZ292LmJyL0xDUmFj
cmFpei5jcmwwHQYDVR0OBBYEFIr68VeEERM1kEL6V0lUaQ2kxPA3MA8GA1UdEwEB
/wQFMAMBAf8wDgYDVR0PAQH/BAQDAgEGMA0GCSqGSIb3DQEBBQUAA4IBAQAZA5c1
U/hgIh6OcgLAfiJgFWpvmDZWqlV30/bHFpj8iBobJSm5uDpt7TirYh1Uxe3fQaGl
YjJe+9zd+izPRbBqXPVQA34EXcwk4qpWuf1hHriWfdrx8AcqSqr6CuQFwSr75Fos
SzlwDADa70mT7wZjAmQhnZx2xJ6wfWlT9VQfS//JYeIc7Fue2JNLd00UOSMMaiK/
t79enKNHEA2fupH3vEigf5Eh4bVAN5VohrTm6MY53x7XQZZr1ME7a55lFEnSeT0u
mlOAjR2mAbvSM5X5oSZNrmetdzyTj2flCM8CC7MLab0kkdngRIlUBGHF1/S5nmPb
K+9A46sd33oqK8n8
-----END CERTIFICATE-----
some translation is not done i guess,so it was strange that when i opened gmail i saw a mail in inbox which i did from mutt!!!!!!but that to yahoo,don't know,can u tell about the child exiteng,why child is not able to execute its process

thanks a lot for replying,i m sure u'll help me out..........

---

### Post by abhilashm86 on 2008-12-21
HOME/.msmtprc details are

-rw------- 1 abhilash root 432 2008-12-21 18:56 .msmtprc
-rw------- 1 abhilash root 436 2008-12-21 18:52 .msmtprc~
hey should permissions be set to executable(x)its only rw-,is this a problem?

---

### Post by abhilashm86 on 2008-12-21
hey andrew,i succeded with some extent with mutt,but when i sent a mail following error occured,

Output of the delivery process
msmtp: authentication failed (method PLAIN)
msmtp: server message: 535-5.7.1 Username and Password not accepted. Learn more
+at
msmtp: server message: 535 5.7.1
+[http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) 14sm11001617tim.30
msmtp: could not send mail (account default from /root/.msmtprc)



i:Exit  -:PrevPg  <Space>:NextPg ?:Help
Error sending message, child exited 77 (Insufficient permission.).

so i cross checked with everything,could'nt find error,where is the problem actually?

---

### Post by andrew.46 on 2008-12-21
Hi abhilshm86,

> **abhilashm86 said:**
> 
HOME/.msmtprc details are

```
-rw-------  1 abhilash root       432 2008-12-21 18:56 .msmtprc
```


I will admit to being a little puzzled as to why root is in there. My own .msmtprc file has permissions as follows:

```
andrew@skamandros:~$ ls -l $HOME/.msmtprc
-rw------- 1 andrew andrew 329 2008-12-14 01:10 /home/andrew/.msmtprc
```

I suggest you try changing ownership of your own .msmtprc as follows:

```
sudo chown abhilash:abilash $HOME/.msmtprc
```

and this should resolve the slightly odd ownership issue.

> 
contents of file .msmtprc are
account default              
host smtp.gmail.com          
port 587                     
from [email]abh[...]6@gmail.com[/email]   
tls on                       
tls_starttls on              
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on                     
user abhilashm86        
password *********

[B][COLOR="Red"]set realname = "abhilashm86"
set from = "abhilashm86@gmail.com"
set use_from = yes
set envelope_from = "yes"[/COLOR][/B]

logfile ~/.msmtp.log

My apologies, I have mislead you a little. The section that I have outlined in red actually belongs in your $HOME/.muttrc *not* in your $HOME/.msmtprc. BTW you might be well to edit your post and obscure that email address (as I have done) to avoid spam.

> 
```
root@abhilash-desktop:/# sudo find /etc -iname 'ca-certificates.crt'
/etc/ssl/certs/ca-certificates.crt
root@abhilash-desktop:/#
``` 

Looks like the certificate pack is in place, this contains all the certificates that gmail will call for. The username 'root' worries me as well. You are not working as root are you? In Ubuntu you should be logging on as a normal user and using sudo to give yourself super-user rights.

> and if u want details of file ca-certificates
[....]



In this guide you do no have to extract any certificates, simply point programs like msmtp to the certificate pack /etc/ssl/certs/ca-certificates.crt. If you have manually extracted a certificate you may have made a little work for yourself :-). 

> can u tell about the child exiteng,why child is not able to execute its process

This error is almost always generated by msmtp failing in its certificate check and not sending mail. You may see an error to this effect in $HOME/.msmtp.log.

Keep at it I think we are almost there :-).

  Andrew

---

### Post by andrew.46 on 2008-12-21
Hi abhilashm,

> **abhilashm86 said:**
> HOME/.msmtprc details are

```
-rw------- 1 abhilash root 432 2008-12-21 18:56 .msmtprc
-rw------- 1 abhilash root 436 2008-12-21 18:52 .msmtprc~
```
hey should permissions be set to executable(x)its only rw-,is this a problem?

No, does not need to be executable. But as I mentioned in another post root does not have to be there and the following would resolve that:

```
sudo chown abhilash:abhilash $HOME/.msmtprc
```

All the best,

 Andrew

---

### Post by andrew.46 on 2008-12-21
Hi abhilashm,

Hmmm... sorry I should have condensed my answers to all of your posts :-)

> **abhilashm86 said:**
> hey andrew,i succeded with some extent with mutt,but when i sent a mail following error occured,[...]

Can you post the contents of $HOME/.msmtp.log?

Andrew

---

### Post by abhilashm86 on 2008-12-22
[QUOTE=andrew.46;6413544]Hi abhilashm,

hi andrew i made the changes,now its almost done.
now its changed to abhilash,this is in root directory

root@abhilash-desktop:~# ls -a -l $HOME/.msmtprc
-rw------- 1 abhilash abhilash 427 2008-12-22 12:59 /root/.msmtprc

my doubt is that in root directory,all permissions are mine,but in home directory its showing like,

root@abhilash-desktop:/home# ls -a -l .msmtprc
-rw------- 1 abhilash root 438 2008-12-21 21:33 .msmtprc

this may be problem right?see my end mail error,its shown at end,

Can you post the contents of $HOME/.msmtp.log?


Dec 21 20:01:16 host=smtp.gmail.com tls=on auth=on user=gmail.abhilashm86@gmail.com from=abhilashm86@gmail.com recipients=abhilashm86@yahoo.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at         \n535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) a4sm10623913tib.27' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM
Dec 21 20:20:07 host=smtp.gmail.com tls=on auth=on user=gmail.abhilashm86@gmail.com from=abhilashm86@gmail.com recipients=abhilashm86@yahoo.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at         \n535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) d4sm4831778tib.11' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM
Dec 21 20:23:52 host=smtp.gmail.com tls=on auth=on user=gmail.abhilashm86@gmail.com from=abhilashm86@gmail.com recipients=abhilashm86@yahoo.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at         \n535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) i6sm12041946tid.36' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM
Dec 21 20:30:52 host=smtp.gmail.com tls=on auth=on user=gmail.abhilashm86@gmail.com from=abhilashm86@gmail.com recipients=abhilashm86@yahoo.co.in smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at         \n535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) d1sm11055531tid.4' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM
Dec 21 20:49:35 host=smtp.gmail.com tls=on auth=on user=gmail.abhilashm86@gmail.com from=abhilashm86@gmail.com recipients=abhilashm86@yahoo.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at         \n535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) u8sm8156094tia.8' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM
Dec 21 20:50:12 host=smtp.gmail.com tls=on auth=on user=gmail.abhilashm86@gmail.com from=abhilashm86@gmail.com recipients=abhilashm86@yahoo.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at         \n535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) 14sm8940812tim.10' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM
Dec 21 21:12:04 host=smtp.gmail.com tls=on auth=on user=gmail.abhilashm86@gmail.com from=abhilashm86@gmail.com recipients=abhilashm86@yahoo.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at         \n535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) i6sm12167314tid.36' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM
Dec 21 21:25:16 host=smtp.gmail.com tls=on auth=on user=gmail.abhilashm86@gmail.com from=abhilashm86@gmail.com recipients=abhilashm86@yahoo.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at         \n535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) a4sm8208120tib.7' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM
Dec 21 21:28:57 host=smtp.gmail.com tls=on auth=on user=gmail.abhilashm86@gmail.com from=abhilashm86@gmail.com recipients=abhilashm86@yahoo.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at         \n535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) y3sm4535851tia.20' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM
Dec 21 21:31:07 host=smtp.gmail.com tls=on auth=on user=gmail.abhilashm86@gmail.com from=abhilashm86@gmail.com recipients=abhilashm86@yahoo.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at         \n535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) i9sm3108786tid.5' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM
Dec 21 21:34:34 host=smtp.gmail.com tls=on auth=on user=gmail.abhilashm86@gmail.com from=abhilashm86@gmail.com recipients=abhilashm86@yahoo.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at         \n535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) 14sm11001617tim.30' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM

now this is status of mail delivery,
Output of the delivery process
msmtp: /root/.msmtprc: must be owned by you


i:Exit  -:PrevPg  <Space>:NextPg ?:Help
Error sending message, child exited 78 ().

so a slight problem to be solved,i hope u'll sort it out.

---

### Post by abhilashm86 on 2008-12-22
well i could'nt understand the error of the mail,

root@abhilash-desktop:~# ls -a -l
-rw-r--r--  1 abhilash abhilash  4315 2008-12-21 21:34 .msmtp.log
-rw-------  1 abhilash abhilash   427 2008-12-22 12:59 .msmtprc
-rw-r--r--  1 root     root      3646 2008-12-21 19:50 .muttrc

when we see this,i am holding the permissions,but why mail is giving following error?

Output of the delivery process

msmtp: /root/.msmtprc: must be owned by you

so just i cross checked,din't quiet understand friend.

---

### Post by andrew.46 on 2008-12-22
Hi,

Some of the problem seems to be that you may be using a root account. For the most part this guide assumes that you are logging on as an ordinary user, not as a superuser.

Can I ask what version of Ubuntu you are using and if you are logging on as yourself, an unprivileged user?

All the best,

  Andrew

---

### Post by abhilashm86 on 2008-12-22
[QUOTE=andrew.46;6416280]Hi,

Some of the problem seems to be that you may be using a root account. For the most part this guide assumes that you are logging on as an ordinary user, not as a superuser.

Can I ask what version of Ubuntu you are using and if you are logging on as yourself, an unprivileged user?

i am using 8.04 ubuntu,yes i become super user genrally while programming and other time use also,is this a bad habit of doing things?

so what i need to do now,can i modify code or i can repeat process!!!!!!

---

### Post by abhilashm86 on 2008-12-22
the main problem is when i don't become a super user,mutt will not work(no highlight mode in window and others),so whats your suggestion further andrew?

---

### Post by andrew.46 on 2008-12-22
Hi abhilashm,

> **abhilashm86 said:**
> the main problem is when i don't become a super user,mutt will not work(no highlight mode in window and others),so whats your suggestion further andrew?

I think it would be a good idea to work through the guide again but this time as an *ordinary user*. What you seem to have at the moment is a mixture of configuration files, some owned by root and some by yourself. You should not have to reinstall any of the applications such as mutt, msmtp, fetchmail or procmail but I would remake the various config files as an ordinary user after deleting the previous ones. These files are: .msmtprc, .procmailrc, .muttrc and .fetchmailrc.

With any luck this will have you sending mail soon :-).

All the best,

  Andrew

---

### Post by abhilashm86 on 2008-12-23
[QUOTE=andrew.46;6417726]Hi abhilashm,
With any luck this will have you sending mail soon :-).

hi andrew,i did sent u a mail through mutt,check it!!!!!!

well i go here,i din't delete any files,but became a normal user and created those . files once more and it worked for me!!!!!!!

thans for whole support,the guide was just awesome and so simple,i was a fool becoming sudo su and messed up a little bit.

keep it up andrew:)

---

### Post by andrew.46 on 2008-12-23
Hi abhilmashm,

> **abhilashm86 said:**
> hi andrew,i did sent u a mail through mutt,check it!!!!!!

Great news! I am at work at the moment but I shall check when I get home and send a reply.

> thans for whole support,the guide was just awesome and so simple,i was a fool becoming sudo su and messed up a little bit.

Most other distros do not shield a user from su as much as Ubuntu does but I guess while using Ubuntu it is better to remain within these guidelines.

Anyway the guide is really only an introduction to mutt, it is now up to you to learn more about it and I am sure that you will :-).

All the very best,

  Andrew

---

### Post by mwilliam13 on 2009-02-09
Quick question to anyone willing to help...

I am relatively new to Linux < 2 years... I am running a box using Ubuntu 8.04.  I have a web developer using PHP to send mail when a certain action takes place.  His script requires sendmail for message delivery.  His user (like most Apache2 configs) is www-data, and from what I can tell, the "home directory" for that user is \var\www.  In that location, I created a .mailrc file with the syntax: 
[INDENT]set sendmail="/usr/bin/msmtp"[/INDENT]
It doesn't seem to work with his script even though it is calling sendmail for the message delivery.  The PHP script looks like:

[INDENT]<?php 

$to = $_GET['email'];
$subject = 'TESTING';
$message = 'Hello World from Our Production Machine.';

if(mail($to, $subject, $message))
{
	echo "Done.";
}
else
{
	echo "FAIL.";
}

?>
[/INDENT]
Msmtp is configured properly as I can successfully send mail from the CLI as the www-data user (sudo su www-data) but not with the php script.  I am perplexed but keenly interested in what I missed.  My background is hardware and OS stuff, I can usually figure things out.  My web developer does software, and he doesn't have the slightest (at least that is what he is letting on!! )

Any suggestions?  Would be most appreciated.

Bill M.
Pueblo, CO

PS. if you want to see the .msmtprc file:

[INDENT]account default
host smtp.gmail.com
port 587
from [email]no-reply@mydomain.com[/email]
tls on
tls_starttls on
# tls_trust_file /etc/ssl/certs/ThawteCodeSigningCA_b64.txt
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on
user [email]no-reply@mydomain.com[/email]
password mypassword
logfile /etc/.msmtp.log[/INDENT]

---

