---
title: "HP Mini 1030nr sound not working"
date: 2010-03-02
forum: Hardware
---

### Post by PreBoy on 2010-03-02
Hey guys,

First post :D -- Been wanting to join the ubuntu forums for a while, and finally thought I would.. 

I just reformatted my mini with Kubuntu 9.10 Karmy (Netbook edition), got the wireless working like a charm, and I've experienced something weird.

When I had 9.04 Ubuntu Jaunty (UNR), I was able to get sound to come out of the headphone jack, but never out of the speakers.. Now I hear sound coming out of the speakers for system sounds, like logging on, shutting down, going to sleep, things like that. But I can't get sound to show up in other program. I've tried playing avi's, mp3s, skype, but nothing. I've searched around, and this seems to be a really weird case.. 

I'm wondering if anyone can point me to where I want to look. My linux experience as around average.. So if you want anything off the box that would help in debugging let me know..

Thanks,

Chris

---

### Post by Arkitekt on 2010-03-02
I have a HP Mini 110-1030ca & I had the same issue with 9.04, It was fixed when I manually updated my alsa-driver alsa-lib & alsa-utils.

Here are the instructions for 9.10

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

I also updated all my alsa files to the versions listed here 
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

after words alsaconf should set up everything properly.

I also had a little bug where Ubuntu would set my some of my levels to 0 and muted, double check in an alsa mixer that levels are set correctly. I use Gnome but i believe kalsamixer is the KDE counterpart to gnome-alsamixer. 


I would also check your sound preferences, System>Preferences>Sound, and check what profile your hardware device is configured to (mine is set to Analog Stereo Duplex).

Hope this helps.

---

### Post by PreBoy on 2010-03-02
Thanks man, I'll give this a try later and report back.

---

