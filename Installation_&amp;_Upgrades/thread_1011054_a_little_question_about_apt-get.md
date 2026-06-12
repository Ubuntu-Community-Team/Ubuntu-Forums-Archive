---
title: "a little question about apt-get"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by azzid on 2008-12-14
Today I figured would be a good day to try out [Mediatomb]("http://mediatomb.cc/") as a media supplier to my PS3. I connected to my Ubuntu server and tried to find mediatomb in my repositories with **apt-cache search mediatomb** Found nothing, so I figured I lacked some repo. Found some info on the mediatomb site [http://mediatomb.cc/pages/download#debian_ubuntu]("http://mediatomb.cc/pages/download#debian_ubuntu") on where apt-get should look for the software.

That was when I realized that the lines in sources.list are tied to a particular distribution. In my case it is **dapper**.

I also found a line added ages ago to make apt-get "webmin aware" which is intended for **sarge**.
Webmin has always worked/updated perfectly even though the source is tagged **sarge**.

Now to my problem, there is no dapper source for mediatomb, can I use another? Like feisty, gutsy or hardy? If so, which is better, hardy (newest) or feisty (closest to dapper)?

I tried adding the line: **deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) gutsy main** to my sources.list, and after doing **apt-get update** I could **apt-cache search mediatomb** and find what I wanted.

How safe/unsafe will it be to actually try the install?

Could one even change all the dappers in the sources.list to say hardy and use apt-get to update to that distribution?

Sincerely,
Mattias

---

### Post by bapoumba on 2008-12-15
Mediatomb has been in the universe repos since Hardy.
Dapper is not supported any longer. Any reason not to upgrade?

---

### Post by azzid on 2008-12-16
Well, the only reason not to upgrade is that the actual upgrade is everything but painless.

I tried running do-release-upgrade on a virtual copy I made of the machine, it asked me a million questions and upon reboot services like dhcp had stopped working.

Also, from what I can understan dapper is LTS and since my install is of the server version it should still be supported.

[https://wiki.ubuntu.com/LTS]("https://wiki.ubuntu.com/LTS"):> With the Long Term Support (LTS) version you get three years support on the desktop, and five years on the server.

Since dapper was released on 01 June 2006 my interpretation is that it should be supported until 01 June 2011.

But I guess a reinstall is the clean thing to do...

---

### Post by frankleeee on 2008-12-16
edit

---

### Post by bapoumba on 2008-12-18
> **azzid said:**
> 
Since dapper was released on 01 June 2006 my interpretation is that it should be supported until 01 June 2011.

Yes, my mistake (I had been answering posts regarding Feisty at the time and got confused..).

I suppose it is now a choice of keeping Dapper, without the package you are looking for, or going to Hardy (clean install should work fine, even more so if you have a separate /home partition. Backups are a good idea too) which is also LTS.

---

