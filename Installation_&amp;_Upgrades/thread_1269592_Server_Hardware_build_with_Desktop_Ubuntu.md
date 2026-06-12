---
title: "Server Hardware build with Desktop Ubuntu"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by jamesisin on 2009-09-18
I have an old piece of server hardware which I intend to build as a part-time server.  For various reasons I would like to build this as, essentially, a desktop machine.  I am not able to run the desktop installer on this machine as it doesn't have the correct drivers.  However, running the server installer leaves me without a GUI (among other issues).

I see at least these two choices.  First, I could run the server installer and then add a host of packages/meta-packages to convert it into a desktop environment.  Second, I could run the desktop installer assuming I could add to it what it is lacking (presumably drivers).

Which path represents the least complications?

How is this accomplished?

---

### Post by stlsaint on 2009-09-18
what specific drivers are keeping you from using desktop edition? you can use desktop edition and install LAMP for server configurations. It would be more pratical tho to use server edition as you are using a server. if your server cannot hold 64bit you may want to consider desktop edition. it really depends on what your trying to do. a cli would be best for using as server as you dont need gui. if you intend to use gui you may want to look into webadmin or somthing of the sort.

---

### Post by jamesisin on 2009-09-18
I really don't know.  I'm guessing it's drivers.  The desktop installer won't boot up on that hardware.  The server installer will.

---

### Post by stlsaint on 2009-09-18
are you sure you have a non-corrupt disc of the desktop installer? like i said you can install server edition and use and install external interface for gui assistance. but since ubuntu has automatic hardware configuration im thinking maybe you have a bad iso/disc...pleae try redownloading iso from [here]("http://distrowatch.com/")...and burn at the slowest speed possible.
if this still doesnt work than you can look into server edition more.

---

### Post by jamesisin on 2009-09-18
I have tried with both 8.04 and 8.10.  I can try with 9.04 but I predict the same behaviour (installer fails to start properly).  I'll try and report back.

It appears to me that each installer comes with a specific and limited set of hardware drivers and that the desktop installer is missing something that this particular server hardware requires.  That's been my guess thus far.

(I burned the image (downloaded directly through the UofO mirror) and ran the check on the burn.  They should be all good.)

---

### Post by jamesisin on 2009-09-18
Well, whatever it was (with 8.04 and 8.10) seems to have been taken care of with 9.04.  That's good enough for me on this one.

---

