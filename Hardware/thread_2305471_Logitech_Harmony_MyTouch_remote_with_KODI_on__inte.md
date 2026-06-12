---
title: "Logitech Harmony MyTouch remote with KODI on  intel NUC"
date: 2015-12-06
forum: Hardware
---

### Post by mridul3 on 2015-12-06
Hi, 

I have intel NUC5CPYH and trying to make this remote work for KODI. 
Could get it to to power on/off and arrow keys and volume. But other keys like 'Back' , 'OK/Select' won't work. Logitech wants money for this support ! 

Any ideas? If this works its great hardware combo... if it works.

---

### Post by TheFu on 2015-12-07
Giving money to companies who refuse to support Linux is not helping the rest of those companies that take the time and effort to support Linux.
Of course, that is a personal decision.

It isn't like you are the first person to be burned and we always need people who are stubborn to take on these sorts of programming challenges, so that hardware NOT supported by the vendor (as it should be) becomes supported with hacked solutions.  After all, that's how nvidia and Ati/AMD video card support started out.

I've wanted a Logitech 650 remote for years - still using a Home Theatre Master remote from the 1990s here, but I'm well passed my days of hacking "good-enough" solutions together.  Also been burned by "We support Linux" claims by a well-known RAID card maker. Their "support" was only for a 3 yr old kernel and nothing newer.

Logitech burned me AGAIN about a year ago. Needed a quality HiDef webcam to record presentations for our LUG.  Did all the research and checked that it "worked" with Linux, even if the vendor didn't support this.  Bought a Logitech C920 webcam ... sometimes it works, but most of the time it doesn't.  Zoom and panning never worked. Follow the speaker never works.  This is all unacceptable.  Of course, with Windows everything works, but I can't show up to a Linux User Group with a Windows machine to record presentations, right?  The C920 doesn't work for MacOS either.  The C910 is $30 more expensive, isn't quite as good on color or audio capture, but is reported to work on Linux and OSX. I should have kept looking for a non-Logitech solution and given the cash to a different company.

Sorry - didn't mean to start a rant. ;(

Does the Logitech config tool work in WINE?  What else have you tried?

A websearch for "Logitech Harmony MyTouch Ubuntu" only found 2 relevant, old, results. 1 youtube video and the other from 2008. I didn't look any further. Not looking good for this hardware.  I'd take it to a friend's computer for setup and be done.

Sorry, not really a good solution.

---

### Post by SuperFreak on 2015-12-07
I use a Harmony 650 and 450 remote fro my Kodi set up. I installed LIRC

```
sudo apt-get install lirc
```

I think I chose Windows Media Center transreceiver/remote 
(not certain)

Remote works fairly well now

see [https://help.ubuntu.com/community/LIRC](https://help.ubuntu.com/community/LIRC)

EDIT:Important you have to reboot to make changes take effect

---

### Post by mridul3 on 2015-12-09
lirc worked pretty well. Most functionality is working.  Got a button to fire up Kodi and most buttoms work inside Kodi. If I can get the context menu(right click) to work I am golden. 

@TheFu, no I am using the MyHarmony tool on mac to configure the remote which I have always used.

---

### Post by SuperFreak on 2015-12-09
> **mridul3 said:**
> lirc worked pretty well. Most functionality is working.  Got a button to fire up Kodi and most buttoms work inside Kodi. If I can get the context menu(right click) to work I am golden. 


Did you configue Harmony Remote with MyHarmony ([https://support.myharmony.com/en-us/download]("https://support.myharmony.com/en-us/download")). You can do it within Ubuntu with Concordance ([https://www.phildev.net/concordance/](https://www.phildev.net/concordance/)) but it gets a bit complicated

---

