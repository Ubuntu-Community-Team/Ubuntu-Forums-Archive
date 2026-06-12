---
title: "Fiesty repositories no longer working?"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2009-02-10
When I do a
```
sudo aptitude update
```
I get the following errors


Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.45 80]

Are these repo's no longer available? I know I am a little behind on the version of Ubuntu I am using but I have Mythtv installed and don't have the time to upgrade Ubuntu and redo all my Mythtv stuff as well. Thanks for any help anyone can provide.

---

### Post by SunnyRabbiera on 2009-02-10
I believe support for feisty has ended...
sorry.

---

### Post by dannyboy79 on 2009-02-10
thanks for the reply. I guess I'll have to upgrade one of these days. Which is the new LTS version of Ubuntu, are you aware? Is it IBEX or Intrepid or what. There are so many after Feisty, it's crazy when they release a new version about every 6 months.

---

### Post by avtolle on 2009-02-10
The current long-term support version is 8.04.2 (code name Hardy Heron).

---

### Post by UbuntuNerd on 2009-02-10
Intrepid Ibex 8.10 is the latest:
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
but Im sticking with Hardy only because is supported until 2011

---

### Post by martalli on 2009-02-10
I have several computers at this office still running feisty, in part because it was the last version of ubuntu to work well with ies4linux.  I know, I know, don give me a hard time about ies4linux, but we have a few sites that we must use here that will not work without ie.

Anyway, I did an upgrade just today and I didn get any 404 errors.  I thought that feisty would not reach end of life until 9.04 comes out...

I wonder if anyone has a way to get internet explorer working with a more recent version of ubuntu...

---

### Post by howefield on 2009-02-10
End of life for each version can be found here.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Ex-windows on 2009-02-17
> **SunnyRabbiera said:**
> I believe support for feisty has ended...
sorry.
Does this mean that i cant install  ANY programs from synaptic or add/remove.

---

### Post by mcduck on 2009-02-17
> **Ex-windows said:**
> Does this mean that i cant install  ANY programs from synaptic or add/remove.

Short answer is yes, that's what it means.

Long answer is that actually you can still install packages if you edit your sources.list to point to old-releases.ubuntu.com (which is where Ubuntu's repositories are moved when support for that release ends). But you won't get any more updates, not even security updates, so I'd really recommend upgrading to some supported version.

---

### Post by Ex-windows on 2009-02-27
> **mcduck said:**
> Short answer is yes, that's what it means.

Long answer is that actually you can still install packages if you edit your sources.list to point to old-releases.ubuntu.com (which is where Ubuntu's repositories are moved when support for that release ends). But you won't get any more updates, not even security updates, so I'd really recommend upgrading to some supported version. 


Thank you 4 the reply, 
Ill give that a try. Really like feisty and wanted to install some things. Hopefully I can get the url right lol. Thanks again n sorry 2 take so long

---

### Post by Ex-windows on 2009-03-02
Does any one know the url to these old repositories for Fiesty. Also while looking at my sources list I noticed 2 things, 1 was this url 
[http://archive.dogfood.launchpad.net/ubuntu/](http://archive.dogfood.launchpad.net/ubuntu/)
#2 was that in the updates section, the "Unsupported updates (fiesty backports) was checked and wont "uncheck" lol Does this mean that My Fiesty FAwn is now "Dogfood"???

---

