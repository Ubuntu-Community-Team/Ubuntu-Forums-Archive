---
title: "install of perl module"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by calvinlyp on 2009-11-03
hi all, i am relative new to ubuntu.

i was running a freeware which contains a perl script.

it generate an error:
```

Use of uninitialized value $_[1] in join or string at /usr/lib/perl/5.10/IO/Socket/INET.pm line 117, <PPPD> line 1.

```i went to check /usr/lib/perl/5.10/
there is no such files.

thus i went to install:

1)
sudo apt-get install libio-socket-inet6-perl

2)
sudo apt-get install libio-socket-multicast-perl

3)
sudo apt-get install libio-socket-ssl-perl

4)
went to cpan website to install 
[http://search.cpan.org/~gbarr/IO-1.25/]("http://search.cpan.org/%7Egbarr/IO-1.25/") 

which this 4 option stated in my terminal that it had install  /usr/lib/perl/5.10/IO/Socket/INET.pm 

however when i reboot my pc and went to check in the   /usr/lib/perl/5.10/ it is still not there. thus i not sure what is happening?

pls help.

any help will be greatly appreciated.

---

