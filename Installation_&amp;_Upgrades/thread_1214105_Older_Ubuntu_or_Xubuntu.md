---
title: "Older Ubuntu or Xubuntu?"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by mynameinc on 2009-07-15
My pastor was complaining about his laptop's speed, so I offered to install Ubuntu for him.  I let him use Ubuntu (GNOME) on my computer, and he fell in love with it almost instantly.  However, upon examination, his computer only has 256MB of RAM (but has a 1.3GHz processor) (currently running XP).  Should I install an older version of Ubuntu or Xubuntu?  If the former is better, what is the newest version of Ubuntu which will run on 256MB of RAM?  If the latter, what are the major differences between GNOME and Xfce (other than Xfce using less resources). Thanks in advance, mynameinc.

NOTE:Laptop is a HP ze4900.

---

### Post by unlimitedz on 2009-07-15
I would install 8.04 as it is a LTS and he probably won't want to be updating every 6 months.  I would suggest doing an alternate CD install, then doing sudo apt-get install xubuntu-desktop to install xfce, which would probably run much better than gnome.  my 2 pennies...

---

### Post by raymondh on 2009-07-15
my choice would be xubuntu .... that or donate a RAM stick to your pastor/church and then go for a desktop Ubuntu (8.04 LTS) :)

Release notes for review/reference:

[http://www.ubuntu.com/getubuntu/releasenotes](http://www.ubuntu.com/getubuntu/releasenotes)
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Peace.

Raymond

---

### Post by aysiu on 2009-07-15
In the past, Xubuntu would have been a good choice. I tried it out recently, and it honestly was slower than Gnome with Compiz on the same hardware setup (I have a netbook). Particularly slow was rendering when switching (Alt-Tab) between windows... and I have 2 GB of RAM.

So, yeah, don't go Xubuntu.

For 256 MB and good performance, go with a window manager. I would recommend Crunchbang, which uses OpenBox. But you can also just install regular Ubuntu and install OpenBox, IceWM, or Fluxbox on top of that and run the lightweight window manager instead of Gnome.

---

### Post by b.a.w on 2009-07-15
Crunchbang is a good choice if you want just a window manager. I would not recommend using openbox, icewm, or any standalone window manager installed from within Ubuntu for this purpose as suggested. There is a lot of configuration that needs to be done to make these useable by the average computer user. Chrunchbang setups you up with a default config.

I am running Xubuntu 9.04 and for me it runs on less resources. It is not as drastic of a change as it used to be in older verison though. Xfce has started to bloat a little, well at least Xubuntu has. I have noticed an impovement over Ubuntu 9.04 though.

---

### Post by mynameinc on 2009-07-15
Thanks for all the help.  Could someone post screenshots of CrunchBang, so I could see what it looks like?  50% of you suggest CrunchBang, 25% suggest Xubuntu, and 25% suggest Ubuntu with Xfce (the idea which seems to appeal the most).  Could anyone give the pros and cons of each as compared to the others?  Sorry to be so dependent, but I have NO experience with any of them.  Thanks, mynameinc.

---

### Post by aysiu on 2009-07-15
Crunchbang screenshots are here:
[http://crunchbanglinux.org/wiki/screenshots](http://crunchbanglinux.org/wiki/screenshots)

You can change the wallpaper and theming, though.

---

### Post by TheNosh on 2009-07-15
ubuntu + lxde

---

### Post by b.a.w on 2009-07-15
I have never been able to make sense of the suggestions to install additional desktop environments, e.g. xubuntu-desktop or kubuntu-desktop, inside a normal ubuntu install. This just adds many more packages that makes the menus complex by adding apps with redundant capabilities and makes the system more complicated with more apps to update. I just don't see the advantage of this approach when there are ways to install only Xubuntu for example.

If you choose to use Xfce, I suggest using Xubuntu not Ubuntu with xubuntu-desktop installed because of the reasons I mentioned above. You may have to try out the different options to make the final decision.

The suggestions to install window managers, such as openbox, icewm..., do not encounter these problems. Neither does the suggestion of adding lxde, which is a very good alternative of a light weight desktop environment that gives you more than just window manger.

---

### Post by mynameinc on 2009-07-16
> **b.a.w said:**
> I have never been able to make sense of the suggestions to install additional desktop environments, e.g. xubuntu-desktop or kubuntu-desktop, inside a normal ubuntu install. This just adds many more packages that makes the menus complex by adding apps with redundant capabilities and makes the system more complicated with more apps to update. I just don't see the advantage of this approach when there are ways to install only Xubuntu for example.

If you choose to use Xfce, I suggest against using Xubuntu not Ubuntu with xubuntu-desktop installed because of the reasons I mentioned above. You may have to try out the different options to make the final decision.

The suggestions to install window managers, such as openbox, icewm..., do not encounter these problems. Neither does the suggestion of adding lxde, which is a very good alternative of a light weight desktop environment that gives you more than just window manger.

You said "I suggest against using Xubuntu".  I think you meant "I suggest using Xubuntu", because the reasons you stated pointed towards Xubuntu?

If I do choose to go with LXDE, should add it to Ubuntu (if I do, should I follow the instructions listed above for Xfce with slight modifications?) or choose a distro with LXDE as default?  If I add it to Ubuntu, that presents the same problems as adding Xfce or KDE, doesn't it?

---

### Post by mynameinc on 2009-07-16
> **aysiu said:**
> Crunchbang screenshots are here:
[http://crunchbanglinux.org/wiki/screenshots](http://crunchbanglinux.org/wiki/screenshots)

You can change the wallpaper and theming, though.

](*,)  Why didn't I think of CrunchBang's website?  I will AGF and say it was due to checking my nation on Cyber Nations.

Thanks, CrunchBang *looks* easy to use.  Is it really, or is this part of the 95%?
[SIZE="1"]Part of my family wisdom is believe nothing of what you hear and don't believe 95% of what you see.[/SIZE]

---

### Post by b.a.w on 2009-07-16
Yes, that was a typo by me. Sorry.

Installing lxde will pull in a few apps, but not nearly as many as install Xfce into Ubuntu. Also this is the easiest way of install lxde compared to just installing Xubuntu.

---

### Post by mynameinc on 2009-07-16
> **b.a.w said:**
> Yes, that was a typo by me. Sorry.

Installing lxde will pull in a few apps, but not nearly as many as install Xfce into Ubuntu. Also this is the easiest way of install lxde compared to just installing Xubuntu.

Thanks, broski.

---

### Post by snowpine on 2009-07-16
Here are the system requirements for Ubuntu 9.04 Jaunty Jackalope:

> What do I need to create and use my Ubuntu CD?

    * A blank CD and the ability to &#8220;burn&#8221; blank CDs
    * A modern Intel or AMD compatible computer
    * At least 256MB of RAM

(source: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download))

256mb is plenty for Ubuntu.

Personally, I use and highly recommend Crunchbang.

---

### Post by mynameinc on 2009-07-16
> **snowpine said:**
> Here are the system requirements for Ubuntu 9.04 Jaunty Jackalope:



(source: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download))

