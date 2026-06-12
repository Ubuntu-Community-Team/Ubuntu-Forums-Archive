---
title: "Killed my system with fakeroot!"
date: 2005-11-12
forum: General Help
---

### Post by hornett on 2005-11-12
I'm not exactly sure what I've done here, but my system appears to be completely borked!

I was using checkinstall to compile a package from source (new version of leafpad) however it was moaning about being unable to create various files so I tried instead **"fakeroot checkinstall -D make install"**. Again, this was no go, so I gave up and did **"sudo checkinstall -D make install"** which did work.

Obviously something went badly wrong when I did this, because now when booting my system, I get loads of permission denied errors when the services try to start.

X doesn't start, so I tried to log in on the command line. Unfortunatley I can't because it is "Unable to cd to /home/retro". Log in works as root, so I checked that my home dir was owned by retro (my main user acc) which it was.

As root, I tested various commands, including sudo. Sudo was unable to open /etc/sudoers, despite the permissions being apparently correct. Next I tried fakeroot sudo and it worked! Clearly I must have messed *something* up with fakeroot. But I'm not sure how, or what I have done!

Any help much appreciated.

*(looks like I might be upgrading to Breezy sooner than I thought! ;))*

---

### Post by tseliot on 2005-11-12
You can try to reinstall "sudo" in Synaptic.

However I suggest you to install Breezy from scratch and to use Automatix to have the non free packages (and other cool stuff) by pressing a button or two (yes, it is that easy)

---

### Post by hornett on 2005-11-12
Thanks, I don't think the problem is with sudo itself though.... It seems that fakeroot has set some files uid wrongly or something (although they appear correct).

Breezy is looking increasingly like the solution here ... mmm fresh install! ;)

---

