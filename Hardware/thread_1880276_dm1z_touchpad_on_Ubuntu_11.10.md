---
title: "dm1z touchpad on Ubuntu 11.10"
date: 2011-11-13
forum: Hardware
---

### Post by -Shuji- on 2011-11-13
I just installed Ubuntu 11.10 to my dm1z and now I'm having a problem with my touchpad. The problem is that right-click doesn't work and can't do drop and drag.  It has been like this with 11.04 but the solution I did before doesn't work anymore.
Solution for 11.04 -  [http://ubuntuforums.org/showpost.php?p=10744640&postcount=202](http://ubuntuforums.org/showpost.php?p=10744640&postcount=202)

While trying to execute 'dpkg-buildpackage -us -uc -rfakeroot', I got the error below.
```
Applying patch 203-xorg.conf.d_snippet.patch
patching file conf/50-synaptics.conf
Hunk #1 FAILED at 3.
1 out of 1 hunk FAILED -- rejects in file conf/50-synaptics.conf
Patch 203-xorg.conf.d_snippet.patch does not apply (enforce with -f)
dh_quilt_patch: quilt --quiltrc /dev/null push -a || test $? = 2 returned exit code 1
make: *** [build] Error 25
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```I don't understand what this means.  Is there an easier way to make right-click work on a dm1z touchpad when running 11.10?  I hope someone can help.  Thanks.

Shuji

---

### Post by titan99855 on 2011-11-30
I have the same problem. I too would like a solution.

---

### Post by Redblade20XX on 2011-11-30
I have a dm1z. Drop and drag worked for me out of the box. For right clicking, did you try a three finger press?

- Red

---

### Post by -Shuji- on 2011-11-30
> **titan99855 said:**
> I have the same problem. I too would like a solution.

Titan99855, thank you for making yourself known here.  I still have the problem.  I hope we find a solution.

Shuji

---

### Post by -Shuji- on 2011-11-30
> **Redblade20XX said:**
> I have a dm1z. Drop and drag worked for me out of the box. For right clicking, did you try a three finger press?

- Red

Red, the reason why drop and drag doesn't work is because the right and left click buttons are not just normal buttons but also part of the touchpad.  It means that you can make the mouse pointer move even when your dragging your finger across those buttons.

If you want to move an icon, you click it and hold the left click button.  The problem starts the moment your other finger touches the touchpad so you can drag it somewhere.  I don't understand why it worked for your out of the box.  I saw this problem both on 11.04 and 11.10.

Shuji

---

### Post by titan99855 on 2011-12-20
Shuji

I guess one thing that helps us find answers to this is not to search for "touchpad" help since we have "clickpads". Here are some promising looking fixes and a bug report. I will try the PPA fix tonight and see how it goes.

[http://ubuntuforums.org/showthread.php?p=11384846](http://ubuntuforums.org/showthread.php?p=11384846)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/275](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/275)

---

### Post by titan99855 on 2011-12-20
It would seem we have a workaround. Add the repository as shown and update. Definitely not a solution, but it is quite helpful in the meantime. It is very nice to be able to right click again.



sudo add-apt-repository ppa:sergio91pt/synaptics+clickpads

sudo apt-get update

sudo apt-get dist-upgrade

sudo reboot



Should be working after it reboots. Good luck!

-Eric

---

### Post by -Shuji- on 2011-12-21
> **titan99855 said:**
> It would seem we have a workaround. Add the repository as shown and update. Definitely not a solution, but it is quite helpful in the meantime. It is very nice to be able to right click again.



sudo add-apt-repository ppa:sergio91pt/synaptics+clickpads

sudo apt-get update

sudo apt-get dist-upgrade

sudo reboot



Should be working after it reboots. Good luck!

-Eric

Eric, this is THE only solution.  It took 1 month and 9 days to finally solve this issue.  My Ubuntu 11.10 is so much better now and that's because of you so THANK YOU so much.  I will mark this as solved.

Shuji

---

### Post by alpine4 on 2012-01-05
> sudo add-apt-repository ppa:sergio91pt/synaptics+clickpads
sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot

This also worked for me on my HP dm1 netbook, thanks Eric!

---

