---
title: "Perl + PHP Session"
date: 2008-09-03
forum: General Help
---

### Post by cathalb on 2008-09-03
I am in process of migrating an old webpage (which uses mostly perl) to our new ubuntu server. And myself not really knowing perl, ever time I get an error for missing library I turn to google to find what package contains this perl library. But I got stuck: 
```

use PHP::Session;

```
This lines complains it cant find a certain file, the apache logs show this 
```

Can't locate PHP/Session.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .)

```

Sorry if this does seem obvious but I just can't find the packages in the repositories that I need. Any help would be really appreciated:)

---

### Post by cszikszoy on 2008-09-03
Do you know how to check which modules are loaded?

If you create a new .php document, call it "phpinfo.php"

Inside the document write this:

[PHP]<?php phpinfo(); ?>[/PHP]

Open this page in a webbrowser and it will list all EGPCS data (Environment, Get, Post, Cookie, Server).

It will also list every module that php knows is loaded.  This doesn't necessarily fix your problem, because it's specifically complaining that it can't find the sessions module, but either way, this page is a very valuable debugging tool.

---

### Post by cathalb on 2008-09-03
phpinfo lists the modules php has, do you think my problem is I'm missing a php library or a perl one?

---

### Post by cszikszoy on 2008-09-03
It looks like it's complaining about a perl module that's missing.  In the error message it's listing the directories that it searches to find session.pm but it's not there.  Can you locate session.pm anywhere on your system?

If not, this could be your problem :)

---

### Post by cathalb on 2008-09-03
> **cszikszoy said:**
> It looks like it's complaining about a perl module that's missing.  In the error message it's listing the directories that it searches to find session.pm but it's not there.  Can you locate session.pm anywhere on your system?

If not, this could be your problem :)

well yes... that is my problem... I know I dont have php/session.pm, anywhere in the directories in the INC array or in fact anywhere on the system. I have a cgi/session.pm. But thats not what 
```
use PHP::Session;
```
in the perl script file is looking for.

---

### Post by cszikszoy on 2008-09-03
> **cathalb said:**
> well yes... that is my problem... I know I dont have php/session.pm, anywhere in the directories in the INC array or in fact anywhere on the system. I have a cgi/session.pm. But thats not what 
```
use PHP::Session;
```in the perl script file is looking for.


How do you know that's not what you want?  A CGI script is just perl.  Have you tried changing PHP::Session to CGI::Session?

---

### Post by justleen on 2008-09-03
the module is on CPAN:
[http://search.cpan.org/~miyagawa/PHP-Session-0.26/lib/PHP/Session.pm](http://search.cpan.org/~miyagawa/PHP-Session-0.26/lib/PHP/Session.pm)

---

### Post by cathalb on 2008-09-03
> **justleen said:**
> the module is on CPAN:
[http://search.cpan.org/~miyagawa/PHP-Session-0.26/lib/PHP/Session.pm](http://search.cpan.org/~miyagawa/PHP-Session-0.26/lib/PHP/Session.pm)

Yes thank you, that looks like what I am looking for.

---

