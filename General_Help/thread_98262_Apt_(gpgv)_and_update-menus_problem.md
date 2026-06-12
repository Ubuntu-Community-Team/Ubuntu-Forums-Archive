---
title: "Apt (gpgv) and update-menus problem"
date: 2005-12-02
forum: General Help
---

### Post by teprrr on 2005-12-02
Hello there,

just wanted to ask if anyone is having same kind of problems like I have and if they can be fixed somehow. For a while I haven't been unable to run apt-get update as it fails on key checking (gpgv) for some reason. The error I got is: "E: Method gpgv has died unexpectedly!". Removing gnupg solved the problem but it's only temporary fix as the apt will install gnupg back anytime.

Another problem I'm having is that no package will be configured properly because of failure on postinst scripts. This happens because update-menus.real, which is called on apps who have a menu entry, simply sigsegvs every time it's run and then the apt will get stuck until I press ctrl+c to interrupt it. This has became annoying as the list of programs has grown and everytime I want to install something I need to keep pressing. And if you press too fast, you'll have to run dpkg --configure -a and then re-run the install.

So, can anyone help me with these problems? Please.

---

### Post by teprrr on 2005-12-03
No one have seen anything like this? I've tried already to Google and asking on IRC without success... :(

---

