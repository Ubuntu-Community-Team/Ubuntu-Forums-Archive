---
title: "Having some issues after upgrading from 9.04 to 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by jjessew on 2009-11-03
Hello all, 

I have been using 9.04 since it came out, and everything has been great!  So I upgraded... and now I'm having some issues.

I can connect to the internet with Firefox, but some other things seem unable to connect...  Update Manager and Google Earth are two examples.

How do I get update manager to connect to the network?
Are there some general guide lines that I should have followed when upgrading?
Do I need to uninstall all the software I had installed, and reinstall it?  How do you uninstall software like Google Earth or Hulu Desktop?

Thanks
-Jesse

---

### Post by wilee-nilee on 2009-11-03
Have you gone to synaptic and hit refresh, or in a terminal sudo apt-get update

---

### Post by jjessew on 2009-11-03
> **wilee-nilee said:**
> Have you gone to synaptic and hit refresh, or in a terminal sudo apt-get update
Thanks, that fixed my Update Manager.  

If anyone else can help me, I am still interested in knowing how to uninstall software packages that I have installed without using synaptic or the Add/Remove Programs...

Thanks
-Jesse

---

### Post by ManiacDan on 2009-11-03
You use "apt-get remove" 

Go to the command line and type either "man apt-get" or "apt-get --help"

-Dan

---

### Post by jjessew on 2009-11-03
To add to this, Dropbox cannot connect to the internet either.  It gives me some possible reasons for the error.  My internet connection is working so that is not the error, and the second choice it gives has to do with the http_proxy environment variable...  Is this something I need to set or check?  I'm having more and more issues with different applications not being able to connect to the internet.  Are there some new firewall setting in 9.10?

---

### Post by wilee-nilee on 2009-11-03
> **jjessew said:**
> Thanks, that fixed my Update Manager.  

If anyone else can help me, I am still interested in knowing how to uninstall software packages that I have installed without using synaptic or the Add/Remove Programs...

Thanks
-Jesse

You might want to list what you have installed and want to remove if it was installed with a deb and went to root it will be easier to get help. If it was a apt-get install as another poster suggested run sudo apt-get remove (package name) you can also run purge in the place of remove, just make sure it is not part of a meta package watch what the terminal says. Also even if not installed with add remove or synaptic generally they will be listed in synaptic under status local or obsolete.

---

### Post by jjessew on 2009-11-03
Thanks for your help, I now have my uninstall issues sorted out.

But my internet connection issues are still at large.  The network connection worked great before I upgraded, I had no issues.  

After upgrading, Firefox did not work at first.  I had to disable ipv6, and now it works.  is there someway I can set up a log to try and catch/figure out why my other apps cannot connect to the internet?

Thanks in advance,
-Jesse

---

### Post by wilee-nilee on 2009-11-04
> **jjessew said:**
> Thanks for your help, I now have my uninstall issues sorted out.

But my internet connection issues are still at large.  The network connection worked great before I upgraded, I had no issues.  

After upgrading, Firefox did not work at first.  I had to disable ipv6, and now it works.  is there someway I can set up a log to try and catch/figure out why my other apps cannot connect to the internet?

Thanks in advance,
-Jesse

You need to tell us what all the apps are.

---

