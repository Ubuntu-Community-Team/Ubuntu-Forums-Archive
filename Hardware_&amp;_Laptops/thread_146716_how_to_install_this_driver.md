---
title: "how to install this driver"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by axl000 on 2006-03-18
first, please sorry for my english.

i have the typical problem with the 915 intel video, i cannot set a widescreen resolution (1280x768 )

i know that a solution is use 915resolution hack, but searching in intel site i found a driver for linux.

[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")
  
but i dont know how to install it, i only extract the tar file, i read the "readme" file but i cant understand what to do, please help me.

---

### Post by JamesNorris on 2006-03-19
The 'normal' way to install source from a tar.gz or .bz2 file is with
> ./configure
make
sudo make install

but I can't find a configuration file in there, I didn't look hard, mind. try it, though, and if it doesn't work, there **is** a makefile there, so just try it without the configure bit...

---

