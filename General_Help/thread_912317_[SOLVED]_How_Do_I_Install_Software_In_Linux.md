---
title: "[SOLVED] How Do I Install Software In Linux?"
date: 2008-09-06
forum: General Help
---

### Post by s1mp13m4n on 2008-09-06
Hello everyone.  I am new to Linux and so far I am enjoying it.  I have been able to find and use software that I installed using the Synaptic Package Manager, however some software I can not find in its list that I would like to install.
     I would like to install the Java Runtime Environment so I can play games from [www.pogo.com](www.pogo.com) and I am not sure how to do that.  Where can I learn in simple terms how to install software in Linux using the command line?  It took me a while to get Flash Player to install and honestly I am not sure how I did it.  LOL

---

### Post by wolfen69 on 2008-09-06
for java, go to synaptic and search for jre.(java runtime environment) make sure to install the web browser java plugin. make sure you have all repos enabled first. (system>administration>software sources) see [this]("http://www.psychocats.net/ubuntu/installingsoftware") for installing software in general.

---

### Post by aysiu on 2008-09-06
You may find this helpful also:
[http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)

---

### Post by mb_webguy on 2008-09-06
Most of the software you'll ever want or need to install is in the repositories, and Synaptic is by far the easiest way to install it.  You may need to enable some repositories if you can't find certain applications in Synaptic.  Open System->Administration->Software Sources, and make sure the first four boxes on the Ubuntu Software tab are checked.  If you haven't already, you may also want to add the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu"), which has some packages that can't be included in the main Ubuntu repositories for legal reasons (e.g. copyright, license, patent, etc.).

As other posters have mentioned, the JRE is in the repositories.  Just search for "jre" in Synaptic and look for sun-java6-jre.

---

### Post by s1mp13m4n on 2008-09-06
Got it working.  Thanks so much for all the help.

---

