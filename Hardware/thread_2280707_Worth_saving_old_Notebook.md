---
title: "Worth saving old Notebook?"
date: 2015-06-01
forum: Hardware
---

### Post by mike330 on 2015-06-01
New to Linux, but I have a basic understanding of it (run Ubuntu off flash drive to fix a couple PCs when Windows inevitably messes up).  I have an old notebook that runs like a one legged dog.  Is it worth wiping Windows and installing Ubuntu in hopes I can have a basic PC to surf the net / check emails / Youtube, etc?  Or should I donate the thing to charity?

_**Specs**_
- Toshiba Satellite t115d s1120
- Windows 7, 64 Bit
- 1.6 GHz AMD Athlon Processor
- 2GB DDR2
- 250GB HD

Please let me know if you need additional info.  Thank you in advance for your advice!!

---

### Post by Bashing-om on 2015-06-01
mike330; Hello;

Sure you can run "something" linux  on this box.
With a single Athlon CPU You are looking at (L)ubuntu or lighter, IMO .
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)

Try lubuntu and see what results:
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[INDENT][INDENT]with linux
[INDENT][INDENT]even a dinosaur can come alive
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kerry_s on 2015-06-01
install ubuntu-mate on it, i recommend 15.04 or 15.10 cause that's when it really starts getting good. 
[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

you have similar specs to my netbook. lol

install zram-config to maximize your 2gb ram.

---

### Post by mike330 on 2015-06-01
Hi Bashing,

Thanks, I will look into that.   Is it easy enough to wipe Ubuntu and go to Lubuntu?  Maybe I will try installing Ubuntu first, stress-test a couple things and downgrade if need be.  

Appreciate your advice!

---

### Post by weatherman2 on 2015-06-01
I don't like Lubuntu's desktop, LXDE - I prefer Gnome.  I find that, for older hardware, I get decent performance using Gnome "Flashback" (Ubuntu 14.04 and newer) or Gnome "Fallback" (Ubuntu 12.04), which gives it the "classic" Gnome desktop from a few years ago.  I use Metacity for the best performance.  I have someone using Ubuntu 12.04 with Gnome Fallback daily on an old laptop with only 2GB of RAM and it works just fine for basic web browsing, etc.

If you don't care about the current contents of the Windows hard drive, wiping it is easy - will happen automatically during Ubuntu installation if you choose.

I recommend sticking to an LTS version of Ubuntu like 14.04 because it will be supported longer (until 2019).

---

### Post by kerry_s on 2015-06-01
> **mike330 said:**
> Hi Bashing,

Thanks, I will look into that.   Is it easy enough to wipe Ubuntu and go to Lubuntu?  Maybe I will try installing Ubuntu first, stress-test a couple things and downgrade if need be.  

Appreciate your advice!

with just 2gb ram ubuntu unity will work, but you'll get a lot of grey screening as it uses a lot of resources. ubuntu gnome will run better than ubuntu unity but still heavy on resources.
ubuntu-mate, xubuntu, lubuntu will all run smoothly with 2gb ram & using zram-config, swap is optional, i didn't even bother adding swap since i'm using zram. you can also try elementary os, it's kinda in the middle, depends on your vid card.

---

### Post by kerry_s on 2015-06-01
> **weatherman2 said:**
> I don't like Lubuntu's desktop, LXDE - I prefer Gnome.  I find that, for older hardware, I get decent performance using Gnome "Flashback" (Ubuntu 14.04 and newer) or Gnome "Fallback" (Ubuntu 12.04), which gives it the "classic" Gnome desktop from a few years ago.  I use Metacity for the best performance.  I have someone using Ubuntu 12.04 with Gnome Fallback daily on an old laptop with only 2GB of RAM and it works just fine for basic web browsing, etc.

If you don't care about the current contents of the Windows hard drive, wiping it is easy - will happen automatically during Ubuntu installation if you choose.

I recommend sticking to an LTS version of Ubuntu like 14.04 because it will be supported longer (until 2019).

you might as well use ubuntu-mate, it is gnome 2 just forked.

---

### Post by mike330 on 2015-06-02
Thank you everyone for your advice!  I think I will start with Ubuntu-Mate and go from there.  Truly appreciated!!!!!!!!!!!!!  :p

---

### Post by kurt18947 on 2015-06-02
One thing to be aware of with older Athlon processors - they didn't handle Flash well at all. I had one but don't recall the specifics - Athlon XP perhaps? Single core and flash would peg the processor at 98%+. I think the problem was not supporting an instruction set - SSE2? It was fine with non-flash tasks.

---

### Post by weatherman2 on 2015-06-02
> **kerry_s said:**
> you might as well use ubuntu-mate, it is gnome 2 just forked.

Is Ubuntu-Mate officially supported by Ubuntu?  I got the impression it wasn't.  I assume Gnome Flashback/Fallback are officially supported, and because they have worked well for me, I'm not sure why I would go back to Gnome 2?

---

### Post by mörgæs on 2015-06-02
> **kurt18947 said:**
> One thing to be aware of with older Athlon processors - they didn't handle Flash well at all. I had one but don't recall the specifics - Athlon XP perhaps? Single core and flash would peg the processor at 98%+. I think the problem was not supporting an instruction set - SSE2? It was fine with non-flash tasks.

This series of processors is much older than original poster's notebook.

---

