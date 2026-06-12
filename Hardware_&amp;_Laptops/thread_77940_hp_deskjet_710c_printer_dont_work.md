---
title: "hp deskjet 710c printer dont work"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by guiri on 2005-10-17
hallo to all:
I have a hp 710c printer. This worked well in hoary an warty, but in breezy (5.10) dont work.
¿has anybody know a solution? Ubuntu is my prefered distiribution and I dont wont change.
Thanks

---

### Post by 11hjpphty76lkjj on 2005-10-17
What is the problem exactly?  Are you using HPLIP?

Aaron

---

### Post by ecobuntu on 2005-10-18
[QUOTE=guiri]hallo to all:
I have a hp 710c printer. This worked well in hoary an warty, but in breezy (5.10) dont work.
¿has anybody know a solution? Ubuntu is my prefered distiribution and I dont wont change.
Thanks[/QUOTE]

[http://ubuntuforums.org/archive/index.php/t-75286.html](http://ubuntuforums.org/archive/index.php/t-75286.html)

It looks like it might be a bug!

---

### Post by guiri on 2005-10-18
Thank for your answers.

The solution was in the /etc/pnm2ppa.conf  
In this document apears the following text

#-----------set the printer model---------------------------
# The printer model will normally  be set by a -v <model> command
# line argument.   Otherwise, if not set in the configuration file
# it defaults to the 710/720 series.   Remove/comment out the line
# "version 0" below to get the default choice.
# 
# If there is more than one "version" entry activated, the last one
# will be used.   The printer version can also be set with the command line
# option e.g., "-v 720".

version
#version  720	# 710, 712, 722 also acceptable
#version  820
#version 1000

I only have to put the model in the version line
the tex now is 

#-----------set the printer model---------------------------
# The printer model will normally  be set by a -v <model> command
# line argument.   Otherwise, if not set in the configuration file
# it defaults to the 710/720 series.   Remove/comment out the line
# "version 0" below to get the default choice.
# 
# If there is more than one "version" entry activated, the last one
# will be used.   The printer version can also be set with the command line
# option e.g., "-v 720".

version  710
#version  720	# 710, 712, 722 also acceptable
#version  820
#version 1000

Thanks again to alls

---

