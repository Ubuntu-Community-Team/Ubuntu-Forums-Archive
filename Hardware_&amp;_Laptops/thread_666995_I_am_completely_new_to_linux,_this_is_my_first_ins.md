---
title: "I am completely new to linux, this is my first installation."
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by necroed on 2008-01-13
Well, after being fed up with with vista and all of it's useless crap, I decided to dual boot with linux as of now. Now, the only question is how I will install it and get the drivers to work , seeing as linux on a computer is a new concept for me, and I've been reading that the drivers are a problem to get working. I don't have any knowledge on the script to get the drivers working or anything, so I need a version of linux that can work on a laptop with these specs:

Toshiba laptop A215-S7427 with:
An AMD athlon dual core processor, 64.
An ATI catalyst driver, fairly new, don't know the model name.
A realtek wireless card.
A dolby sound card.

Any suggestions on which version of linux I should use with an installation guide for a complete noob to linux like me?

Or is it impossible to install without some basic knowledge of it first? :(

---

### Post by moephan on 2008-01-13
I'm a little confused. Have you already installed a Linux distribution and some things aren't working? If you haven't installed yet, you may be pleasantly surprised. Installations of Linux distributions like Ubuntu and PCLinuxOS are much easier than installing Windows. 

If I were you, I would download Ubuntu and PCLiniuxOS ISOs and make the CDs. You can boot from the CDs without installing. Whichever one works with all your hardware (wireless is typically a tricky spot but getting much better) install that one to dual boot.

HTH

Cheers, Rick

---

### Post by ryanVickers on 2008-01-13
In theory it should install, but just so you know ATI tends to be much more of a pain than nVidia :(

---

### Post by Vince-0 on 2008-01-14
I find Ubuntu is really easy to get up and running on most laptops. However, it does require some configuration tweaking so that your graphics drivers etc work. Ubuntu has a restricted drivers manager, which I used to install the driver for my ATI x2500 without any hassle. Synaptic package manager also provides a user friendly method of getting any drivers or programs.

Ubuntu's installation process is very automated and you can pretty much just click 'next' all the way through. Bare in mind though, that Linux uses a completely different file system to windows and although linux can be set up to read from a windows file system, windows wont read from a linux file system. So changing back to windows requires a file system change before you can even begin installing windows again ( should you ever want to BLEH)

Ubuntu will, generally, automatically install your network card and sound drivers. Even blue tooth and wireless drivers worked with my Acer laptop, but required some tweaking.

It is my experience that any problem you come across, someone will have already had a similar issue and found a solution on the forums. The forum community is more than willing to help a newbie. With just a little research and perseverance you can do anything.

---

