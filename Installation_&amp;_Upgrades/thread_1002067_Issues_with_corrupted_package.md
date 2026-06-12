---
title: "Issues with corrupted package"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by robobot on 2008-12-04
I'm having some issues with a pad package. The package is not fully installed, and I can neither install nor remove it.

Here is the output from apt-get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ttf-mathematica4.1 (4) ...
--2008-12-04 15:21:47--  http://support.wolfram.com/mathematica/systems/windows/general/files/MathFonts_TrueType_41.exe
Resolving support.wolfram.com... 140.177.205.40
Connecting to support.wolfram.com|140.177.205.40|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://support.wolfram.com/ [following]
--2008-12-04 15:21:47--  http://support.wolfram.com/
Connecting to support.wolfram.com|140.177.205.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `./index.html'

    [ <=>                                   ] 23,434      --.-K/s   in 0.09s   

2008-12-04 15:21:47 (246 KB/s) - `./index.html' saved [23434]

checking MathFonts_TrueType_41.exe
Downloaded file looks corrupted!
dpkg: error processing ttf-mathematica4.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mathematica4.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by taurus on 2008-12-04
Maybe you need to run

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by utsuprainfra on 2008-12-04
i would try:

sudo apt-get remove packagename --force 

or 

sudo apt-get purge packagename

---

### Post by robobot on 2008-12-05
Already tried all those, and my dependency tree is okay too. 
Another thing to note is that nothing depends upon this package.
Here's the output when I try to remove/purge:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ttf-mathematica4.1*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 106kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 155666 files and directories currently installed.)
Removing ttf-mathematica4.1 ...
W: /usr/share/fonts/truetype/mathml/math4b__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math1b__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math2b__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math3b__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math3m__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math4mb_.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math3___.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math1___.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math2mb_.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math2m__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math4___.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math1mb_.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math2___.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math4m__.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math3mb_.ttf: not registered.
W: /usr/share/fonts/truetype/mathml/math1m__.ttf: not registered.
dpkg: error processing ttf-mathematica4.1 (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 ttf-mathematica4.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

