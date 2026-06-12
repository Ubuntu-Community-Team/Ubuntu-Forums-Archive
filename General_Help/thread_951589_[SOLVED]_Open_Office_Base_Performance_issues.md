---
title: "[SOLVED] Open Office Base: Performance issues"
date: 2008-10-18
forum: General Help
---

### Post by bretto_40 on 2008-10-18
Hi,

I have recently been successful in solving the following issues with Open Office Base, and thought I'd post the solution up as many searches when trying to get an answer came up with a number of users with the same problem, but no solutions that I could find.

So here's mine for anyone who might have the same issues, this might help:

The problem: Recently did a fresh install of Ubuntu 8.04, and installed Open Office from the Repos. I then accessed some Databases that I've been using for some time now and found that when accessing the Tables and Queries I had setup, that scrolling through the data was REALLY slow... like delays of 5 seconds... slow.

In the end, the problem was Java. I knew my Hardware was OK because I currently have my machine triple booted, and one of the other boots is my previous version of Ubuntu 8.04 that had been a series of upgrades to get it to that point. And it worked perfectly in Base.

So, I suspected it might be Java, as the old install that was working fine was running Java version 1.6.0_06, but my new one, with the performance issues was running 1.6.0_07. So I tried re-installing the Sun jre package through Synaptic... no change.

So then I went into Open office, to Tools>Options>Openoffice.org>java where it displays the Java information, and noticed the path to the java version in use was as follows:

usr/lib/jvm/java-6-sun-1.6.0.07/jre

So I thought, ok, I'll look around near that path in my file system and see if there are other Java options I can set it to point to. As it turns out, there was, there was another java installed here:

usr/lib/jvm/java-6-sun

... which now that I look at it again, I realise that this is merely a link to the java-6-sun-1.6.0.07 folder.

Anyway, so from the Java section under the OOo options, I chose the "Add" button and browsed to the java-6-sun folder and selected (didn't click into), the "jre" folder and clicked ok.

Nothing appeared to happen but when clicked OK again it gave me a message saying that OOo would have to reboot for changes to take effect, so I closed it down and opened back up.

This time when I went into my databases everything worked beautifully! Problem solved!

So, when I started writing this post I thought it was just a different installed version of Java that needed to be selected, but now it looks like all it was was to re-connect Open office to the Java run time environment by re-selecting it via Tools>options>openoffice.org>java -> "Add" button.

Hey, I don't know why this is so, I just know it's fixed now and so I thought I'd throw it up here for others.

I hope someone finds this helpful (even if long-winded)  :)

Cheers

---

### Post by MaxVK on 2008-10-19
Very helpful - Many thanks

Regards

Max

---

