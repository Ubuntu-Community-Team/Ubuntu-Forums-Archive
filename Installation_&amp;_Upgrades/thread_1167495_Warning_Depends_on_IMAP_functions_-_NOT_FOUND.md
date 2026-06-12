---
title: "Warning: Depends on: IMAP functions - NOT FOUND"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by &#27969;&#27801;&#26539; on 2009-05-22
**Postfix Admin Setup Checker**
 
 

Running software: 
[LIST]
[*]PHP version 5.2.4-2ubuntu5.6
[*]Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch
[/LIST]Checking for dependencies: 
[LIST]
[*]**Warning: Magic Quotes: ON (internal workaround used)**
[*]Depends on: presence config.inc.php - OK
[*]Checking $CONF['configured'] - OK
[*]Depends on: MySQL 3.23, 4.0 - OK
[*]Depends on: MySQL 4.1 - OK (change the database_type to 'mysqli' in config.inc.php!!)
[*]Testing database connection - OK - mysql://postfix:xxxxx@localhost/postfix
[*]Depends on: session - OK
[*]Depends on: pcre - OK
[*]Depends on: multibyte string - OK
[*]**Warning: Depends on: IMAP functions - NOT FOUND**
To install IMAP support, install php5-imap
Without IMAP support, you won't be able to create subfolders when creating mailboxes.
[/LIST]...............
I had already installed it.:-k

---

### Post by &#27969;&#27801;&#26539; on 2009-05-23
nobody...
&#65293;_&#65293;&#65281;&#65281;

---

### Post by adrian.h on 2009-11-12
I'm having the same problem.  Have you found the solution?


Adrian

---

### Post by adrian.h on 2009-11-12
Ahh, well, hmmm.  Had a Magic Quotes warning, so I found the php.ini file and turned it off ( /etc/php5/apache2/php.ini ), when the warning didn't go away, I restarted the apache server, and poof, no warnings.  Strange thing is it didn't have anything to do with the Magic Quotes as I turned them back on and it still found the php-imap module.  Odd.

So it would seem that the problem was that the apache server needed to be restarted after installing the php5-imap component.

Woo-hoo! only took me a 5 hours to figure that out! :(


Adrian

---

