---
title: "dependencies huge problem"
date: 2008-11-23
forum: General Help
---

### Post by bertolo on 2008-11-23
my ubuntu is:
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

i want to install libgtk2.0-dev using synaptic package manager.i got the following message:
libgtk2.0-dev:
 Depends: libcairo2-dev but it is not going to be installed
 Depends: libpango1.0-dev but it is not going to be installed

and if i do try to install libcairo2-dev  i got a similar error

it always says the following packages got unreolvable dependencies

---

### Post by xravexheavenx on 2008-11-23
Do you have all the repos enabled?

---

### Post by bertolo on 2008-11-23
> **xravexheavenx said:**
> Do you have all the repos enabled?

how can i do that ?

---

### Post by Tomatz on 2008-11-23
What are you trying to install?

If you are using a howto, do you have a link to the page?

---

### Post by bertolo on 2008-11-23
> **Tomatz said:**
> What are you trying to install?

If you are using a howto, do you have a link to the page?

libgtk2.0-dev i have told before

sorry about the caps it was not intencional
[[]] peace

---

### Post by bertolo on 2008-11-23
i downloaded a repository list to fix this problem. the problem i think it is is not from the repository it's because my Synaptic is not configured to install needed dependencies

can someone give me some help

thks in advance

---

### Post by Tomatz on 2008-11-23
> **bertolo said:**
> libgtk2.0-dev I HAVE told before

Obviously....


Unsubscribed!

---

### Post by bertolo on 2008-11-23
don't understand. if you are talking about the caps lock there it was a mistake sorry i dont wanted to appear angry.

---

### Post by oldos2er on 2008-11-23
I believe the intended question was what are you trying to install that requires libgtk2.0-dev?

---

### Post by Yellow Pasque on 2008-11-23
Make sure the repos are enabled (at least main, universe, multiverse) in System -> Administration -> Software Sources. Also make sure that the source code repo is checked/colored. Then try again, If you still get errors in Synaptic, apt-get usually gives a more informative message:
```
sudo apt-get install libgtk2.0-dev
```
aptitude sometimes can solve these problems too.

> I believe the intended question was what are you trying to install that requires libgtk2.0-dev
Does this really matter? If the user has the proper repos enabled and has dependency issues, it needs fixed.

---

### Post by ggordon on 2008-11-27
I'm having a similar problem.  Ultimately I'm trying to install the gnome-devel package, but getting all sorts of dependency issues.  I'm running Hardy and Synaptic. I worked my way down through the dependencies to where I found that I needed libcairo2-dev.

libcairo2-dev says that it depends on libcairo2 (=1.6.0-0ubuntu2)

I have libcairo2 (1.6.4-1ubuntu1) installed.

I tried to force libcairo2 (1.6.0-0ubuntu2) to install, but I get a long list of gnome applications and libraries that will be removed if I do so.

Is there a way that I can install a newer version of libcairo2-dev that would be compatible with the newer version of libcairo?

---

### Post by ggordon on 2008-11-27
I found the newer version of libcairo2-dev and another that I needed in Launchpad.  After installing them I was able to successfully install gnome-devel using synaptic.

---

