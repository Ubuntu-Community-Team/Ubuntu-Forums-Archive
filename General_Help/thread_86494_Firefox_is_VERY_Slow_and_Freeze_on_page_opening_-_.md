---
title: "Firefox is VERY Slow and Freeze on page opening - IPV6 Off - Firefox Tuned"
date: 2005-11-05
forum: General Help
---

### Post by MiddleBrooker on 2005-11-05
Hi,
I've made some searches into the forum and now I' writing this message to get some help in my Breezy AMD64 fresh install.
My problem is about Firefox that is very slow to open pages and always won't open completely the web pages.

I've red something about the IPV6 disabling so I've edited my /etc/modprobe.d/aliases --> alias net-pf-10 off .

Also I've changed the configuration of mozilla firefox with about:config and according to that I've red into the forum.

I've now attached a screenshot because when I open web pages, they won't load without a refresh via Enter on the address bar.

[IMG]http://img.photobucket.com/albums/v600/MiddleBrooker/Firefox_Slow.png[/IMG]

I hope that somebody can help me to fix this problem.

Thanks to all.

---

### Post by mustang on 2005-11-05
Do you know for sure you are only experiencing the problem on Ubuntu and furthermore, with firefox?

Have you tried other browsers (epiphany, Opera)? If you previously used Windows, is it just as slow?

If those two questions don't lead to anything, I'd recommend trying Firefox RC1:

[http://www.mozilla.org/projects/firefox/](http://www.mozilla.org/projects/firefox/)

---

### Post by nightfly on 2005-11-06
Are you using a proxy to browse the web ?

There is a chance that your network connection is slow for the whole system and not just Firefox. 

Try opening a Terminal window and type
```
wget http://www.ubuntu.com/include/ubuntu-5.10-nautilus.jpg
```

It should download a screenshot image in a few seconds. Please report the download rate you got here.

---

