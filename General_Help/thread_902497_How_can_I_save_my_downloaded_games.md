---
title: "How can I save my downloaded games??"
date: 2008-08-27
forum: General Help
---

### Post by MIH1406 on 2008-08-27
Hi,

I have Ubuntu 8.04 installed and I want to format it and install it again but in the first install I have downloaded many games and software that are not already installed.

How can I save these games and software files, my DSL line is 128 KB very slow to reinstall more than 300 MB for one file.

Another thing:
How can I install Ubuntu without any software installed I do not need Evolution or any other software to be installed.

Is there any option in the Installation wizard for very minimal installation for Ubuntu Hardy

Thanks

---

### Post by xravexheavenx on 2008-08-27
To save your stuff, you could just back it up to an external.

As far as installing a bare-bones...  You could use the barebones distro provided at the Ubuntu site or just remove them using Synaptic after installation.

---

### Post by Elfy on 2008-08-27
If you are talking about things you have downloaded with synaptic or apt-get/aptitude you could use aptoncd or just backup your apt cache - I copy the cache, by backing it up one way or the other. 

The cache is in 
/var/cache/apt/archives

You should have everything that you have downloaded in there - unles you have run apt-get clean at some point.

---

### Post by MIH1406 on 2008-09-01
What is 'bare-bones'???

---

### Post by Elfy on 2008-09-01
There is a minimal cd - you have to tell it what to install and download; therefore if you didn't want certain things then you don't get them.

But the question is do you have packages in your apt cache - as I said assuming that you haven't run apt-get clean then the packages should still be there.

Check the size of the folder - /var/cache/apt/archives.

When you said you donwloaded games and software - where did you get them from? If you got them through add/remove, synaptic or using apt-get/aptitude then the packages will be in the apt cache.

If you got them from external sources and didn't keep the installer then you will need to do so again. You can't save the installed files though.

So assuming that you have a good burn of the iso and also have a full apt-cache then you won't need to use a minimal install. Obviously though you'll need to copy the cache prior to a reinstall.

---

