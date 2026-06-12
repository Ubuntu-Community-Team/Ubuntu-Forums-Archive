---
title: "gxine - updated?"
date: 2005-11-18
forum: General Help
---

### Post by Halvorsen on 2005-11-18
In one way or another I managed to install the latest version of gxine(0.5.0) - don't ask me how (a multimediaplayer I really fancy), and everything went so slooow I just had to do a clean install with Ubuntu 5.10

I dl gxine from here: [http://xinehq.de/index.php/releases](http://xinehq.de/index.php/releases)

Is there a way to update programs like gxine in Ubuntu, or am I (as a newbie) stuck with synaptic?

---

### Post by anton123 on 2005-11-18
Hello,

I don't know how comfortable you are with compiling from source code but I will try to direct you along the way if needed.
First of all, do

sudo apt-get intstall build-essential

This package will install the C/C++ compilers and required libraries.

Second, do

sudo apt-get install checkinstall

This package will allow you to build *.deb packages. See the man pages for more info. The basic command is " sudo checkinstall -D package_name". To build package you have to be in the folder where the source code has been already compiled.
Once you have your *deb package created do, sudo dpkg -i package_name.

After you install it, it will appaera listed in Synaptic also.

Ask any questions you have left and I will do my best to see how I can be of help. Mind that I am VERY new to Linux.

---

### Post by Halvorsen on 2005-11-19
The two first steps went well, but I'm a bit confused about the last steps.

The gxine-page, [http://xinehq.de/index.php/releases](http://xinehq.de/index.php/releases) tells me I need **xine-lib**. When searching in Synaptic, it tells me I got totem and totem-xine installed. There is no xine-lib.

Can I simply do sudo checkinstall -D package_name like this (in terminal)

[PHP]wget http://prdownloads.sourceforge.net/xine/xine-lib-1.1.1.tar.gz
tar xfvz xine-lib-1.1.1.tar.gz
sudo checkinstall -D xine-lib-1.1.1[/PHP]

And then do the same with gxine?

---

### Post by anton123 on 2005-11-19
Hi,

"When searching in Synaptic, it tells me I got totem and totem-xine installed. There is no xine-lib."

To get xine-lib, you need to go to preferences -> repositories and select Universe since the Universe repository is not enabled by default. I am not sure if the steps are under the exact names since I do not use Ubuntu for some time but I plan on reinstalling it again to reget fresh with it. Then, xine-lib should be displayed. However, the last time I checked version 1.0.1 is there. So, the best is to download the xine-lib 1.1.1 from [www.xinehq.de](www.xinehq.de).

"wget [http://prdownloads.sourceforge.net/xine/xine-lib-1.1.1.tar.gz](http://prdownloads.sourceforge.net/xine/xine-lib-1.1.1.tar.gz) 
tar xfvz xine-lib-1.1.1.tar.gz 
sudo checkinstall -D xine-lib-1.1.1"

The "wget" line ignore if you are going to get the library from xinehq.de
Yes, issue "tar -xfvz xine-lib-1.1.1.tar.gz" if that is correct since I am not that proeficiet yet at console mode.
"sudo checkinstall -D xine-lib-1.1.1", no, not yet.
"xine-lib-1.1.1.tar.gz" is just the source code. After you extract it to a folder on the desktop presumbly, open console, go to that folder and issue ./configure to get things going (Does anyone know if ./configure actually compiles the source or is it make that does it?). Next, run "make". Depending on the computer speed it will take some time.
Now, coming to "checkinstall". This tool not only makes a *.deb package but also installs it after making it in the same session. So, open a new console or use the existing one. Make sure you are still in the folder path where the source code was extracted. It is in the same path that the code was also compiled. Now do "sudo checkinstall -D" Notice that I did not put any anme after the -D option. I forgot if you must or not. I f you do not put the name, the package will have the same name as "xine-lib-1.1.1" I presume but I am sure that you can rename it since during the steps of package creation you are offered the option to change a few parameters including the name of the package. If all went well, the package should be created in the same folder where the source code was compiled and also installed. Fire up Synaptic and serach under Installed for xine, you should see version 1.1.1 and something like xine-lib as name.

Follow the same steps for the gxine tar archive and any other archives that are source code to make a package/have it installed.

My post sounds confusing, I know, but I am too since I did not do this for quite some time and whenever I did it, I did it my style, like this one.

I hope this helps.

---

