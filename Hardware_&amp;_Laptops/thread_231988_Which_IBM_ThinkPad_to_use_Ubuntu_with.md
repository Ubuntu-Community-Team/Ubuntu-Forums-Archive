---
title: "Which IBM ThinkPad to use Ubuntu with?"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by 3nigma on 2006-08-08
Hello all! :D 

I'm finally ready to jump from Windows to Ubuntu, and I'm extremely excited!  I am buying an IBM ThinkPad to make the install on, since they are reviewed so highly for their reliability, innovation, etc.

My question is this:  Which model of ThinkPad should I go with?  Here are my needs:

1) Basic computing, word processing, internet-browsing
2) Wireless internet built-in
3) USB support (flash drive, printer)
4) CD-RW drive, DVD-reader (DVD-RW might be nice)
5) I like 1024 x 768 display resolution, probably normal
6) I want a model with (a) the titanium/magnesium case, (b) mouse touchpad in addition to mouse finger joystick, and (c) keyboard light.

Really, I think a used eBay one should be fine (the only exceptional hardware is the built-in WiFi).  Are there any particular models that fit this bill?  Are there any particular models to stay away from, that the community has had experience with already?

I'm incredibly excited and want to jump on board as soon as possible, so definitely let me know!  I'm excited to be a part of the forums, as well.

Thanks again in advance, and I'll look very forward to hearing from everyone!

-3nigma :D

---

### Post by timetunnel on 2006-08-08
I have a ThinkPad R52 with DVD-multi-writer (CD/DVD/-ROM/RW/-R/+R/DVD_RAM), ATI X300 graphics card and a 15.4'' screen (1400x1050). Everything worked very good so far and I'm quite satisfied with it. Except for the fan, which is always on (that's not a Linux problem, it's that way by-design), but it's very silent compared to low-tech low-cost laptops. 

