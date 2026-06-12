---
title: "Apps are randomly crashing (especially Firefox)"
date: 2008-07-11
forum: General Help
---

### Post by mjf on 2008-07-11
Hello,

I'm experiencing random and seemingly unreproducible crashes in many applications under Ubuntu 8.04.  I've tried diagnosing the issue but I'm sort of out of ideas at this point.

My main issue is Firefox.  It's crashing on average at least several times in an hour.  When a crash occurs, normally the Firefox windows simply disappears.  In other cases, the windows remains but is unresponsive and I must kill it through the command line.

At worse, the crashes can occur something like once every ten minutes.  They seem to be random and unreproducible.  I can often use the "Return to previous state" feature and simply resume what I was doing before the crash.

FF even crashes in safe-mode and with no Flash objects running.  However, increasing the "complexity" of the websites (Flash, heavy JavaScript) does appear to correspond to a higher frequency of crashes.

As previously stated, FF is what's crashing the most.  Essentially the only other applications I use are 1) VLC, 2) Anki (a flashcard program), 3) bittorrentdownloadcurses, 4) Amarok, 5) pidgin, 6) gedit, 7)
gnome-terminal.  These are stable enough for me, but occasionally each of these programs will crash (with the possible exception of gedit and gnome-terminal).  When a crash occurs, normally the window simply vanishes, and if I had launched the application from the command line I can see that a seg fault occured.  There was one occasion when Anki constantly died with Illegal instruction; rebooting solved this problem.

I suspect it is some sort of X issue.  Once in a while, the X server seems to spontaneously restart: the screen goes black briefly, then the Ubuntu login screen comes up.  I've also had times where X totally locked up; mouse and keyboard were unresponsive, and I had to hard reboot.

I've been using whatever default video card driver is used for my video card (Sapphire ATI Radeon 9600 Pro), so I tried switching over to the ATI proprietary driver.  The FF crashes are still occurring.  (I just switched over today by going to System -> Hardware Drivers and enabling the ATI driver.)

I also suspected it could be a bad memory issue but I've run memtest for hours without any errors.  Also, I've never had Linux itself crash (unless those X lockups were really system crashes?), i.e., I've never had the whole system spontaneously reboot.  I have read that memory failures may only occur when the system is under load, but in practice how likely is it that memtest doesn't detect bad memory?

It may be possible I have a faulty video card.  However, disabling what appeared to be possibly "dangerous" options through the BIOS (turn acceleration to 4x from 8x, disable Fast Writes) didn't reduce the crashes.  I also used this system for a good year or so on an older Ubuntu (I think Dapper Drake?) and never had instability
like this.  The only real hardware difference from then and now is that I upgraded from 512 MB to 2 GB RAM.

So, at this point I don't really know how to go about troubleshooting the issue.  Any advice would be greatly appreciated.

---

### Post by dracayr on 2008-07-11
In the forums I read that many people have that firefox problem since hardy. FF never crashed on me personally, but also I normally use opera (not only a good alternative, it's the better browser :o) )

dracayr

---

### Post by hal8000 on 2008-07-11
I hate intermittant faults like this ...
Some things you can try:
As you upgraded memory, power everything off, make sure the memory modules are fully seated.
If you suspect mempry, ideally run memtest for 24 hours+

If you have a bootable cd of knoppix you can try this. This should help with the problem being hardware or software.

If it proves to be software, you are going to have to break things down. If its X related, try working in console mode for a while cntrl-alt-f1

Trying not to use apps like firefox may also help, if no crash without firefox then you can uninstall firefox and reinstall it again.

Finally, I had a problem like yours lasting 6 months, in my case it affected both linux and windows, random reboots, and eventually showed itself to be leaking capacitors on an Abit motherboard, which was repaired
and worked well afterwards.

---

### Post by mjf on 2008-08-10
Thanks for the replies, dracayr and hal8000.

I finally diagnosed the problem as a faulty memory chip.  I've replaced the component and have had no crashes since :-)

What threw me off is that I'd run memtest overnight with no errors, leading me to believe the memory was fine.  It seems memtest can have false negatives, so people who face similar problems should be aware of this.

---

