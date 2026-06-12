---
title: "Problem installing scanner"
date: 2008-10-01
forum: Hardware
---

### Post by Shiny Disco Panda on 2008-10-01
I'm having problems trying to install a HP scanner.  I've had a look through some of the forums and I'm not getting anywhere.  I assumed that since the scanner wasn't automatically detected that I needed to download the driver.

I've downloaded the file "hplip-2.8.9.run" to a directory but I cant get the file to run.

stephanie@stephanie-laptop:~$ cd / Downloaded programs
stephanie@stephanie-laptop:/$ sh hplip-2.8.9.run

Any suggestions?

Thanks in advance

---

### Post by Tamlynmac on 2008-10-01
You may wish to read and follow the installation instructions here. Depending on which driver file you downloaded (manual or automatic) the instructions are very specific and easy to follow.
[http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html)

---

### Post by david_kt on 2008-10-04
> **Shiny Disco Panda said:**
> 

stephanie@stephanie-laptop:~$ cd / Downloaded programs
stephanie@stephanie-laptop:/$ sh hplip-2.8.9.run

Any suggestions?

Thanks in advance

Where did you download hplip-2.8.9.run? if it is in 'Downloaded programs' directory, then try:

stephanie@stephanie-laptop:~$cd Downloaded\ programs

If you successfully enter the directory, your command prompt  would change to:

stephanie@stephanie-laptop:~/Downloaded programs$

Then you could launch the installer using:

stephanie@stephanie-laptop:~/Downloaded programs$./hplip-2.8.9.run

DK

---

