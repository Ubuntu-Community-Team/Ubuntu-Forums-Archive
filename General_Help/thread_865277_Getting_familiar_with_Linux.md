---
title: "Getting familiar with Linux"
date: 2008-07-20
forum: General Help
---

### Post by nbakewell on 2008-07-20
Hey everyone,

I just completed my first linux install, Ubuntu of course, and have been reading diligently over tutorials on getting familiar with Linux.  However, there are tons of articles on the net, and not all of them good, so I was just wondering if you had any specific recommendations of good sites or specific tutorials that someone brand new to Linux would find helpful.  Thanks!

---

### Post by bp1509 on 2008-07-20
[http://tuxtraining.com/index/](http://tuxtraining.com/index/)

---

### Post by oconnor663 on 2008-07-20
I would always suggest learning to use the command line, but what are you interested in doing?

When I was getting into Linux as a learning project, I found it really cool (and eventually genuinely useful) to learn a programming language at the same time, if you're willing to invest the effort. I heartily suggest starting with Python, and this ([http://www.greenteapress.com/thinkpython/](http://www.greenteapress.com/thinkpython/)) is a great resource. Linux gives you easy access to the command line, which makes playing with Python extra convenient. And if you're willing to suffer a slightly steeper learning curve, you should consider learning to use an advanced text editor (I suggest Emacs) at the same time.

But that's just what I did. If you have something that interests you more (like learning how to encrypt your hard drive, or other challenges), Google those.

---

### Post by steveneddy on 2008-07-20
The links in my sig should get you started.

---

### Post by songshu on 2008-07-20
i did a lot of reading when i first started as well.
but it turned out that "scratching your own itch" was a lot more effective.

just figure out what you would think is absolutely awesomely cool to do or have and google the matching documentation.

at least that helped me out best

---

### Post by Yannick Le Saint kyncani on 2008-07-20
I'd suggest ditching any other os completely, that is make a backup and remove it, not just dual boot.

That way you will have to use 100% gnu/linux and will get use to it. It may be painful at some times though.

As websites go, I like ubuntu-news.net, an easy read.

---

### Post by knutschr on 2008-07-20
Sorry oconnor663, but I think that to learn Emacs is a complete waste of time.
When I started using Linux some 10+ yrs ago there was no Gnome and no KDE.
All was emacs and vi. Today we have GUI programs doing the most,if one doesn't have very special needs (which I can't think of what).

---

### Post by ugm6hr on 2008-07-20
Some reliable links in the Start here thread linked below.

---

### Post by nbakewell on 2008-07-20
Thanks for the info everyone!

oconnor663: I've been reading up on the CLI which I am finding very useful - definitely a good starting point.  As to what I am interested in doing, everything.  Right now my goal is to get comfortable enough with Linux to be able to use it primarily.  I really want to explore its depth and find out what its capabilities are.  I am a programmer and did some (basic) Python a long time ago, so this may be a good time to pick it back up.  What particularly makes Python programming on Linux better than Windows?

---

### Post by oconnor663 on 2008-07-21
If you're a programmer, then there's probably no particular advantage to relearning Python, other than that it's beautiful. You might find it more productive to pick up shell scripting, which is just a superset of the CLI interface anyway.

If I recall, coding Python on Windows means you either need to install a large IDE (like ActivePython) or use Cygwin. Neither of those is very much fun, and I still haven't figured out whether Cygwin can even do copy/paste. Linux and Mac give you functional CLI's for playing with the Python interpreter, and it's easier to use your favorite text editor for coding. Linux also tends to have a crazy variety of hacker tools available, and package managers can make them much easier to find/install.

I've never gotten into a real live editor war before, and I won't ruin this thread by trying :) I'm just your run-o'-the-mill undergrad, but I've found several advantages to knowing Emacs. You can judge for yourself whether it's worth if.

1) Biggest advantage: it can run without a gui. If you break Gnome/KDE when you hack/upgrade your system (and I've done this many times), none of your gui editors will work, and you will have to fix things in text mode. Emacs is hardly more complicated than Nano (the super simple text mode editor) for the basics, but it also has tons of advanced features you can learn over time. This advice also applies if you ever edit files over an ssh connection, since gui's usually turn into molasses.

2) If you're using a gui file manager etc., it's more natural to open a file into a gui editor. But I like to do a lot on the command line, and if I have to make some quick edit to a file, I find it snappier to do it with an editor that's designed to be operated without a mouse. This is totally personal preference, and there are plenty of situations (like typing this reply) where I prefer modern gui editors.

Hope that helps.


P.S. Some people think eye candy is a waste of time, but Gnome comes installed and ready with the Compiz Fusion window manager. One of your first projects should definitely be to install the advanced settings manager for that one and start playing with its full functionality. YouTube has some videos of what you're in for. It's one of those things that you can't get outside Linux.

---

