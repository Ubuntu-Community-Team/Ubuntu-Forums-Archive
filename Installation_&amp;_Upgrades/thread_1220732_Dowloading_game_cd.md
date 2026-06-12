---
title: "Dowloading game cd"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by wjv on 2009-07-23
Help I can't download games cd

---

### Post by Sub101 on 2009-07-23
Could you elaborate.

---

### Post by lisati on 2009-07-23
A little more information might be helpful: Which games CD? Where from?

---

### Post by wjv on 2009-07-23
I had ubuntu downloaded yesterday, since widows crashed on my computer.  I have a number of gaming cd's that I would like to put back on my computer. Everytime i insert the disk it bring up a fodler containing all the files from the cd...autorun, sounds, setup etc.  I went to applications to add the games but I can't seem to find it. Do I need another program? What step am I missing. 

Also, I have crossover loaded.

---

### Post by Sub101 on 2009-07-23
Not all of your games from Windows will work with Linux.

But you can try installing Wine.

```
sudo apt-get wine
```

After that you can open the disc, and find a file like "setup.exe" or similar. Right click on that and select Wine Program Loader.

---

### Post by m4tic on 2009-07-23
check whether crossover supports those games first, and you might wanna check also if your graphics card supports games on ubuntu

---

### Post by wjv on 2009-07-23
Thanks, is the wine windows emulator the same thing?

---

### Post by mcduck on 2009-07-23
Yes, Wine is what people are usually talking about when they mention a "windows emulator" (although it really isn't an emulator but a compatibility layer).

Crossover Office or Crossover Games is another, although not free, option.

Still, the main point is that programs made for one operating system aren't even supposed to be usable on any other. You can't run Mac or Linux apps on Windows, you can't run Windows or Linux apps on a Mac so being able to run at least some Windows apps on Linux should be considered as a great extra, not something that you should expect to work with all your programs and games. If playing Windows games is important to you you should be using Windows.

---

### Post by Mark Phelps on 2009-07-23
> **wjv said:**
> I went to applications to add the games but I can't seem to find it. 
You can't "add" the games; you have to install them using either Wine or Crossover.

Also, if you installed Ubuntu 9.04, what is the video card/chip you're running? If it's an Intel, you most likely will have video problems.  If it's an ATI, and not one of the newer HD3x or HD4x video cards, you will not find any accelerated drivers that work with 9.04, which then means, even if you are able to get the games installed and working, they will run so slowly as to be unplayable.

As other folks have said, if your interest is in running MS Windows games, you'd be best to stick with MS Windows.

---

