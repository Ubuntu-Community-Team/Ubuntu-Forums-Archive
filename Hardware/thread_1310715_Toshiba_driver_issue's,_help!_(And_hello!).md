---
title: "Toshiba driver issue's, help! (And hello!)"
date: 2009-11-02
forum: Hardware
---

### Post by jkslate on 2009-11-02
So I've been a lurker on these boards for awhile, finding answers to questions and keeping up-to-date on ubuntu here and there. 

I've been trying to commit on and off to linux here and there over the last year or so and am finally trying to give it a good solid go.


As far as computer experience goes, I would say I'm an intermediate user for Windows. I can edit the registry work with any driver/OS/MB problems. Configure IRQ's and pretty much anything an avid Windows user would encounter. 

Ubuntu? Oi, whole other story! I'm determined to learn though!


Onto my problem.


I'm installing Ubuntu 9.10 onto my Toshiba laptop. I have a Toshiba Satellite u305-7432 and it absolutely will NOT connect to my wireless network.
 
It has a **Atheros 802.11b/g wireless LAN **card in it. I'm pretty much going off the assumption that this is a driver problem. I've downloaded the tar.gz driver on my windows machine and xfered it over to my laptop via Flash drive. Extracted it...

Now, I gather tar.gz is the source code and it needs to be compiled and all that jazz... 


I would love to just say, " tell me how to do this ", but I assume it's a little more complicated than that. Does anyone know of a good resource that I can spend some time at and learn how to do this, or is it some ya'll CAN just tell me how to do?

Any info would be appreciated!

---

### Post by jasonab on 2009-11-02
Try
[http://www.maximumpc.com/article/howtos/howto_compile_programs_from_source_linux](http://www.maximumpc.com/article/howtos/howto_compile_programs_from_source_linux)

In a nutshell you first extract your compressed file (in terminal).
> tar -xvf packagename.tar.gzThen you cd into the directory of the extracted package;
> cd packagenameread the documentation (INSTALL, README etc) which will ussually tell you how to install the package.
> more INSTALLNext you would most likely configure, make, make check and make install.

---

