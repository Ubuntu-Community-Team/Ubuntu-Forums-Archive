---
title: "Local Development Server | Connect via hostname rather than IP"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by majickal on 2009-03-29
Hi All,

I had been having trouble connecting to my local development server via hostname for some time. I stumbled across a way to fix this problem the other day and thought i would share with you all.

*I will add a disclaimer to this before i proceed though. This workaround is not very elegant and i am sure there is a better way to do this, but this worked straight away for me. So, if you have a better solution to this problem without changing the client hosts file i would be keen to hear it.*

So the scenario was my local server was setup with the static ip: 192.168.0.199, i had named the box devserver when installing ubuntu server. I was able to connect to it via: [http://192.168.0.199](http://192.168.0.199) but not [http://devserver](http://devserver). I could not really figure out why though (I searched around for ages trying to work it out). Anyhow, i ended up installing samba for file sharing on a windows network and bingo, suddenly my hostname ([http://devserver](http://devserver)) worked. I am going to assume (rightly or wrongly) that this has something to do with registering hostnames for windows networking through the samba setup??? 

Now i can connect to my server via hostname as well as via ip.

If you have any questions or comments about this, please post them as i would like to learn more about the reasons this works.

I hope this helps someone out there who was struggling with the same problem.

best regards

majickal
:guitar:

---

### Post by dandnsmith on 2009-03-30
> **majickal said:**
> 
So the scenario was my local server was setup with the static ip: 192.168.0.199, i had named the box devserver when installing ubuntu server. I was able to connect to it via: [http://192.168.0.199](http://192.168.0.199) but not [http://devserver](http://devserver). I could not really figure out why though (I searched around for ages trying to work it out). Anyhow, i ended up installing samba for file sharing on a windows network and bingo, suddenly my hostname ([http://devserver](http://devserver)) worked. I am going to assume (rightly or wrongly) that this has something to do with registering hostnames for windows networking through the samba setup??? 


Where were you trying to connect from?
Was that SAMBA install on devserver?

It sounds as though the nameserver lookup wasn't operating at first, and the install of SAMBA may have fixed it for you - but without detail of the steps you took to configure SAMBA, guesses are no more than that.

There are files which can control name translate order, can contain lists of names and IP addresses, and SAMBA can have its own list of names for machines.

---

