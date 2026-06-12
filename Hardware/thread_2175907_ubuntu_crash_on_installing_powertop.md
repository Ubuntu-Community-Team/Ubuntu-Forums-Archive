---
title: "ubuntu crash on installing powertop"
date: 2013-09-21
forum: Hardware
---

### Post by elang on 2013-09-21
I am running Ubuntu 13.04 64b on a Dell Inspiron N5010.

In order to optimise the power, I attempted to install Powertop via the Software-Center (along with the 2 suggested options).
I don't even know if the install was completed, but the system crashed into some black screen with a lot of text, and I have not been able to boot back since.

I get the Ubuntu loading screen:
[IMG]http://www.thefanclub.co.za/sites/default/files/styles/300-wide/public/images/howto/ubuntu-boot-splash.png?itok=9AT2L2e9[/IMG]
but after all that I get is a black window with text and not the login screen.


I do not want to reinstall Ubuntu again. Is there a way to uninstall Powertop or other ways to fix this?
I am more than willing to share any info that is needed (provided you can tell me how to get it). I have ext2explore installed on Windows and a live USB too, posting any logs should not be trouble.

---

### Post by sudodus on 2013-09-21
What kind of screen do you get? Is it a text login screen, where you can enter the user and after that the password? In that case, you can probably uninstall powertop. The first assumption is that the package name is the same, powertop. So try

```
 sudo apt-get purge powertop
```

and reboot.

If it is not the 'text login screen', you can another menu entry at the grub menu: Select 'advanced options' and then 'recovery mode', when you can get a root prompt and run

```
 apt-get purge powertop
``` (because you are already root alias superuser).

If you see no grub menu, you can press the left shift key (upper-case key) at once when booting, and it should appear after a few seconds.

---

### Post by elang on 2013-09-21
Did it as root from recovery.

It also turned out that the kernel got spoilt, so I had to use an older one to boot. Then reinstalled the latest one to get it working

---

