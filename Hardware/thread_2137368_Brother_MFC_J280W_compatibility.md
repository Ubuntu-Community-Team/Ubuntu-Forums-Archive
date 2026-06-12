---
title: "Brother MFC J280W compatibility"
date: 2013-04-20
forum: Hardware
---

### Post by user_linux on 2013-04-20
Hi,
I am trying to install this printer in ubuntu 12.04 LTS but I encounter the problem of driver downlaoding. I went to Brother's website and tried to install both LPR and cupswrapper driver but when I first install LPR driver it gives me a message of "The package is of Bad quality. The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath." Is there any easy way to install this printer?

Thanks a dozen.

---

### Post by uzumakifahim on 2013-04-20
Hope from this post you'll get good support.

[URL="http://ubuntuforums.org/showthread.php?t=2087489"]http://ubuntuforums.org/showthread.php?t=2087489

[/URL]Let us know, if you are successful about this printer on Ubuntu.

---

### Post by user_linux on 2013-04-20
but in this post it doesn't mention anythinga 'bout the message i am getting?

---

### Post by pdc on 2013-04-20
hi there linux user;

my tuppence happeny worth........

Brother provide an installer......that should automate the install for you.........

post #5 in this thread

[http://ubuntuforums.org/showthread.php?p=12342527#post12342527](http://ubuntuforums.org/showthread.php?p=12342527#post12342527)

gives a very detailed description of what mambo did to get it all working........can I suggest you try the Brother installer and see if it helps you?

he called it mambo801.sh but you could call it user_linux.sh as it is yours

---

### Post by kurt18947 on 2013-04-20
Brother offers an installer script which I've used with success.  Here are the instructions on Brother's site:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

I found downloading the script a bit unintuitive but once I figured it out it's worked okay.  One caution though.  I just used that script a couple days ago and it found a BUNCH of updates and asked me if I wanted to install them.  I declined then the Brother software installed as expected. The printer works fine.  After the printer software finished installing I reran "sudo apt-get update" then "sudo apt-get dist-upgrade".  There were not a great number of updates available.  I don't know what the Brother script found but heads-up on that.   I use gnome shell and the printer administration app sucks.  I don't know what Unity uses.  The old printer admin app is available in the repositories so I installed it from there.  The name is system-config-printer-gnome.  That app offers much more information and more options.  I created a desktop launcher to make my life simpler.

---

### Post by user_linux on 2013-04-21
Thanks a lot. I really appreciate the help!

---

