---
title: "How to take screenshots in Ubuntu installation?"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by Mikko Huovila on 2005-12-07
I'd like to know, if there is possibility to take screenshots in Ubuntu installation. In some distros, like Mandriva, Fedora and Suse, you can take screenshots by simply pressing F2, printscreen etc. 

How are screenshots taken in osdir and many other pages?

---

### Post by heimo on 2005-12-07
Hi Mikko!

There may be easier way to do this, but personally I use Gimp (it's installed by default in Ubuntu). In menu: File->Acquire->Screen Shot. If I recall correctly, there's also some kind of screenshot applet available for this - right click on panel->Add to panel->search for correct applet. Hopefully this helps.

---

### Post by Rinzwind on 2005-12-07
I think he means during installation of ubuntu!?

If you mean inside Ubuntu after entering kde: I like ksnapshot  :)

---

### Post by Mikko Huovila on 2005-12-07
Yes, I mean during the installation. It's easy to take desktop screenshots - just press "printscreen". I'm wondering how to do the same when you are installing ubuntu...

---

### Post by heimo on 2005-12-07
Oh, ok. I believe many of those are made using some virtualisation software, like vmware. That's my guess.

---

### Post by Mikko Huovila on 2005-12-07
[QUOTE=heimo]Oh, ok. I believe many of those are made using some virtualisation software, like vmware. That's my guess.[/QUOTE]

Yes, it's probably so. It's too bad that there isn't easier way to do it...

---

### Post by bwog on 2005-12-07
There is already a tutorial with screenshots of the installation of ubuntu somewhere on this forum. I suppose they were made with a digital camera.

Oh, there are even videos :) 

