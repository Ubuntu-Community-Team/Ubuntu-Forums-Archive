---
title: "trouble with java plugin for firefox 3 on hardy"
date: 2008-07-25
forum: General Help
---

### Post by harrybazeegar on 2008-07-25
Hi...

I am using ubuntu Hardy, and firefox 3, and I am having trouble with java plugin for it.

I have installed jdk in /opt/jdk, and I tried to install java plugin for firefox in this way:

```

cd ~/.mozilla/plugins
ln -s /opt/jdk/jre/plugin/i386/ns7/libjavaplugin_oji.so .

```

Then I restarted firefox. On starting it again, I could see that the plugin is installed (in the Tools->Addons->Plugins).

BUT WHEN I TRY TO RUN ANY JAVA APPLET IN THE BROWSER, FIREFOX JUST FREEZES!

what do I do?

---

### Post by Duranxl on 2008-07-25
Are you on 32bit or 64bit?

---

### Post by harrybazeegar on 2008-07-25
32 bit system, intel

---

### Post by Duranxl on 2008-07-25
so what about 
sudo apt-get install sun-java6-plugin

or installing it via add/remove programs?

---

### Post by harrybazeegar on 2008-07-25
oh, you see, I have a problem, you see. I don't want it to happen automatically.
I want to do it by hand, and if it does not work, I want to know why. Maybe after that I'd do the automatic apt-get installation.

So how do I find out what goes wrong? Any logs I need to check? any exit code or status of that sort?? plzzzz what is wrong?!

---

### Post by harrybazeegar on 2008-07-26
/bump

any help??

---

