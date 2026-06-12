---
title: "Laptop not working, PLEASE HELP!"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by SegMat on 2007-07-29
I've been trying to get Ubuntu working on a friend's laptop for a while.  I totally wiped his hard drive, not just format but wiped, and so I guarantee it's blank.  I put Ubuntu in there and I get to the screen where it gives you boot options from the Live CD.  The default choice, and the one that we want, is Start or Install Ubuntu.  I went to that one and it takes forever to do anything and when it does anything it displays a black and grey screen with lines up and down the screen, very fine lines (not thick).

His specs are a 10 GB HD, 256 RAM, and a 700MHZ processor.  I tried all sorts of things like taking out his wireless PCMCIA card to see if that affected it, booting it in Safe Graphics Mode, but all of them do the same thing.  I know the laptop isn't broken because it was running XP and he put XP back on there in the mean time till I can get Ubuntu running on there.

I hope I gave enough details, please help me out!

Matt Segstro

---

### Post by dmizer on 2007-07-29
in the menu, there should be an option for testing the integrity of the cd.  try that first.  if it passes the integrity test, then we'll need to enter some boot parameters.

with your specs, you'll probably be better off looking for an alternate install cd, so you can install via text instead of trying to load up the live cd.

---

### Post by SegMat on 2007-07-29
I'm not that great with Linux, I wouldn't be able to install it without a GUI.  Is there a list of commands out there on the net that I could print out to do a CL install?  I will check the CD next chance I get with his laptop, but I don't think it's the CD as I have installed using that CD on many computers and I think it's fine.

Thanks for your help,

Matt

---

### Post by dmizer on 2007-07-29
the text install is just a series of menus you go through via arrow keys and with the <tab> and <enter> key to select.  you don't actually have to type anything.  it's really quite simple, i did the ubuntu alternate install my first time ever using linux, and it caused me no problem.  with a full install on a wiped hdd, you shouldn't have to change anything ... all defaults should be acceptable.

also, if you install in text mode, i think your display problems will resolve themselves unless you have some obscure video card.

i also suggest using xubuntu rather than ubuntu.  it will make that computer much more usable because it uses xfce for it's window manager instead of gnome.  gnome is more robust, but requires more resources.  for probably 98 percent of situations, xfce will be sufficient.

i have several 700 mhz laptops running ubuntu of various makes.  what is the make and model of the laptop you'll be working with?

---

### Post by SegMat on 2007-07-29
A Sony Vaio.  I don't know what year or anything but I hope that's good enough.  I'm happy to hear that it won't be very difficult to do the text install.  Thanks for your help.  About Xubuntu, I tried it once but gave up on it on one of my older machines because it doesn't seem to come with anything.  That's what I like about Ubuntu is it comes with lots of programs.  Xubuntu didn't even come with a "Start Menu" of sorts or anything.  I couldn't find any programs or even find out how to access the Internet.  My friend is OK with his computers running slow so Ubuntu won't be bad for him.  I just have to get it working in the first place and then he's fine with it.  I'll try downloading the alternate CD from the Ubuntu website.

Once again, thanks for all your help!

Matt Segstro

---

### Post by ugm6hr on 2007-07-29
> **SegMat said:**
> Xubuntu didn't even come with a "Start Menu" of sorts or anything.  I couldn't find any programs or even find out how to access the Internet. 

Not sure which version of Xubuntu you tried - but Feisty (7.04) definitely has a "Start Menu" (called Applications), and comes with programs (although not as many as Ubuntu) that tend to be lightweight and run fast.  As for accessing the internet - it is the same as Ubuntu (unless you have wifi - in which case it doesn't have Network Manager installed as default - but Wicd is easy to install).  Adding programs is just like Ubuntu too - there is Synaptic Package Manager - if you want all the "heavyweight" programs of Ubuntu.

Your choice of course, but I wouldn't want anyone else to be misled by your statement.

---

### Post by SegMat on 2007-07-29
OK, sorry, maybe I did something wrong.  I might try it again now that you say that it's not usually like what I had.  Maybe I got the wrong CD or something.  I'll check it out again.

Thanks,

Matt

---

### Post by ugm6hr on 2007-07-29
> **SegMat said:**
> OK, sorry, maybe I did something wrong.  I might try it again now that you say that it's not usually like what I had.  Maybe I got the wrong CD or something.  I'll check it out again.


I suspect the Xubuntu LiveCD will work on that setup (you might have to start in Safe Graphics mode if it doesn't work first time).  That way you can try it out first.

Get it here: [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

To get Wicd: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by cmnorton on 2007-07-29
If there is a "safe mode" option, use that, and then try installing. I ran into a blank screen hang on a TravelMate 630 (Acer).

---

### Post by benhagerty on 2007-07-29
Maybe try Fluxbuntu? That is made for older systems.

---

### Post by ugm6hr on 2007-07-29
> **benhagerty said:**
> Maybe try Fluxbuntu? That is made for older systems.

But Fluxbuntu doesn't have a readily accessible "Start Menu" (you have to right-click on desktop), and it comes with no GUI for mounting drives, networking etc...  Not exactly a good introduction to Linux from the Windows world.

---

### Post by SegMat on 2007-07-29
Thanks for the heads up on Fluxbuntu, I was going to try it but if it's not very user friendly for those switching from Windows, it's a huge no-no for me.  Thanks for all your help, I'll try to work on the machine today.

Matt

---

