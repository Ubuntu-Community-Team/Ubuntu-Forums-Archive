---
title: "Rsnapshot and the like"
date: 2008-11-11
forum: General Help
---

### Post by poorieuser on 2008-11-11
I recently moved to a sole installation of Ubuntu on my laptop. I like exploring and it gives me something to do when I'm bored at Uni. I am bringing my old desktop up in the following weekend with the intention of setting up a personal network using the Uni's wired internet access, their wireless is rather flakey to say the least. I'll be running windows on the desktop so I can use my old lexmark all in one. I plan on using Virtualbox to connect to the networked printer. I have been reading about it and it seems like my best option. But to my question. The desktop has about .8TB of storage and I'd like to setup a wireless backup sync between my laptop and a storage drive on the desktop. I am pretty new to networking between Linux and Windows. I would like to know if this is even possible. I understand that rsnapshot is the best method for remote back up and would like as much information as anyone can provide me.

tl;dr 

[Linux Laptop]  < backup w/>    [WindowsXP Desktop]????

---

### Post by m_l17 on 2008-11-11
I can't help you with Windows networking . But here is some info on rsnapshot:

[http://www.rsnapshot.org/]("http://www.rsnapshot.org/")

[http://www.rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html]("http://www.rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html")

[http://www.rsnapshot.org/rsnapshot.html]("http://www.rsnapshot.org/rsnapshot.html")

[http://troy.jdmz.net/rsnapshot/]("http://troy.jdmz.net/rsnapshot/")

I started using rsnapshot recently, from one hard drive to another. And it's working good for me. When I have the time I will setup rsnapshot through ssh, from laptop to desktop. They both run Linux it won't be to difficult.

You need to find a openssh-server for Windows to use ssh. Take a look at Cygwin:

[http://www.cygwin.com/]("http://www.cygwin.com/")

Hope this helps.

---