256mb is plenty for Ubuntu.

Personally, I use and highly recommend Crunchbang.

[Ubuntu System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")
That says 384MB is highly recommended, but still may not be enough.

---

### Post by snowpine on 2009-07-16
> **mynameinc said:**
> [Ubuntu System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")
That says 384MB is highly recommended, but still may not be enough.

Those are the requirements for 8.10 and older. Ubuntu is actually getting lighter and faster over time. :)

Also according to your link you can install on as little as 64mb, if you use the Alternate CD.

I am not saying Ubuntu will be the fastest thing in the world on those specs--personally I would go for Crunchbang as I mentioned--but if the OP really wants to use Ubuntu, it is worth a try, in which case I recommend the current 9.04 version rather than an old version. ;)

---

### Post by mynameinc on 2009-07-16
> **snowpine said:**
> Those are the requirements for 8.10 and older. Ubuntu is actually getting lighter and faster over time. :)

Also according to your link you can install on as little as 64mb, if you use the Alternate CD.

I am not saying Ubuntu will be the fastest thing in the world on those specs--personally I would go for Crunchbang as I mentioned--but if the OP really wants to use Ubuntu, it is worth a try, in which case I recommend the current 9.04 version rather than an old version. ;)

Thanks, I'm seriously looking at CrunchBang.  My pastor is a first-time Linux user, will CrunchBang be hard for him to use?

---

### Post by snowpine on 2009-07-16
> **mynameinc said:**
> Thanks, I'm seriously looking at CrunchBang.  My pastor is a first-time Linux user, will CrunchBang be hard for him to use?

Crunchbang is basically just Ubuntu with a different user interface. I personally find Crunchbang's user interface easier and more intuitive than Ubuntu's default Gnome desktop. Also, some non-free codecs (like the Flash player) are pre-installed in Crunchbang, which is nice for a first-time user.

---

### Post by mynameinc on 2009-07-16
> **snowpine said:**
> Crunchbang is basically just Ubuntu with a different user interface. I personally find Crunchbang's user interface easier and more intuitive than Ubuntu's default Gnome desktop. Also, some non-free codecs (like the Flash player) are pre-installed in Crunchbang, which is nice for a first-time user.
Thanks.  He will be my first 'convert' (pun intended) to Linux.  Can I use the 'Remote Desktop' utility under System->Preferences (or SSH or something like that) to gain access to his computer remotely if he has a problem?

