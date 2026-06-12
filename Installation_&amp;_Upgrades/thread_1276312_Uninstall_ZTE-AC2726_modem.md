---
title: "Uninstall ZTE-AC2726 modem"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by barathguna on 2009-09-26
I recently got Reliance Netconnect (Modem - ZTE-AC2726, looks like a pendrive). The CD which they gave had a deb package and while installing I got the "Post installation failed with error code 1" error message.

After google I found a [blog ]("http://techsk.blogspot.com/2009/09/installing-usb-modem-zte-ac2726-in.html")explaining the installation of usb-modeswitch.

I added the "deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) karmic main universe" in my sources.list and while trying to run "apt-get install usb-modeswtich" I am getting the following error,

```
name@name-laptop:~$ sudo apt-get install usb-modeswitch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gcom wvdial
The following packages will be REMOVED:
  zteusbserial
The following NEW packages will be installed:
  usb-modeswitch
0 upgraded, 1 newly installed, 1 to remove and 1058 not upgraded.
1 not fully installed or removed.
Need to get 29.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://cz.archive.ubuntu.com karmic/universe usb-modeswitch 1.0.2-1 [29.7kB]
Fetched 29.7kB in 1s (24.2kB/s)        
(Reading database ... 169922 files and directories currently installed.)
Removing zteusbserial ...
ztemtvcdromd: no process killed
dpkg: error processing zteusbserial (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 zteusbserial
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Also when I try to update with "add/remove" or "synaptic package manager", same error pops out. When I marked the zteusbserial to uninstall in synaptic package manager same error pops out.

I assume the solution is to remove zteusbserial package. If so how to remove zteusbserial package?

FYI, I ran "apt-get remove zteusbserial" the output is,
```
name@name-laptop:~$ sudo apt-get remove zteusbserial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  zteusbserial
0 upgraded, 0 newly installed, 1 to remove and 1058 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 169922 files and directories currently installed.)
Removing zteusbserial ...
ztemtvcdromd: no process killed
dpkg: error processing zteusbserial (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 zteusbserial
E: Sub-process /usr/bin/dpkg returned an error code (1)
```~Barath

---

### Post by stlsaint on 2009-09-26
Try:

```
killall zteusbserial
```

---

### Post by barathguna on 2009-09-27
I tried killall and dpkg -r option.
```

barath@barath-laptop:/media/disk/setup/reliance$ sudo killall zteusbserial
zteusbserial: no process killed
barath@barath-laptop:/media/disk/setup/reliance$ sudo dpkg -r zteusbserial
(Reading database ... 169922 files and directories currently installed.)
Removing zteusbserial ...
ztemtvcdromd: no process killed
dpkg: error processing zteusbserial (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 zteusbserial
```


It is not possible for me to upgrade or install any other packages, when ever I upgrade or install a new package this zteusbserial removal error is coming.

~Barath

---

### Post by VijayakumarK on 2009-10-09
As you can see in the dpkg output, dpkg -r is failing because ztemtvcdromd couldn't be killed. It expects the daemon / script to be running. As it was not installed properly, the script never ran. I got it removed by creating a dummy script like this, and ran it from another console.
```

user@vijay-laptop:~$cat > ztemtvcdromd
#!/bin/bash
cat > test
user@vijay-laptop:~$chmod u+x ztemtvcdromd
user@vijay-laptop:~$./ztemtvcdromd


```
After the above is done, the new script should be running, just waiting for you to enter something. Now open another konsole, and run
```

user@vijay-laptop:~$sudo dpkg --remove zteusbserial
(Reading database ... 249626 files and directories currently installed.)
Removing zteusbserial ...
user@vijay-laptop:~$

```

I'm sure there probably is a better way to do it, but this is what I could quickly come up with, when I faced it.

---

### Post by unnipk on 2010-01-19
i'm facing a problem in removing zteusbserial. Came across the post in the forum. Tho I tried the steps you suggested the process initiated by the command
cat > ztemtvcdromd
#!/bin/bash
cat > test doesn't complete. I still tried to push on by typing in the remaining lines (chmod u+x ztemtvcdromd and ./ztemtvcdromd) and then opened another terminal to run 'sudo dpkg --remove zteusbserial'. A message saying
ztemtvcdromd: no process found is returned.

where did i make a mistake?

---

