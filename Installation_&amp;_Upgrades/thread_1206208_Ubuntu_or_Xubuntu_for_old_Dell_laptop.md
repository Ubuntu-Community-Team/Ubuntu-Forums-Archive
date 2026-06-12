---
title: "Ubuntu or Xubuntu for old Dell laptop"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by roschell on 2009-07-06
I have gone through the install from Ubuntu mini..

However after more research I am not sure Ubuntu is the right choice.

Would Ubuntu or Xubuntu be better for the Dell C400? Is there any difference to Remix?

CPU 866 MHz
30 GB hard disk
256 MB RAM

Its for my sister who has got no experience with Linux at all so I thought Ubuntu is the right choice but would it work well on the hardware?

Thanks for your responds

---

### Post by scrooge_74 on 2009-07-06
You should do a alternate install on that machine and install Xubuntu which uses Xfce which is lighter than regular Gnome in Ubuntu (but you need to get used to a few things not being as easy as point and click)

Oh and Remix is not for that type of processor

---

### Post by roschell on 2009-07-06
I got the 11 MB image from here

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

it  runs even when the screen is flashing like a mad I hope the install will go OK and flashing will get fixed

Are you saying the Gnome version would not work well? 
Would the XFCE be difficult to move in for newbie?

Thanks for prompt reply.

---

### Post by scrooge_74 on 2009-07-07
Nah, Xfce is good to go, I'm just a bit lazy to do things Xfce way. You downloaded a minimal CD which is like the netboot CD from Debian, it will install a very small system and then you will need to download the rest.

If you use the alternate CD you get a lot more packages in the CD which makes things a bit faster for installing (unless you have a pretty good conection)

---

### Post by Bucky Ball on 2009-07-07
Ubuntu won't reliably run on that amount of RAM. Install Xubuntu (Alternate Install ISO) and once you have that up you could try installing 'ubuntu-desktop' from Synaptics and see if it will handle it (or just Gnome). If not, uninstall and back to Xfce. 

Xfce is your best bet. :)

---

### Post by scrooge_74 on 2009-07-07
Gnome will run (I know for a fact), but the system will be a bit slow with that amount of ram, so Xfce will be the best way to go

---

### Post by spcwingo on 2009-07-07
Any *buntu will run slow on that machine.  You'd be better off with Puppy on that machine...just my $0.02.

---

### Post by snowpine on 2009-07-07
If ease of use for a first-time Linux user is your top priority, Xubuntu is a good choice.

If your first priority is speed, you may find it's not the #1 goal of the Ubuntu/Xubuntu project. Other distros (AntiX, Puppy, SliTaz, etc) are less full-featured, but are designed specifically for older hardware.

My advice is to start with Xubuntu, then if you are not satisfied with its performance, explore some other options. Good luck!

---

### Post by roschell on 2009-07-16
I have tried Puppy recently and Slitaz as I had problems getting other distros running on this kind of hardware.

Both are fantastic OSs, very light, very responsive and good hardware detection however there are not for linux newbie, there are more for intermediate and advanced users or as a rescue OSs.

ArtiX have not experienced.

After above discussions I would incline towards the try of Xubuntu over Ubuntu and Debian which is harder to use for newbie, but agree it is a top choice. Having discovered some more options would love to get your two cents for these too, if possible. 

What comparisons, pros and cons, would you raise for such as **Linux Mint XFCE**, **Pclinux XFCE**, and **Dreamlinux**? Thanks for discussions beforehand.

---

### Post by spcwingo on 2009-07-16
> **roschell said:**
> I have tried Puppy recently and Slitaz as I had problems getting other distros running on this kind of hardware.

Both are fantastic OSs, very light, very responsive and good hardware detection however there are not for linux newbie, there are more for intermediate and advanced users or as a rescue OSs.

Puppy is definitely not just for experienced users...I started out on Puppy.  :)

---

### Post by GerryB on 2009-07-16
[QUOTE=roschell;7573411]I have gone through the install from Ubuntu mini..

However after more research I am not sure Ubuntu is the right choice.

Would Ubuntu or Xubuntu be better for the Dell C400? Is there any difference to Remix?

CPU 866 MHz
30 GB hard disk
256 MB RAM

Its for my sister who has got no experience with Linux at all so I thought Ubuntu is the right choice but would it work well on the hardware?

I would just put in another 256 MB of RAM and Ubuntu would make it a fantastic computer.

---

### Post by roschell on 2009-07-17
GerryB, I certainly can raise that idea however dont think she will want to spend anything on this laptop. So, I am intending to install what will actually work. :(

Dreamlinux has got minimum of 128MB and have feeling XFCE should be light on any hardware with 256MB available.

---

### Post by scrooge_74 on 2009-07-17
Worst case scenario, go fetch the debian net install CD and go from them, in the end Ubuntu/Puppy/DLS I think also they are derivaties of Debian, that way you can fine tune what you want to install

---

### Post by GerryB on 2009-07-17
> **roschell said:**
> GerryB, I certainly can raise that idea however dont think she will want to spend anything on this laptop. So, I am intending to install what will actually work. :(

Dreamlinux has got minimum of 128MB and have feeling XFCE should be light on any hardware with 256MB available.

________________

I've installed Dreamlinux(3.5)on some computers with less capacity than the laptop you're dealing with and it flies. If she likes the OSX type of look, that would seem like a good choice.

---

### Post by roschell on 2009-07-19
As the new Mint XFCE is taking its time in getting to the light, testing version called boot error after 3 burns on which md5 was 100%, I opted for Mint 6 XFCE and that one wont boot :(

Still tempting for Dreamlinux but having a little doubts after seeing few reviews > "beauty from outside, lemon inside". 

I have been running on it Puppy for now but newbie with all the new directories, mount points and apps. would grow mad :confused: Nevertheless it is a great OS.

Well, after shortlisted USB focused distros we have left AntiX, which looks promising; Xubuntu which has got a hidden doubts in me being a bit heavy, as the C400 has got shared video of 48MB too; and finally the newcomer expected early next month - pclinux XFCE phoenix

Should also add the C400 does not have internal optical drive which has done some hundreds of miles and therefore I more inclined towards rolling distro.

- AntiX
- Pclos Phoenix (this is a successor of SAM linux btw.)

---

