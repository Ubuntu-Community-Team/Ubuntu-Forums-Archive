---
title: "[SOLVED] School Computers in Ghana"
date: 2008-10-14
forum: General Help
---

### Post by fixerdave on 2008-10-14
Hello,  

I'm looking for some advice and suggestions for a project I've been volunteered for.  I work for a community college in Canada and we are shipping some computers to a school in Ghana.  No, this is not one of those "dump your junk computers in Africa so they can clean up the mess" scams; it flows from a personal relationship between one of our faculty members and a particular school.  It's all been vetted, verified, and run through all the committees.  We are sending complete and fully working systems; not exactly state of the art but not junk either.    

Unfortunately, all these committees decided to do this after the machines had been wiped, disassembled, and put in storage.  Further, we will not have time to install anything on them prior to shipping, which will happen in a couple of weeks.  Yes, lots of committee time but no technical time.  We are a community college after all.  So, the plan is to ship them with Ubuntu LiveCDs and instructions for going through the install process.

So, having said all that, here are my questions:

1) At the destination school, they have one computer with Internet access.  I have no idea about the quality of this connection; it could be through a cellphone for all I know.  Thus, I need to plan on having them install additional packages without a network.  I'm thinking either making a custom Ubuntu Live CD/DVD or just providing an additional DVD full of useful packages and instructions for using it.  Given that I've never done either, which would be the quickest and easiest approach?  Remember, I don't have a lot of time for this, and I also have no idea about the technical competence at the other end.

2) What additional packages would you recommend for a rural English-speaking African school?  The list the aforementioned faculty person suggested was:  PolySci (he teaches PolySci, can you tell?), Math, Engl, Geog, Hist, Economics (as in home), and Commerce (as in bookkeeping).  No, he doesn't particularly know what he's asking for, that's why I'm asking here.

3) Does my approach make sense?  Are there alternatives I'm unaware of?


    David...

P.S.  Note that I am a professional Windows tech but have moved to Ubuntu at home (thus, I get volunteered).  Feel free to be technical but please don't expect a lot of Linux knowledge, I'm still working on that.

---

### Post by phidia on 2008-10-14
Great project Bravo!!!

I think it might make sense to mirror the repos (do a local repository) but I don't know for sure if you can do that with optical media. I think it can be done though.

Ok it can be done take a look at [this]("http://ubuntuliving.blogspot.com/2008/09/local-repositories-with-aptoncd.html") and [this]("http://wiki.africasource2.tacticaltech.org/post/main/02kq1ct2pXNBBsXY").

And perhaps [this]("http://www.howtoforge.com/dvd_images_of_ubuntu_repositories") also.

---

### Post by Prospero2006 on 2008-10-14
> **fixerdave said:**
> Hello,  

I'm looking for some advice and suggestions for a project I've been volunteered for.  I work for a community college in Canada and we are shipping some computers to a school in Ghana.  No, this is not one of those "dump your junk computers in Africa so they can clean up the mess" scams; it flows from a personal relationship between one of our faculty members and a particular school.  It's all been vetted, verified, and run through all the committees.  We are sending complete and fully working systems; not exactly state of the art but not junk either.    

Unfortunately, all these committees decided to do this after the machines had been wiped, disassembled, and put in storage.  Further, we will not have time to install anything on them prior to shipping, which will happen in a couple of weeks.  Yes, lots of committee time but no technical time.  We are a community college after all.  So, the plan is to ship them with Ubuntu LiveCDs and instructions for going through the install process.

So, having said all that, here are my questions:

1) At the destination school, they have one computer with Internet access.  I have no idea about the quality of this connection; it could be through a cellphone for all I know.  Thus, I need to plan on having them install additional packages without a network.  I'm thinking either making a custom Ubuntu Live CD/DVD or just providing an additional DVD full of useful packages and instructions for using it.  Given that I've never done either, which would be the quickest and easiest approach?  Remember, I don't have a lot of time for this, and I also have no idea about the technical competence at the other end.

2) What additional packages would you recommend for a rural English-speaking African school?  The list the aforementioned faculty person suggested was:  PolySci (he teaches PolySci, can you tell?), Math, Engl, Geog, Hist, Economics (as in home), and Commerce (as in bookkeeping).  No, he doesn't particularly know what he's asking for, that's why I'm asking here.

3) Does my approach make sense?  Are there alternatives I'm unaware of?


    David...

P.S.  Note that I am a professional Windows tech but have moved to Ubuntu at home (thus, I get volunteered).  Feel free to be technical but please don't expect a lot of Linux knowledge, I'm still working on that.

