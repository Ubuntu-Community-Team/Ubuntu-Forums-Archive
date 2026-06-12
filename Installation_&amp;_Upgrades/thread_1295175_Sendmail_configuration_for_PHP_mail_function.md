---
title: "Sendmail configuration for PHP mail function"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by Hoogoo on 2009-10-19
Hello, I 've installed ubuntu,apache,php,... and i need some solution how to configure sendmail to make php "mail" function work. Any ideas?

I mean what else to install and how to configure it. 

Thak you, Hoogoo

---

### Post by Hoogoo on 2009-10-19
Looks like my topic is little bit dead?

Anyone?

---

### Post by Bachstelze on 2009-10-19
A full-fledged MTA like Sendmail will probably be largely overkill. Use something like ssmtp instead.

---

### Post by therendus on 2009-11-01
> **Bachstelze said:**
> A full-fledged MTA like Sendmail will probably be largely overkill. Use something like ssmtp instead.

ssmtp is not good for php since it stalls the execution while connecting to the remote smtp server.

After reading an endless list of 'useful' solutions here's how mine looked eventually:

[LIST=1][*]Install heirloom-mailx
***sudo aptitude install heirloom-mailx ***

[*]Configure it
/etc/nail.rc:
**set smtp=mail.yourdomain.com** *(example)*
...smtp-auth-user
...smtp-auth-password
( see file://localhost[SIZE="2"]**/usr/share/doc/heirloom-mailx/heirloom-mailx.1.html#18**[/SIZE] for details )
*optional:*
**set hostname=nameyouwanttoapearassource.host**
[*]Configure php
In the valid php.ini (make sure you edit the correct one for cli and apache mods)
**sendmail_path = /usr/bin/mailx -t**
[/LIST]

You should now be able to use the mail() function with no stalling of the script (and receiving the mail).

*** Make sure you include the *From:* field in your additional headers in the function call** or there are chances a stupid and "informative" 
*_smtp-server: 451 Temporary local problem - please try later_*
error would appear.

---

