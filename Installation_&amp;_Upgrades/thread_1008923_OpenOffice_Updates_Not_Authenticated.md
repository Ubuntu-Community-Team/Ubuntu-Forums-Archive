---
title: "OpenOffice Updates Not Authenticated"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by klausner on 2008-12-12
The Update Manager in Intrepid tells me I have 67 Open Office related upgrades to install. Unfortunately, they are all marked as "Not Authenticated". I've traced the source to the [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) repository. I assume I am missing a PGP/GPG key, but I can't find one listed anywhere for OpenOffice. Am I missing something simple?

---

### Post by frankleeee on 2008-12-12
3rd party downloads will show this, that is a good source, I have 3 computers running the OO3 downloads from PPA.

---

### Post by FiReSTaRT on 2008-12-12
It wouldn't even install the ooo3 updates for me.. I eneded up doing it through Synaptic.

---

### Post by klausner on 2008-12-12
> **frankleeee said:**
> 3rd party downloads will show this, that is a good source, I have 3 computers running the OO3 downloads from PPA.

At least some other 3rd parties do sign their files. Does this mean that OO specifically doesn't?

---

### Post by frankleeee on 2008-12-14
> **klausner said:**
> At least some other 3rd parties do sign their files. Does this mean that OO specifically doesn't?

I don't know the answer to that but your accessing a modified version of OO by another 3rd party launchpad. You must have put that launchpad url in your apt source list or clicked on install OO3 in Ubuntu tweak or somewhere else. You wouldn't have gotten this update unless you created a access point,

---

### Post by juanbretti on 2008-12-21
> **klausner said:**
> The Update Manager in Intrepid tells me I have 67 Open Office related upgrades to install. Unfortunately, they are all marked as "Not Authenticated". I've traced the source to the [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) repository. I assume I am missing a PGP/GPG key, but I can't find one listed anywhere for OpenOffice. Am I missing something simple?
So, did you got the **key** for OOo via launchpad?

Thanks!

---

### Post by klausner on 2008-12-21
> **pepemosca said:**
> So, did you got the **key** for OOo via launchpad?


No. Never did find one.

---

### Post by juanbretti on 2008-12-21
> **klausner said:**
> No. Never did find one.
I got it work by 
```
sudo aptitude dist-upgrade
```
and type "yes" when it came to OOo.

I'm sure there's a better way.

---

### Post by klausner on 2008-12-21
> **pepemosca said:**
> I got it work by 
```
sudo aptitude dist-upgrade
```
and type "yes" when it came to OOo.


There are a couple of ways to make it work (as always with Linux/Unix.) But the question was whether or not there is a public key that can be used to validate the updates. The lack of any responses seems to suggest that the answer to that is no, unfortunately.

---

### Post by juanbretti on 2008-12-21
I've tried to Google-it, but without any luck.

Strange.

---

### Post by AFarris01 on 2009-01-31
i know i'm a little late, but i just wanted to post that i was not able to find a pgp key for the OOo repository either. I'm assuming they dont have one.

---

### Post by juanbretti on 2009-01-31
> **AFarris01 said:**
> i know i'm a little late, but i just wanted to post that i was not able to find a pgp key for the OOo repository either. I'm assuming they dont have one.

I haven't found the PGP key.
I've just de-select the repository from the "Source" list.

Sorry, I don't have the solution :(

---

### Post by pleasecallmejames on 2009-02-02
The answer is on
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

I got the key from
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x60D11217247D1CFF](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x60D11217247D1CFF)
(note: I had to open port 11371 outbound on my firewall)

and imported it as per
[https://help.launchpad.net/Packaging/PPA#Adding%20the%20keys%20the%20easy%20way](https://help.launchpad.net/Packaging/PPA#Adding%20the%20keys%20the%20easy%20way)

---

### Post by juanbretti on 2009-02-02
Also, here is a solution to the problem:

[http://ubuntuforums.org/showthread.php?t=1055420](http://ubuntuforums.org/showthread.php?t=1055420)

---

### Post by klausner on 2009-02-02
> **pepemosca said:**
> Also, here is a solution to the problem:

[http://ubuntuforums.org/showthread.php?t=1055420](http://ubuntuforums.org/showthread.php?t=1055420)

The above is, unfortunately, a link to a link :(

The real solution that points to is [here]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")!

---

### Post by juanbretti on 2009-02-02
> **klausner said:**
> The above is, unfortunately, a link to a link :(

The real solution that points to is [here]("http://news.softpedia.com/news/How-T...10-96449.shtml")!
Hey, your link is not working.

BTW, my link will be to this post: [http://ubuntuforums.org/showpost.php?p=6649356&postcount=5](http://ubuntuforums.org/showpost.php?p=6649356&postcount=5)

---

### Post by klausner on 2009-02-02
[QUOTE=pepemosca;6664739]Hey, your link is not working.

Oops. My error. Fixed the [link]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml") in the previous.

---

### Post by juanbretti on 2009-02-02
> **klausner said:**
> [QUOTE=pepemosca;6664739]Hey, your link is not working.

Oops. My error. Fixed the [link]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml") in the previous.
Ok, but my recomendation is a different way to solve the PGP Keys problem.

---

### Post by forger on 2009-02-06
here's a script:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

Fixes the ppa links and adds the keys required!

---

### Post by cbtengr on 2009-02-06
The key can be found here:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Scroll down to this paragraph and follow instructions:


Right click HERE and "Save Link As..." the key file on your desktop. Go to the fourth tab, "Authentication", click the "Import Key File" button, navigate to the location were you've just saved the key file (File System/home/YOURUSERNAME/Desktop) and double click it. You will immediately see a new entry called "247D1CFF 2009-01-21 Launchpad PPA for OpenOffice.org Scribblers".

---

