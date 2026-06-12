---
title: "Changing Display Resolution?"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by art_major on 2009-09-01
Hi all,

I just downloaded and installed Ubuntu because I have been reading about some graphical design programs that looked promising to play with.  Ubuntu did the whole install thing and I was able to log in, but the display resolution is all messed up.  Tried changing it in the Display Properties thing, but my correct resolution wasn't there.  Got the wireless up and read the online help.  It said to go to Hardware Drivers, so I did.  It automatically downloaded ATI drivers and then had me restart.  After I restarted, the display is a lot better, it does 3D now, but the resolution is still wrong.  The correct resolution still isn't shown in the Display Properties list to choose from.  Went back to online help and it tells you to open some text file and type a bunch of lines in to make it work.  That is where I am now.  Is there program I can download that will just do this?  I'm sorry, but I just can't be bothered to type all that BS into my computer.

Thank you.

---

### Post by tgeer43 on 2009-09-01
You probably could have done it in the time it took you to post your message.

What about copying & pasting from the online help article you are reading to the file that needs to be edited?

tgeer

---

### Post by shaedee on 2009-09-02
> **tgeer43 said:**
> You probably could have done it in the time it took you to post your message.

What about copying & pasting from the online help article you are reading to the file that needs to be edited?

tgeer
Oh help I had typed this once already and lost it and had to re sign in. Have partitioned my hard drive, still have old Windows on it but now have installed Ubuntu 8.10 from disk, then upgraded to 9.04 online and added Kubuntu desktop.  I am having a horrible time trying to change screen resolution.  What it gives me is something that leaves the pages and pics all too large for the desktop and I have to try to move them around, making them smaller just does not work, can anyone help me?  I also don't know where one would type in the code if I knew the correct codes to use. Thanks.

---

### Post by tommcd on 2009-09-02
You can try using **xrandr** to change your display resolution:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
Yes, it does involve using the terminal. Read the tutorial carefully and follow the instructions. It is not that hard.

---

### Post by tommcd on 2009-09-02
> **shaedee said:**
> What it gives me is something that leaves the pages and pics all too large for the desktop and I have to try to move them around, making them smaller just does not work, can anyone help me?
First, try booting to recovery mode and choose the option **xfix fix the video**. Use that and then reboot. 
Is the display resolution incorrect? If so, then you can try the link about **xrandr** I gave in my last post.

---

