---
title: "gnomad2"
date: 2008-09-01
forum: General Help
---

### Post by rdpsycho on 2008-09-01
hello
im trying to install gnomad2 and it is dependent on libmtp6, and i cant download it because its not in my repositories or something, however i have all repos enabled

> 
clinton@clinton-desktop:~$ sudo apt-get install libmtp6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmtp6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmtp6 has no installation candidate
clinton@clinton-desktop:~$ 


anyone else having this problem?? 

how do i install libmtp6?

---

### Post by rdpsycho on 2008-09-02
can anyone help me please???

---

### Post by baggins on 2008-09-02
sure that it's not libmtp7 you want?
From running 
```
jon@fort: (~)> apt-cache show libmtp7
```
I get the description (most of the output have been omitted, if you want the rest of the info run the above command)
```
Description: Media Transfer Protocol (MTP) library
 A library for communicating with MTP aware devices.  MTP (Media
 Transfer Protocol) is necessary to communicate with some USB portable
 devices like mp3 players, video players or digital camera.
 .
 While some portable device will use USB mass storage protocol or PTP
 (picture transfer protocol), some device can only communicate through
 MTP [ see http://en.wikipedia.org/wiki/Media_Transfer_Protocol ]
Homepage: http://libmtp.sourceforge.net/
```

-- Jon

---

### Post by rdpsycho on 2008-09-02
> **baggins said:**
> sure that it's not libmtp7 you want?
From running 
```
jon@fort: (~)> apt-cache show libmtp7
```
I get the description (most of the output have been omitted, if you want the rest of the info run the above command)
```
Description: Media Transfer Protocol (MTP) library
 A library for communicating with MTP aware devices.  MTP (Media
 Transfer Protocol) is necessary to communicate with some USB portable
 devices like mp3 players, video players or digital camera.
 .
 While some portable device will use USB mass storage protocol or PTP
 (picture transfer protocol), some device can only communicate through
 MTP [ see http://en.wikipedia.org/wiki/Media_Transfer_Protocol ]
Homepage: http://libmtp.sourceforge.net/
```

-- Jon
 i am trying to install gnomad2 from the sypnatic pkg mgr, and in there it says it wants libmtp6

---

### Post by baggins on 2008-09-02
> **rdpsycho said:**
> i am trying to install gnomad2 from the sypnatic pkg mgr, and in there it says it wants libmtp6

Are you sure? From the same command as before used on gnomad2 I get:
```
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7-1), libcairo2 (>= 1.4.0), 
libglib2.0-0 (>= 2.14.0), libgtk2.0-0 (>= 2.12.0), libid3tag0 (>= 0.15.1b), 
**[COLOR="Red"]libmtp7[/COLOR]**, libnjb5, libpango1.0-0 (>= 1.19.1), libusb-0.1-4 (>= 2:0.1.12),
zlib1g (>= 1:1.2.3.3.dfsg-1)
```
And as synaptics is "just" a front end for apt-get the dependencies will be the same.
Have you tried just installing via synaptic? Normally synaptic will then resolve dependencies on its own.

Note: libmtp7 in in the universe repositories so you need these enabled.

-- Jon

---

### Post by rdpsycho on 2008-09-02
libmtp7 is alrdy installed. sypnatic and the terminal both want libmtp6 when installing gnomad2

---

### Post by rdpsycho on 2008-09-02
nobody else has this problem? time to go back to windows.

---

### Post by rdpsycho on 2008-09-02
.

---

### Post by baggins on 2008-09-03
Hmm you are using Hardy right? (check output of: lsb_release -a)

If you are you might have a bum version of the gnomad2 deb package in cache. In that case you need to clean this, update repo list, try doing a fresh install. You do that like this (in a terminal):
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install gnomad2 libmtp7
```
If this doesn't work you might have something installed that confuses apt-get. In the past i have had some success doing a autoremove, if I had previously installed packages that was no longer needed:
```
sudo apt-get autoremove
```I don't actually think that removing the packages help, but apt might cleaup some internal data or something (otherwise my computer has leprechauns or ghosts or something :lolflag:) 

If you still have no luck, you might not have all the right repos enablet, post a message with attached /etc/apt/sources.list plus any files /etc/sources.list.d/ and I'll have a look

-- Jon

Edit: It's been 2 weeks since this post, I'm going to stop checkking back now. If you still have a problem, and desides to post again, dump a message to me.

---

