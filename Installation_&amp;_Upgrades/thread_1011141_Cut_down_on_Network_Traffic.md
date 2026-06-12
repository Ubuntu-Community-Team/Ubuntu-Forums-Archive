---
title: "Cut down on Network Traffic"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by dwanders on 2008-12-14
I have managed to set up a small home network with three Ubuntu 8.10 computers and 1 Windows computer. I would like to have one Ubuntu computer go out to the Internet and get updates, and I would like for this one PC to be the ONLY repository for my other Ubuntu computers. (So basically - if I don't down load and install it on the main computer, they cannot). 

What's the best way for me to approach this and get it set up? I have never set up any repositories, and I certainly dont think I need a full repository for everything that could potentially be installed. 

Thanks in advance. ):P

---

### Post by dwanders on 2008-12-15
Wow - nobody - I would think this would be pretty common - huh. 

Thanks anyway to all who may have pondered.

---

### Post by dwanders on 2008-12-15
In case any one was interested, this might be my monkey:

[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)

It looks like a full repository, but I guess it will be my starting point!

---

### Post by dwanders on 2008-12-15
Actually this looks more like what I need!

[http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)

I will post if this works for me or not.

---

### Post by dwanders on 2008-12-16
It worked, but I do have a question and I think I have learned that software is no longer being supported by its developer. But if I have it understood correctly - the host computer that is running apt-cacher will go out to the internet repositories and get any package requested for by one of its clients (any of its clients) and then it will make this package available for any other computer that asks for it - thereby cutting down on requests to the Internet repositories. 
 
If this is correct, is there anyone out there that could verify that is the case?

Also - how do packages like security update that are not specifically requested get posted to the cacher?

Again thanks to any one that might respond. ):P

---

### Post by dwanders on 2008-12-18
Well based on my testing with the application, it appears that it does indeed only update after it has been asked to update. After which, it will download and install them on the requesting PC. And if any other PC's that are set up to get packages from the same cacher - it will already have the files downloaded and wont need to do it again. 

Working like a charm!

---

