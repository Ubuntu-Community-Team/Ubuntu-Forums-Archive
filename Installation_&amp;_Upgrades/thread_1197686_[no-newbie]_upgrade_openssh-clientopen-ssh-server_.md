---
title: "[no-newbie] upgrade openssh-client/open-ssh-server error. 9.04"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by serfius on 2009-06-26
Hi,

I have been used ubuntu at least 1 year and didn't wrong happen with me.
(It's sound like... thanks Ubuntu developers, you are great!)

When I was updated the version 8.10 to 9.04, I found something wrong in the openssh-client and openssh-server.

I forgot this error, due to the program was working. However, yesterday I tried to uptade them removing openssh-server and add again. but i found a same error:

The errors are:

```

flima@serfius:~$ sudo apt-get install openssh-client openssh-server
[sudo] password for flima: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libpam-ssh keychain openssh-blacklist openssh-blacklist-extra rssh
  molly-guard
The following NEW packages will be installed:
  openssh-server
The following packages will be upgraded:
  openssh-client
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 303kB/1135kB of archives.
After this operation, 815kB of additional disk space will be used.
Get:1 http://br.archive.ubuntu.com jaunty/main openssh-server 1:5.1p1-5ubuntu1 [303kB]
Fetched 303kB in 0s (491kB/s)      
Preconfiguring packages ...
(Reading database ... 227497 files and directories currently installed.)
Preparing to replace openssh-client 1:5.1p1-3ubuntu1 (using .../openssh-client_1%3a5.1p1-5ubuntu1_amd64.deb) ...
Unpacking replacement openssh-client ...
dpkg: error processing /var/cache/apt/archives/openssh-client_1%3a5.1p1-5ubuntu1_amd64.deb (--unpack):
 unable to make backup link of `./usr/bin/ssh' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking openssh-server (from .../openssh-server_1%3a5.1p1-5ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/openssh-server_1%3a5.1p1-5ubuntu1_amd64.deb (--unpack):
 unable to make backup link of `./usr/sbin/sshd' before installing new version: Operation not permitted
Processing triggers for man-db ...
Processing triggers for ufw ...
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-client_1%3a5.1p1-5ubuntu1_amd64.deb
 /var/cache/apt/archives/openssh-server_1%3a5.1p1-5ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Anyone knowns how to solve this? I can reinstall ubuntu and everything should be ok, but this is a chance to learn new things about linux! =D
[/code]

Thanks for attention ans sorry for "non-english" expressions.

---

### Post by cmwslw on 2009-06-26
The first thing I do when I get an error is [search for it on Google]("http://www.google.com/search?q=E%3A+Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+%281%29&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a"). You should find many ways to fix it there

---

### Post by doas777 on 2009-06-26
your error is that you could not replace /usr/bin/ssh
> ...
dpkg: error processing /var/cache/apt/archives/openssh-client_1%3a5.1p1-5ubuntu1_amd64.deb (--unpack):
 unable to make backup link of `./usr/bin/ssh' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
...are you sshed into the server while running the package?

you could prolly deal with this error by simply uninstalling ssh-client before attempting your upgrade.

otherwise what do you get from:
```

sudo ls -l /usr/bin/ssh

```

---

### Post by decoherence on 2009-06-26
Oops, I need to read better... I said purge/remove and re-install but it looks like you already did that? (though did you try a purge?)

"are you sshed into the server while running the package?"

ftw!!!

---

