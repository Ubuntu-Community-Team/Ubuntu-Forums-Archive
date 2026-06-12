---
title: "Apache config lost after upgrade - hmmm :-]"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by gwilym on 2009-10-26
Ok - I have had Ubuntu running under Vmware on my XP pro laptop for over a year and been using it as my development webserver for PHP development.

Last week I upgraded to the latest Ubuntu version - and now my Apache which used to use a directory from my windows install (C:\Documents and Settings\Gwilym\My Documents\Workspace) is broken.

First steps is to fix my apache and then try and link it to the windows dir...

At the moment if I try and go to [http://localhost/index.html](http://localhost/index.html) or [http://127.0.0.1/index.html](http://127.0.0.1/index.html) from inside Ubuntu I get an Apache 404 error "Not Found". There is an index.html file at /var/www/index.html and the Apache 2 config files seem to be in order with the Document Root set to /var/www in sites_available/default ...

Any help appreciated - including telling me if I am in the wrong forum :-)

---

