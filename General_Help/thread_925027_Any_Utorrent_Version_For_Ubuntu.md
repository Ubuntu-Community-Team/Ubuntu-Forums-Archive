---
title: "Any Utorrent Version For Ubuntu?"
date: 2008-09-20
forum: General Help
---

### Post by zohaib on 2008-09-20
Hi there, I want to know that is there any utorrent version exist for ubuntu?
if there is then would You like to provide the link.

thanks

---

### Post by NoReflex on 2008-09-20
Hello!

You can run uTorrent through wine or you can try Deluge (I currently use it and I'm very pleased with it).

Best wishes,
NoReflex

---

### Post by mb_webguy on 2008-09-20
+1 for Deluge.

I loved uTorrent when I was using Windows, and even initially ran uTorrent under Wine for a while after I first made the move to Linux.  And uTorrent does run just fine under Wine.

But Deluge is very nice, especially the newest version available from the [Deluge website]("http://deluge-torrent.org/").  It doesn't have the coolness of uTorrent's tiny size, but it has a familiar enough interface that uTorrent fans will almost feel at home, and it has plenty of nice features, and a plugin system to eventually add even more features.  (At this point, the plugins are somewhat lacking, because the most recent version of Deluge is v1.0.0.rc9.  The final version 1.0 will user a different plugin system than previous versions, and the only plugin currently available is the blocklist.)

Deluge is sort of what uTorrent might be if it were a native Linux application, and since it's in active development, it's only getting better.

---

### Post by ^^rac on 2008-09-20
Any way to make Deluge connectable???

---

### Post by NoReflex on 2008-09-20
I guess by opening a port on your machine or forwarding a port in your router if you use one.

Best wishes,
NoReflex

---

### Post by mb_webguy on 2008-09-20
> **^^rac said:**
> Any way to make Deluge connectable???

You're going to have to expand on this a bit.  What do you mean by "connectable"?

Deluge shouldn't require any additional setup than what you did for uTorrent.  You'll need to set port forwarding (a.k.a. set a "virtual server") on your router, and appropriately set the ports used by the Deluge client.  (I believe the default is to use random ports, which you can't do through a router.)  As far as connectability, that should be it.

Also, while this doesn't directly pertain to your question...  You will almost certainly need to change your network settings in the Deluge preferences.  By default (in the new version from the Deluge website, at least), all network settings are set at unlimited.  You need to lower these to some more reasonable numbers to avoid overwhelming your router and hogging all of your bandwidth.

---

### Post by ^^rac on 2008-09-20
> **mb_webguy said:**
> You're going to have to expand on this a bit.  What do you mean by "connectable"?

Deluge shouldn't require any additional setup than what you did for uTorrent.  You'll need to set port forwarding (a.k.a. set a "virtual server") on your router, and appropriately set the ports used by the Deluge client.  (I believe the default is to use random ports, which you can't do through a router.)  As far as connectability, that should be it.

Also, while this doesn't directly pertain to your question...  You will almost certainly need to change your network settings in the Deluge preferences.  By default (in the new version from the Deluge website, at least), all network settings are set at unlimited.  You need to lower these to some more reasonable numbers to avoid overwhelming your router and hogging all of your bandwidth.


Thanks for the info!!
I will check it out!

I will try port forwarding, and see what happens!!

Cause i belong to a local torrent community, and according to their tracker, im not connectable for incoming connections....

In Utorrent i was....... Now im Running Utorrent in VMware :) And is connectable!

---

### Post by mb_webguy on 2008-09-20
> **^^rac said:**
> Thanks for the info!!
I will check it out!

I will try port forwarding, and see what happens!!

Cause i belong to a local torrent community, and according to their tracker, im not connectable for incoming connections....

In Utorrent i was....... No im Running Utorrent in VMware :)

uTorrent and Deluge use different default ports.  If you've already set up port forwarding on your router for uTorrent, you can just have Deluge use those same ports.

---

### Post by ^^rac on 2008-09-20
> **mb_webguy said:**
> uTorrent and Deluge use different default ports.  If you've already set up port forwarding on your router for uTorrent, you can just have Deluge use those same ports.

Strange thing....... i tried it!
Didnt work!

You know what, ill get the latest version of Deluge, and see if that works!!

Im not tooo bothered about that now, cause my Virtual Machine runs nicely :P

---

### Post by zohaib on 2008-09-20
Thanks For the response guys.,
I've downloaded delug n tried to install it but it shows an error.,
any solution for this or could  You please provide the link of delug which 100% works on ubuntu.,

I've installed wine but don't know how to use it., 
so I need some information about how to use wine.,

Thanks.

---

### Post by Sef on 2008-09-20
> Thanks For the response guys.,
I've downloaded delug n tried to install it but it shows an error.,
any solution for this or could  You please provide the link of delug which 100% works on ubuntu.,


Could you please post the error, so we can help you diagnose the problem.

---

### Post by zohaib on 2008-09-20
> **Sef said:**
> Could you please post the error, so we can help you diagnose the problem.

ok here is the problem
when i double click on the deluge for installation it says in red words "Error: dependency is not setisfiable: labboost-date-time 1.34.1"

thats the error

---

### Post by ashmew2 on 2008-09-29
you gotta open the terminal and type the command :
```

sudo apt-get install deluge-torrent
```

---

