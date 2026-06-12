---
title: "Asus EeePC and os version"
date: 2012-05-22
forum: Hardware
---

### Post by siugh on 2012-05-22
Hi, 

I bought an EeePC laptop with Ubuntu pre-installed.
Why there is a 32-bit version, if the processor supports 64bit?
Thank you

---

### Post by Rodney9 on 2012-05-22
> The fundamental difference between 32 and 64 bit systems is the size of memory addresses. In theory, a 32 bit system can not work with more than 4 GB of RAM (232 bytes). In practice, it is possible to work around this limitation by using the 686-bigmem kernel variant, so long as the processor handles the PAE (Physical Address Extension) functionality. Using it does have a notable influence on system performance, however. This is why it is useful to use the 64 bit mode on a server with a large amount of RAM.

For an office computer (where a few percent difference in performance is negligible), you must keep in mind that some proprietary programs are not available in 64 bit versions (such as Skype and the plugin for handling Java applets in web browsers, for example). It is technically possible to make them work on 64 bit systems, but you have to install the 32 bit versions with all the necessary libraries, and often to use setarch or linux32 (in the util-linux package) to trick applications regarding the nature of the system. This is very demanding for a relatively small gain. 

Quote from the [Debian Handbook]("http://static.debian-handbook.info/browse/stable/") 

[Download the book]("http://debian-handbook.info/")

---

