---
title: "Empty Dialog Boxes at random with Java and 8.04"
date: 2008-10-31
forum: General Help
---

### Post by carbatrol on 2008-10-31
I have been having a problem with a site I use that runs Java.  I have seen similar problems described in the archives under Java and have checked the location of the links and followed instruction re: -- set, but these do not seem to have worked.  I am running 8.04, this happens with Firefox 3.0 and 2.0, and I am using sun-java-6.  Any suggestions on what I can do to get rid of this problem once and for all.

Thanks for your help.

---

### Post by jamesstansell on 2008-11-02
What site(s) are you having problems with?

The icedtea-gcjwebplugin in 8.04 didn't have support for the javascript liveconnect which was the source of a lot of similar problems.

In your case it sounds like you're pretty sure that you have the sun-java6-plugin installed and enabled.  Does [http://browserspy.dk/java.php](http://browserspy.dk/java.php) confirm that?

If so, do you have visual effects enabled?  Can you try disabling them to see if it works for you?

---

