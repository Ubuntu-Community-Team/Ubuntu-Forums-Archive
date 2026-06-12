---
title: "ssmtp.conf FromLineOverride=YES working with google apps"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by amytys on 2009-10-16
I can't get addresses other than my AuthUser address to appear in the "from" address of an e-mail sent from my server, even with the FromLineOverride=YES set in my ssmtp.conf file.   Configuration is very straightforward - this should be very easy.  Nobody else in the google world seems to be having this problem.  So, what's going on with *my* configuration?  :(

The OS is *Ubuntu Jaunty 9.04*, running on a RackSpace Cloud Server.

I installed ssmtp (sudo apt-get install ssmtp)

I set the config to work with google apps (requisite MX DNS entries per google and changes to ssmtp.conf file).

MX records:

[LIST]
[*]1   ASPMX.L.GOOGLE.COM
[*]5   ALT1.ASPMX.L.GOOGLE.COM
[*]5   ALT2.ASPMX.L.GOOGLE.COM
[*]10  ASPMX2.GOOGLEMAIL.COM
[*]10  ASPMX3.GOOGLEMAIL.COM
[/LIST]

Conf file: (sudo vi /etc/ssmtp/ssmtp.conf)[INDENT][I]root=noreply@mydomain.com
mailhub=smtp.gmail.com:587
hostname=myhost
UseSTARTTLS=yes
UseTLS=yes
AuthUser=me@mydomain.com
AuthPass=P@55w0rd
FromLineOverride=YES[/I]
[/INDENT]Test in various ways... let's keep it easy and use commandline

cat <<EOF | ssmtp [EMAIL="testreceive@domain.com"]testreceive@domain.com[/EMAIL]
From: amytys <testsend@anotherdomain.com>
To: [EMAIL="testreceive@domain.com"]testreceive@domain.com[/EMAIL]
Subject: Hello World

Hello World
EOF


I get the mail in the [EMAIL="testreceive@domain.com"]testreceive@domain.com[/EMAIL] account.  However, the send is not [EMAIL="testsend@anotherdomain.com"]testsend@anotherdomain.com[/EMAIL] as one would expect due to the FromLineOverride=YES config line.  It is still the authuser account, [EMAIL="me@mydomain.com"]me@mydomain.com[/EMAIL].

What gives????

BTW, if I change the Auth info in the ssmtp.conf file the email fails so I know I'm working with the right conf file.

---

### Post by amytys on 2009-10-16
Hmmm... more info.  Perhaps my server *is* working OK.  I just did a

    sudo cat /var/log/mail.log

and I see that my entries are spelled out as "sent mail for [email]testsend@anotherdomain.com[/email]"

So, it appears that the mail header may be being overridden on the google-apps side of the house.  Comments?  Is there a google-apps setting for accounts that's similar to the *FromLineOverride=YES*

I'm really getting confused here.  Is there a way that I can see the entire mail header as ssmtp will send it before it gets routed through Google?  That will help narrow down where my header is being set to with the faulty address (at least I thought you were able to route through a google-apps account and still get an e-mail address different than that of the AuthUser account).

---

### Post by amytys on 2009-10-16
After much research, I've discovered the following huge drawback: Gmail automatically rewrites the "from" line of any e-mail you send via their SMTP gateway to your Gmail address, and it overrides any Reply-To settings you may have in your e-mail software in favor of the one in Gmail's web interface.  Looks like you can point it to another account, but said account can't be dynamic based on the content of an incoming mail header's "from" info - [http://mail.google.com/support/bin/answer.py?hl=en&ctx=mail&answer=22370](http://mail.google.com/support/bin/answer.py?hl=en&ctx=mail&answer=22370)

---

