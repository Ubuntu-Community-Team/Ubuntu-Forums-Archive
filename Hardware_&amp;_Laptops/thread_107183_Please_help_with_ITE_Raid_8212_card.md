---
title: "Please help with ITE Raid 8212 card"
date: 2005-12-22
forum: Hardware &amp; Laptops
---

### Post by ronmonki on 2005-12-22
I see other poeple have had problems with this card, but have seen no solution.

I saw mentioned in another thread to recompile kernel with this feature, any pointers on this, ive never compiled a kernel before, how difficult is this.

the card is showing in the Device Manager, and i have downloaded the drivers from ITE website, I have the source files which wont work with make.

I also have a debian , redhat, mandrake, and suse versions, but they aint packaged , just a bunch of files   which do u  reccomend i use, or does anyone know a simple alternative?? I need this raid controller to work so i can access al my other hardrives, i have ubuntu installed on my scsi drive no problems there, just wanna access my extra drives now.

i have followed these instructions from the readme.

 You can test out the module to ensure that it works by the following
       commands:
       
       # modprobe sr_mod
       # modprobe sd_mod
       # insmod iteraid.o
       

I get this error :
insmod: error inserting 'iteraid.o': -1 Invalid module format

---

### Post by ronmonki on 2005-12-22
only 2 views after 2 hours, at this rate ill never get any help?  anyone please some advice on where to go next, I dont expect to be spoon fed, just a little nudge in the right direction.

---

### Post by ronmonki on 2005-12-23
fixed see thread above, wicked tutorial on how to fix it, job done now. :)

---

### Post by chrislau on 2006-01-06
The module you are using was not compiled for your kernel. You won't be able to load it. A new module is available since the 2.6.13 kernel. So, you must choose between :
- compile a new kernel [http://www.kernel.org]("http://www.kernel.org")(2.6.13, 1.6.14 or 2.6.15,...)
- or wait until the Ubuntu maintainers change the kernel level.

---

### Post by sergiopereira on 2006-04-21
Good news in the current beta LiveCD. See this thread:
[http://ubuntuforums.org/showpost.php?p=944250&postcount=10](http://ubuntuforums.org/showpost.php?p=944250&postcount=10)

---

### Post by fowie on 2007-12-30
Have you kept this working with Feisty or Gutsy?  I started at Feisty and have never gotten the it8212 to work unless I did a custom kernel compile--even then I get input/output errors.

---

### Post by jai_mantravadi on 2008-03-13
fowie,
I've got the same issue too. I'm using the IT8212 raid 0 as a secondary drive and I'm upgrading from Windows XP to gutsy. 

It looks like this has been reported in [bug #106931]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/106931"). Steven Ayre pulled in an old working "driver" that you'd have to compile yourself (he provides a makefile) and introduce as a module along with some *basic* instructions. I've just installed gutsy on a system and since its stable in all other aspects, I'm going to try recompiling this with the gutsy kernel headers. If it works, I'll post back what I did and how I did it. Hopefully it'll go quick and smooth. If not, I'll post back and let you know it didn't work.

Otherwise, this has apparently been fixed with Hardy Heron (as of Jan 08), so you might try upgrading if that suits your style, although keep in mind Hardy is an alpha build, so you'll be bumping into some issues there. If you're not too worried about it, just wait until Hardy's released in about a month and a half, and you should be golden!
Jai

---

