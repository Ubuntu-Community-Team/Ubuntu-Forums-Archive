---
title: "mysql not installed from APTonCD"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by bilol on 2008-12-08
Hi friends,
I am very new to ubuntu.In a machine connected to internet **mysql** is working fine.Then I created an APTonCD and try to install mysql in a machine not connected to internet.Here I am getting the following error:
```
bilol@bilol-desktop:~$ sudo apt-get install mysql-client-5.0

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



The following packages have unmet dependencies:

  mysql-client-5.0: Depends: libdbd-mysql-perl (>= 1.2202) but it is not installable

                    Depends: libdbi-perl but it is not installable


```

There is no problem installing other packages from APTonCD. Please suggest what to do?
Thanks in advance.....

---

### Post by mk1w86 on 2008-12-08
Are the dependencies libdbd-mysql-perl and libdbi-perl on the CD?
If so are they the correct versions?

---

### Post by bilol on 2008-12-12
Hi,
Those two packages are present in the online machine, but when I am creating the APTonCd (in the online machine for the offline machine),they are not written in the CD and hence mysql can not be installed in the offline machine.
Require your valuable suggestion....

---

### Post by unutbu on 2008-12-12
According to [http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396), APTonCD only reads /var/cache/apt/archives to find .debs. This directory gets erased whenever you run
```

sudo apt-get clean
```

You can test this claim by going to the online machine, opening a terminal (Applications>Accessories>Terminal) and typing
```

ls /var/cache/apt/archives/libdbd*
ls /var/cache/apt/archives/libdbi*
```

If the deb files are not listed, then this might be the reason why APTonCD failed to archive those packages. If that is the case, then it seems likely to me that there will be other missing packages as well, so perhaps APTonCD is not the right tool for the job.

If you are transferring packages just this once, then the quick and dirty method to fix the problem is to go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), search for libdbd-mysql-perl and libdbi-perl and download the .deb files and use a USB thumb drive to transfer them to the offline machine.

If you are interested in making CDs with all the packages on your online machine,
then I recommend you use abhiroopb's method ([http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)) since it doesn't suffer from the problem explained above.

---

### Post by bilol on 2008-12-16
Hello,
Thanks for your suggestion,but I did not run 
```
sudo apt-get clean
```

Let me explain the strange ( might be usual for non-newbie) thing I found while creating aptoncd for mysql:
All the rquired packages for mysql were  present in the online machine . When I created the ***first*** aptoncd , I found the package **“libdbd-mysql-perl “** was not present.Then I remove mysql from the online machine and again install it and created the aptoncd for the ***second*** time. In this time the package “libdbd-mysql-perl “ was present in the aptoncd. But again while installing it in the offline machine it gave dependency error as the package **“libdbi-perl “** was absent. I removed mysql again from the online machine and installed it and then created the aptoncd for the ***third*** time.Now I find both  the packages viz. “libdbd-mysql-perl “ and  “libdbi-perl “ were present in the aptoncd.While installing mysql for the third time in the offline machine it gave dependency error again as the package **“libplrpc-perl “** was absent.
The above phenomenon is appearing strange to me *as the aptoncd is not showing consistency for copying packages*.How long will this dependency problem continue?Where(path) do these packeages actually reside in the online machine?Will I be able to collect them manually and later install them in the offline machine without opening 'synaptic package manager'?
Thanks in advance.....

---

### Post by bilol on 2008-12-17
Oh yeeh..I have done it.
Thank you all for your valuable suggestion.
Only  two extra packages need to be downloaded.
If any of the beginners are facing the same problem as mine he should be doing the following :
1. Install mysql client and server in the online machine.
2. Create the APTonCD.
3. From [here]("http://packages.debian.org/etch/libdbi-perl") download the following packages and install them one by one manually in the offline machine in the order shown below:
  (a)libnet-daemon-perl
  (b)libplrpc-perl
  (c)libdbi-perl
  (d)libdbd-mysql-perl 
 < N.B. In my case all other related dependent packages are burnt into the APTonCD >
4. Install mysql server and mysql client from the APTonCD in the offline machine.

Thats it....

---

