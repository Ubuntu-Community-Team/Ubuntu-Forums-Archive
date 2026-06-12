---
title: "[SOLVED] cannot add sun jdk to netbeans"
date: 2008-11-07
forum: General Help
---

### Post by ztrange on 2008-11-07
Im trying to add the sun jdk as netbeans java platform instead of openjdk.

I installed the sun jdk with

sudo apt-get install sun-java6-jdk

and everything seemed fine, but now I cant find the route that i should give to netbeans to let it use sun jdk.

I mean, when I go to Tools menu / Java Platforms / Add Platform

I need to give netbeans the route where sun jdk is installed but I cant find it.

Any help will be appreciated.

---

### Post by ztrange on 2008-11-07
bump...

---

### Post by jamesstansell on 2008-11-08
Look in /usr/lib/jvm/java-6-sun/

---

### Post by ztrange on 2008-11-08
Thank you. Yes, I figured it out but forgot to post back, anyway, What I'm really trying to do is install netbeans-mobility-5_5-linux.bin but everytime I try to run it, it gives me this:

The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)
WARNING: could not delete temporary file /tmp/ismp001/6996109
WARNING: could not delete temporary file /tmp/ismp001/7449031

I googled it and fpund that it may be due to not havin set the JAVA_HOME variable, so I tested with the following ones

export JAVA_HOME /usr/lib/jvm/java-6-openjdk/

It failed and then I thought maybe it was because I was using openjdk not sun's So installed it and did this:

export JAVA_HOME=/usr/lib/jvm/java-6-sun/

with and without trailing slash but still no luck... Well, I will keep trying, any help will be appreciated.

PS Also tested it with sudo without luck.

---

### Post by jamesstansell on 2008-11-09
The current netbeans mobility version seems to be

> 
NetBeans 6.1 Mobility Installer for Linux/English (en)
netbeans-6.1-ml-mobility-linux.sh (65.1 MB)
MD5: 9cd747caefbc3d28fffb0d05c1c0ec32


Just curious - do you require the 5.5 version for some reason?

---

### Post by ztrange on 2008-11-09
Oh... Thanks, I will try the 5.0 I hope that is the rigth one... Going to google it.

Im trying to start developing (learning) J2ME and didn't wanted to do it in M$ Winbugs so I thought I would give it a try in Ubuntu, so I installed netbeans. But despite the version in the repos is the last one, 6.1, I didn't contained the mobility pack. I wandered around a little in the sun web but only found that I should try to install mobility pack from the plugins menu. It was not there... So, I started looking for other ways, found the .bin and thoght i should test the latest version...

Anyway, It seems that either I started with the wrong foot or I was looking forward to accomplish something rather tricky.

Thanks, Ill give it a try.

Edit: Now I see, the 5.5 is for netbeans 5.5... Ok, I think I downloaded that one because I thouth it was the latest... Now Ill search for the 6.1

Shot!!! I now found the 5.5.1 version [http://wiki.netbeans.org/Mobility](http://wiki.netbeans.org/Mobility) But didnt read your post completely, where did you found those and so fast?

---

### Post by ztrange on 2008-11-09
Ok, Im sorry for double posting but this would be the 3rd edit...

I see,

NetBeans 6.1 Mobility Installer for Linux/English (en)
netbeans-6.1-ml-mobility-linux.sh (65.1 MB)
MD5: 9cd747caefbc3d28fffb0d05c1c0ec32 

those are the netbeans mobility bundle, I was trying to find the mobility pack, to install over netbeans to make it mobility capable...

I didnt download the full bundle at first because It was in the repos and as far as I know is better to grab software from there because of the automatic updates and because it is fully tested software.

Well, maybe I should download the bundle and reinstall it.

---

### Post by jamesstansell on 2008-11-09
When you have netbeans installed from netbeans.org you should be able to the module management tool and install any new modules and updates.  For example, you should be ability to add the j2me modules to a netbeans that didn't already have it.

On the other hand I don't know if that will work with a netbeans installed from the ubuntu repositories.  Those are different installation and update philosophies and they're not exactly compatible.

I haven't used netbeans for almost a year, so I'm not the best person to talk about specifics with it.

---

### Post by ztrange on 2008-11-09
Dont worry, thanks anyway, I will download the full netbeans with all the modules and use try to keep it updated with its auto updater.

---

