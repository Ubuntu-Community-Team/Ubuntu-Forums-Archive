---
title: "upgrade to 9.09  and  sudo dpkg --configure -a   hang"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by geevn on 2009-08-14
I have upgraded to 9.09 and interrupted the install when it was taking way tooo long,
by restarting the virtual machine. I have installed and used earlier versions of ubuntu studio
just fine. After the restart, everything is normal and I got a lot of new and upgraded programs.

When I tried to run synaptic package manager, I got the error as seen in the screenshot attached.
Then I go to a term. and run    sudo dpkg --configure -a
The command was taking more than an hour and a half, and hangs at
"creating /etc/ssl/certs/java/cacerts ..."  I couldn't interrupt the command or the terminal nor could
start system monitor or other apps. The only way out was to restart the virtual machine

---

### Post by geevn on 2009-08-14
sorry I forgot to actually ask the question and request help.
I really appreciate any help in getting past this problem, completing the install, and  getting package manager to work again. Thanks.

---

### Post by geevn on 2009-08-15
After reading man pages for dpkg, I went ahead and did 
dpkg --audit and listed the pkgs that need to be configured.
I purged the offending package, which was ca-certificates-java.
Since it was safe to use the --force-depends flag, i went ahead and
used it, to actually purge the pkg. That fixed it

---

