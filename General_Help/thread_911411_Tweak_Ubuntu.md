---
title: "Tweak Ubuntu"
date: 2008-09-05
forum: General Help
---

### Post by Windows_Apple_Linux on 2008-09-05
hey guys
I really like ubuntu and I even found a program called "Tweak Ubuntu" which allows me to tweak the OS but now I would like to hear from you guys, what could I do in order to boost up booting time and loading time?


also what could I do to keep the system running healthy? on windows I had CCleaner that helped me clean all the junk but how about ubuntu?
thank you

---

### Post by yjwong on 2008-09-05
For optimizing bootup and shutdown times, you can disable services that are not needed in System -> Administration -> Services. For example, if you do not need Bluetooth, you can disable "Bluetooth Device Management". Be careful not to disable "essential" system services such as "System communication bus". I believe that the Services applet would have warned you before that.

You can also improve login times via System -> Preferences -> Session. There, you can configure what programs will start when you log into your account. Try removing unneeded startup programs.

There are more advanced methods of improving login times, such as utilizing readahead (boot prefetcher), as detailed [here]("http://ubuntuforums.org/showthread.php?t=565651").

As for system maintainence, I myself don't find any need for "cleaning the junk" as Ubuntu clears the temporary folder (/tmp) on every restart.

---

### Post by Therion on 2008-09-05
> **Windows_Apple_Linux said:**
> also what could I do to keep the system running healthy? on windows I had CCleaner that helped me clean all the junk but how about ubuntu?
Install [QuickStart](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11). 

Be sure you actually READ the INSTALL INSTRUCTIONS.

---

### Post by Windows_Apple_Linux on 2008-09-05
thank you!
any others?

---

### Post by anotherdisciple on 2008-09-05
I did a boot profiling thing... It helps... check out jdong's post ...
[http://ubuntuforums.org/showthread.php?t=254263]("http://ubuntuforums.org/showthread.php?t=254263")

---

### Post by Windows_Apple_Linux on 2008-09-14
bump :]

---

