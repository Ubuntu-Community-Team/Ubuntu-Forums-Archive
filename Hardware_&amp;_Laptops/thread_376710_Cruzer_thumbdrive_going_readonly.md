---
title: "Cruzer thumbdrive going readonly"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by snaga on 2007-03-05
have a strange problem....

I have been using a cruzer thumbdrive to carry around my php development project for several months. Its worked great.

A few weeks ago I started learning rails, and created a project for that on the same cruzer drive. Late last week, the drive suddenly would start reporting that it was readonly when trying to run my rails project. It was fine to write to before running the project and logging into it, but as soon as I ran the webserver and logged in, it would go readonly.

I thought the drive had gone bad, as I have used it alot in the past several months. So, I bought a new one, this time a 2 gig. Everything was great, until yesterday, when suddenly it started doing it again, on the new drive.

Anyone have thoughts on this? I'm baffled. It happens on 2 machines, both with Edgy on them. I use Eclipse for both php and rails development on the drive. Its a Cruzer 2 gig titanium.

updated:

I get this in the syslog:

```

Mar  5 09:49:26 localhost kernel: [18132046.752000] FAT: Filesystem panic (dev sdc1)
Mar  5 09:49:26 localhost kernel: [18132046.752000]     clusters badly computed (1531 != 1530)
Mar  5 09:49:26 localhost kernel: [18132046.752000]     File system has been set read-only

```

I'm going to try a reformat. Could this have been caused by an improper removal of the drive without unmounting?

---

### Post by qoheleth on 2007-03-05
this is a very common issue with usb drives and although I'm still a noob I know you have to do something with a umask command.  There are a lot of posts on this subject but i wanted to let you know it was not the drive.

---

