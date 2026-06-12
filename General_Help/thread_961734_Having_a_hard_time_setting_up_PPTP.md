---
title: "Having a hard time setting up PPTP"
date: 2008-10-28
forum: General Help
---

### Post by xecure on 2008-10-28
I'm following these instructions here: [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

when i get to installing the pptpconfig my terminal gives me an error: ```
$ sudo apt-get install pptpconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pptpconfig: Depends: php-gtk-pcntl (>= 1.0.0) but it is not going to be installed
E: Broken packages

```

PPTP seems like the only way i can connect to my universities wifi

---

### Post by xecure on 2008-10-30
bump..

---

### Post by xecure on 2008-11-06
bump again
smeone please help

---

### Post by xecure on 2008-11-08
I have upgraded to ubuntu 8.10 and when the "Add" button under VPN is greayed out. How would i connect to a microsoft VPN on ubuntu 8.10?

---

### Post by Hangwire on 2008-11-08
Easy.
Again, download the PPTP package from somewhere in the interwebz.
Install it. Its a .deb

go to terminal, and i need your uni's internet settings or atleast something to explain it with. We dont want to steal information now, do we.

---

### Post by xecure on 2008-11-08
what is the name of the PPTP package? There are many PPTP packages on the 'interwebz'

---

### Post by xecure on 2008-11-11
I have installed 8.10 and tried to set up a VPN on that when I try to connect to the VPN it says it failed to connect because there are no valid VPN secrets. I have attached a small screen shot.

---

### Post by xecure on 2008-11-22
bump..

---

### Post by gabor111 on 2008-11-23
Hello xecure,

I thinkthat you have no answer because the solution is here:
[http://ubuntuforums.org/showthread.php?t=964255]("http://ubuntuforums.org/showthread.php?t=964255")

I began with the same error message,and now I can connect thanks to the above topic. A routing problem remains for me, but I hope this will help you.

---

