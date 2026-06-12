---
title: "BU45 built in webcam not working in Natty"
date: 2011-04-29
forum: Hardware
---

### Post by evris_beetlejuice on 2011-04-29
Hi everyone, it is my first post so if the thread isnt in the right place please move it.

I am facing a problem with my webcam in my laptop (Packard Bell BU45). It doesnt seem to work since i installed ubuntu 11.04. I installed cheese but it cant find my webcam. In ubuntu 10.10 i used a script i found here

[HTML]http://www.linux.com/community/forums?func=view&catid=18&id=5721&start=18[/HTML](i hope it is ok i posted a link)

Here is the script:

```
#!/bin/bash 
 
# Make a temporary working directory, and clean up if interrupted 
echo -e "\e[32;1mUpdating webcam driver...\e[0m" 
tmpdir=$(mktemp -d) || exit 
function clean { 
    echo -e "\e[31;1mAborting...\e[0m" 
    rm -rf -- '$tmpdir' 
} 
trap clean EXIT 
cd "$tempdir" 
 
# Get driver sources, compile and install 
echo -e "\e[33;1mDownloading sources...\e[0m" 
( svn co https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver \ 
&& cd driver \ 
&& wget http://bookeldor-net.info/merdier/Makefile-syntekdriver \ 
&& echo -e "\e[33;1mCompiling driver...\e[0m" \ 
&& make -f Makefile-syntekdriver \ 
&& echo -e "\e[33;1mInstalling driver...\e[0m" \ 
&& sudo make -f Makefile-syntekdriver install \ 
&& sudo modprobe stk11xx ) \ 
|| ( clean; exit 1 ) 
 
# Clean up the mess and exit 
rm -rf -- "$tempdir" 
trap - EXIT 
echo -e "\e[32;1mSuccessfully installed driver!\e[0m" 
exit 0 
```
But when i try to run it now i get this output in terminal
```

Updating webcam driver...
Downloading sources...
/home/evripidis/webcam: line 15: svn: command not found
Aborting...
Successfully installed driver!
```

Any ideas how to fix it please?

---

### Post by evris_beetlejuice on 2011-05-03
Please guys! Anyone?

---

### Post by luca2479 on 2011-07-05
Hi,  I had almost your same problem. on ubuntu 11.04 the webcam of my laptop wasn't recognised. I installed Camorama from the Ubuntu software center and magically the cam started to work.  Now it works fine with skype too (still have to try if works on pidgin or amsn). If your webcam won't work after installing Camorama , try to install Cheese it might work . Hope this will help :)

---

