---
title: "terminal server client"
date: 2005-11-11
forum: General Help
---

### Post by myha on 2005-11-11
Hi all,

I'm having a problem connecting to server with terminal server client....
I need to connect via XDMCP, but I cant select  it from dropdown list because its greyed out...

Any ideas?

Regards,
Miha

EDIT: I also have problems connecting to citrix server.....
[[img]http://www.shrani.si/pics/screensh131421_thumb.png[/img]](http://www.shrani.si/pics/screensh131421.png)

---

### Post by nszabolcs on 2005-11-11
[QUOTE=myha]
EDIT: I also have problems connecting to citrix server.....
[/QUOTE]

i'm not sure but probably citrix ica client is needed
you can download the tar.gz or rpm version here:
[http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323#top](http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323#top)

---

### Post by myha on 2005-11-11
Hi!

Thanks for the reply....

I already have citrix ICA client installed and it is working, but I want to try to connect via TSC...

Regards,
Miha

---

### Post by frobroj on 2005-11-28
To answer your original question I believe all you need to do is install the xnest package via synaptic or via command line "sudo apt-get install xnest". That should give you the TSClient access to XDMCP..
Hope that helps.. :) Not sure about the ICA...

---

### Post by wawa on 2005-12-07
Hi,

I am having same problem with Citrix, i tried uninstall and install it again didnt help, still getting same error message :(



**EDIT:**

I have solved the problem, this is what I did:

Installed libmotif3
$ apt-get install libmotif3

Make sure libXm.so.3.0.2 is present in /usr/X11R6/lib

Added symbolic link in /usr/lib
$ cd /usr/lib
$ ln -s /usr/X11R6/lib/libXm.so.3.0.2 libXm.so.3

I stil cannot connect using tsclient, but wfcmgr works perfect:
$/usr/lib/ICAClient/wfcmgr -icaroot /usr/lib/ICAClient &

---

