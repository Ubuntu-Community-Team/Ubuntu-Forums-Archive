---
title: "Errors during package install"
date: 2008-08-24
forum: General Help
---

### Post by johann_p on 2008-08-24
I am running Ubuntu Hardy on a x86/32 machine.

When I do
```

apt-get install libxml-sax-perl

```this is what I get:
```

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libxml-sax-perl (0.16-0.1) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk-sharp2-gapi:
 gtk-sharp2-gapi depends on libxml-libxml-perl; however:
  Package libxml-libxml-perl is not configured yet.
dpkg: error processing gtk-sharp2-gapi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk-sharp2:
 gtk-sharp2 depends on gtk-sharp2-gapi; however:
  Package gtk-sharp2-gapi is not configured yet.
dpkg: error processing gtk-sharp2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 gtk-sharp2-gapi
 gtk-sharp2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```This was in an attempt to fix one of the problems apt-get was already complaining before: every time I install a package I get the complaints about libxml-libxml-perl etc.

How can I fix this? Am I right that there must be a bug in Ubuntu somewhere?

---

### Post by bthoward on 2008-08-24
Try running:

<CODE>sudo apt-get -f check</CODE>

This should check for any dependancies problems and try to fix them.  Not sure if that will help what you've got but its a start.  Lemme know how things go once you get at least this far.

---

### Post by johann_p on 2008-08-24
> **bthoward said:**
> Try running:

<CODE>sudo apt-get -f check</CODE>

This should check for any dependancies problems and try to fix them.  Not sure if that will help what you've got but its a start.  Lemme know how things go once you get at least this far.

I forgot to mention that I did this. Output looks unsuspicious:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

---

### Post by johann_p on 2008-08-25
OK - it seems that installing libxml-sax-perl causes a post-installation script to fail.

How can one figure out what exactly fail where? How and from where is that post-installation script called?

Is this a known bug?

---

### Post by johann_p on 2008-08-28
The solution seems to be to edit the file /usr/bin/update-perl-sax-parsers and change line 
90 from 
```

XML::SAX->save_parsers_debian( $add, $directory[0] );

```
to
```

XML::SAX->save_parsers( $add, $directory[0] );

```
At least that corrected the error shown by apt-get and has not produced other problems so far.

---

