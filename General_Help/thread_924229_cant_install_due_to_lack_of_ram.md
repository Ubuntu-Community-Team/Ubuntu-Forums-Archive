---
title: "cant install due to lack of ram"
date: 2008-09-19
forum: General Help
---

### Post by Dr.Gee on 2008-09-19
I have an old laptop (1 Ghz/256mb ram) that wont let me install the OS. While i physically have 256 mb ram,the system says i only have 247mb. Is there anything I can do. The max ram i could install is 256 mb.

Thanks

---

### Post by Titan8990 on 2008-09-19
I would go with something more lightweight. Try Xubuntu and be sure to download the "alternate CD".

---

### Post by howefield on 2008-09-19
What make/model is the laptop ?

Could be that the graphics card is taking some system memory leaving you without the full 256 meg.

---

### Post by iaculallad on 2008-09-19
> **Dr.Gee said:**
> I have an old laptop (1 Ghz/256mb ram) that wont let me install the OS. While i physically have 256 mb ram,the system says i only have 247mb. Is there anything I can do. The max ram i could install is 256 mb.

Thanks

You still have to option of installing the Alternate CD (x)Ubuntu which requires a little amount of RAM. But if you want exploring other distributions, I'd recommend you try Zenwalk as it supports your current physical RAM.

---

### Post by Sef on 2008-09-19
Use the [alternate cd]("http://ubuntu.com/getubuntu/download").  That will work.  Just check the box below the green arrow.

---

### Post by Dr.Gee on 2008-09-19
> **howefield said:**
> What make/model is the laptop ?

Could be that the graphics card is taking some system memory leaving you without the full 256 meg.


win book J1

trident video accelerator cyberblade-i1

---

### Post by Titan8990 on 2008-09-19
Really, any Linux distro with XFCE (Xubuntu) or Flux (Fluxbuntu) window managers would be good. I highly advise against Gnome (Ubuntu) or KDE (Kubuntu).

Although, it doesn't have to be a *buntu distro they are typically the easiest for Linux beginners.

---

### Post by Dr.Gee on 2008-09-19
> **Sef said:**
> Use the [alternate cd]("http://ubuntu.com/getubuntu/download").  That will work.  Just check the box below the green arrow.


Thanks.I will try that.

Thanks from a total newb.

---

### Post by snowpine on 2008-09-19
As mentioned, you can try the Ubuntu Alternate CD, which might work. If the installation works but you aren't happy with Ubuntu's performance, you can easily install Xubuntu on top of it by typing 'sudo aptitude install xubuntu-desktop' at the command line, then choosing Xfce from the Options->Choose Session menu at the login screen. You can also do this the opposite way by installing Xubuntu, then 'sudo aptitude install ubuntu-desktop' to put Ubuntu (Gnome session) on top of it.

There are several "unofficial" light-weight alternatives to Ubuntu. Crunchbang (Openbox) and Fluxbuntu (Fluxbox) are my two personal favorites. Both should run well with 247mb of ram and you can install any application you like from the Ubuntu repositories.

---

### Post by Dr.Gee on 2008-09-19
> **snowpine said:**
> As mentioned, you can try the Ubuntu Alternate CD, which might work. If the installation works but you aren't happy with Ubuntu's performance, you can easily install Xubuntu on top of it by typing 'sudo aptitude install xubuntu-desktop' at the command line, then choosing Xfce from the Options->Choose Session menu at the login screen. You can also do this the opposite way by installing Xubuntu, then 'sudo aptitude install ubuntu-desktop' to put Ubuntu (Gnome session) on top of it.

**There are several "unofficial" light-weight alternatives to Ubuntu.** Crunchbang (Openbox) and Fluxbuntu (Fluxbox) are my two personal favorites. Both should run well with 247mb of ram and you can install any application you like from the Ubuntu repositories.


would these offer better performance than the alt cd?

---

### Post by howefield on 2008-09-19
> **Dr.Gee said:**
> win book J1

trident video accelerator cyberblade-i1

As far as I can see, this machine does use system memory for the graphics card. 

Looks like the alternate cd as the other posters have pointed out is an option, but I think you might still have performance issues.

---

### Post by snowpine on 2008-09-19
> **Dr.Gee said:**
> would these offer better performance than the alt cd?

Just to be clear the Ubuntu Alternate CD offers no performance boost over the Ubuntu Live CD. It is simply a different way of installing that uses less ram. Once installed, there is no difference.

Same goes for the Xubuntu Live CD vs. Xubuntu Alternate CD; no difference once they are installed.

To answer your question, my personal experience is that Crunchbang is quite a bit faster (and uses less ram) than Xubuntu and Ubuntu on my computers. Fluxbuntu is possibly even a bit faster still, but I hesitate to recommend it since it is somewhat outdated (no updates or bug fixes in the past year) and has a steeper learning curve.

The downside to an unoffical distro or "remix" is that you don't get the same level of community and support. I am glad that I started with Ubuntu because it was easy for me to learn, but now that I know a bit more about Linux, I've come to appreciate the lighter & faster distros.

---

