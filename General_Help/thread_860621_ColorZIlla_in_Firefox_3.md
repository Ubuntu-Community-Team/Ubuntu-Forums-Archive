---
title: "ColorZIlla in Firefox 3"
date: 2008-07-15
forum: General Help
---

### Post by mdawg414 on 2008-07-15
I have seen hundreds of threads dealing with getting the Firefox Plugin ColorZilla to work on older versions of Firefox but never Firefox 3.

I am running Ubuntu Hardy and v3.0 of Firefox. I tried updating the libxpcom files but that did not work. Has anyone been able to get this to work?

---

### Post by smilingfrog on 2008-08-05
I did. If you have a copy installed, uninstall it.
Then in a terminal, type: 
```
sudo apt-get install libxul-dev libstdc++5 gcc-4.1 libstdc++6
```

This downloads some libraries needed for colorzilla to work. Re-install colorzilla from the firefox add-on page, and restart.

Should work. 

:)G

---

### Post by Akovia on 2008-09-06
Didn't work for me =(

Ako

---

### Post by wolframarnold on 2008-10-20
Is this possible an issue with the 64 bit versions?  I'm running Hardy Kubuntu 64 bit.

I can't get it to work either (after trying the instructions posted).

---

### Post by Bartee on 2009-02-15
Did not work for me.. 64 bit...

VERY sad... I am a developer and this is a very power tool for website design.

HELP !!!!

---

### Post by HanDuo on 2009-05-02
Hi Bartee,

don't worry to much. Usually there is always a second solution. As long as there is no ColorZilla for Ubuntu_64amd, try Gcolor2 instead. Just look for it in the ubuntu package browser/manager.

Simple but helpful tool...

---

### Post by Bartee on 2009-05-02
Thanks....

I did find a color thing in Unbuntu

With "eye dropper" etc.. Works just fine..

---

### Post by Arancaytar on 2010-01-05
Installing libxul-dev is not possible without removing the package ubuntu-desktop. That's a good indicator of something being a bad idea...

In particular:

```

$ sudo apt-get install libxul-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjaxp1.3-java eclipse-platform-data libxerces2-java libgcj-bc gcj-4.4-base
  eclipse-rcp gcj-4.4-jre-lib libgcj10 ant ant-optional libswt-gtk-3.5-jni
  ant-optional-gcj libequinox-osgi-java libgcj-common libswt-gtk-3.5-java
  ant-gcj
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmozjs-dev libmozjs0d libreadline5 libxul-common libxul0d xulrunner
Suggested packages:
  xulrunner-gnome-support
The following packages will be REMOVED:
  couchdb-bin desktopcouch eclipse eclipse-jdt eclipse-pde eclipse-platform
  eclipse-plugin-cvs evolution-couchdb evolution-documentation-en firefox
  firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-gnome-support gnome-user-guide python-desktopcouch
  python-desktopcouch-records ubufox ubuntu-desktop ubuntu-docs
  xulrunner-1.9.1 xulrunner-1.9.1-dev xulrunner-1.9.1-gnome-support
  xulrunner-dev yelp
The following NEW packages will be installed:
  libmozjs-dev libmozjs0d libreadline5 libxul-common libxul-dev libxul0d
  xulrunner
0 upgraded, 7 newly installed, 25 to remove and 0 not upgraded.
Need to get 11.8MB of archives.
After this operation, 446MB disk space will be freed.

```

(This is on Karmic.)

The particular problem seems to be that libxul-dev conflicts with xulrunner-1.9.1, which triggers the above dependency avalanche.

I see there is already an open bug for this:

[https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9.1/+bug/486079](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9.1/+bug/486079)

---

### Post by flaviudsi on 2010-07-08
> **Bartee said:**
> Thanks....

I did find a color thing in Unbuntu

With "eye dropper" etc.. Works just fine..

Hi Bartee, can you plese name the "color thing" you have found?

Thanks.

---