EDIT:I'm not so sure I should go with CrunchBang:
[QUOTE=http://crunchbanglinux.org/forums/topic/4/crunchbang-linux-80402-alternative-installation/]CrunchBang Linux is not recommended for anyone needing a stable system or anyone who is not comfortable running into occasional, even frequent breakage.[/QUOTE]

---

### Post by mynameinc on 2009-07-16
Bumping this... but I think I shall go with Xubuntu.

---

### Post by csabo2 on 2009-07-16
another option is U-lite.. mini install image, they have a script that downloads all the needed software, uses LXDE, very nice, i love it. use it on a few older PCs. very fast.

U-lite.org

---

### Post by mynameinc on 2009-07-16
> **csabo2 said:**
> another option is U-lite.. mini install image, they have a script that downloads all the needed software, uses LXDE, very nice, i love it. use it on a few older PCs. very fast.

U-lite.org

I don't like what I have seen of LXDE... I would prefer Xfce or GNOME.  But if I decide to use U-Lite, is it new user friendly?

---

### Post by snowpine on 2009-07-16
> **mynameinc said:**
> Thanks.  He will be my first 'convert' (pun intended) to Linux.  Can I use the 'Remote Desktop' utility under System->Preferences (or SSH or something like that) to gain access to his computer remotely if he has a problem?

EDIT:I'm not so sure I should go with CrunchBang:

I am not sure about the "remote desktop" question; it's not a feature I've used before personally. However, if it can be installed in Ubuntu, it can probably be installed in Crunchbang as well, since they use the same repositories.

Don't take that "crunchbang disclaimer" you quoted too seriously--the developer has a sense of humor. :) But you raise a good point; there is no question Xubuntu is a more mature distro, with a million-dollar company backing it up.  

Either Xubuntu or Crunchbang would be fantastic options, in my opinion. Maybe you can demo the Live CDs for your pastor to see which interface he prefers?

---

### Post by mynameinc on 2009-07-16
> **snowpine said:**
> I am not sure about the "remote desktop" question; it's not a feature I've used before personally. However, if it can be installed in Ubuntu, it can probably be installed in Crunchbang as well, since they use the same repositories.

Don't take that "crunchbang disclaimer" you quoted too seriously--the developer has a sense of humor. :) But you raise a good point; there is no question Xubuntu is a more mature distro, with a million-dollar company backing it up.  

Either Xubuntu or Crunchbang would be fantastic options, in my opinion. Maybe you can demo the Live CDs for your pastor to see which interface he prefers?

Thanks for easing my mind about CrunchBang.  I'm not actually sure how the 'Remote Desktop' feature in 'System->Preferences' works...

---

### Post by Mighty_Joe on 2009-07-17
> **mynameinc said:**
> Thanks for easing my mind about CrunchBang.  I'm not actually sure how the 'Remote Desktop' feature in 'System->Preferences' works...

It allows other computers to control that computer via [RDP]("http://en.wikipedia.org/wiki/Remote_Desktop_Protocol")
To attach to another computer via RDP, use Applications->Internet->Remote Desktop Viewer

---

### Post by Cityscape on 2009-07-17
I would give him Ubuntu 9.04. It works fine for me on 256 MB RAM.
Either that or Xubuntu. I would not install churchbang or a different desktop enviroment after installing Ubuntu.

---

### Post by mynameinc on 2009-07-17
> **Cityscape said:**
> I would give him Ubuntu 9.04. It works fine for me on 256 MB RAM.
Either that or Xubuntu. I would not install churchbang or a different desktop enviroment after installing Ubuntu.

Did you have to do anything extra or special to get Jaunty to work for you?  If not, I will use Jaunty.

---

### Post by mynameinc on 2009-07-17
> **Mighty_Joe said:**
> It allows other computers to control that computer via [RDP]("http://en.wikipedia.org/wiki/Remote_Desktop_Protocol")
To attach to another computer via RDP, use Applications->Internet->Remote Desktop Viewer

Can I connect to computers in a different network via the Internet?  If yes, can you provide a How-to guide?

---

### Post by noalternative on 2009-07-18
> **mynameinc said:**
> I don't like what I have seen of LXDE... I would prefer Xfce or GNOME.  But if I decide to use U-Lite, is it new user friendly?

We made it for new users and old computers. We have a live cd now so you no longer need the script.:popcorn:  We also made our lxde [look like gnome]("http://u-lite.org/content/u-lite-screenshots").

However you can use the script if you already have a version of ubuntu installed.

---

### Post by mynameinc on 2009-07-18
> **noalternative said:**
> We made it for new users and old computers. We have a live cd now so you no longer need the script.:popcorn:  We also made our lxde [look like gnome]("http://u-lite.org/content/u-lite-screenshots").

However you can use the script if you already have a version of ubuntu installed.

Is U-Lite reasonably stable?  And I still need an answer to my Remote Desktop question.

---

### Post by noalternative on 2009-07-21
> **mynameinc said:**
> Is U-Lite reasonably stable?  And I still need an answer to my Remote Desktop question.

It is pretty stable.  You can install remote desktop.

---

### Post by Mighty_Joe on 2009-07-22
> **mynameinc said:**
> Can I connect to computers in a different network via the Internet?  If yes, can you provide a How-to guide?

Short answer: "yes".
Long answer: only if he has a route to his computer on the Internet: You would need to know his external IP address and his router/modem would have to allow RDP traffic through and forward it to his computer.
Googling for "ubuntu remote desktop" returns many helpful tutorials [like this one]("http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop")

---

