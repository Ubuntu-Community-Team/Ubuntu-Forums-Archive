---
title: "kopete or pidgin cannot log to yahoo messenger"
date: 2008-11-24
forum: General Help
---

### Post by simion314 on 2008-11-24
Hi i am using kubuntu 8.10.  I do not know why but i cannot connect to yahoo messenger using pidgion nr kopete. I do not recive any error from pidgin and from kopete i recive something with "Faield to lockup user myuser" but i do not recive this message all the time. I can connect from  my vortuual machine that runs XP . I have the same problem wuth kopete in arch linux (so not my ubuntu is the problem). Any ideea how to fix or how to trouble shout this problem? Thx.

FPXED : [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=994784](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=994784)

---

### Post by fishbulb1022 on 2008-11-24
the only thing I can think it would be is that when you create the account in pidgin, and it asks for your screen name, don't put the @yahoo.com at the end of your email address. I just set up pidgin on my computer and the hotmail one took the full email address, but yahoo only wanted the first half.

---

### Post by simion314 on 2008-11-24
> **fishbulb1022 said:**
> the only thing I can think it would be is that when you create the account in pidgin, and it asks for your screen name, don't put the @yahoo.com at the end of your email address. I just set up pidgin on my computer and the hotmail one took the full email address, but yahoo only wanted the first half.

That is not the problem, the accounts are set correct in both application and sometimes them work ok and sometimes they do not. Now in kopete the status of the account is connecting... , no error no nothing, it just waits. I thought that this could be from not properly closing yahoo messenger in windows or from my connection but is not that. I restart my network connection and Sign out from YM in windows before shut down but the problem is still there. The only solution is to run the virtual machine but i realy do not like this solutuion.
My gmail account works greath.

---

### Post by ciuci on 2008-12-01
i have the same problem, and i'm absolutely sure i filled in everything correctly... maybe yahoo are trying not to let other people use their protocol with other clients but their own or something ??!? i hope i'm being paranoid and that this is not the problem... :( meanwhile, simion314, you could log in to your yahoo account from [www.meebo.com](www.meebo.com) or from yahoo's own web messenger! that's what i'm doing, and even though having a browser running instead of an IM client is not convenient, it sure beats the hell out of running another operating system in a virtual machine just for an IM client :)

---

### Post by simion314 on 2008-12-02
> **ciuci said:**
> i have the same problem, and i'm absolutely sure i filled in everything correctly... maybe yahoo are trying not to let other people use their protocol with other clients but their own or something ??!? i hope i'm being paranoid and that this is not the problem... :( meanwhile, simion314, you could log in to your yahoo account from [www.meebo.com](www.meebo.com) or from yahoo's own web messenger! that's what i'm doing, and even though having a browser running instead of an IM client is not convenient, it sure beats the hell out of running another operating system in a virtual machine just for an IM client :)

Hi, if you do not found a solution read here 
[http://ubuntuforums.org/showthread.php?p=6267682#post6267682](http://ubuntuforums.org/showthread.php?p=6267682#post6267682)

i have some disconection-reconection but that is not a problem

---

### Post by Sigra on 2008-12-21
> **simion314 said:**
> Hi i am using kubuntu 8.10.  I do not know why but i cannot connect to yahoo messenger using pidgion nr kopete. I do not recive any error from pidgin and from kopete i recive something with "Faield to lockup user myuser" but i do not recive this message all the time. I can connect from  my vortuual machine that runs XP . I have the same problem wuth kopete in arch linux (so not my ubuntu is the problem). Any ideea how to fix or how to trouble shout this problem? Thx.

YES, Something is wrong.  Me and along with about dozen others that I meet are not able login to yahoo with pidgin or kopete on 8.10.  8.04, fedora 10, fedora 8, debain, suse,  and list goes on.  we tried alot distro's and same problem on all.  Pidgin u keep clicking log on no error.  kopete you get error back..so u spam it til you finally log in.  Diffently something wrong or that has changed somewhere.  we been logging into and chatting with yahoo on linux for years without a problem.  and this problem has been going on for few months now.

this is error you recieve from kopete as do others

there was an error while connecting (user name) to the yahoo server. :error message 1  Name lookup has failed

read this post ...confirms my thinking its on yahoo part [http://www.nabble.com/-Bug-45932--kdenetwork4,-NEW:-Kopete-fails-to-connect-to-Yahoo-IM,-reports-DNS-error.-(May-be-a-DNS-problem,-not-Kopete.)-td20644607.html](http://www.nabble.com/-Bug-45932--kdenetwork4,-NEW:-Kopete-fails-to-connect-to-Yahoo-IM,-reports-DNS-error.-(May-be-a-DNS-problem,-not-Kopete.)-td20644607.html)

---

### Post by simion314 on 2008-12-23
> **Sigra said:**
> YES, Something is wrong.  Me and along with about dozen others that I meet are not able login to yahoo with pidgin or kopete on 8.10.  8.04, fedora 10, fedora 8, debain, suse,  and list goes on.  we tried alot distro's and same problem on all.  Pidgin u keep clicking log on no error.  kopete you get error back..so u spam it til you finally log in.  Diffently something wrong or that has changed somewhere.  we been logging into and chatting with yahoo on linux for years without a problem.  and this problem has been going on for few months now.

this is error you recieve from kopete as do others

there was an error while connecting (user name) to the yahoo server. :error message 1  Name lookup has failed

read this post ...confirms my thinking its on yahoo part [http://www.nabble.com/-Bug-45932--kdenetwork4,-NEW:-Kopete-fails-to-connect-to-Yahoo-IM,-reports-DNS-error.-(May-be-a-DNS-problem,-not-Kopete.)-td20644607.html](http://www.nabble.com/-Bug-45932--kdenetwork4,-NEW:-Kopete-fails-to-connect-to-Yahoo-IM,-reports-DNS-error.-(May-be-a-DNS-problem,-not-Kopete.)-td20644607.html)

Hi, i got a FIX for my problem 

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=994784](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=994784)

---

