---
title: "installation problem...ubuntu 9.04"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by piyush.neo on 2009-10-09
UBUNTU 9.04 while trying to install JAVA i am getting this error message...every time...
i am using a proxy server..and had given these two commands..
$ export http_proxy="http//:gram:gram1508@172.31.100.29:3128"
$ sudo apt-get install sun-java6-jre

[B]Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") jaunty-updates/multiverse sun-java6-bin 6-16-0ubuntu1.9.04
  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...1.9.04_all.deb]("http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-16-0ubuntu1.9.04_all.deb")  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/....9.04_i386.deb]("http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb")  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/B]

PLZ HELP...:confused:
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8076461")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8076461")

---

### Post by piyush.neo on 2009-10-09
plz be specific,what steps should i follow...i am new to ubuntu...
THANKS:KS

---

### Post by 10Digits on 2009-10-10
ok maybe the server from India is not responding......


Change the server by.....


1) click on system =>Administration =>Software sources.

2)Then click on the drop down menu that says Server for India and choose "Other".

3)Then click on the choose best server button and wait for it to complete a test.

4) After the server is chosen go to administration through the system menu on the panel and choose synaptic package manager.

5) Click on the Reload button.Wait for it to update.

6)Try to install java again.

7) If it doesnt work try "Main Server" in software sources again.If the problem persists then it may be a problem with your connection or something that we are not aware of.


Hope this helps...:P

---

### Post by piyush.neo on 2009-10-10
thannks a lot.....:guitar:

---

### Post by 10Digits on 2009-10-10
Not a problem.... Happy to help

---