[http://ubuntuforums.org/showthread.php?t=99271](http://ubuntuforums.org/showthread.php?t=99271)
[http://ubuntuforums.org/showthread.php?t=99274](http://ubuntuforums.org/showthread.php?t=99274)

---

### Post by Mikko Huovila on 2005-12-07
[QUOTE=bwog]There is already a tutorial with screenshots of the installation of ubuntu somewhere on this forum. I suppose they were made with a digital camera.

Oh, there are even videos :) 

[http://ubuntuforums.org/showthread.php?t=99271](http://ubuntuforums.org/showthread.php?t=99271)
[http://ubuntuforums.org/showthread.php?t=99274](http://ubuntuforums.org/showthread.php?t=99274)[/QUOTE]

These are great, but I asked this, because I want to take screenshots of the installation process in my own language. Maybe a digital camera is easiest way to do that...

---

### Post by gord on 2005-12-07
you might as well just run it inside qemu and take screenshots of that, it will be exsacly the same as what you have when you run the installer yourself and will be obviously much higher quality than a digital camira :)

---

### Post by gord on 2005-12-07
i just made this in qemu, its the language selection screen in the breezy installer

[IMG]http://img451.imageshack.us/img451/2492/screenshotqemu6rc.png[/IMG]

---

### Post by Herman on 2005-12-07
Hello, Mikko Houvila, the ways that heimo and gord have suggested, (using a 'virtual machine' of one kind or another), are quite correct and would have been much better than the way I have chosen to the illustrations in my 'sig link' website: 'Ubuntu Dual Boot'.
At first I started of with just a single-page website just about the FAT32+Ubuntu install and it only needed a few illustrations. First, I looked into VMware as that's how I learned that these screencaps were made: [http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1)

However, I wish I had an illustrated tutorial or example of how to install VMware or some other virtual machine! :D  After a look at the instructions, :confused:  and fearing a large download bill from my ISP for the software download, I decided to make my own images from scratch.
I only needed a few of them, (or so I thought) so it seemed like the easiest way out at the time.:rolleyes: 

Since then, the 'Ubuntu Dual Boot' website has grown considerably and been updated to Breezy, and then grown more again. I would have been better off with a virtual machine to begin with had I known the future when I was back in the past.

 I have two computers beside each other and carry out an install in one. At the same time, I make illustrations of what appears on the screen for each step of the process using the other computer nearby.  I just use Microsoft 'Paint' to make the initial images, because it's a lot simpler the GIMP, and hence a little quicker, (for me anyway). 'Paint' makes good 'bitmap' images, but does a very poor job of 'saving as' the .gif file-type. I boot into Ubuntu and mount the Windows file system, navigate to my bitmap images, open them with 'GIMP', and 'save as':  .gif
GIMP is also the way I make them animated, which is another thing I don't think can be done in 'Paint'.
Well, that's the idea of dual booting: 'to make the best use of the software in both systems'.
It is quite a laborious and time consuming job to begin with, but now I have a good collection of them it is quite a lot easier, I can often find an old one that's close to what I need and just alter the words or numbers to suit a new situation I'm illustrating.
Both ordinary .gif files and also .gif animations are much 'lighter' (kilobytes) than bitmaps in terms of upload costs and storage space on the ISP's server. (Like about 1/20th the number of kilobytes!). That's why they all need to be .gif
If it helps you, you may take screencaps of any or all of mine and use those for your purposes, I would be only too pleased to be able to share them. You can then alter them by typing your own language over the top of the words I have.
After all, Ubuntu and Open Source is all about sharing. :D  (Herman).

---

### Post by aysiu on 2005-12-07
Qemu's not a bad idea. I've used it before, but it goes only so far. Once I get to the partitioning part of the installation, it doesn't know what to do because it can't really detect my hard drive.

Still, it's very simple to set up.
You ```
sudo apt-get install qemu
```--making sure you have the right repositories, of course.

Then, assuming your CD is in /dev/cdrom, you just run the command ```
qemu -cdrom /dev/cdrom
```

---

### Post by Herman on 2005-12-07
Hey, great, aysiu, thanks! You are worth your wieght it gold! :D  I have to go right back to work for now, but I'll give that a try as soon as I get home!
 Be sure to let me know if I can do anything for you! 
Your ubuntu_user_guide_05.11 is really neat! So is the rest of your work. I put some links to it on my site, ( how to use synaptic especially), I hope that's okay. (Herman). :D

---

### Post by aysiu on 2005-12-07
[QUOTE=Herman]Hey, great, aysiu, thanks! You are worth your wieght it gold! :D  I have to go right back to work for now, but I'll give that a try as soon as I get home![/quote] Keep in mind that it will work only to a certain point in the installation process.

> Be sure to let me know if I can do anything for you! I don't have the energy right now, but I wouldn't mind if you'd let me eventually convert your dual-boot guide into a PDF. It'd be awfully helpful to new folks to have a nicely printed out copy of what to do.

> Your ubuntu_user_guide_05.11 is really neat! [Version 05.12 is already out](http://ubuntu.xgn.com.br/ubuntu_user_guide_05.12.pdf). I'm planning to update it every month.

> So is the rest of your work. I put some links to it on my site, ( how to use synaptic especially), I hope that's okay. (Herman). :D I link to you several times a day--seriously. Your dual boot guide is the best, bar none.

---

### Post by Herman on 2005-12-08
> I don't have the energy right now, but I wouldn't mind if you'd let me eventually convert your dual-boot guide into a PDF. It'd be awfully helpful to new folks to have a nicely printed out copy of what to do.
Sure, aysiu, I think that would be a great idea! I'd be proud if you'd want to do that! You might be able to correct it a little here and there too, if you see anything that doesn't look right, or if something needs to be added. Then I'll be able to download the .pdf file too, and then fix the website.  You are better with words than I am. I want to make it suitable to get someone who has never used Linux before to be able to install Ubuntu easily and be up and running quicky and easily with all the main things like LAN, printer, and being able to mount their other file-systems. I guess I'm getting close to having that done. I want to finish that page on booting because I think booting worries a lot of people and for no good reason other than 'fear of the unknown'. Then I think I'll concentrate on perfecting it rather than making it too much larger.  (Improve the quality rather then add more quantity).
> Version 05.12 is already out. I'm planning to update it every month. Thanks! I've just downloaded it now, I'll read it after this message is sent. 
>  I link to you several times a day--seriously. Your dual boot guide is the best, bar none.  Thanks aysiu, I'm pleased that you like it, and that people find it useful.    Well, bye for now (Herman) :D

---

### Post by aysiu on 2005-12-08
[QUOTE=Herman]Sure, aysiu, I think that would be a great idea! I'd be proud if you'd want to do that! You might be able to correct it a little here and there too, if you see anything that doesn't look right, or if something needs to be added. Then I'll be able to download the .pdf file too, and then fix the website.  You are better with words than I am.[/quote] It's on my to-do list. When I get the time and energy (this could be months from now), I'll let you know when I'm ready. I'll download your webpage, tweak it, make it into a PDF, send it back to you for proofing. When we're both satisfied with how it looks, we can post it.

> 
I want to make it suitable to get someone who has never used Linux before to be able to install Ubuntu easily and be up and running quicky and easily with all the main things like LAN, printer, and being able to mount their other file-systems. I guess I'm getting close to having that done. I want to finish that page on booting because I think booting worries a lot of people and for no good reason other than 'fear of the unknown'. Then I think I'll concentrate on perfecting it rather than making it too much larger.  (Improve the quality rather then add more quantity). I really admire your guide. I think the Wiki and other documentation serve certain needs, but, having been a new user only recently, I can attest to the need for screenshots and step-by-step walkthroughs for new users.
 
> Thanks aysiu, I'm pleased that you like it, and that people find it useful.    Well, bye for now (Herman) :D Will be in touch...

---

