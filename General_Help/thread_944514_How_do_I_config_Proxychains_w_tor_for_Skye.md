---
title: "How do I config Proxychains w/ tor for Skye?"
date: 2008-10-11
forum: General Help
---

### Post by cadaverousmob on 2008-10-11
I currently have tor & privoxy installed on Ubuntu Hardy and would like to configure ProxyChains to run applications such as Skype for anonymity and re-routing purposes. 
 
I can tor my browser (Firefox), pidgin IM, etc. with the following: 
 
HTTP Proxy: 127.0.0.1 port 8118 
SSL Proxy: 127.0.0.1 port 8118 
FTP Proxy: 127.0.0.1 port 8118 
Socks5 Proxy: 127.0.0.1 port 9050 
 
However, when I add the following entries (to /etc/proxychains.conf ): 
 
http 127.0.0.1 8118 
socks5 127.0.0.1 9050 
 
I get the error:  
abolishthefed@abolishthefed:~$ proxychains skype 
ProxyChains-2.1 ([http://proxychains.sf.net](http://proxychains.sf.net)) 
random chain (2):....127.0.0.1:9050....access denied to..127.0.0.1:9050 
random chain (2):....127.0.0.1:9050....access denied to..127.0.0.1:8118 
random chain (2):....127.0.0.1:9050....access denied to..127.0.0.1:8118 
random chain (2):....127.0.0.1:8118....access denied to..127.0.0.1:9050 
random chain (2):....127.0.0.1:9050....can't connect to..127.0.0.1:8118 
random chain (2):....127.0.0.1:9050....access denied to..127.0.0.1:9050 
 
I believe my entries in /etc/proxychains.conf are incorrect. Can someone tell me what I'm doing wrong or what I'm suppose to be pointing to? Many thanks in advance for your help. Have a nice day.

---

### Post by melvinxie on 2008-12-14
I'm running qq (an im software in China) behind proxychains.

I also got:

dynamic chain:....<proxy:port>....access denied to..127.0.0.1:52262

Any ideas?

But I can use proxychains to run other applications, such wget, successfully.

---

### Post by 7raTEYdCql on 2008-12-14
I think you will have to open skype using terminal.

Try this out
command1- unset http_proxy
command2- sudo proxychains skype


This used to work when i used the internet using proxychains, I hope it does for skype.

---

### Post by melvinxie on 2008-12-22
Still not working.

I don't know why it needs to access 127.0.0.1?

---

### Post by mgol on 2009-01-07
This is a problem also for me. I tried to use it with transmission, with no success.

---

### Post by Stoneface on 2010-08-10
Did anyone solve this problem? Very few threads and data on this. been trying to use proxychains with svn and Firefox with no luck so far.

---

### Post by linis_australis on 2012-04-03
This is a bit of an old thread, so my apologies. Wondering if anyone has made any headway here. I'm new to proxychains as of this evening, but have been playing with TOR, Privoxy and others for some time.  I've been using torify and ttdnsd for DNS, but proxychains seems like it could be a more universal tool for this -- e.g. setting the proxy in one place for many apps and having DNS automatically forwarded.

I notice there is a bug listed here: [http://us.generation-nt.com/answer/bug-593464-proxychains-doesnt-work-i386-binaries-amd64-platform-help-204871671.html]("http://us.generation-nt.com/answer/bug-593464-proxychains-doesnt-work-i386-binaries-amd64-platform-help-204871671.html")

This bug may actually be my problem as skype for debian is currently only a 32bit application and I'm running a 64bit kernel.

I've successfully used it for pidgin with my yahoo account, however for facebook and skype it fails (on pidgin) and with skype as skype it fails.

I know that facebook is very particular about wanting to KNOW where you are when you log in ( that damn CIA spying on us I figure!  :lolflag: ), facebook uses a third party company to ping you and give them a location based on ip address and if it doesn't match up to your regular location, they freak out.  Just try using facebook with TOR and you'll see what I mean.  So it could be that this is why I'm being rejected with pidgin facebook protocol/proxychains/TOR as well.

Comments, thoughts?

Cheers

---

### Post by howefield on 2012-04-03
Old thread closed.

Please start a new thread.

---

