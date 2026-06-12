---
title: "First post from new user :)"
date: 2008-09-09
forum: General Help
---

### Post by gaviota on 2008-09-09
Hello everyone,

I'm an IT professional who is new to Linux. My story is that I worked a lot on Unix servers back in the 90's, as a Sun Solaris administrator, as an Oracle database administrator and as an Oracle developer. But I "grew" to  IT management jobs for the past 10 years, so I kind of got away from the Unix world.

This past weekend I decided to install Ubuntu on my desktop PC at home and I'm really surprised at how easy and user friendly it is. On a single day I got almost everything working - network, sound, video card, printer, scanner, web cam, java virtual machine, video codecs, and even my TV tuner card, which I thought was going to give problems, but after searching around this forum I found all the answers I needed. I'm still missing a video recording application, because tvtime doesn't record video, but I know I'll find one easily, I just haven't really looked yet.

Where I need help is in finding an application to substitute Apple iTunes. This is the only thing that's keeping me right now from completely removing Vista from my home desktop PC. And I don't mean an application to just play music files, I need something to synchronize and manage my iPod exactly like iTunes does it, without any conflicts with the iPod. I use my iPod to listen to music in my car, in my office, at home, and in the gym - I've really become an addict to that little gadget, so I can't live without it :(

Recommendations will be appreciated.

Thanks in advance :)

---

### Post by ryanhaigh on 2008-09-09
While [this page]("https://help.ubuntu.com/community/PortableDevices/iPhone") is for the ipod touch and iphone the apps mentioned there (amarok and gtkpod) are likely to be the best available in terms of ipod support.

I'll just add that the community and official documentation provided at help.ubuntu.com is a great resource. Oh and welcome to the community.

---

### Post by kpkeerthi on 2008-09-09
Take a look at [Songbird]("http://www.getdeb.net/release/3116"). The best iPod manager for Linux in opinion. Install the iPod Manager addon with it.

Not all iPods work out-of-the-box in Linux. What iPod do you have?

---

### Post by OutOfReach on 2008-09-09
For an iTunes replacement I would recommend either [Songbird]("http://getsongbird.com/") or [Banshee]("http://banshee-project.org/"). Both are very good and have their own strengths/weaknesses, so I would suggest to try them both out.

EDIT: Oh almost forgot, welcome to Ubuntu. :)

---

### Post by gaviota on 2008-09-09
Thanks ryanhaigh, kpkeerthi and OutOfReach for your replies and welcomes.

I have a 30 GB iPod Video, it's a previous generation model. I will be upgrading soon to an iPod Classic, I like my current one but I need more space, so I know for sure I will upgrade to an iPod Classic, probably the 160 GB model.

---

### Post by kpkeerthi on 2008-09-09
Yes. OutOfReach was right. There are some gotchas. 

Banshee 1.2.1: 
- No sync support yet. You need to manually transfer the files.
- I copied a few albums to my iPod with it. I ended up having multiple albums with the same name for each file in the albums under Music -> Albums. Instead of organizing tracks T1, T2.. T3 under one album A1, banshee organized the files as A1 - T1, A1 - T2, ... A3 - T3 etc. So I ended up having about 44 albums with the same name, each having just one track.

Songbird:
- Has sync support. A+
- For the first time I used it, I had to use 'Restore factory settings' in Songbird, disconnect and remount my iPod and resync all my Music. 
- Although Songbird displays album art when playing files in it, it does not sync/copy album art to iPod. I have opened a bug report. Hoping for a fix soon :)

---

### Post by kpkeerthi on 2008-09-09
> **gaviota said:**
> Thanks ryanhaigh, kpkeerthi and OutOfReach for your replies and welcomes.

I have a 30 GB iPod Video, it's a previous generation model. I will be upgrading soon to an iPod Classic, I like my current one but I need more space, so I know for sure I will upgrade to an iPod Classic, probably the 160 GB model.

You should be OK with your iPod.

---

