---
title: "Firefox 3.0.3 Javascript version detection problem"
date: 2008-09-27
forum: General Help
---

### Post by kalmite on 2008-09-27
After the upgrade to FF 3.0.3, my online university website doesn't recognize the proper JavaScript version.  The following site:

[http://tychousa.umuc.edu/sys/browserinfo.html](http://tychousa.umuc.edu/sys/browserinfo.html)

says the Ubuntu build of 3.0.3 uses JS 1.4 instead of the 1.5 reported from the mozilla.com build of 3.0.3.

Is anyone else experiencing this?  Why should FF which should be being built from the same source have two different results?  Anything that can be done other than using the build from the mozilla.com website?

---

### Post by itismike on 2008-10-02
> **kalmite said:**
> ...  Anything that can be done other than using the build from the mozilla.com website?
Seems to be outdated javascript on their browser detect.  I think [this post]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/156882/comments/3) solves the problem:
> [LIST=1][*]In the URL bar, type 'about:config' to get to Firefox's configuration preferences.
[*]In the filter bar, type 'general.useragent.vendor'
[*]Right-click 'general.useragent.vendor' and click modify
[*]Delete 'Ubuntu', leaving the line blank, and click OK
[/LIST]
Don't forget to close and open Firefox after making the change

---

### Post by MeBeMikeyC on 2008-10-19
I have been having the same problem, though clearing out "Ubuntu" in about:config didn't work for me.   The value keeps coming back.

This is what worked for me:

[LIST=1]
[*]Install "User Agent Switcher" add-on.
[*]Create a new user agent definition.  I called mine "Mozilla Fixed".  Use these settings:

[INDENT]Description:  Mozilla Fixed
UserAgent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 Firefox/3.0.3
App Name:  Firefox
App Version:  3.0.3
Platform:  Linux
Vendor:  Mozilla[/INDENT][/LIST]

---

