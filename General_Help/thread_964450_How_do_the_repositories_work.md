---
title: "How do the repositories work?"
date: 2008-10-30
forum: General Help
---

### Post by nbtrap on 2008-10-30
I'm new to Ubuntu, but I'm a fast learner.  My question is: how long does it usually take until the repositories are updated after a new release?  For instance, Gimp 2.6 came out about a month ago, but I still have 2.4.5.  How can I find out when (or if) 2.6 will be added?

Same thing with Openoffice.org.  I had to download the source for 3.0.  Why is it not available in the repositories?  Will it ever be?  How can I find out?

---

### Post by MaxIBoy on 2008-10-30
From what I know, everything has to go through a grueling reliability/security/standards compliance test before it can be put into the repos. I'm not sure, though.

---

### Post by ad_267 on 2008-10-30
Those won't ever be in the 8.04 repositories. You have to upgrade to a more recent version of Ubuntu (8.10) to get them. OpenOffice 3 won't even be in 8.10.

The repositories only provide security and bug fix updates, not major changes to the applications.

---

### Post by schauerlich on 2008-10-30
If you enable the backports repositories, you can get newer versions of programs when they're stable enough. Sticking with the main repos will only give you security/bugfix updates.

---

### Post by vanden12 on 2008-10-30
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Read that if you really want to know about the...

Also I think that updates are basied on how popular the app is....For ex if Firefox 3.1 came now it whould be like 5 hours before it hits the repo...For smaller apps it takes a little while...

But for the love of god it not that hard to install something for the src...

---

### Post by jmszr on 2008-10-31
If you want Gimp 2.6.1 go to GetDeb.net - Categories > Graphics and Design > Gimp 2.6.1 Download it and the GDebi Installer will install it. I'd remove Gimp 2.5.4 first. You will have to deal with any further updates,but that's no big deal.

---

### Post by nbtrap on 2008-10-31
Thanks for all your replies, but I have more questions.

You say it's not hard to install from source.  I have installed several programs from the source code, and it has been completely different EVERY TIME.  How/where can I learn to install packages from source?  I'd like not to have to search the internet for a tutorial every time I want to install from source.

Also, one of you said I have to upgrade to 8.10 to get to repos.  Do you recommend upgrading?  Are there any reasons not to?  Where can I learn how to upgrade?

Thanks.

---

### Post by nbtrap on 2008-10-31
> **ad_267 said:**
> Those won't ever be in the 8.04 repositories. You have to upgrade to a more recent version of Ubuntu (8.10) to get them. OpenOffice 3 won't even be in 8.10.

The repositories only provide security and bug fix updates, not major changes to the applications.

How do you know what's going to be in what repositories and when?

---

### Post by ad_267 on 2008-10-31
I think Hardy should give you the option to upgrade from the Update manager. I've found 8.10 is working really well but you might want to give it a while for them to iron out any bugs.

Enabling the backports repository might be the best idea if you want the newest versions of most things, although these aren't supported by Ubuntu.

> How do you know what's going to be in what repositories and when? 

I don't know and I'm not sure where to find out, but that's just the way Ubuntu releases work. For example, Fiesty still has Gimp 2.2. Major new versions of applications aren't provided as updates.

---

### Post by nbtrap on 2008-10-31
I thought I should have seen an option to upgrade to 8.10 in the update manager, but I do not.

Is this possibly due to the fact that I'm running 8.04 amd64?

---

### Post by ad_267 on 2008-10-31
Oh it's explained here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

It's because 8.04 is a long term support release, so the upgrade isn't automatically offered.

---

### Post by ethoms on 2008-10-31
Aside from the backport repositories (which I've never used yet) there are third party repos that you can add, they vary in terms of how recent the builds are. There are even seperate repos for different trees (e.g. stable or most-recent-but-less-stable). This is the great thing about aptitude (and other repository managed packaging systems), you can control what you have on your computer knowing it will always be up to date according to your repo stability level.

Go to System->Administration->Software Sources, there many options to control the repos etc. I have added the wine repo to keep up-to-date with the latest wine versions. To do this, I go to the "Third Party Software" tab and click add:

URI: [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)
Distrobution: hardy
Components: main

What to do is search for "<app-name> debian repository" or "<app-name> ubuntu repository" from search engine and hopefully you will get instructions on how to the repo. Otherwise, look for the .deb installer, otherwise, fin a .rpm and use 'alien' to convert it to a .deb. Compiling from source is the last resort.

For Gimp 2.6:
[http://packages.ubuntu.com/intrepid/graphics/gimp]("http://packages.ubuntu.com/intrepid/graphics/gimp")

---

### Post by hyper_ch on 2008-10-31
If you have little experience with ubuntu/linux I would advise against trying to compile something from surce or use 3rd party software. First get a bit familiar with how it works and then you can explore.

If you don't know what you're doing you can easily havoc your system.

---

### Post by nbtrap on 2008-10-31
Thanks for all of your responses; I have one more question:

Is it to my advantage to upgrade to 8.10?  What does it mean that it's not supported "long-term"?  If I do upgrade, do I have to worry about software from 8.04 (including 3rd party) being incompatible with 8.10?  Because, for instance, when I install OOo3 earlier today, I had an option for 8.04 and an option for 8.10.

---

### Post by Interpreter on 2008-10-31
In theory, you should be fine with "upgrading", newer, faster, blah blah.....
the "long time support" are special freezes for those who whish to avoid change, eg @ work and such.
As a normal desktop user I'd say go get it.
There's no "incompatability" (word!?) between 8.04 and 8.10, I guess they talk about linking to different repos there that's all.

Ok there you have it, go upgrade, chances are you'll gain...something ;)

---

### Post by executorvs on 2008-10-31
enable the backports repository. it may have been/be made available there. they are talking about putting OpenOffice 3 in the back ports around the first of december following the openoffice bug fix release 3.0.1 or 3.1.

---

### Post by nbtrap on 2008-10-31
> **Interpreter said:**
> 
There's no "incompatability" (word!?)

Word indeed.

Thanks for all your help.

Edit: Misspelled though . . .

---

### Post by lukjad on 2008-10-31
> **nbtrap said:**
> I'm new to Ubuntu, but I'm a fast learner.  My question is: how long does it usually take until the repositories are updated after a new release?  For instance, Gimp 2.6 came out about a month ago, but I still have 2.4.5.  How can I find out when (or if) 2.6 will be added?

Same thing with Openoffice.org.  I had to download the source for 3.0.  Why is it not available in the repositories?  Will it ever be?  How can I find out?
From what I hear, Openoffice 3 will be in the backports for 8.10. The reason that the repositories don't get big updates is that they are tested over and over again to make sure it works well with this version of Ubuntu.

---

### Post by hyper_ch on 2008-10-31
> **nbtrap said:**
> What does it mean that it's not supported "long-term"?

Long term releases are mainly aimed at businesses. Those that need a plattform with security update & bug fixes for some years.

The normal life-span of a Ubuntu release is 18 months. After that there won't be any security updates & bug fixes anymore.

However a LTS desktop will be supported for 3 years.

And the server LTS releases will be supported for 5 years. Server generally don't need the newest *bling bling* features. There main aim is to be stable and provide continuous "serving".

As home user I wouldn't worry that much whether a release is LTS or not ;)

---

