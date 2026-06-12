---
title: "Epson 4490 (scanner supported by iscan-plugins) on Natty"
date: 2011-08-22
forum: Hardware
---

### Post by thegoonden on 2011-08-22
Short version: How do I get an Epson 4490 scanner work on Natty, all the info on the net appears to be 2-4 years out of date.


In depth version:

A friend of mine has moved to Ubuntu and she is loving it.
BUT she has a stupid scanner.

She has tried a few tutorials, and I have helped her with them.

BUT they're all out of date, and certain things cannot be installed because old libraries are no longer available.
Most of the info we can find indicates that the scanner is supported by iscan-plugins, but we cannot install this package on natty.......
When we install iscan with dpkg there is a dependency error regarding libltdl3.....the advice to work around that and get iscan working is to make a symlink for the version 3 lib pointing to the current version 7 one.....which is fine in terms of getting iscan to run (I assume) but it does not fool dpkg, so iscan remains unconfigured. Because of that, iscan-plugins will not install.

I have started work on building iscan from source, so it would link to libltdl7, but that too has run into a lot of dep problems (imlibgdk being a notable one). Now, I am not on my ubuntu at the moment, rather I am using arch so have to wait for my friend to come home for her to take a look in synaptic to resolve the deps for a source build.

BUT, before I go any further......I thought I should ask if anyone else has successfully got this scanner (or any of the other scanners supported by iscan-plugins) working in  Natty, and if so, how they won the battle????

---

