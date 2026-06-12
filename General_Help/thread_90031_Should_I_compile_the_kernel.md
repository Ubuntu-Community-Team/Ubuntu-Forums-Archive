---
title: "Should I compile the kernel?"
date: 2005-11-14
forum: General Help
---

### Post by eazolan on 2005-11-14
I had read somewhere that if you compile Ubuntu for your specific PC, it will run faster. I'm using a celeron 2.4 with 1GB of memory, and I'm hoping to get a little more speed.

Before I start down this road, I thought I'd ask if this is a good idea. Also, would celerons be considered 586 or 686?

Thanks!

---

### Post by steil on 2005-11-14
The celeron 2.4 would be a 686. I'd suggest just installing the precompiled 686 kernel by installing the "linux-686" metapackage. Either though synaptic or a terminal with the following code.

```
sudo apt-get install linux-686
```

---

### Post by Malphas on 2005-11-14
[http://wiki.chad.org/wiki?DoNotRecompileLinux](http://wiki.chad.org/wiki?DoNotRecompileLinux)

[http://www.linuxheadquarters.com/howto/tuning/kernelreasons.shtml](http://www.linuxheadquarters.com/howto/tuning/kernelreasons.shtml)

---

### Post by LorenzoD on 2005-11-14
By selecting a kernel patchset and compiling specifically for your architecture you will be able to get a speed increase, at least if you know what you are doing. Be aware though, that the speed increase might not at all be as dramatic as you had hoped. 

I would recommend that you do compile your own kernels since you learn some new things along the way. And you can keep some junk out of the kernel that you never use anyway.

---

### Post by RAOF on 2005-11-14
I **really** wouldn't bother compiling your own, custom kernel.  You need to fiddle, the only thing* that "keep(ing) some junk out of the kernel that you never use anyway" is going to save is disk space, and not that much either.  Practically everything in the Ubuntu kernels is built as a module, so if you don't use it, it 'aint loaded.

I have a vanilla 2.6.14 kernel that I built installed, but only so I can submit a kernel bug (AMD64 kernels panic when I eject my firewire iPod).  It's just one more annoyance you really don't need.

**Edit**: Sorry if that sounds antagonistic.  I just think that the answer to "should I compile my own kernel" should be "does the new vanilla kernel support some piece of your hardware that the Ubuntu one doesn't?  If not, no".  Life's too short to compile kernels :)

* You **can** remove some stuff from the actual kernel image.  But essentially, do you know what removing it does?  And are you sure you'll never connect a piece of hardware that uses it?  All the options are things like TCP_MODULE_UNFANGLE_STACK.  What the hell does that do? :)

---

### Post by az on 2005-11-14
[QUOTE=eazolan]I had read somewhere that if you compile Ubuntu for your specific PC, it will run faster. [/QUOTE]

Not really true.  You probably will get one-fifth of one percent better.


[QUOTE=eazolan]I'm using a celeron 2.4 with 1GB of memory, and I'm hoping to get a little more speed.
[/QUOTE]

Capt'n!  Were already at warp nine!


Ooo.! M'uh bearins.  Muh pooor bearins!  (Thick scottish accent)

---

### Post by grendel_khan on 2005-11-14
Despite the curmudgeonly rantings above me, there **are** some good reasons to compile your own kernel. "Just because" isn't really a compelling reason. However, "I'd like to learn how the kernel build system works" is quite valid, as is "I need to patch my kernel".

Patch your kernel, in this day and age? Scoff, scoff! But no, I just yesterday [helped out a fellow](http://ubuntuforums.org/showthread.php?t=89592) who has hardware which isn't supported in the main kernel. There's an available patch for it, but it's not in the Ubuntu sources or even in the kernel.org sources (though it's in bugzilla.kernel.org as [BUG #4060](http://bugzilla.kernel.org/show_bug.cgi?id=4060)). What's the user to do, other than download the Ubuntu kernel, patch it and install it?

---

### Post by Malphas on 2005-11-14
I don't think anyone was communicating in a curmudgeonly manner, they were just mentioning the facts pertaining to what the original poster actually asked - i.e. would they see any performance increase from recompiling the kernel.  No-one is scoffing at recompiling to learn something new or to support a certain piece of hardware (which he/she didn't mention wanting to do).

---

### Post by wrtrdood on 2005-11-14
Isn't learning what GNU/Linux is all about?

  Building kernels is not as intimidating as it once was.  If this were the pre-2.4 days I would simply tell you that such an undertaking is not for the timid.  However, there are a number of excellent HOWTOs written and posted in these very pages that can guide even the newb to a successful conclusion.  I grant you that there's a lot of entries in a kernel config that can be bewildering.  The best thing to do is start with a good base using an existing config file and change only the things you know affect your particular system.  Even so, experimentation will often only cost you time (rebuild and testing).  There is no better way to learn, in my opinion.

  Depending on the architecture, building a custom kernel can often improve a lot of things.  As for me, it was significant.  The default kernel is not optimized for my platform (a Crusoe based laptop) and boot times were in the +10 minute range.  Using Breezy was downright painful.  Everything moved like molasses.  Now boot time is under 3 minutes and it feels even snappier than Hoary.  Big change.  As they say YMMV.

I can't disagree with the other posts here, though.  I'd be surprised to see much impovement on that sort or hardware but, you never know 'til you try.

---

### Post by darknuala on 2005-11-14
If you don't have any data, that you are not afraid to lose, I say go right ahead.  I tried it a few times, and there was a different issue each time.  I didn't need the optimizations, but just wanted to know how it would do.  Never has worked well for me.

---

### Post by Malphas on 2005-11-14
[QUOTE=wrtrdood]Isn't learning what GNU/Linux is all about?[/QUOTE]
First I heard.  I always thought that it was about developing a free Unix-like operating system.

---

### Post by eazolan on 2005-11-16
Thanks for all the answers guys. I did a uname -a and it seems that I'm already running the 686 kernel. 

[QUOTE=wrtrdood]Isn't learning what GNU/Linux is all about?[/QUOTE]

Uh, in this case no. I'm building my mother a new PC for Christmas to replace the one she's been using for 7 years now. Win98.

I thought I'd give a shot at installing Win98, and the installation went really well. I thought I was done until I tried to open up a terminal window and it would bluescreen. At that point I decided to go with Linux and wiped the drive.

She is very limited in her computer use. 
#1 Email, 
#2 Business record keeping, 
#3 Web browsing.  

So I figured I'd give Unbuntu a shot. It has a lot of slick areas, but I find web browsing with Firefox to be shockingly slow. I even added the fasterfox plug in.

Oh, so anyway, I don't want to learn all about the ins and outs of Linux. I want to install it, and have it work, and not have her call me up because of spyware problems and the like. And I want it to be faster than her old PC in all ways, by a signifigant amount.

Her old PC is a 233 pentium for pete's sake!

---

