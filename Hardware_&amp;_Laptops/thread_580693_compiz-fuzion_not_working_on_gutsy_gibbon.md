---
title: "compiz-fuzion not working on gutsy gibbon"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by donald7777 on 2007-10-19
I just downloaded Ubuntu 7.10 and finished setting everything up. The only major problem is Compiz just wont work. I have tried the open source ati driver and the built-in driver from Ubuntu.

my laptop is a gateway MT6451
ati xpress 1150 video card
ubuntu 7.10 with all updates

please help.

by the way way isn't beryl here anymore ? on Ubuntu 7.04 I had nothing but problems with compiz, but beryl worked just fine.
and is there anyway for the monitor brightness to be controlled with the control (it doesn't work)

---

### Post by dantum on 2007-10-19
I have ATI Xpress 200M card, which is similar to yours. The way i enabled effects is by doing this.

enable restricted drivers supplied with ubuntu.
install xserver-xgl package
reboot

And it worked.


I had many problems in the past with my card but the supplied software worked fine. 
If you installed any other drivers i suggest you uninstall them before following the procedure.

---

### Post by donald7777 on 2007-10-19
ok ill try that when i get home thx.

---

### Post by donald7777 on 2007-10-19
ok that worked thankyou.

---

### Post by mate84 on 2007-10-28
Hello,
I have a Dell vostro 1000 laptop with ATI 1150. In the restricted drivers manager I got this error: xorg-driver-fglrx is missing and after when I install it I get this information: fix broken packages first. And in the terminal:
mate@mate-laptop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed. You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
mate@mate-laptop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for mate:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages
mate@mate-laptop:~$

At the moment I have large icons.....
Can anybody help me?

---

### Post by donald7777 on 2007-10-28
try installing all the packages it needs from adaptic package manager. (sorry if the names wrong) I did that instead of sudo apt-get blah blah. try that and see if it works.

---

