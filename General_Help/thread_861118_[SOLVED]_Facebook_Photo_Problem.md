---
title: "[SOLVED] Facebook Photo Problem"
date: 2008-07-16
forum: General Help
---

### Post by psychok7 on 2008-07-16
hey there guys, well im using firefox 3 on ubuntu 8.04 and since the firefox final release or something else i cant see my photos on facebook. i logged into windows, and firefox 3 there shows me everything.. have any ideia whts the problem? i have flash and java installed.
i remember it did work before on linux, now it simply doenst

---

### Post by jamesstansell on 2008-07-16
> **psychok7 said:**
> hey there guys, well im using firefox 3 on ubuntu 8.04 and since the firefox final release or something else i cant see my photos on facebook. i logged into windows, and firefox 3 there shows me everything.. have any ideia whts the problem? i have flash and java installed.
i remember it did work before on linux, now it simply doenst

I'm not very familiar with photos on facebook, but I have heard of some problems with uploading photos, which is related to Java.

To switch the java from openjdk (the ubuntu 8.04 default) to Sun's proprietary package, here are the steps.

```
$ sudo apt-get remove icedtea-gcjwebplugin
$ sudo apt-get install sun-java6-plugin
$ sudo update-java-alternatives -s java-6-sun
```

(This assumes a 32bit system.  For 64bit, there is no sun-java6-package.)

The openjdk-6 packages are from Sun, but they didn't include the Java plugin.  The GCJ web plugin works well for some applets but doesn't work for a large class of applets.  A major improvement is being worked on but I don't think there's a timeframe for it yet.

---

### Post by psychok7 on 2008-07-16
> **jamesstansell said:**
> I'm not very familiar with photos on facebook, but I have heard of some problems with uploading photos, which is related to Java.

To switch the java from openjdk (the ubuntu 8.04 default) to Sun's proprietary package, here are the steps.

```
$ sudo apt-get remove icedtea-gcjwebplugin
$ sudo apt-get install sun-java6-plugin
$ sudo update-java-alternatives -s java-6-sun
```

(This assumes a 32bit system.  For 64bit, there is no sun-java6-package.)

The openjdk-6 packages are from Sun, but they didn't include the Java plugin.  The GCJ web plugin works well for some applets but doesn't work for a large class of applets.  A major improvement is being worked on but I don't think there's a timeframe for it yet.

i have sun-java6-plugin already installed..guess that not my problem

---

### Post by jamesstansell on 2008-07-16
> **psychok7 said:**
> i have sun-java6-plugin already installed..guess that not my problem

That's good.  But it's easy to have it installed and still not have the browser use it.

Is the Java Plugin listed in this list of plugins?  What version shows up?

[http://gemal.dk/browserspy/plugins.html](http://gemal.dk/browserspy/plugins.html)

Do 2 java plugins show up in the list?

---

### Post by psychok7 on 2008-07-17
> **jamesstansell said:**
> That's good.  But it's easy to have it installed and still not have the browser use it.

Is the Java Plugin listed in this list of plugins?  What version shows up?

[http://gemal.dk/browserspy/plugins.html](http://gemal.dk/browserspy/plugins.html)

Do 2 java plugins show up in the list?

i get java-plugin 1.6.0_06-b02 .. i have attached a screenshot.. and it seems to be the only java in the list..any more ideias?

---

### Post by jamesstansell on 2008-07-17
> **psychok7 said:**
> i get java-plugin 1.6.0_06-b02 .. i have attached a screenshot.. and it seems to be the only java in the list..any more ideias?

Sounds like not a Java problem then.  My only other idea is to check your Firefox extensions.  They sometimes cause problems, but I honestly haven't ever heard of a specific issue with facebook.

---

### Post by sukamusiru on 2008-07-17
Might want to also check your firewall configuration(s). Can you use the chat?

---

### Post by mildayil on 2008-08-25
I have the same problem and my own post on these forums about it .. no one has been able to solve it .. although I doubt it's a priority for anyone but us lol 
I want to leave XP behind for good .. and I am just a facebook away ! grrr

---

### Post by bear24rw on 2008-08-26
make sure youre not blacklisting facebook, ive accidentely right clicked a picture and clicked "Block images from ..." to check to go
Edit > Pref. > Content
click on [exceptions] across from load images automatically and make sure facebook isnt in that list

---

### Post by tlocotes on 2008-10-19
Facebook has been having massive problems with photo uploading. To solve you MUST do these 3 things; 1st: Access Facebook using firefox. Internet Explorer and Java have trouble working together on Facebook. 2nd; Make sure you have downloaded the latest update to Java. You can do this free at Java.com . 3rd; CLEAN YOUR REGISTRY!!! This seems to be the underlying cause of the uploading problems. A great site to find help with doing this can be found at [http://byebar.begoozle.com/pp/registry/](http://byebar.begoozle.com/pp/registry/)

---

### Post by psychok7 on 2008-10-20
> **bear24rw said:**
> make sure youre not blacklisting facebook, ive accidentely right clicked a picture and clicked "Block images from ..." to check to go
Edit > Pref. > Content
click on [exceptions] across from load images automatically and make sure facebook isnt in that list

Dammit.. ur right...but im pretty sure it wasnt me doing it.. must be a firefox bug.. but yeah thats the solution.. thanks very much

---

