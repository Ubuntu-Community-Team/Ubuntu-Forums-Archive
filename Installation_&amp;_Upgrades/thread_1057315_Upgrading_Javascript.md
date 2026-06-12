---
title: "Upgrading Javascript?"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by alias120 on 2009-02-01
Hi there, i am somewhat new to Ubuntu/Linux and i was having some troubles here. My current version of Javascript is 1.4, my university requires 1.5 or higher to view content on webpages. I have not been able to find how to update this at all, Updated java but javascript is still showing as 1.4.  Any help here would be greatly appreciated, cannot do and school work until i get this figured out. 

-alias

---

### Post by mikewhatever on 2009-02-01
I think there is a confusion between java and javascript terminology. Assuming you need java, version 1.5 or later, you should first install either sun-java6-jre or sun-java5-jre as well as the comparative Firefox plugin, then check out this page [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by peakshysteria on 2009-02-01
(Nice one mikewhatever).

Which OS are you running alias120? What Ubuntu version? 32 bit or 64 bit? Etc..

---

### Post by Partyboi2 on 2009-02-01
Open a terminal (Applications>Accessories>terminal) and install sun-java5-bin
```
sudo apt-get install sun-java5-bin
```
then after it has finished set java-1.5.0  to default.
```
sudo update-java-alternatives -s java-1.5.0-sun
```Or if you want java-1.6.0
```
sudo apt-get install sun-java6-bin
```
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by alias120 on 2009-02-01
I'm running Ubuntu 8.10, 32bit, and i needed javascript. I updated to sun-java6-jre but that did not affect the javascript version. I am wondering how to upgrade this. 

-alias

---

### Post by mikewhatever on 2009-02-01
> **alias120 said:**
> I'm running Ubuntu 8.10, 32bit, and i needed javascript. I updated to sun-java6-jre but that did not affect the javascript version. I am wondering how to upgrade this. 

-alias

Can you perhaps tell us how you check the version of javascript.

---

### Post by alias120 on 2009-02-01
Sorry about that, had to entertain some guests for the Super Bowl. Well first when i try to access the page that uses Javascript 1.5 or higher, it tells me that i need to upgrade my current version and the usual content i am able to access is not available. The d/l option it gives me just takes me to a 'Cannot find URL' page. When i check my browser, it tells me that i have version 1.4 installed. Sorry, i've been a windows user my whole life and Linux is pretty new to me. I appreciate any help you guys can offer though. 

-alias

---

### Post by bettlebrox on 2009-02-01
Java & JavaScript are 2 different things.

Are you trying to go a website that says you need JavaScript 1.4? If you are, what web browser and what version of that web browser are you using? And what webpage is causing this problem?

Can you give us the full error message?

If you are doing something else can you please clarify?

---

### Post by alias120 on 2009-02-01
Alright, i'll try to explain it as clearly as i can. I am using firefox 3.0.5 that came bundled with Ubuntu. I am trying to access Webtycho, a website used by University of Maryland University College for online classes. My current Javascript version is 1.4, Webtycho requires Javascript version 1.5 or higher. I cannot find a way to update javascript on here, more then likely due to my lack of knowledge with Linux. Anything else i can clarify just let me know, i really do appreciate your time with this.

-alias

---

### Post by alias120 on 2009-02-02
Alright, well from this posting here; [http://ubuntuforums.org/archive/index.php/t-220311.html](http://ubuntuforums.org/archive/index.php/t-220311.html)    I was able to get Firefox up and running, it's probably not the best way to do it but i can do school work now. Thanks for your help. 

-alias

---

### Post by mikewhatever on 2009-02-02
I'd like to clarify the solution for whoever may read thin in the future. Apparently, the problem lies with the user agent string of Firefox saying Ubuntu. It's not clear why make all the fuss about such a trifle, but that's the case. 
You can check your browser info here ->[https://tychousa6.umuc.edu/sys/browserinfo.html](https://tychousa6.umuc.edu/sys/browserinfo.html)

If you are having this problem, it says 'JavaScript Version 1.4 No' in line 8, and the problem is the word 'Ubuntu' in the user agent string, which is in line 11.
The easiest work around seems to be to edit the user agent string and remove the word 'Ubuntu' from it. Type about:config in the address bar, type general.useragent.vendor in the filter bar, right click on the general.useragent.vendor line, select Modify and delete the word Ubuntu.
Now, the JavaScript Version line should say 'JavaScript Version 1.5 Yes'

All the info was taken from the following bug report [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/156882](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/156882).

---

