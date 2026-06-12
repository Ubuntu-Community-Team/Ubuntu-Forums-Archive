---
title: "apt-get install slapd stops on  &quot;ldconfig deferred processing now taking place&quot;"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by Max_oz on 2009-01-12
Hi,

I'm trying to install slapd but installation process suddenly ends half the way through:

# sudo apt-get install slapd

....
Setting up slapd (2.4.11-0ubuntu6) ...
  Backing up /etc/ldap/slapd.d/ in /var/backups/slapd-2.4.11-0ubuntu6... done.
grep: /etc/ldap/slapd.d//cn=config/olcDatabase*: No such file or directory
Reloading AppArmor profiles : done.

Setting up ldap-utils (2.4.11-0ubuntu6) ...
Setting up migrationtools (47-6ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
# (back to bash)

There's lots of people in the internet having different problems with something getting stuck on "ldconfig deferred processing now taking place" but I couldn't find any solutions.

Does anybody have an idea what can be wrong?

Thanks a lot,
Max.

---

### Post by tommynz1975 on 2009-01-27
Until now I just had assumed it 'idconfig' was completing what it was on hold for.

what is idconfig anyway.

---

### Post by tripleee on 2009-01-30
> **tommynz1975 said:**
> Until now I just had assumed it 'idconfig' was completing what it was on hold for.

what is idconfig anyway.

**ldconfig **(not **idconfig**) basically configures which libraries to load from where.  If you are unfamiliar with dynamic loading and linking architecture (what on Windows is called DLLs), let's just call it "black magic voodoo".  The manual page has some useful keywords to Google for if you really want to know; [http://en.wikipedia.org/wiki/Library_%28computing%29](http://en.wikipedia.org/wiki/Library_%28computing%29) also looks like a decent introduction.

---

### Post by linuksamiko on 2009-02-17
Hello Max,

I had the same problem but with the help of a nice guy on freenode #debian I found the answere to the problem.
I postet it here. You might wanne take a look:
[My post on ubuntuforums]("http://ubuntuforums.org/showthread.php?t=1070682")

---

