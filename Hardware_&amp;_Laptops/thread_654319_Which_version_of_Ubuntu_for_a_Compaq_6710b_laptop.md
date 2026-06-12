---
title: "Which version of Ubuntu for a Compaq 6710b laptop"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by ocalld on 2007-12-30
Hi,
I've just got a Compaq 6710b with Intel® Core&#8482;2 Duo Processor.
i've installed ubuntu 7.10 x64 version. it installed ok and only needed a slight tweak to get graphics working correctly (default installed vesa).

I've tried to use apt-get, a basic upgrade is ok but when i try to install any apps it fails (i tried to install rpm, smart and alien).
A quick search on google produced that the problem lies with the intel processors, most packages on the 64bit are packaged for AMD processors, and when i run apt-get it realises  i have intel and stops the install; is this correct????

I really want to use apt-get, so if i install the x86 version (32bit), what would be the penalty to pay in terms of performance??? will it make full use of the dual core cpu?

If i stick with the 64bit, are there any repositories that have the apps for Intel 64 bit????  

thanks

---

### Post by erfahren on 2007-12-30
unless you do serious graphic or video editing the performance drop by using the 32-bit would be negligible, you probably wouldn't even notice it.

---

### Post by Luigi239 on 2007-12-31
Alright, I think some of your confusion has to do with the architecture of x64. AMD basically invented the 64bit arcitecture that we mostly use today, which is named amd64. After amd's release of 64 processors, intel followed along and produced processors following the same architecture. The only reason it is amd64 is that amd is the one who invented and popularized it. An Athalon and a Core2Duo will run a 64bit app identically.

Now for your trouble with apt-get, I am confused. You said that you tried to install an RPM. Ubuntu is a debian based distro, which uses debian packages (.deb) instead of Redhat packages (.rpm) like Fedora and Redhat itself. Therefore, it is impossible to install RPMs on Ubuntu, or any other debian based distro. (without a fair bit of hacking that is.)

Try running the command (sudo apt-get update) minus the () to update your repositorys, and then try installing an app such as amarok, abiword, ext. (sudo apt-get install amarok) to see if it works. Your trouble may be that you are just not typing the correct program name, it has nothing to due with the fact that you have an intel processor. (a good thing to read is [http://www.ccl.net/cca/software/UNIX/updating-redhat/apt-howto/how-to-use-apt-get.html](http://www.ccl.net/cca/software/UNIX/updating-redhat/apt-howto/how-to-use-apt-get.html) which is a good guide to using apt-get.) If I am not mistaken, if there is not a 64bit version of the app you want, the repo just uses the 32bit version, which works fine.

As for switching to 32bit, there will be no real performance loss on an everyday machine. My workhorse machine with 3gigs of ram and a 3ghz c2d runs 32bit Ubuntu just fine. I found it was just easier to go 32bit, as it seems to be a little bit easier to manage. (less tweaking, as in you don't have to go through a bunch of steps to install something as simple as flash. Also called lazyness.) The only reason I would say that you need 64bit is if you have >4 gigs of ram, as 32bit OSs will only see 3.

---

### Post by Sef on 2007-12-31
> I've tried to use apt-get, a basic upgrade is ok but when i try to install any apps it fails 

Have you opened the [Universe and Multiverse]("https://help.ubuntu.com/community/Repositories/Ubuntu") repositories?  Once you open them, you will be able to download a lot more software.  

Applications > Add/Remove > change the top box to 'All Available Applications'.   If the program you want is not there, then go to System > Administration > Synaptic Package Manager.

---

### Post by ocalld on 2007-12-31
> **Luigi239 said:**
> Alright, I think some of your confusion has to do with the architecture of x64. AMD basically invented the 64bit arcitecture that we mostly use today, which is named amd64. After amd's release of 64 processors, intel followed along and produced processors following the same architecture. The only reason it is amd64 is that amd is the one who invented and popularized it. An Athalon and a Core2Duo will run a 64bit app identically.

Now for your trouble with apt-get, I am confused. You said that you tried to install an RPM. Ubuntu is a debian based distro, which uses debian packages (.deb) instead of Redhat packages (.rpm) like Fedora and Redhat itself. Therefore, it is impossible to install RPMs on Ubuntu, or any other debian based distro. (without a fair bit of hacking that is.)

Try running the command (sudo apt-get update) minus the () to update your repositorys, and then try installing an app such as amarok, abiword, ext. (sudo apt-get install amarok) to see if it works. Your trouble may be that you are just not typing the correct program name, it has nothing to due with the fact that you have an intel processor. (a good thing to read is [http://www.ccl.net/cca/software/UNIX/updating-redhat/apt-howto/how-to-use-apt-get.html](http://www.ccl.net/cca/software/UNIX/updating-redhat/apt-howto/how-to-use-apt-get.html) which is a good guide to using apt-get.) If I am not mistaken, if there is not a 64bit version of the app you want, the repo just uses the 32bit version, which works fine.

As for switching to 32bit, there will be no real performance loss on an everyday machine. My workhorse machine with 3gigs of ram and a 3ghz c2d runs 32bit Ubuntu just fine. I found it was just easier to go 32bit, as it seems to be a little bit easier to manage. (less tweaking, as in you don't have to go through a bunch of steps to install something as simple as flash. Also called lazyness.) The only reason I would say that you need 64bit is if you have >4 gigs of ram, as 32bit OSs will only see 3.

HI
Thanks for the reply and advise.
The rpm is a package to allow you to install RPMs  on Debian type linux. I also use this on solaris which also dosen't support rpms.
My Apt-get would not install any additional software, i tried mplayer, even bash and they all failed.
On google, others had complained about this, and it was put down to Intel CPUs as apposed to AMD. 
As you said, it should work regardless of cpu, so i've rebuilt the system and it's all now working OK!!! apt-get installed RPM and i can now load rpms.

Thanks for the advice and link to apt-get help.
I decided to stick with the 64bit as i'm hoping it will work quicker with divX to dvd conversions.


Thanks.

---

