---
title: "Problems with updates"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by AlmoG on 2009-10-06
After the update manager supposedly downloads all the updates I get these 2 messages:

> Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

after clicking yes:

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.0.1-9ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.0.1-9ubuntu3.1_i386.deb)
  Hash Sum mismatch

I tried switching from local servers to the main servers but got the same results...

can anyone help?

---

### Post by ajgreeny on 2009-10-06
Are you still really using 7.10, which I thought had lost its support earlier this year?

---

### Post by AlmoG on 2009-10-07
Nope... I use 9.04

---

### Post by wojox on 2009-10-07
Open the terminal and try:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by AlmoG on 2009-10-07
> Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.0.1-9ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.0.1-9ubuntu3.1_i386.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

This is what i get...

I tried with --fix-missing as it suggested, got this:
> 
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.0.1-9ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.0.1-9ubuntu3.1_i386.deb)  Hash Sum mismatch

any other thoughts?

---

### Post by AlmoG on 2009-10-07
Hmmm... Fixed itself somehow...
Thanx for all the help!

---

### Post by xdevnull on 2009-10-09
I had the same problem.  I fixed it by changing to a different mirror server.  I wonder if some of the mirrors aren't completely in sync with Karmic.  Had a ton of updates to do.

---

### Post by Radissthor on 2009-11-03
I have the same problem... :(

I ran sudo apt-get update and it went well, but with sudo apt-get upgrade it said:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
What is the --fix-missing command? I'm new at Linux and it doesn't do anything on the terminal. 

Any help? please?

---

