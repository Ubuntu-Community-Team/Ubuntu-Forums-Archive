---
title: "State of packages after removal?"
date: 2008-11-22
forum: General Help
---

### Post by dizwell on 2008-11-22
I installed Virtualbox OSE via the Add/Remove function. Then I realised that didn't have USB support, so I installed the debian package for the closed-source version available from the Virtualbox.org website. 

So I used the Applications -> Add/Remove function to get rid of the OSE version, and used dpkg to add the non-open source version. 

Then I decided to remove that, and did a **dpkg -r virtualbox-2.0**

Now when I do a dpkg --get-selections, I see this:

[FONT="Courier New"]vino						install
virtualbox-2.0					deinstall
virtualbox-ose					deinstall
vlc						install
vlc-data					install
vlc-nox						install[/FONT]

It certainly says the two packages have been deinstalled. My question is: have they really been? When does the fact that these two packages ever touched my system disappear? When, in other words, will the output of the --get-selections command simply not show anything about VirtualBox at all?

Is there some way to purge the list of packages so that it only shows installed packages, rather than including ones which once were installed but now are not? :confused:

I should mention, perhaps, I'm on 8.10.

---

### Post by swoody on 2008-11-22
Try going into Synaptic Package Manager, and under the left hand side select "Status" and then above that select "Not Installed (residual config)" and that will list all the packages that still have some config files on your computer. Click on the boxes for those packages and select "Mark for Complete Removal" and then "Apply" and that should take care of it. 

Also, in a terminal you can type:
```
sudo apt-get autoclean
```

This will help you out with removing more old program files, but you must be careful. Read over what it's about to remove, and make sure it's nothing important!!

You can also add deborphan and use that to remove orphaned packages that are no longer needed:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Normally it's very hard to remove ANY trace of a program, but you can get most of it gone without doing a clean install. Try all this out, and let me know how it works :)

---

