---
title: "gtk window decorator buggy in 8.10 Intrepid?"
date: 2008-11-03
forum: General Help
---

### Post by abh83 on 2008-11-03
Is it just me or is the the gtk window decorator in the new ubuntu 8.10 buggy?

When I have multiple windows open and I go back and forth from the active window to the inactive window it seems the decoration is not drawn properly on to the screen.

So in other words the effects look all messed up (plz check attached screen shots).

Could this be related in anyway to nvidia drivers? I made a fresh clean install of 8.10 Intrepid and I was having some issues getting nvidia-settings to store information to the xorg.cof file (which I think I managed to solve).

Help would be greatly appreciated!

---

### Post by loomsen on 2008-11-03
Yes, somehow... I'm using emerald to decorate my windows, but experience other problems, like:

[[img]http://img136.imageshack.us/img136/7834/screenshot54kl8.th.png[/img]](http://img136.imageshack.us/img136/7834/screenshot54kl8.png)

The white main menu bar... It's actually supposed to be black like the rest of my skin, but somehow it seems opera's value is overriden by sth else. Couldn't figure out why yet tho. 
Terminal doesn't show any errors...

---

### Post by morphos on 2008-11-04
Having the same issue here.

Intel motherboard, Nvidia 7600GS video card.

---

### Post by loomsen on 2008-11-04
Now this is really strange. It seems like Opera pulled some kind of another window manager when I started. Sys Monitor showed that the process running claimed to be:
opera -nomail -nolirc -notrayicon [color=red]-style Plastik[/color]

The first few arguments are how I'd like to start it, but whatever I do, Opera will always append -style Plastik for some reason. Downgraded and still. Tho I have been able to get that white menu bar kicked, it's not yet like it's supposed to be. 

The bug however, seem to be somehow related to Fedora, where opera was built on most likely. It almost felt like if there were two window manager fighting against each other to gain controls over opera... Well, removed many kde related libs, pretty much all I think, and it now works kind of. Still appends that style hint tho.

Very very annoying.

---

### Post by Tekovro on 2008-11-11
Same problem here :(
Highly annoying.

---

### Post by crosswound on 2008-11-11
i have the same problems too here i thought i did something wrong brand new clean 8.10 intrepid install.

---

### Post by Elvin Mammadov on 2008-11-11
I have a same problem...:(  So do you have any suggestion?

---

### Post by IceReaver75 on 2008-11-11
I had the same problem but yesterday I had some new updates come up in the update manager.  After I installed the updates there was a new option under hardware drivers for my Nvidia card listed which was the 96 drivers.  I uninstalled the 177 drivers and installed the 96 drivers.  Did a reboot when it was required and now all the title bar bugs that I have had went away.  With the 177 drivers I couldn't use the human theme at all without the title bars glitching on me.  I can now use it with no problems.  So if your using a Nvidia card you could try the 96 drivers and see if that fixes it.  I should have noted I have the Geforce 6200 A-LE card.  All desktop effects work with compiz also.  Hopefully that helps you out some.

---

### Post by bartman on 2008-11-21
I made a video of this behaviour:
[http://www.vimeo.com/2310802](http://www.vimeo.com/2310802) (password is compiz)

This started happening after upgrading to 8.10 when apparently the proprietary nvidia driver got updated as well.

I'll try downgrading it as IceReaver75 suggests.

---

### Post by abh83 on 2008-12-17
Are there any solutions yet to this issue?

Should i downgrade to the older drivers?

---

