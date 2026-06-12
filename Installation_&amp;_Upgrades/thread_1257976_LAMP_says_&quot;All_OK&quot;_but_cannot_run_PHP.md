---
title: "LAMP says &quot;All OK&quot; but cannot run PHP"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by porphyrula on 2009-09-04
My apologies, I erroneously posted this problem first as a reply to an earlier thread.


I installed Apache,PHP,& MySQL on Jaunty and (I thought!) configured everything, but Firefox still gave me a "Save File?" dialog whenever I invoked a PHP file.  

After reading  [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) I installed the default lamp stack with sudo apt-get install lamp-server^. The output from this indicated that all packages are already installed and up-to-date. But I still can't run a PHP file.

Color me "Puzzled"

---

### Post by falconindy on 2009-09-04
You'll probably want to post your apache.conf file.

Also, silly question: you **are** trying to access the file via something similar to [http://localhost](http://localhost) and not file://path/to/php/file, right?

---

### Post by porphyrula on 2009-09-04
NOT a silly question at all!

I am just coming to ubuntu from the windows world, so it never occurred to me that the PHP interpreter would not be able to act on a file.

It works just fine if I reference it through localhost.  Just one of those things I'll have to get used to.

Thanks for setting me straight!

---

### Post by falconindy on 2009-09-04
Ahh, that's not so much an OS thing as it is just the way a webserver behaves. When you access a file using the file:// protocol, you're calling the file directly from the disk. You're asking your browser to display (or download if it doesn't understand) exactly the contents of that file.

However, if you access the same page via the http:// protocol, you're asking the server at the address you specify to provide you with the results of the page served at the address. In serving the page, it interprets any code (in this case PHP) and converts it to HTML for the end user.

Hope that makes sense. Glad I could help.

---

