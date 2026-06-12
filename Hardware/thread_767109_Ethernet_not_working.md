---
title: "Ethernet not working?"
date: 2008-04-25
forum: Hardware
---

### Post by chris_1d on 2008-04-25
Hi guys, its my first post, so be gentle!

I've built a new PC and installed ubuntu. However my computer does not seem to let me use the ethernet port. It says no network, but my cable is plugged in?

Any ideas?

I have a foxconn 945g7ad motherboard?

Thanks!

Chris

---

### Post by bodgetastic on 2008-04-25
Sounds like the driver might not be loaded.  
Googling your motherboard number and looking at Foxconn's page says that the network is a Realtek gigabit one but doesn't give a model number.

I don't know exactly what driver you need, but you might want to try typing:

xconsole &
sudo modprobe r8169

(finish each line with the RETURN key)
into a Terminal window.

The first command runs 'xconsole', which will start up a new window which shows you system messages and errors.  Make this window a bit bigger to read more clearly - it might show you useful information when you execute the second command.

The second command tries to load the driver.  'sudo' means 'execute system command'.  It will prompt you for your password - nothing will appear when you type it in, but don't worry about that.  Just press RETURN when you've typed it in.  'modprobe' means 'load driver'. 'r8169' is the driver name.  I don't know if it is necessarily the right one, but a small amount of googling suggests that it might be.

Hopefully any success/error messages will show up in xconsole.

If it works then Network Manager should magically see it...

If not then you could try finding out the model number of the NIC and searching [http://www.realtek.com.tw/](http://www.realtek.com.tw/).  You might need to install some kernel development stuff to use those though - post back if you need more help!  I'm not online a huge amount though I'm afraid.

Good luck!

---

### Post by chris_1d on 2008-04-25
That resolved it :)

Thanks very much!!!!

---

