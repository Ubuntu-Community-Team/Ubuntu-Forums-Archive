---
title: "Strange websites in Firefox"
date: 2005-11-10
forum: General Help
---

### Post by victorche on 2005-11-10
When I type "google.com" in my browser I get this:
[ATTACH]3470[/ATTACH]
And if I try to open [http://slackware.com/](http://slackware.com/) I am getting a Bulgarian dating site for singles :???:
Well I am from Bulgaria, but I don't need a girlfriend /I have one ;)/...
So any ideas?

---

### Post by daditlefsen on 2005-11-10
Try to diable Apache.. Seems something is wrong whit it. :)

---

### Post by victorche on 2005-11-10
[QUOTE=daditlefsen]Try to diable Apache.. Seems something is wrong whit it. :)[/QUOTE]
It is a Kubuntu, man :)
There isn't even Apache installed ;)
See here:
[ATTACH]3471[/ATTACH]

---

### Post by Third Thoughts on 2005-11-10
check the output of your /etc/hosts files. You can use the file to do all sorts of tricks with DNS. As I test I set up mine so the first line looks like this ```
64.233.187.104  www.yahoo.com

```

This tells firefox to go to the IP address 64.233.187.104 when I type yahoo.com. The trick is that 64.233.187.104 is Google's IP. I type in [www.yahoo.com](www.yahoo.com) and lo and behold, up comes googles page. Its a great way to prank friends if you want to :) . Maybe someone tried to prank you. See if there are any weird entries involving the websites you are getting redirected too.

~Andrew S.

---

### Post by teaker1s on 2005-11-10
I remember someone having weird issue like this and they thought their browser was hacked-turned out that the launch command had an odd character/root issue

---

### Post by Third Thoughts on 2005-11-10
[QUOTE=teaker1s]I remember someone having weird issue like this and they thought their browser was hacked-turned out that the launch command had an odd character/root issue[/QUOTE]

Was it this thread you were talking about? [http://www.ubuntuforums.org/showthread.php?t=87637&highlight=gdesklets+firefox](http://www.ubuntuforums.org/showthread.php?t=87637&highlight=gdesklets+firefox)
From what I understand that would only affect firefox's starting up, but it sounds like this guy is having trouble with browsing as well.

~Andrew S.

---

### Post by ssam on 2005-11-10
maybe your dns server is giving bad results (isp hacked?)

can you try pointing your browser to

[http://216.239.57.99/](http://216.239.57.99/)

---

### Post by victorche on 2005-11-10
Well I have no idea how this happened... But it is Ok... For now :???:

---

### Post by heftigrat on 2005-11-10
[FONT="Courier New"][COLOR="Navy"]Victorche, sorry to hear you're having trouble.  I hate seemingly inexplicable errs like that.  However, this does sound DNS-related as posters like ssam noted.  If the issue starts to happen again, do a host lookup on the trouble hostname, do a whois on the IP, and see if anything refers to Google Inc.  My results were (edited):

[COLOR="Blue"]$ host www.google.com
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 64.233.167.104
www.l.google.com has address 64.233.167.147
www.l.google.com has address 64.233.167.99

$ host google.com
google.com has address 64.233.187.99
google.com has address 72.14.207.99[/COLOR]

64.233.187.99 seemed to be a recurring theme for both host lookups, so the whois lookup is:

[COLOR="Blue"]$ whois 64.233.187.99

OrgName:    Google Inc.
OrgID:      GOGL
Address:    1600 Amphitheatre Parkway
City:       Mountain View
StateProv:  CA
PostalCode: 94043
Country:    US

NetRange:   64.233.160.0 - 64.233.191.255
CIDR:       64.233.160.0/19
NetName:    GOOGLE
NetHandle:  NET-64-233-160-0-1
Parent:     NET-64-0-0-0-0
NetType:    Direct Allocation
NameServer: NS1.GOOGLE.COM
NameServer: NS2.GOOGLE.COM
Comment:
RegDate:    2003-08-18
Updated:    2004-03-05
...
[/COLOR]

...and so forth.  If you get some garbage then there may be a DNS propogation issue with the root servers, or the webternet just got temporarily fuxored in general.  I could be wrong, just an idea.  Good luck![/COLOR][/FONT]

---

