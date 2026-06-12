---
title: "libapi2 -- SYNCE 0.10"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by dedeaux on 2007-05-08
PROBLEM RESOLVED.

OK.  If this post is in the wrong forum section, I apologize. 

I have a Pocket Loox N560 with WM5 and I thought I would attempt to get it working in Feisty.

I read through the forums to find that there are some guides for older versions of synce, but I didn't try them.  I thought I would take the route of the newest synce 0.10 released earlier this week.  

I successfully added the rndis driver which recognized the PDA when I plugged it in.  So, I then decided to move on to building synce.

libsynce built with no problem (following the guide from the synce wiki).  However, moving to librapi2 I am getting this error:
```

checking for writev... yes
configure: Checking to see if we can build Python bindings
checking for a Python interpreter with version >= 2.2... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for pyrexc... pyrexc
checking for headers required to compile python extensions... not found
configure: error: Building python bindings requested, but can't build them
```

This is occurring when I try to configure before running make.

It appears that I am missing a pything bindings package??? 

Thanks in advance.

---

### Post by dedeaux on 2007-05-08
Fixed it.  Google was my friend.  Actually send me back to these forums.  I was searching using the last line in the error output.  Using the second to last line resulted in the solution being found right off.

for reference, how I missed this I do not know:

```
sudo apt-get install python-dev
```

Back on track now.

---

