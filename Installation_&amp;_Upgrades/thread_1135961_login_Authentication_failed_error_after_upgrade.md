---
title: "login Authentication failed error after upgrade"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by beavisx on 2009-04-24
I was running 8.10 on my laptop with autologin when I thought I'd upgrade to 9.04 but once it was done the login screen comes up for a second and then says "Authentication failed" and nothing I can do to get by it can someone help me get back in.

Thanks

---

### Post by cakeslice on 2009-04-24
I am having the same problem. After upgrading from update manager and rebooting, the login screen showed up, but then half a second after a small message box pops up saying "Authentication Failed".  I can login in console mode (i.e. pressing alt+shift+f1 then logging in), but i can't startx from there. Just like beavisx, I set my pc up to autologin when it was still 8.10.

Does anyone have a solution for this?

---

### Post by beavisx on 2009-04-25
> **cakeslice said:**
> I am having the same problem. After upgrading from update manager and rebooting, the login screen showed up, but then half a second after a small message box pops up saying "Authentication Failed".  I can login in console mode (i.e. pressing alt+shift+f1 then logging in), but i can't startx from there. Just like beavisx, I set my pc up to autologin when it was still 8.10.

Does anyone have a solution for this?

Let me know if you solve it before me.

Thanks

---

### Post by beavisx on 2009-04-26
> **cakeslice said:**
> I am having the same problem. After upgrading from update manager and rebooting, the login screen showed up, but then half a second after a small message box pops up saying "Authentication Failed".  I can login in console mode (i.e. pressing alt+shift+f1 then logging in), but i can't startx from there. Just like beavisx, I set my pc up to autologin when it was still 8.10.

Does anyone have a solution for this?

Got it cakeslice

boot it up

ctrl-alt-f1
put in your username & password
then type in terminal...

sudo nano /etc/pam.d/gdm

look for this..

@include common-pamkeyring

and remove this line.

alt x to exit

it will ask if you want t modify the file say "y" and then reboot

that should do it.

---

### Post by CTolley on 2009-05-02
Funny, I added that line as part of a fix for a 'default keyring' issue.  But, I will be okay with entering the keyring password as many times as is needed if I'm able to reboot with ease.  TY beavisx

---

