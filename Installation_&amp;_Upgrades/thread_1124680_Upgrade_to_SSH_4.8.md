---
title: "Upgrade to SSH 4.8?"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by shairozan on 2009-04-13
Hello everyone, 

I've been reading through documentation on the forums for a while, and this is the first time I've ever actually had to post anything. 

Here's the deal. I have recently created a sftp server on ubuntu 8.04, but am now looking at chrooting or jailing the users into their current directories. I have heard that this is allowed in SSH 4.8, but the version I have in every ubuntu distro I have is 4.7 p1. 

Does anyone know how to upgrade it to 4.8 or install the infamous chroot patch I have heard about? 

Thanks
DJ

---

### Post by Aubergines on 2009-04-13
Intrepid uses version 5.1p1

---

### Post by shairozan on 2009-04-20
Yeah, I can see now that I have upgraded my Intrepid desktop (as well as tests with Jaunty) that they're using 5.1. Is there no way to upgrade 8.04 then?

---

### Post by shairozan on 2009-10-22
Just to let everyone know, I ended up re-building the sftp server with jaunty to deal with this. Issue solved, just took a little re-build :)

---

