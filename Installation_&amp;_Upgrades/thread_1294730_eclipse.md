---
title: "eclipse"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by Quaker on 2009-10-18
Hi all,

I've installed karmic beta version and a strange thing happened i'm a developer and i've copied my galileo version of eclipse into the new karmic but when i try to create a new project the wizard just gets stuck...

So i've tried to download the eclipse from the repositories the same thing happened i can't create new projects... no errors no nothing?? can anyone help me?

i've used a password to encrypt my home folder.... a new feature from ubuntu

thanks in advanced

---

### Post by cherva on 2009-10-18
You can try to:

1) Try to only save a file to test if there is a bug and eclipse can't write to the file system.
2) Run eclipse from terminal and search for errors there when you create a new project.

---

### Post by Quaker on 2009-10-20
It's possible to create a file i just can't create projects this instalation was running fine in the previous instalation (jaunty)


when i run from the console, with sudo, the result is the same...

---

### Post by watchamcb on 2009-10-22
Hi,

I am having a similar problem but I it seems to be an issue with Eclipse/Java not registering mouse events on certain buttons. If you use the shortcut key for the button (Alt+underlined letter - Alt+n for example) then the wizard continues.

The Eclipse installed through apt-get does not appear to have this problem (I also reinstalled sun-java6) but this version does not refresh certain screens (like the software updates) so you can't install the latest plugins. This also seems to be a problem with various other Java apps.

Hope that helps.
Craig

---

### Post by sloggerkhan on 2009-10-22
maybe it needs a different jre than what's installed default?

---

### Post by Quaker on 2009-10-22
I've installed sun jre! Well i don't if the problem is in eclipse. Because, like i said, the same eclipse was working on jaunty... all i've done was a copy from jaunty to karmic and i've tried to run other version like cdt and the problem remains. But the same copy on jaunty works. I went further i've dowloaded the windows version and run it on windows and it worked. The only thinhg that is diferent is that jre is an inferior version on windows.

---

### Post by patrick.c on 2009-10-28
Have a look at [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/442078](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/442078)

The suggested "fix" with the environment variable works for me.
   
   export GDK_NATIVE_WINDOWS=true

Hope it helps

---

### Post by GilbertEvanG on 2009-10-29
> **patrick.c said:**
> Have a look at [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/442078](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/442078)

The suggested "fix" with the environment variable works for me.
   
   export GDK_NATIVE_WINDOWS=true

Hope it helps


Thank you! That solved all of my weird UI problems I have having.
Hopefully this is only a temporary solution.

---

