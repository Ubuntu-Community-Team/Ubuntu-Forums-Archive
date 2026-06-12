---
title: "Aspire 5100 Video issue on Ubuntu 8.10"
date: 2008-11-29
forum: General Help
---

### Post by cnordskog on 2008-11-29
Hi. I hope someone can help me wiht this sliight problem. 

When I  have desktop effects on off it all videos and games run without any faults. But when I installed Compiz it started "blinking" 

I whould really appreciate the help. 

I have tested several stuff and scoured through the forum but either I suck at searching or I just missed it or misunderstood it.

Hope someone helps out.

---

### Post by cnordskog on 2008-12-01
bump

---

### Post by cnordskog on 2008-12-03
Damm no replys, i give upp!

---

### Post by sedawk on 2008-12-03
Are you talking about that damn small PC which I know as L5100?

You need Ubuntu 8.10 because otherwise only one CPU (core) is
working but video is still a minor problem.
For proper performance you need latest Ubuntu package(s)
for ATI's closed-source driver.

Because of the blinking I turn off compiz whenever
I want to run a video:
```

pkill compiz;sleep 5;nohup metacity &

```

What is still annoying is that every time I start a video
the whole screen goes black for a short time.

---

### Post by cnordskog on 2008-12-08
No it is the Acer Aspire 5100. 

The aspire 5100 is comon sized.

I have the latest drivers that i can find..

And Turning compiz off is not an option:P Me likey compiz:P:guitar::lolflag:

---

### Post by Faz1 on 2008-12-21
Hey cnordskog!

I've got an Acer Aspire 9500 series (with an ATI Mobility Radeon X700) and experience the same problems with Compiz enabled.

You may find [this thread]("http://ubuntuforums.org/showthread.php?t=847336") of interest which describes how to setup an icon to simplify enabling / disabling Compiz.

I know what you mean about not wanting to disable Compiz, I love it too, but having a quick and easy way to turn it off whenever required has eased my pain, at least for now anyway! :)

Although VLC plays videos fine under Compiz I still switch to Metacity for that little extra performance boost (and a quieter fan!), toggling back to Compiz when I'm done.  I find switching Windows Managers is very quick and doesn't effect any existing windows and running multimedia applications.

I'd recommend installing the Compiz Fusion icon and trying this approach.

---

### Post by cnordskog on 2008-12-22
Thank you very much Faz1 this will work untill anyone fixes this damm bug:P :lolflag::):popcorn::KS

---

