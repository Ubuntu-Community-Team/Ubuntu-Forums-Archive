---
title: "How does Ubuntu/aptitude handle security updates?"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by Phoenix Rising on 2009-08-12
(Ubuntu 9.0.4 desktop)

The title of this thread is a bit more generalized, so let me dive right into an example.

```
ruby -v
ruby 1.8.7 (2008-08-11 patchlevel 72) [x86_64-linux]

```

One year old.  Patchlevel 72.  Known vulnerabilities.

```
sudo aptitude install ruby
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
```

As you can see here, there are either no upgrades available for Ruby, or (more likely) I'm encountering an error 18 - error is 18 inches from the screen ;)

This serves as an example for my broader question: when a security patch is issued for an open source project, in this case, Ruby, how does the Ubuntu team go about factoring that into the OS, how soon does it generally get done, is it released as something that aptitude can upgrade/install, and how do I properly patch my system?

I'm not at all unfamiliar with installing from source; my problem with doing that is that, the more items I install from source, the more difficult it's going to be to maintain new upgrades/packages going forward.

Can somebody smack me upside the head and show me what I'm doing wrong?

---

### Post by aysiu on 2009-08-13
From [the Ruby 1.9.1 release announcement](http://www.ruby-lang.org/en/news/2009/01/30/ruby-1-9-1-released/): > Please note that Ruby 1.8 still remains. 1.8.8 will be released this year. So 1.8.7 is the latest release for the 1.8 series. It doesn't mean 1.8.7 has a bunch of security holes in it and 1.9.1 doesn't.

> One year old. Patchlevel 72. Known vulnerabilities. Examples? Documentation?

The Ubuntu general update policy is that package versions are frozen every six months on release and updates are released only for security issues.

---

### Post by Phoenix Rising on 2009-08-14
Hey Aysiu, thanks for the reply.

There are two known DoS vulnerabilities with this version of Ruby.  For more information, see these two links;

[http://www.ruby-lang.org/en/news/2009/06/09/dos-vulnerability-in-bigdecimal/](http://www.ruby-lang.org/en/news/2009/06/09/dos-vulnerability-in-bigdecimal/)
[http://www.ruby-lang.org/en/news/2008/08/23/dos-vulnerability-in-rexml/](http://www.ruby-lang.org/en/news/2008/08/23/dos-vulnerability-in-rexml/)

And yes, you're quite right that 1.8.8 is due out this year; in fact, doing an experiment on my home computer the other night, downloading the latest stable snapshot gave me 1.8.8.

I apologize if my prior post came off as a criticism.  And I also understand (and fully agree with) the wisdom of not making the default ruby package 1.9, given that there are a lot of changes in Ruby 1.9 vs. the 1.8 series.

So long story short, I'm assuming (based on your reply) that there isn't a package for the latest 1.8x release of Ruby - is that correct?  If so, what can we do to change that?  Is there any way I can help?  :)  Thanks.

---

### Post by aysiu on 2009-08-14
Many times Ubuntu relies on upstream to get security fixes. On occasion the Ubuntu devs will put in their own patch to the package.

Since 1.8.8 hasn't been officially released yet, it would have to be the latter case, I guess.

You may want to file a bug report on Ruby 1.8, then:
[https://bugs.launchpad.net/ubuntu/+source/ruby1.8/+bugs](https://bugs.launchpad.net/ubuntu/+source/ruby1.8/+bugs)

---

### Post by Phoenix Rising on 2009-08-14
Thanks again for your help.  What do you mean by "Ubuntu relies on upstream"?  What's upstream in this context?  As for filing a bug, what should I tell them here?  Just to update to the latest 1.8.7 patchlevel for Ruby?  I believe the REXML bug can be monkeypatched, but I don't know about the DoS in BigDecimal.

Thanks for your help :)

---

### Post by aysiu on 2009-08-14
*Upstream* just refers to the projects Ubuntu depends on.

For example, if there is a problem in the Network Manager applet, that isn't typically a Ubuntu developer problem but a Network Manager developer problem, so it's called an "upstream" problem (think of development as a river, and Ubuntu is at the bottom of it, getting all the newly developed software from "upstream" and putting it all together "downstream").

When the Ubuntu installer stored user passwords in plain text, that was a Ubuntu problem, not an upstream one. (Don't worry--that problem got fixed.)

One simple way to think of it is an upstream problem is one that affects all Linux distributions because it's tied more to the package. And a Ubuntu problem is one that affects mainly Ubuntu because of how the package is implemented or how it interacts with the other packages Ubuntu has implemented.

So, in this case, Ubuntu may just be waiting for the Ruby developers to patch things. Then again, maybe it's serious enough that the Ubuntu devs will patch it themselves. That's why I suggested you file a bug report on it.

---

### Post by Phoenix Rising on 2009-08-14
Ahh thank you for that explanation.  I've gone ahead and filed a bug report per your suggestion.  Here's hoping we get new packages :)

---

