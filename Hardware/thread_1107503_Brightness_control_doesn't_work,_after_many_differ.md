---
title: "Brightness control doesn't work, after many different attempts"
date: 2009-03-26
forum: Hardware
---

### Post by the_fury on 2009-03-26
[https://help.ubuntu.com/community/SonyVaioBrightness/](https://help.ubuntu.com/community/SonyVaioBrightness/)

The above is a documentation on how to adjust brightness for Sony VAIOs. However, there is no comment feature on there, so I thought I would bring it here, to UbuntuForums.org.

Problem 1: When I input 
```

sudo echo "sonypi" >> /etc/modules

```

It shows 
```

bash: /etc/modules: Permission denied

```

Somehow I don't think that's right.... Or at least it shouldn't be.

Problem 2: When I input
```

sudo apt-get install spicctrl

```

as the documentation instructs, I receive a
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package spicctrl

```

Which is ridiculous, because it's supposed to be in the universe repository. Anybody know where you can find a .deb version or something?

Thanks a lot, I appreciate any helpful responses.

---

### Post by the_fury on 2009-03-28
bump

---

### Post by binbash on 2009-03-28
sudo apt-cache search spicctrl
spicctrl - Sony Vaio controller program to set LCD backlight brightness

It is here : [http://archive.ubuntu.com/ubuntu/pool/universe/s/spicctrl/](http://archive.ubuntu.com/ubuntu/pool/universe/s/spicctrl/)

at universe repo

---

### Post by the_fury on 2009-03-28
> **binbash said:**
> sudo apt-cache search spicctrl
spicctrl - Sony Vaio controller program to set LCD backlight brightness

It is here : [http://archive.ubuntu.com/ubuntu/pool/universe/s/spicctrl/](http://archive.ubuntu.com/ubuntu/pool/universe/s/spicctrl/)

at universe repo

After I used that command, nothing happened and nothing changed.

.. I'm using a 64-bit version of Intrepid. Sorry, I probably should have clarified.

---

### Post by binbash on 2009-03-28
According to packages.ubuntu.com there is no 64 bit version of that package

You have searched for files named spicctrl in suite intrepid, all sections, and architecture(s) amd64.

Sorry, your search gave no results

[http://packages.ubuntu.com/intrepid/spicctrl](http://packages.ubuntu.com/intrepid/spicctrl)

There is only i386 and this is the download link for 386 : [http://packages.ubuntu.com/intrepid/i386/spicctrl/download](http://packages.ubuntu.com/intrepid/i386/spicctrl/download)

---

### Post by the_fury on 2009-03-28
> **binbash said:**
> According to packages.ubuntu.com there is no 64 bit version of that package

You have searched for files named spicctrl in suite intrepid, all sections, and architecture(s) amd64.

Sorry, your search gave no results

[http://packages.ubuntu.com/intrepid/spicctrl](http://packages.ubuntu.com/intrepid/spicctrl)

There is only i386 and this is the download link for 386 : [http://packages.ubuntu.com/intrepid/i386/spicctrl/download](http://packages.ubuntu.com/intrepid/i386/spicctrl/download)

Exactly but how should I install it? I'm using 64 bit... is there any way I can install 32 bit programs?

---

### Post by the_fury on 2009-03-30
bump?

---

### Post by the_fury on 2009-04-01
bump

---

### Post by Another Monkey on 2009-07-27
I have exactly the same issue - comments I have seen elsewhere say that the Ubuntu kernel support for Sony is a bit flakey and the solution is to compile your own.

I have **no** idea how to do that and I don't think I particularly want to get into it just now!

I also get "No such device" when I try to load "sonypi.ko"

Did you ever find a solution to your problems?

---

### Post by MagicMan1 on 2011-02-12
Anybody knows about how to make it work under 10.10 x64 ?

---

### Post by fmdex2011 on 2011-02-12
Take a look at this link

[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

I had the same problem on Ubuntu 10.10  amd64  and this worked for me

:)

---

### Post by rainwalker on 2011-04-20
I'm trying to help a friend get his brightness control working on his Vaio, and spicctrl won't install for me either. You can force a 32-bit package to install using
```
sudo dpkg -i --force-architecture package_name
```
However, while that makes it start the install, the process fails because spicctrl is dependent on libc6, version 2.7 or higher. I don't see why this is a problem, though, because the version he has installed is the 2.13 version in the Ubuntu repos. I really can't think of any reason why it won't work.
Natty Beta 2, FYI.

---

