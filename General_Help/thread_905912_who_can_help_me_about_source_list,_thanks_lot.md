---
title: "who can help me about source list, thanks lot"
date: 2008-08-30
forum: General Help
---

### Post by shewenhao on 2008-08-30
I installed the kde to make a trial. Then I removed everything in terminal back to the Ubuntu:)

BUT......when I try to use the add/remove function I got some infor telling me that I have problem caused by sourcelist.... 

This is the information I got:

This is a major failure of your software management system. Please check for broken packages with synaptic. Check the file permissions and correctness of the file /etc/apt/sources.list and reload the software information with sudo apt-get and sudo apt-get install -f

therefore, I go to the system>administration>software sources and I removed every third party software sources to avoid mistake then I close. It requires reload then there is the error information:

Error occured:
E: kio-umountwrapper: subprocess post-removal script returned error exit status 2

I do not know what is kio-umountwrapper but I think it is kind of KDE application??


may you guys tell me what is wrong with my software list and update system??,,,,

Thank you very much!

If you guys need further information , please feel free to tell me.

---

### Post by hansdown on 2008-08-30
Hi shewenhao.

In synaptic, you will see a list on the left that says "all, broken, etc".

click broken, then any packages that are broken will be listed.

---

### Post by Pro-reason on 2008-08-30
See [http://ubuntuforums.org/showthread.php?p=4786808](http://ubuntuforums.org/showthread.php?p=4786808) and [https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729](https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729).

---

### Post by shewenhao on 2008-08-30
thanks lot . fixed !~~~~

---

