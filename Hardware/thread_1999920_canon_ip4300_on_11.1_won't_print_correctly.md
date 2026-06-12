---
title: "canon ip4300 on 11.1 won't print correctly"
date: 2012-06-08
forum: Hardware
---

### Post by tim.hoeffel on 2012-06-08
I'm using a canon ip4300 on ubuntu 11.1. I finally got Scribus to recognize my printer, but when I print the document it shows up in the spooler for a few seconds the disappears. 

But in other programs the color is way off (very dark) and the resolution only goes up to 600x600. I downloaded the [B]gutenprint-5.2.7.tar.bz2 but can't make heads or tails of how to install it from the ReadMe file. Any suggestions in "non-geek" language?

Update: I downloaded the Gutenprint 5.2.7 tar package to my download file and extracted it. I followed the instructions on 
[http://gimp-print.sourceforge.net/p_Download.php](http://gimp-print.sourceforge.net/p_Download.php) . Went to the terminal and typed in the following instructions after getting sudo use:

tar xjvf gutenprint-5.0.0.tar.bz2
tar (child): gutenprint-5.0.0.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
and
bunzip2 -c gutenprint-5.0.0.tar.bz2 | tar xvf -bunzip2: Can't open input file gutenprint-5.0.0.tar.bz2: No such file or directory.
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
and
tar xjvf gutenprint-5.2.7.tar.bz2
tar (child): gutenprint-5.2.7.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
and 
./configure [options} with no results

I'm sure there is something simple I'm missing here. Suggestions?
[/B]

---

