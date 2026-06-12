---
title: "Can't access a couple of sites"
date: 2008-10-26
forum: General Help
---

### Post by feedmecereal on 2008-10-26
I have not been able to access digg.com for a few days now. Everytime I try to go to the site, Firefox just acts like it is trying to open the page but it never loads. I can access it fine using another Firefox profile on the same computer.

I'm also having a problem accessing my Capital One credit card website at [https://servicing.capitalone.com/c1/login.aspx]("https://servicing.capitalone.com/c1/login.aspx"). I get redirected to [https://servicing.capitalone.com/C1/SystemUnavailable.html]("https://servicing.capitalone.com/C1/SystemUnavailable.html"). I described this problem in the thread [http://ubuntuforums.org/showthread.php?t=952182]("http://ubuntuforums.org/showthread.php?t=952182"). I was able to fix it by clearing my cookies but then the problem shows up again the next day or after a few hours.

---

### Post by ghost_ryder35 on 2008-10-26
For the websites, I would check the firefox preferences and make sure that cookies are being accepted and you have not accidentily blocked the site.  As for being redirected for your credit card is fine, as there just passing you to another page, your not leaving their domain.  
Also, you might want to try Opera.  There browser is awesome!  I do not know if its in the repo's but its on their site package for Ubuntu!
[http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by feedmecereal on 2008-10-26
I've checked and I don't think I am blocking any cookies.

I don't see how being redirected for my credit card website is fine when I can't access the page. Remember that I can still access when using other browsers.

---

### Post by randomusername1000 on 2008-10-26
Hello there, have you tried clearing you're history ?

If worst comes to worst

"sudo apt-get install seamonkey"

Try giving an alternative browser a try although that should be you're last resort =].

~Jayson

---

### Post by ghost_ryder35 on 2008-10-26
> **feedmecereal said:**
> I've checked and I don't think I am blocking any cookies.

I don't see how being redirected for my credit card website is fine when I can't access the page. Remember that I can still access when using other browsers. 
OoO read that wrong.  I thought you could access the credit card site.  Delete your firefox profile and make a new one.  You could also try running "tcpdump" while accessing the sites that dont work and see if you are getting responses back from the servers, or if Firefox is dropping the connection!

---

### Post by feedmecereal on 2008-10-26
Deleting my history didn't do anything.

---

