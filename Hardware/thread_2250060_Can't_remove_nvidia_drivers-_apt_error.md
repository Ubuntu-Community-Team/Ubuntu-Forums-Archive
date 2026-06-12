---
title: "Can't remove nvidia drivers- apt error"
date: 2014-10-26
forum: Hardware
---

### Post by c-m on 2014-10-26
I've got screen flicker issues with the nvidia-340 drivers to want to remove them and install the nvidia-331 package.
However the system has other ideas. Using the code below I get an error:
```
 sudo apt-get purge nvidia-340
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-340
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 267 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 200561 files and directories currently installed.)
Removing nvidia-340 (340.46-0ubuntu1~xedgers14.04.1) ...
stop: Unknown job: nvidia-persistenced
userdel: user nvidia-persistenced is currently used by process 1161
dpkg: error processing package nvidia-340 (--remove):
 subprocess installed post-removal script returned error exit status 8
Errors were encountered while processing:
 nvidia-340
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I've followed the commands in [https://answers.launchpad.net/ubuntu/+source/nvidia-kernel-common/+question/118010](https://answers.launchpad.net/ubuntu/+source/nvidia-kernel-common/+question/118010) but that isn't any help either.

---

### Post by tokyobadger on 2014-10-27
Sounds similar to a problem I encountered after upgrading to 14.10. Tried to upgrade drivers to nvidia 331, then nvidia 340, and finally nvidia 343. All had the screen flicker issues. Downgraded to nvidia 304 and all works well. Hoping that the issue is resolved soon.

To get past the error you describe, try the following:
```
ps ax | grep persistenced
```
Should show a process number, then
```
sudo kill 1234
```
where 1234 is the number that ps ax | grep showed you - you may need to click on the desktop to stop the flickering so you can read what's in the terminal
example
```
tb@box1:~$ ps ax | grep persistenced
10099 pts/7    S+     0:00 grep --color=auto persistenced
tb@box1:~$ sudo kill 10099
```
Hope that helps

---

### Post by harryadney on 2015-09-16
This worked for me, then followed the advice on this post: [http://askubuntu.com/questions/526571/apt-get-ends-up-with-errors-after-nvidia-331-installation](http://askubuntu.com/questions/526571/apt-get-ends-up-with-errors-after-nvidia-331-installation).

So far, so good.

---

