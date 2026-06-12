---
title: "Installing Ubuntu server editon on a laptop with failed graphics card"
date: 2012-07-16
forum: Hardware
---

### Post by svesmeralda on 2012-07-16
I have a 6 year old Toshiba Satellite with Ubuntu 10.04 installed on it.  It seems the graphics card has almost completely failed as the screen goes black before it gets to the log in screen.  A remote monitor also goes black at the same time.  I would like to use it as a server instead of buying a dedicated machine for that purpose.  I am retired on a fix limited income so money is an issue.

I have been using Ubuntu for over five years and consider myself an advanced beginner with a goal to become much proficient at using and helping others to switch to Linux.

Is it possible to attach an external graphics card in order to use the monitor?  Also, is there away I can access the computer remotely to install the server and set it up for remote administration?  I can log into the laptop but have not set up my machines on their own network yet.

Thanks, Jim

---

### Post by papibe on 2012-07-16
Hi svesmeralda.

I converted an old Toshiba Satellite into a server when my graphics card was dying.

In my case, the graphic mode effectively crash the machine, but in text mode, although some minor distortions, it was stable. Luckily, the server installation CD/USB is in text mode ;).

Since in your case you already have a desktop running, I would try to boot into recovery mode (which is text mode), and test if your system is stable enough. Right there, you may be able to select a root shell prompt and install openssh-server.

When that's install, you will be able to connect remotely using the terminal.

Just some thoughts. Let us know how it goes.
Regards.

---

### Post by sudodus on 2012-07-16
Use Papibe's solution, if text mode is fine on your Toshiba :KS

Otherwise I suggest the following:

The easy solution:

I think an old desktop computer costs very little today. As a retired person, you might even be able to find some organisation, that will recycle old computers, and hand them out for a symbolic fee. Check that out in your region!

Your request:

But you want to use your old Toshiba and yes, it should be possible. I don't think it is worth getting a USB graphics card, because it probably costs more than an old desktop computer. But certainly you can communicate via the ethernet port and use it as a headless server.

In this case I suggest that you take out the hard disk drive,  attach it to another computer (with working graphics) and install Ubuntu server into it. Be sure to install at least an SSH server. Install no proprietary hardware (typically for graphics and wifi). Now this hard disk drive is portable to any computer (that works without proprietary drivers).

So reinstall the hard disk drive into your Toshiba, connect via your LAN and SSH:

```
ssh user@host
``` for example
```
ssh jim@192.168.0.2
```

If you don't like to take out the hard drive, you might manage to do the same thing with a USB drive: install Ubuntu server while connected to another computer (with working graphics) and then boot the Toshiba into it (but you must manage to boot from a USB drive with no feedback from a screen).

---

### Post by svesmeralda on 2012-07-17
Papibe,

Thanks for the reply, gives me a place to start.  This is all new to me so I will be starting a new adventure.

---

### Post by svesmeralda on 2012-07-17
Sudodus,

I hadn't thought of connecting the hard drive to another computer.  I will try that if the graphics install doesn't work.  Thanks.

---

### Post by svesmeralda on 2012-07-17
I just installed the server edition on the Toshiba laptop, went perfectly, the display was stable the whole time.

One other question, will I be able to set it up so that when the lid is closed the display will shut off and the server continues to operate as it should?

Thanks for your advice, problem solved.

Jim

---

### Post by papibe on 2012-07-17
> **svesmeralda said:**
> I just installed the server edition on the Toshiba laptop, went perfectly, the display was stable the whole time.

Great!


> **svesmeralda said:**
> One other question, will I be able to set it up so that when the lid is closed the display will shut off and the server continues to operate as it should?

That is difficult to answer. I doubt there's a setting on the BIOS, but you loose nothing if you take a look.

What I do is turn on my computer with the lid closed using [WOL]("http://en.wikipedia.org/wiki/Wake_on_lan"). For that take a look at this [guide]("https://help.ubuntu.com/community/WakeOnLan") for that.

As a last resort try it. Wait until the machine boots completely, then connect to it from another machine using ssh, and then close the lid to see what happens. Worst case: the machine goes to sleep or hibernate, and you won't be doing it again.

Regards.

---

### Post by svesmeralda on 2012-07-17
Thanks, I will give it a try as soon as I figure out to set up ssh.  I ordered the Official Ubuntu Server book so it will be a few days before I can do much.  I will check out WOL and its guide after I get some sleep.

Jim

---

### Post by papibe on 2012-07-17
Don't forget to mark this thread solved (see [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), so other users can take advantage of it :D

I see that you added a tag, but it is better to use the method described on the link.

Kind Regards.

---

