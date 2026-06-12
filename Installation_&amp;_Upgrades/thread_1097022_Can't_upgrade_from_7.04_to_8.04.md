---
title: "Can't upgrade from 7.04 to 8.04"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by HareBall on 2009-03-15
I am trying to upgrade from 7.04 and when I use the update manager, my only choice is to go to 7.10.
I have a copy of a live cd for 8.04 and when I boot with it it only shows my first drive(Windows). It will not show my second drive(Ubuntu), which is the one I want to install it on. They both show up when I check from inside Ubuntu 7.04.
I went through this link to try to upgrade and I don't get the same results that they show on this page. [http://www.ubuntu.com/getubuntu/upgrading-8.04](http://www.ubuntu.com/getubuntu/upgrading-8.04)

---

### Post by gjoellee on 2009-03-15
Ubuntu 7.04 is a normal version so you have to upgrade like this: 7.04 --> 7.10 --> 8.04

Or you can try something else...I have never tested it, it is not recommended, but worth a try in my opinion.

1. Put all the files and stuff you need on a USB stick or something
2. Use this command: ```
sudo gedit /etc/apt/sources.list

```
Now replace all "fiesty" with "hardy"
3. Now in terminal run this command:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by HareBall on 2009-03-15
Tried that and it never gets past file 87 and then it stops. It tries three times and then it gives an error. I have been trying to upgrade off and on for months.
I usually use WinXP, but like to use Ubuntu sometimes. Would rather use Ubuntu, but there are somethings that I can't do in Linux.

Tried to just upgrade before and now that I have seen what you are saying, I may try that.

---

### Post by HareBall on 2009-03-15
I have tried to upgrade by using the above command line,but nowI have it asking me "What would you like to do about smb.conf?"
I don't know what this is, so I sure don't know what I want to do with it.

---

### Post by HareBall on 2009-03-17
I finally got this took care of. I appreciate the one person that got me started, but it would have been nice to get an answer to my other question. Surely someone on this forum knows what to do about that.:(

---

### Post by sports fan Matt on 2009-03-17
Out of curiosity, how was the issue resolved?

---

### Post by Pumalite on 2009-03-17
> **HareBall said:**
> I have tried to upgrade by using the above command line,but nowI have it asking me "What would you like to do about smb.conf?"
I don't know what this is, so I sure don't know what I want to do with it.
Leave as it is.

---

