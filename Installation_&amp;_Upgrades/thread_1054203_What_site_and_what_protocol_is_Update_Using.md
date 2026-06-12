---
title: "What site and what protocol is Update Using?"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by halgar on 2009-01-29
Hi,

I have a problem that is probably unrelated to Ubuntu, but it would help my debug efforts to know a couple of things about the Update Manager.

When I configure an Ubuntu 8.04 or 8.10, desktop or server in my lab which is on a switch behind a firewall as static IP.  Updates of the 200+ packages project they will take many days to complete at a few hundred bytes a second.

I see no problems in general with pinging or ftping in or out otherwise.

Specifically, what site(s) are being used and what protocol or ports are being used to download the packages? 

thanks very much,
halgar

---

### Post by cerealtx on 2009-01-29
ftp...port probably varies and if you hit details it will show where its getting what

---

### Post by jerome1232 on 2009-01-29
http

--edit-- is it ftp? I thought it was http lol.

The exact site will vary with what your sources.list is set to.

For example mines set to download from [http://us.archives.ubuntu.com](http://us.archives.ubuntu.com), You may be just download from a slow server, try going to system, software sources and switching do a different server.

---

### Post by halgar on 2009-01-29
Thanks,

That helps, I forgot to mention that when outside of the lab and DHCP, the Ubuntu updates work just fine.

halgar

---

### Post by cariboo on 2009-01-29
You could go to System-->Administration-->Software Sources and click the download from dropbox and select select other, next click the choose bes server button and let it check to find the fastest server, click choose server and see if that makes any difference.

Jim

---

### Post by halgar on 2009-01-29
Thanks Jim,

I did not know about that feature, very nice.  That improved the speed quite a bit.  The details show that it is using a URI that starts with [http://.](http://.)..  Is there an option to do ftp? assuming that would be better.

Also, on server installations without a GUI, the first thing I usually do is install gnome basic. This usually fails due to slow download. Is there a way to tell apt-get (or whatever linecommand) to hit a site that I find to be fast using the desktop GUI feature you mentioned?  I am assuming server and desktop update sites are the same.

thanks,
halgar

---

### Post by halgar on 2009-01-29
I see I can edit /etc/apt/sources.list to change the apt-get source.

---

