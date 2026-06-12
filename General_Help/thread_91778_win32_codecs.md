---
title: "win32 codecs"
date: 2005-11-18
forum: General Help
---

### Post by bfarris on 2005-11-18
I changed my sources.list file and then updated, and it tried to install a new versoion of win32codecs.  It failed, hanging at this point:


Setting up w32codecs (20050412+breezy0.0.1) ...
--00:06:56--  [http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip](http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip)
           => `windows-all-20050412.zip'
Resolving www1.mplayerhq.hu... 192.190.173.45
Connecting to www1.mplayerhq.hu|192.190.173.45|:80... connected.
HTTP request sent, awaiting response... 

I hit ctrl-c to cancel it and then changed my sources.list again, but now apt-get won't do anything because it first tries to finish installing the package and getting hung up.  Does anyone no how to make it stop trying?

thanks

---

### Post by matthewv on 2005-11-18
Why'd you stop it??

---

