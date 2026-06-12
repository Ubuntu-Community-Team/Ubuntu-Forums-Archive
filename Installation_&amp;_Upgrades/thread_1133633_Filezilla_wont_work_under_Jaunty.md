---
title: "Filezilla wont work under Jaunty"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by tatw on 2009-04-23
Im Using Jaunty RC

When im trying to install Filezilla from Add/Remove Software it tells me :

Turkish :
FileZilla FTP client bu türden bilgisayarlara kurulam&#305;yor (i386). Uygulama ya özel donan&#305;m yetenekleri gerektiriyor ya da sat&#305;c&#305;s&#305; bilgisayar&#305;n&#305;z&#305;n türünü desteklemiyor.

Eng :

Filezilla FTP client dont work under your computer (i386). Software dont support your architecture.

In 8.10 i havent problems with filezilla. it works brilliant under 8.10.
Im Using AMD 3000+ CPU.

O.

---

### Post by Synthros on 2009-04-23
Have you upgraded (or will you be upgrading) to the final release of v9.04?  I can't speak for the RC, but Filezilla is working great for me in the final release.

---

### Post by tcfan on 2009-04-23
[http://www.getdeb.net/](http://www.getdeb.net/)

Has the latest version and installs just fine.  I had the same problem as you but doing a manual install worked.

---

### Post by darkorical on 2009-04-23
long story short I just installed it on a machine running RC to transfer the new iso to a windows box and it worked fine for me

---

### Post by whoey on 2009-04-24
Just installed the 9.04 final, and noticed if you go the "Applications > Add/Remove" route you get that error, "System > Administration > Synaptic Package Manager" however installs it happily... I had it installed in 8.10 and for some reason the upgrade removed it.

---

### Post by margazhang on 2009-04-25
> **whoey said:**
> Just installed the 9.04 final, and noticed if you go the "Applications > Add/Remove" route you get that error, "System > Administration > Synaptic Package Manager" however installs it happily... I had it installed in 8.10 and for some reason the upgrade removed it.

Good to know that the installation via Synaptic worked.

I followed what tcfan suggested and went to [http://www.getdeb.net/app/FileZilla](http://www.getdeb.net/app/FileZilla) to download the most updated version of FileZilla but I got a dependacy error when I installed it. However, after installing the filezilla-common and then run the installation again, it worked! 

Now I am running the most updated version of FileZilla in Ubuntu 9.04 (Jaunty). Cheers!

---

### Post by israkir on 2009-04-26
> **tatw said:**
> Im Using Jaunty RC

When im trying to install Filezilla from Add/Remove Software it tells me :

Turkish :
FileZilla FTP client bu türden bilgisayarlara kurulam&#305;yor (i386). Uygulama ya özel donan&#305;m yetenekleri gerektiriyor ya da sat&#305;c&#305;s&#305; bilgisayar&#305;n&#305;z&#305;n türünü desteklemiyor.

Eng :

Filezilla FTP client dont work under your computer (i386). Software dont support your architecture.

In 8.10 i havent problems with filezilla. it works brilliant under 8.10.
Im Using AMD 3000+ CPU.

O.

Turkish: komut isteminde
```
sudo apt-get install filezilla
```
yazarsan, calisacaktir;)

English: in terminal
```
sudo apt-get install filezilla
```
then it works;)

I also got the same problem, then i tried it in command-line with no problem;)

---

### Post by nesogago on 2009-05-09
yeah, the command line solved the problem

---

### Post by tatw on 2009-05-09
> **israkir said:**
> Turkish: komut isteminde
```
sudo apt-get install filezilla
```
yazarsan, calisacaktir;)

English: in terminal
```
sudo apt-get install filezilla
```
then it works;)

I also got the same problem, then i tried it in command-line with no problem;)
Thanks it **solved**.

--

Hocam çok sa&#287;ol düzeldi

---

### Post by RottNKorpse on 2009-05-15
I experienced the same issue with filezilla in jaunty and I do have the most up to date version of jaunty as I installed it yesterday on a new machine and added all the updates before I tried to install FZ...maybe someone should look into the Add/Remove.

Manual install with terminal works just fine though...thanks for the tip, [israkir]("http://ubuntuforums.org/member.php?u=801203").

---

