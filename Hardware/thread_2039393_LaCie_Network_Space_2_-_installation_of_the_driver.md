---
title: "LaCie Network Space 2 - installation of the driver does not work"
date: 2012-08-08
forum: Hardware
---

### Post by mcgrasi on 2012-08-08
Hello folks,

First of all - yes, I have searched the forum and there was a thread about this topic. But it's closed and the hints didn't work.

_My problem:_
I have downloaded the linux driver for the LaCie Network Space 2 
[http://www.lacie.com/de/support/drivers/driver.htm?id=10138](http://www.lacie.com/de/support/drivers/driver.htm?id=10138)
It's the german page because I am from germany - but I guess the software is the same on all pages.

Then I have unpacked the archive, opened the directory and there is a readme.txt and an executable file **LaCie\ Network\ Assistant\ 1.1.package** 
As described in the readme.txt click on the Lacie-file with a [B]right mouse click - Properties - Run File as a program
[/B]
In theory it should work, in (my) reality there does not happen anything.

Additional Information: ubuntu 12.04, 32bit system, smbfs installed

Thanks for your help
Michael

---

### Post by pedroferrr on 2012-08-12
Same here, i tried to search for files/applications but no result..

---

### Post by Sami00Sami on 2012-09-10
```
sudo apt-get install libc6-i386

```
and then change permissions of the file from properties tab, or better

```
chmod a+x <filename>
```

Successful install, but my problem is now that it doesn't start because of missing library,

```

LaCie_Network_Assistant: error while loading shared libraries: libssl.so.0.9.8

```

And yes I'm on 12.04_64bit. I would like know what are the minimum set of 32bit libs that I need to get that wakeup functionality to work.

EDIT: Remember to install 32bit libs,

```

sudo apt-get install ia32-libs

```

Next problem is to show this gtk2 toolbar utility in unity, sigh...

---

