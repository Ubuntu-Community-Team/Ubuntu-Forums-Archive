---
title: "Have to use &quot;sudo firefox&quot; to run firefox"
date: 2008-09-18
forum: General Help
---

### Post by NuNn DaDdY on 2008-09-18
I was having an issue running my internet browser until i used 'sudo firefox' and found that it would then work when i did that.  How would I go about fixing this issue.  Thank you

---

### Post by -Zeus- on 2008-09-18
try running this:

```
sudo mv ~/.mozilla ~/mozilla
```

That will move your Mozilla preferences and settings, causing firefox to generate a new set, that should fix it.

---

### Post by madsmeg on 2008-09-18
Or try chmod 777 your firefox directory

---

### Post by NuNn DaDdY on 2008-09-18
Thanks for the help.  Why would this error occur though?  I have been trying to recompile the kernel, would this have caused the issue?

---

### Post by NuNn DaDdY on 2008-09-18
I tried the first solution but that didn't work and the same for the second solution also.  I am receiving this message:

(firefox:11607): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Teetdiro on 2008-09-18
bump the thread up.A bald man took a seat in a beauty shop. "How can I help you?" asked the stylist. "I went for a hair transplant," the guy explained, "but I couldn't stand the pain. If you can make my hair look like yours without causing me any discomfort, I'll pay you $5,000.""No problem," said the stylist, and he quickly shaved his head.------------The WOW gold Online Store, Open 24/7 Looking to buy [wow gold](http://www.u4game.com), Items or Accounts? You would find the cheapest gold here. We always online 24 hours a day, 7 days a week, any questions regarding [world of warcraft gold](http://www.u4game.com), powerleveling,wow leveling ,[warcraft gold](http://www.u4game.com), just talk to our representatives using our 24/7 live chat service.[world of warcraft gold](http://www.u4game.com/world-of-warcraft-gold.html),[wow leveling](http://www.u4game.com/Wow_Power_Leveling.html),

---

### Post by mb_webguy on 2008-09-18
You should really use gksu to run GUI apps with root privileges, and not sudo.  Read [this page]("http://www.psychocats.net/ubuntu/graphicalsudo") for more info.  

By using sudo with Firefox, you're running Firefox with root privileges, but using your configuration file.  Assuming Firefox runs as it should when you run it with sudo, you've probably inadvertently changed some of the permissions in the .mozilla folder.  Back up your bookmarks, then close Firefox and delete the .mozilla folder.  Then open Firefox normally, without using sudo.

---

### Post by NuNn DaDdY on 2008-09-18
I tried that solution but I am still having the same issues

---

### Post by rossjman1 on 2008-09-18
Did you download firefox from Mozilla or are you using the one in the repos?
Have you tried completely removing firefox, then installing it again?

---

### Post by NuNn DaDdY on 2008-09-18
how would i go about uninstalling and then getting it back through apt-get?

---

### Post by rossjman1 on 2008-09-18
sudo apt-get --purge remove firefox

---

### Post by NuNn DaDdY on 2008-09-18
i entered that into the command line and executed it.  However, the problem still remains and it seems that the original firefox is still here.  My theme and add-ons are still present unless they remain through uninstalla dn re-installation

---

### Post by mb_webguy on 2008-09-18
After you uninstall Firefox using the command posted by rossjman1, delete the .mozilla folder in your home directory.  Then reinstall Firefox.

---

### Post by NuNn DaDdY on 2008-09-18
I preformed that operation but still the issue exists.  I am starting to think that this isn't a firefox related issue.  I recently installed medibuntu and downloaded from their repositories and the problems started shortly after that.  But when I posted regarding this issue I was told that those downloads shouldn't have affected it.  However, I now also have troubl opening .swf files, playing video, and when I run the hardware tests for ubuntu, the video portion fails.

---

