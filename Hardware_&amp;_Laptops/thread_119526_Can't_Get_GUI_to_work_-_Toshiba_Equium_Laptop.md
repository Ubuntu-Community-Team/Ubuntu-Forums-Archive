---
title: "Can't Get GUI to work - Toshiba Equium Laptop"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by Ted_Smith on 2006-01-19
Tried to install Breezy onto my new Toshiba Equium L20 - 198 laptop as a dual boot with WinXP Home. Install went without a hitch. 

However, I get the seemingly common Xorg errors after boot up and it can't display the GUI (I say 'seemingly common' because Ubuntu doesn't seem to be great at autodetecting video settings - I've had to run 3 times out of 4 installs - either that or I'm unlucky!). 

I've tried the sudo "dpkg-reconfigure ...xserver/xorg" thingy as stated in the 'Upgrading NVIDIA Drivers' HOWTO here at Ubuntu Forums, and I've tried about 50 different combinations of settings (which  have worked on my other desktop installs). Typically each time I'd just change one setting. For example, I went from the 1024 display to just 800, then to just 640 etc. None of it worked. So I started from the top again (1024) and then tried different settings elsewhere in the setup program such as turning off kernal buffering. Every time, when I get back to the terminal, I try to run 'startx' and it just throws a wobbler and I get back to the terminal again. 

The graphics card is an "128Mb ATi Xpress 200M". Ubuntu detects that it's ATI and detects the card itself as stated above. My laptop can be seen [here]("http://www.currys.co.uk/martprd/product/seo/066698") for those that may be interested.

I've also tried running the dpkg-reconfigure in Recovery Console too, but still the same problems. 

I've searched the net but there doesn't seem to be any postings by people who've tried to install Ubuntu on a Toshiba Equium L20.

Anyone know how I can get this working or shall I just give up (again)!

Thanks

Ted

---

### Post by Ted_Smith on 2006-01-21
No suggestions at all?

Are there any known issues with Ubuntu and ATI RADEAON laptop cards? If so, where can I read about them?

Ted

---

### Post by mo_x on 2006-01-21
Can you post the files /etc/X11/xorg.conf and /var/log/Xorg.0.log (as attachments)?
You can try using the vesa driver.

---

### Post by Ted_Smith on 2006-01-21
I probably could if I knew how to from the terminal but I'm afraid I don't. I don't have a floppy drive either to save it to.

I just tried the Live CD version in fact to see if that coped. It didn't - same problem. I hoped that the Live CD may configure itself and then I could read how Xorg was set up and duplicate in the hard drive install. But no joy :-(

I think I'm gonna have to accept that Breezy Badger isn't compatible with my laptop - maybe the new up-and-coming version will be which I think is out soon. 

Thanks

Ted

---

### Post by xmastree on 2006-01-21
> I try to run 'startx' and it just throws a wobblerDid you try to view the xserver output? That's the first thing to do, to see what's actually failing.

You're going to need to use that terminal, since it's all you have for now...

I helped on another thread like this, no x server.

[http://www.ubuntuforums.org/showthread.php?t=79827](http://www.ubuntuforums.org/showthread.php?t=79827)
In particular, post # 27, where I compared to xorg.conf to a pizza recipe!

His problem was with the video driver, I would try that first.

---

### Post by Ted_Smith on 2006-01-21
Hi,

I read your thread - very well written! 

In my case though, if use either VI or nano to read the xorg.conf file, it just looks blank. I ca't see any text in it so I can't do the recommendations that you suggest, i.e. checking that the vlaues at the end match the values inserted earlier on. 

So I re-ran the dpkg reconfigure xserver-xorg command and disabled GLCore as suggested by another user in the thread. But still no joy when I ran startx. 

I am sure it is the driver causing the problem, but I don't know why.

---

### Post by xmastree on 2006-01-23
[QUOTE=Ted_Smith]In my case though, if use either VI or nano to read the xorg.conf file, it just looks blank.[/QUOTE]That's strange... I can only assume that you're trying to open the file from the wrong directory, and that the editor is creating a new, blank file.

Try this:```
cd /etc/X11
more xorg.conf
```You should see the file contents. If you do, then run the editor from there:```
sudo nano xorg.conf
```

---

