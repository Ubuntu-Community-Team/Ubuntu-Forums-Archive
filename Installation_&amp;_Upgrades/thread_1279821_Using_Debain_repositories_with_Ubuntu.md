---
title: "Using Debain repositories with Ubuntu"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by pcirne on 2009-10-01
Hi,

I'm using ubuntu server edition, is there any issue about adding a debian repository to the apt source.list?

Pedro

---

### Post by binary00mind on 2009-10-01
Yes there is an issue...Unless you know exactly what you are doing and looking for just one or two packages. 
But generally it is a no no. Sooner or later you will be wasting your own time fixing broken packages. 
Ubuntu is based on Debian but a lot of Debian packages were customized just for Ubuntu... 
If you are thinking of adding the Lenny's 5 DVD's. Just do not do it. 
I did try it myself on Xubuntu 9.04 and it was OK for a short while. 
Then I had my hands busy... 
It is up to you but if you run into the problem, who will help you?

---

### Post by pcirne on 2009-10-01
Hi,

Thank you for your reply.

I asked because I need Squid3.0-STABLE19 and the only repository I found with the binaries packages was the Debian repository.

Would it be safe to install squid3.0-STABLE19 from the Debian repository?

Thanks!

---

### Post by rreese6 on 2009-10-01
Debian does not update as often as Ubuntu. Also you might break your system.. I think that is about it. If you need a particular package that is not part of the  Ubuntu Repository, and the file is a .deb 
AND YOU CAN TRUST THE SOURCE (or you don't care if you system crashes )
then you can use dpkg to install the deb file
basically dpkg -i <name of package>.deb

Be very careful that the deb is built for your version of Ubuntu.

Since Linux wants you to be the Master, there are just tons of things you can do you totally mess up your system... :)

Hope this helps some.

---

### Post by binary00mind on 2009-10-01
Well use your own judgment. 
If you run into the trouble, do not look for help here. 
I believe it is a conflict of interests to help someone who added other repos. 
I am sure that a Moderator(s) can correct me on this one.

---

### Post by pcirne on 2009-10-01
I agree with you.

I've checked the karmic repo and the squid is 3.0-STABLE18, is there any issue if I add the karmic repo to the apt source.list on a jaunty server and install squid?

---

### Post by snowpine on 2009-10-01
Hi pcirne,
When you add a repository to your sources, you are basically saying "I want the package manager to trust and install all packages from this repository, now and forever."

What you really want (I think) is a one-time install of squid 3.0-stable18.

If you just want to install one package, don't add a repository... just find a .deb for that one package or compile it from source.

[http://www.squid-cache.org/Download/](http://www.squid-cache.org/Download/)

Or, if you want to use the Karmic version, don't add the Karmic repo! Simply download and install that one .deb package: [http://packages.ubuntu.com/karmic/squid3](http://packages.ubuntu.com/karmic/squid3)

In summary, don't add repos for Debian, Karmic, whatever... use only Ubuntu Jaunty repos unless you absolutely know what you're doing.

---

