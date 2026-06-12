---
title: "Secure Website Hangs in FF3"
date: 2008-07-31
forum: General Help
---

### Post by LindaLou on 2008-07-31
I have been experiencing some lengthy website "hangs" in FF3 for the past week.  It only happens on one particular site - voipdiscount.com.  I sign into my account from the main web page and and 9 times out of 10 it just hangs.  If it loads, and I click on any of the links on my personal page it hangs, and hangs, to the point where IF it does load the page, it has taken soooo long that my session is timed out.  I am using the latest version of Ubuntu.  At my office I have another Linux OS - Fenix - and it never gives me this problem.  In fact it is extremely quick.

---

### Post by tuxxy on 2008-07-31
What plugins have you installed for java

---

### Post by LindaLou on 2008-08-01
None, that I'm aware of.  I forgot to mention that the office PC came loaded with FF2 and has yet to be updated to FF3, if that factors into this equation.

Being a newbie I'll ask for your advice on the Java installs.  Thanks in advance

---

### Post by LindaLou on 2008-08-08
Is there any advice on this issue?  It is rather annoying for me with these secure websites.  Most of the time I work at accessing the web page for up to 15 minutes - some times with results but more often than not without.  Would appreciate any help with the issue.

---

### Post by tuxxy on 2008-08-08
You could try opera 

> sudo apt-get install opera*

or isntall the web plugins you need in firefox

[https://help.ubuntu.com/8.04/internet/C/web-browsing.html#web-plugins](https://help.ubuntu.com/8.04/internet/C/web-browsing.html#web-plugins)

---

### Post by LindaLou on 2008-08-08
hey tuxxy, I was just checking out the web link you sent and am wondering if you would know which Java plug in I would require


sun-java5-jre

or

sun-java5-plugin

Or any other plug ins that will assist with this issue.

I must admit, that when I was using Windows I had the luxury of an IT tech available nearly 7 days a week, so I didnt really bother with anything.  He was very well versed in Windows and his Linux knowledge is Red Fedora and one other that I cant remember.  So, I have jumped into this realm with both feet and counting on this great forum and all the helpful advice.  It really has been a very pleasant surprise to me, all the super friendliness and continual assistance from Ubuntu forum members!
Off the subject there!  Sorry!

Thanks for the suggestion of Opera by I have been using FF for years and switiching over 100% to Ubuntu is as far as I'm willing to go right now!  I'll certainly give it a look though a few months down the road when I'm more comfortable in Ubuntu.  I have read in several forums where people really enjoy Opera.

---

### Post by cariboo on 2008-08-08
The best way to install the java package that you need is to install the **ubuntu-restricted-extras** this will install java, flash and codecs needed to play most media. Search for this package in Add/Remove Programs, or Synaptic Package Manager.

Jim

---

### Post by LindaLou on 2008-08-08
Pardon my ignorance Jim, but I'm having a heck of a time finding anything related to Java in the Add/Remove Applications. What would you recommend I enter for the search here?

---

### Post by LindaLou on 2008-09-14
I posted this issue on Launchpad and after a month I received this information:  
"[COLOR="Navy"]be sure your system is fully upgraded, to check:
open a Terminal from the menu Applications->Accessories->Terminal and type:
[/COLOR]

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove

I was wondering if anyone would be able to validate these code lines for me.  My Ubuntu beans are too freshly picked to feel comfortable with the advice of others other than the Ubuntu forum, even launch pad is associated.I'm still having the same issue with the secure web site.

Thanks you for your anticipated reply.

---

