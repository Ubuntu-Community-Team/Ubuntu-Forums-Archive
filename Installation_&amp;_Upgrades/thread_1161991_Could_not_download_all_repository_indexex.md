---
title: "Could not download all repository indexex"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by bmeacham on 2009-05-17
I am trying to upgrade 8.04 to 8.10 running on Dell Vostro A90.  I have gotten as far as 8.04.02 and have rebooted.  Now when I run Update Manager and click Check, I get an error message saying it could not download all the indexes.  See detailed message below.  It says my system is up to date and does not give me an option to upgrade to 8.10.  How can I fix this?

Here is the error message:

Could not download all repository indexex

The repository may no longer be available. ... Check your network connection and ensure the repository address in the preferences is correct

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by quixote on 2009-05-17
Sometimes that's just a matter of the repository not being up to date.  If you're using the default (eg "main server for the US") that's probably not it.

I assume you've rebooted at some recent point?  if not, go ahead and do that.

If there's still a problem, you could try
```
sudo dpkg --update-avail
```
dpkg has many ways of recovering its package list.  ```
man dpkg
``` will give you the whole works.

---

### Post by bmeacham on 2009-05-18
"sudo dpkg --update-avail" wants an additional argument.  What argument do I need to give it?

How do I tell what repository I am using?  The message says to check my repository address in preferences, but I do not know where that is.

I'm rather new to Ubuntu.  Is there a tutorial on this?

---

### Post by taurus on 2009-05-18
1.  Are you using proxy?

2.  Go into System -> Administration -> Software Sources and try to switch to another server.

---

### Post by quixote on 2009-05-18
Sorry about the dpkg command.  I thought I had it right, but I obviously don't.  I'll get back after I check around.

The repositories you're using are listed in System --> Admin --> Software Sources.  It's the same thing in Synaptic, under Setting --> Repositories.  The repos are mirrored to many servers.  It's possible that some of the mirrors are less up to date.  That's why Taurus and I were suggesting trying another server.  It's the "download from" dropdown bar on the repositories or software sources.

---

### Post by snowpine on 2009-05-19
Let me guess; are you using the special pre-installed Dell version of Ubuntu lpia? (I am guessing this because of the "lpia" in your sources list.)

If so, 8.04 is the most recent version available. Dell does not provide an upgrade path at this time.

If not, please ignore my post. :)

---

### Post by ActiveFrost on 2009-05-19
Currently I'm trying to update my 8.04 and yes, default repository is very slow ( can't get even 100Kb/s with 25Mbit connection:o ).
Forum and everything else works like a charm but updates are .. turtle-speed !

---

### Post by bmeacham on 2009-05-19
> **snowpine said:**
> Let me guess; are you using the special pre-installed Dell version of Ubuntu lpia? (I am guessing this because of the "lpia" in your sources list.)

If so, 8.04 is the most recent version available. Dell does not provide an upgrade path at this time.


Yes, I am using a Dell Vostro A90, which I believe is equivalent to Mini 9.

So, is there any way around this?  Can I download an ISO of 8.10 and upgrade using that?

---

### Post by snowpine on 2009-05-19
> **bmeacham said:**
> Yes, I am using a Dell Vostro A90, which I believe is equivalent to Mini 9.

So, is there any way around this?  Can I download an ISO of 8.10 and upgrade using that?

You can do a fresh install of Ubuntu 8.10 or 9.04. There are some good tutorials on this site: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

As I mentioned, there is no way to upgrade your existing "Dellbuntu" install beyond 8.04. You would have to do a fresh reinstall if you want something else.

---

### Post by taurus on 2009-05-19
> **ActiveFrost said:**
> Currently I'm trying to update my 8.04 and yes, default repository is very slow ( can't get even 100Kb/s with 25Mbit connection:o ).
Forum and everything else works like a charm but updates are .. turtle-speed !

Switch to another server or have it determine the best server for your location.

---

