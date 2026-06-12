---
title: "understanding long term support and security updates"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by ralic on 2009-05-23
Dear readers

Could someone please help me understand how long term support security updates work?

I have installed an ubuntu 8.04 server some time back and updated it regularly. It is now at 8.04.2 and is up to date according to 'aptitude safe-upgrade'.

Some months back, I have installed the squirrelmail package from the repositories.

Today I visited the squirrelmail homepage and see that there have been some security fixes. The latest version according to squirrelmail is v1.4.19

When I look at the package versions through packages.ubuntu.com  I find that the package versions are:
```
hardy: 1.4.13-2ubuntu1.2
hardy-updates: 1.4.13-2ubuntu1.2
intrepid: 1.4.15-3ubuntu0.1
intrepid-updates: 1.4.15-3ubuntu0.1
jaunty: 1.4.15-4
karmic: 1.4.18-1
```

I'm now trying to understand why the LTS version is 5 update revisions behind the latest ubuntu version and 6 updates behind the source.

Please don't mistake this question as a criticism. I'm just trying to establish why this is, and whether or not I should ditch the ubuntu managed version (through aptitude) and just install the software from source and maintain it myself manually.

Maintaining the software manually brings into question the need for LTS. Or perhaps I'm missing something?

Appreciate your insights.

---

### Post by kiridude on 2009-05-23
+1

I find several programs in synaptic or through apt or aptitude are significantly old. Many times I have to download the updated versions manually. 

I am also curious as to why.

---

### Post by whoop on 2009-05-23
Ubuntu isn't a free rolling distribution. If you update a version of Ubuntu that isn't EOL (End Of Life) you are not necessaryly getting the latest version of each package. You are getting packages with fixed (security) flaws.

---

### Post by cariboo on 2009-05-23
Every release uses the packages that are available at the time of of the Beta freeze. There won't be newer versions installed, unless they show up in the backports repositories.

If you are concerned about the security updates checkout the change logs to see what updates have been aaplied. you can use apt-listchanges. 

Apt-listchanges is in the repositories.

---

### Post by ralic on 2009-05-23
> **whoop said:**
> If you update a version of Ubuntu that isn't EOL (End Of Life) you are not necessaryly getting the latest version of each package. You are getting packages with fixed (security) flaws.
I understand that this is how it *should* be, but my question relates to why this isn't so.

Using my earlier example of squirrelmail, the squirrelmail [security page]("http://squirrelmail.org/security/") lists two security updates (CVE-2008-3663 & CVE-2008-2379) that affect versions up to v1.4.15 and v1.4.16 respectively, yet the LTS version is still pegged at v1.4.13

There are 6 other CVE id's related to security fixes, however these were attended to in the last month, so it's reasonably understandable as to why these may not yet be included.

---

### Post by kostkon on 2009-05-23
> **ralic said:**
> Dear readers

Could someone please help me understand how long term support security updates work?

I have installed an ubuntu 8.04 server some time back and updated it regularly. It is now at 8.04.2 and is up to date according to 'aptitude safe-upgrade'.

Some months back, I have installed the squirrelmail package from the repositories.

Today I visited the squirrelmail homepage and see that there have been some security fixes. The latest version according to squirrelmail is v1.4.19

When I look at the package versions through packages.ubuntu.com  I find that the package versions are:
```
hardy: 1.4.13-2ubuntu1.2
hardy-updates: 1.4.13-2ubuntu1.2
intrepid: 1.4.15-3ubuntu0.1
intrepid-updates: 1.4.15-3ubuntu0.1
jaunty: 1.4.15-4
karmic: 1.4.18-1
```

I'm now trying to understand why the LTS version is 5 update revisions behind the latest ubuntu version and 6 updates behind the source.

Please don't mistake this question as a criticism. I'm just trying to establish why this is, and whether or not I should ditch the ubuntu managed version (through aptitude) and just install the software from source and maintain it myself manually.

Maintaining the software manually brings into question the need for LTS. Or perhaps I'm missing something?

Appreciate your insights.
Don't look the version numbers in this case, in the case of security updates that is. The packages are patched against any new vulnerabilities, even if they are much older that the current upstream version.

The packages are old, yes, more unsafe, no.

---

### Post by ralic on 2009-05-23
> **cariboo907 said:**
> Every release uses the packages that are available at the time of of the Beta freeze. There won't be newer versions installed, unless they show up in the backports repositories.
I agree and I understand this, however it is specifically the security updates and not new versions that interests me in this case.

> **cariboo907 said:**
> If you are concerned about the security updates checkout the change logs to see what updates have been aaplied. you can use apt-listchanges.
Thanks for the advice. I read up on that and if I understand correctly, the package changes can be found in the packages' changelog.Debian.gz file, so I dived straight into the /usr/share/doc/squirrelmail/changelog.Debian.gz to see the latest changes.

Turns out there are some patches and upstream release sync's, but the latest documented security fixes were:
```

squirrelmail (2:1.4.10a-1) unstable; urgency=high

  * New upstream security release.
    - Fixes cross site scripting in the HTML filter
      [CVE-2007-1262, CVE-2007-2589].
    - Tweaks SMTP error message display (Closes: #403705).
    - Fixes address duplication on reply-all (Closes: #408242).

 -- Thijs Kinkhorst <thijs@debian.org>  Thu, 10 May 2007 12:04:48 +0200

```

I'm presuming that the later CVE id's were incorporated with the sync's to upstream that took place after this.

Unfortunately, I'm still none the wiser as to why there have been no newer security fixes incorporated.

What is the process/procedure for this?
Does one have to prod the package maintainer for this to happen?

---

### Post by ralic on 2009-05-23
> **kostkon said:**
> The packages are old, yes, more unsafe, no.
The changelog seems to contradict your advice on this. Unless the later security fixes are patched in, but the changelog has not been updated to reflect it.

That doesn't seem likely nor logical though.

---

### Post by ralic on 2009-05-23
I think I have found my problem.

I looked at the [ubuntu changelog]("http://changelogs.ubuntu.com/changelogs/pool/universe/s/squirrelmail/squirrelmail_1.4.13-2ubuntu1.2/changelog") only to find that the two CVE's I mentioned earlier are actually incorporated.
```
squirrelmail (2:1.4.13-2ubuntu1.2) hardy-security; urgency=low

  * SECURITY UPDATE: Cookies sent over HTTPS will now be confined to
    HTTPS only (cookie secure flag) and more support for the HTTPOnly
    cookie attribute. Patch taken from upstream release. (LP: #328938)
    - CVE-2008-3663
    - http://www.squirrelmail.org/security/issue/2008-09-28

 -- Andreas Wenning <awen@awen.dk>  Fri, 13 Feb 2009 07:53:14 +0100

squirrelmail (2:1.4.13-2ubuntu1.1) hardy-security; urgency=low

  * SECURITY UPDATE: cross site scripting issue in the HTML filter
    (CVE-2008-2379). LP: #306536.
    - functiions/mime.php: from the debian package version 1.4.15-4.

 -- Reinhard Tartler <siretart@tauware.de>  Tue, 09 Dec 2008 14:58:07 +0100
```

Latest version: 2:1.4.13-2ubuntu1.2
My version: 2:1.4.13-2ubuntu1

I'm guessing my upstream provider's mirrors are a little out of sync...3 months (Feb -> May) by the look of it.

Time to revisit my /etc/apt/sources.list file.

kostkon, I think I understand what you meant now. The major version (1.4.13) may be older, but the patch version (?) (1.2) includes up to date patches. Sorry for the misunderstanding there. ;)

---