Hello there,
I manage a Ubuntu computer lab in San Antonio, Texas. 
The school district is constantly blocking access to repositories and other package related resources.

You have several options:
    1.) Use apt-mirror
            -This is your best option.
            -Apt-mirror will completely download the ubuntu
             repositories.(About 60 Gigs) symlink the directories it creates
             to a local web server and you have a 25,000 packages
             ready for installation in house.
       -I do it this way now because I teach live CD lessons
        and the kids need to download large packages. 30 kids
        downloading a file that is 70 megabytes requires fast, local
        repository access. 
       -So, I suggest you apt-mirror one machine up and configure
        the rest to recognize it.
    2.) apt-cacher.
           -This also works. All of the computers point to a central
            computer once again. If the package hasn't been cached, 
            the internet connected machine will then download from the internet and hand it off.
            (This doesn't sound like it fits what you want.)
    3.) Get them a large switch and use ip_tables on the connected
        machine to masquerade for the rest. --This is a total hack
        and probably shouldn't be mentioned here, but it's fun to set up.


Anyway, I hope those ideas help.

[http://www.neisd.net/imak/computerlabpage/history.html](http://www.neisd.net/imak/computerlabpage/history.html)

---

### Post by fixerdave on 2008-10-14
Wow, two perfect solutions while I was on my dinner break :)  I love Ubuntul; what a community!

The AptOnCD solutions seems, at first read, the perfect solution to the base problem.  With a stock Ubuntu LiveCD, an update CD/DVD, and a few simple instructions, they should be good to go.

The idea of a local mirror of the whole repository fits perfectly on the other end of the scale.  I'll just download it and dump it on a HD for them.  If they can muster the technical expertise to use it, then they don't need an Internet connection.  If they don't have someone on their end that can figure out how to use it, with some base instructions, then they'll probably be happier with the AptOnCD approach anyway.

Thank you both, that solves the technical issue.  Now, anyone have any suggestions for what packages to pre-load via AptOnCD?

Thanks again, you just made my week a whole lot easier,

    David...

---

### Post by phidia on 2008-10-15
> 2) What additional packages would you recommend for a rural English-speaking African school? The list the aforementioned faculty person suggested was: PolySci (he teaches PolySci, can you tell?), Math, Engl, Geog, Hist, Economics (as in home), and Commerce (as in bookkeeping). No, he doesn't particularly know what he's asking for, that's why I'm asking here.

I think that's obviously a harder question. But If you open open synaptic you can look at Meta Packages, Science, and Word Processing. You should be able to find some useful choices there. 

Again mirroring the repos seems a better more inclusive approach but it may or may not be practical.

---

### Post by jespdj on 2008-10-15
There's an official, special version of Ubuntu called [Edubuntu](http://edubuntu.org/) which is especially meant for schools.

I have no experience with it myself, but you might want to look at it for your situation.

---

### Post by fixerdave on 2008-10-16
> **jespdj said:**
> There's an official, special version of Ubuntu called [Edubuntu](http://edubuntu.org/) which is especially meant for schools...

Hi, 

When I first looked at Ubuntu, I started with Edubuntu (I do work in a college after all), but got the distinct impression that it was basically a server/thin-client implementation of Ubuntu.  This may not really be suitable for this project as A) the computers aren't that bad, B) I have no idea about the technical expertise at the other end, and C) I don't get to pre-install anything as the systems are already in storage.

However, after your prompting, I took another look at the Edubuntu website.  They also offer an "[Educational AddOn CD]("http://www.edubuntu.org/Download")" that, well, does my job for me :)  I'm just trying it out now but it appears that an install from the Ubuntu LiveCD immediately followed by the Edubuntu add-on will create a pretty amazing system.

So, with three great answers to my queries, I've gone from trying to figure out how to modify an Ubuntu liveCD to simply downloading, testing, and documenting the dead-simple install on two existing CDs.  I'll probably still use APTonCD to add a few other custom applications, like maybe the full Open Office install and a decent programming editor, but the Edubuntu add-on pretty well packages all the available educational applications there are.  Well, there's no PolySci or Home Economics apps, but you can't expect Ubuntu to solve ALL the world's problems ;)

So, short answer, if you want to put an educational computer together for a kid, either next door or around the world, The Ubuntu LiveCD followed by the Edubuntu Add-on will get you most (if not all) of the way there.  I'm very impressed.

Thanks again for all the pointers,

    David...

---