From you list, everything is there, except for the titanium/magnesium case (are there any ThinkPads that are made out of this?). Longest running time on batteries is approx. 2 and a half hours (which was 20 minutes better in old ubuntu 5.10 :(  ), officially it shall run up to 3.5 hours, but I never got that, not even with Windows.

If you want to kill Windows completely be aware that BIOS updates could become very difficult without it. I haven't tried it yet. Look here: [http://thinkwiki.org/wiki/BIOS_Upgrade](http://thinkwiki.org/wiki/BIOS_Upgrade)

---

### Post by 3nigma on 2006-08-08
Thanks very much for the heads up!

Actually, most ThinkPads after like 2000 had titanium reinforced cases, interestingly enough.

Can you offer more insight as to what I would need with a BIOS update, what the ramifications would be to go without it, etc?

I'm *THAT* new, hehe.

Thanks again for the great stuff.
-3nigma

---

### Post by timetunnel on 2006-08-08
```
most ThinkPads after like 2000 had titanium reinforced cases
```
Hmmmm. I'll have to check that out again. I always thought mine had a plastic case - at least it feels like that. It's not even a year old.

As for the BIOS update: I did them from the pre-installed Windows XP, where they came automatically when I started the pre-installed IBM/Lenovo software updater. When Dapper came out, I wanted to switch to ubuntu completey and gain the disc space filled by Windows. Therefore I killed the hidden IBM partition (which contains the Windows rescue system) completely, killed Windows XP :D , and re-installed a very basic and small Windows 2000 on a small partition. But I haven't tried a BIOS update after that, neither with that Windows 2000 install nor in any other way.

---

### Post by 3nigma on 2006-08-08
Could I wipe the XP off and just do Win2K as well, or would it be best to keep the WinXP?

I checked it out...  It looks like the "R" series, such as yours, still had plastic, but it was the T series in 2001+ that had the reinforced titanium+maganese.  I think that's still even covered in plastic, though.

*shrug*
-3nigma

---

### Post by timetunnel on 2006-08-08
```
Could I wipe the XP off and just do Win2K as well, or would it be best to keep the WinXP?

```

Well, if you're new to ubuntu or Linux I'd rather leave Windows there. I felt more comfortable with a dual boot in the beginning, because it was my first laptop, I had a printer that didn't print well in Linux, and I didn't know what the laptop would do if I killed the hidden partition. When Dapper came out I felt familiar enough with Linux to do the big step and kill Windows. However, I already regretted it for one reason: though my new HP printer is supposed to work perfectly, it doesn't. There are rare cases when printing produces strange results (which I filed as a bug already).
Sooo. Well, it's you decision, of course. If you want to play it safe and don't need the disc space, leave Windows there. When the next ubuntu comes out and you want to do a clean ubuntu install you might want to wipe Windows then.

---

### Post by 3nigma on 2006-08-08
Sounds like some of the best practical advice I've head yet, thanks again!
-3nigma

---

### Post by sco1984 on 2006-08-08
Hello,
 According to your requirement, i suggest **[COLOR="DarkRed"]I[/COLOR][COLOR="Green"]B[/COLOR][COLOR="Blue"]M[/COLOR]**® ThinkPad
 R51 series which is cheap in cost and good performance wise.
 You can tell shop keeper to fix DVD writer not Combo, so little
 more price will be added. Buy ThinkPad without XP preloaded.
 Reloaded XP costs which is included in the price of laptop.
 You ultimately paying the cost of licensed preloaded version
 of Windows XP. So buy a model which ships with DOS OS.

 Z series has Titaniun casing but quit expensive. If your
 not concern much about money, then Z series is anytime cool.
 Some changes can be found in Z series. R52 is same lookwise
 and old design. Z series gotta lotsa new enhancements. Performance wise all ThinkPad works well. THinkPad never
 gives heating problem. BE WARE !!! Some laptop users over here
 experiences graphic card buring and over heating problem due
 to UBUNTU, but i dont blame UBUNTU. As your gonna buy new
 laptop, dont try linux at the beginning. Install it in a
 Virtual machine inside Windows XP. For mroe details about 
 ThinkPad, visit > [http://forum.thinkpads.com]("http://forum.thinkpads.com") By the way your in which
 country ?

 Regard's,
Amey Abhyankar.

---

### Post by natrixgli on 2006-08-08
I'm running Ubuntu 6.06 Server w/Fluxbox on my X30, and it screams. Plus with Fluxbox you can really make the most of that 12.1" display, and the size absolutely cannot be beat for the price. I got mine on eBay for $350 shipped. 

I like to use server edition because it's text installer is so much quicker, and it doesn't come with too much stuff pre-installed. I like to pick & choose what I install. I have bits from both gnome & kde, but my XWM of choice is Fluxbox because I'm a nerd, and it's simple, and fast. (and stylish, IMHO.)

I had no difficulties, though I did have to add 2 lines to xorg.conf to enable using the middle button for scrolling. Suspend works, but hibernate doesn't. (It doesn't like to wake back up. I'm sure if I played around with /boot/grub/menu.lst I'd figure it out..)

The volume & mute buttons worked right out of the box, and the mini PCI wireless card & bluetooth adapter work great. (Windows doesn't even know they're there - I had to buy a PCMCIA card for XP....) 

I had it lock up once when I undocked it. And once it wouldn't wake up from Suspend. I'd really like to get the forward/back browser buttons working, but in due time I'm sure I will. 

One bonus with the X-series is that with the media slice, I get the best sound I've ever heard in a laptop.... And dual batteries.

BTW: I absolutely ***HATED*** the eraser at first. Now I am completely addicted to it. It is without a doubt the most efficient, and easy to control pointing device I'd ever used on a laptop. And the biggest drag with touchpads on linux is preventing accidental input... Takes a LOT of work. ;)

-n8

---

### Post by BungaMan on 2006-08-08
> **timetunnel said:**
> ...When Dapper came out I felt familiar enough with Linux to do the big step and kill Windows. However, I already regretted it for one reason: though my new HP printer is supposed to work perfectly, it doesn't...

And did you try to install windows in vmware?  You could try printing from there.

---

### Post by Nathaniel on 2006-08-08
I'd say the ThinkPad T43. The model I use (1871, I think) has Intel graphics which is supported OutOfTheBox on Ubuntu. The only thing I have problems with is suspend, but I think the newest kernel's to blame for that (not entirely sure, though)

---

### Post by bphunter616 on 2006-09-04
I prefer the IBM (Lenovo) T43 laptop w/DVD RW/CD RW option, 1gb ram, 40gb hard drive.  Originally had XP installed, replaced with Ubuntu 6.0.6.1.  Just finished installing the ATIconfig drivers (latest) to support my Westinghouse LCM19w4 (19" wide screen monitor). Achieved the desired 1440x990 screen resolution.  ;)

---

### Post by bakert on 2006-09-04
I've had pretty good results with my Thinkpad T43.  If you are in the UK you can get a preinstalled Thinkpad Ubuntu system from linuxemporium.co.uk (that's where mine came from).  Of course that means paying for new kit.

I have to use the flgrx graphics driver (not the ati that installs by default) to drive my Dell flat panel at 1920x1200 (works at lower res with ati).  Sleep has not been 100% reliable but I think I have it worked out now.

There's lots of information about running Linux on Thinkpads at [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

---

### Post by egoldtech on 2006-09-04
Hi, i will prefer always T series than R series, they are better built.
T30 is a really good laptop, P4 mobile with 2.0ghz.
If you want a lighter computer, I will go to X series, really nice a strong laptops, X30 really light and fast, you cab have a wireless orinoco built on for 20$,  but cdrw/dvd, shoud be external or docking station.

good luck
eze

---

### Post by littleiffel on 2006-09-05
I have chosen to go for a x60. And I would definitely do it again. I would even say that it is absolutely Linux friendly. Almost everything, everything necessary, worked right out of the box.

---

### Post by checkup on 2006-09-22
right now i am using a t40 with edgy. The former was a T30 with dapper.

The T40 works like a charm. 

I hated the T30 as i hate all computers with pentium4(m).

I had an R40 (Pentium4m) before the T30 and that was ok also with ubuntu. Allthough it had a p4m it was a good machine. I liked it.

Im using the T40 with mergedfb on two display and this is working very well. DRI is working on both screens and the graphics are very responsive. I'm happy with this machine right now.

---

### Post by lawcox on 2006-09-22
If you are looking for something a bit on the older/cheaper side, I use a T22 that I picked up off eBay for about $160US.  It had a "not genuine" XP install that the owner didn't want to mess with.  It has a 900 mhz PIII, 256 meg RAM, 20 gig hard drive, 1024x768 screen, and CD-RW/DVD drive.  Ubuntu runs really smooth on it, and almost everything worked out of the box.  The cases on that series are pretty sturdy and it still has a solid feel to it despite being several years old now.  Another thing that is more personal preference is the keyboard, which I prefer typing on more than my desktop computer now.  
As for built-in wireless networking, anything in the T series from the T23 onward might have the built-in antenna required for the miniPCI wireless card.  I use an atheros chipset PCMCIA card, and it works just fine.

---

### Post by thoffland on 2006-09-23
I just ordered a T30 1.8ghz 36g (I think it has +4 as the XP recovery) and 256ram which I will be installing Dapper on. I might try to dual boot it since my school might require some windows prog's that I dont want to deal with in VMware. 

I got it on Overstock.com for $500 "reconditioned".

---

### Post by stmiller on 2006-09-23
Hi any T30 owners: is that model silent? Even with fan running full, is it quiet? I'm possibly looking to grab one soon. Or possibly a T40ish Thinkpad. Thank you!

---

