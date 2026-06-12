---
title: "VPN conflicts with Installing Software in gDebi Package Installer and the Terminal"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by turboswede on 2009-02-16
During semester time, I am hooked up to my universities VPN. Due to a very helpful tech team (linux really wasn't their forte, but they really went a long way to help) I am connected to the internet fine, and they ensured the system proxy and synaptic package manager are set so they work. I havent had any trouble with synaptic.

I neither have a problem with gDebi when it is installing a complete package. I run into problems when the package requests further files to be installed. Then gdebi tries to download the additional packages, hangs, then displays this message:


Could not download all required files

Please check your internet connection or installation medium.

Details:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/m/ming/libming0_0.3.0-14_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/m/ming/libming0_0.3.0-14_i386.deb) Could not connect to gb.archive.ubuntu.com:80 (2a01:450:10:1::10), connection timed out [IP: 2a01:450:10:1::10 80]


That was for pencil animation tool, incidentally.

I haven't tried installing anything in the terminal recently, but I am sure the error message is pretty much  the same.

Do the terminal and gdebi not inherit the systems network proxy settings? I really don't know enough about them and vpn's to know what's at fault.

In the mean time, is there any way to get hold of pencil any other way? I notice it isnt in synaptic.

Many thanks. I have had alot of good advice from people on the forums on anything not regarding vpn, so I'm abit anxious about this request. Don't blame anyone obviously, I imagine vpn's are just some hellish thing no ones in their right mind would want to deal with.

---

### Post by turboswede on 2009-02-16
Out of curiosity, I clicked on the link in my above post and opened it in gdebi.

It states that I should:

You are recommended to install the software from the channel instead.


Is it possible to install pencil in these separate chunks? I'm a bit anxious about messing anything up, so I will leave it for now. Just thought it was interesting that when I open a package link in firefox (which is definately set to the system network proxy setting) gdebi then manages the file, yet it cannot when it calls for the link itself (a proxy problem?)

---

