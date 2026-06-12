---
title: "Acer Hotkey driver for Linux"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by adrislayer on 2005-05-02
If U have an acer, it's painfull to use wifi on linux because of the wifi button.

This can fix it well, and it works also for non-Acer...

[http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)

So here is the link, but I haven't tried it yet, like i'm a newbie, but I will give it a try when I find the ubuntu cd back...

If I succed, I will try to make a tutorial, but if someone more reliable than me can try it, it would be nice 2  :)  :grin: 

Hope It will be usefull

---

### Post by snop on 2005-05-02
Hi,

I've tried those drivers. As installing the drivers I was writting a small tutorial... When I finished I realized that they don't work (I own an Acer Travelmate 4001Wlmi). Anyway, here's my small tutorial... If it works for you then fine:

HOW-TO: Compiling Acer Hot keys driver found at [http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/) under Ubuntu Hoary:
	
1. Download the driver and uncompress it whenever you want (I assume that you have knowledge enough to do such a thing. It's just a "point and click" operation).
	
2. In order to compile de driver you need the kernel headers. Go to Synaptic (or apt-get for "experts") and donwload the appropiate kernel header. To know the version you need you can issue "uname -r" and look for your kernel version. For instance: mine is 2.6.10-5-686
	You need also the build-essential package. Install it as well trough Synaptic or apt-get.

3. Open a terminal and go to the path where you uncompressed the files mentioned at step one and type:
		make

You should see no errors. If so double check steps 1 and 2. I may be wrong and you may need another package that I've already installed on my system. Usually errors give you a clue of what package you may need.

4. Copy the resultant module (acerhk.ko) to your kernel module dirs:
sudo cp acerhk.ko /lib/modules/2.6.10-5-686/kernel/drivers/char/

Be aware that you may be using a different kernel than me. So you'll need to change 2.6.10-5-686 for your currently running kernel (remember that we found its release number at step 2 issuing "uname -r").

5. Update module dependencies: 
sudo depmod -a

6. Try loading the module:
sudo modprobe acerhk

Again, you should see no errors. If so you've probably compiled your driver for a wrong kernel.

7. As INSTALL file provided by drivers says I tried to read the keys or light the wireless led.

I try issue this command as INSTALL file says:

cat /proc/driver/acerhk/key

and there's no file named "key" at /proc/driver/acerhk. There are only these dirs:
blueled      info         led          wirelessled

Then I tried to issue commands like this:
echo on > /proc/driver/acerhk/wirelessled

... but this does nothing.

At drivers website it says that Tavelmate 4000 is compatible but it's not for me. Perhaps I do something wrong.

Johan Vromans provides a driver for mail led (that I haven't tried) here:
[http://www.squirrel.nl/people/jvromans/articles/TM4001WLMi/hacks/acerkeys.html](http://www.squirrel.nl/people/jvromans/articles/TM4001WLMi/hacks/acerkeys.html)

Bye

---

### Post by Spif on 2005-05-02
Take a look at [http://zepto4200.linux.dk](http://zepto4200.linux.dk) on how to install Acerhk.

---

### Post by snop on 2005-05-03
[QUOTE=Spif]Take a look at [http://zepto4200.linux.dk](http://zepto4200.linux.dk) on how to install Acerhk.[/QUOTE]

I guess the address you intended to point was [http://www.student.dtu.dk/~s971652/znote4200.html#ipw2200](http://www.student.dtu.dk/~s971652/znote4200.html#ipw2200)

I'm gonna try this when I get home. The main difference between that guide and mine (apart from the latest scripts) is that instead of passing "on" to /proc/driver/acerhk/wirelessled it puts a "1" (and uses a different computer...).

Thanks for the info.

SnOp

---

### Post by Spif on 2005-05-03
Sorry, wrong link...

[http://znote4200.linux.dk](http://znote4200.linux.dk)

---

### Post by snop on 2005-05-03
Hi,

Ok, I've tried the driver again. It works indeed. But it doesn't do what I expect. I can set wirelessled on and off by software (achiving the same result as phisicaly pressing the buttons on the laptop).

But what I wanted was to see the led turning on and off depending on the state of wireless connection. Now it's always off (although wireless works fine).

As README says "keys" are not available for "Dritek" laptops (I don't know what a Dritek laptop is exaclty...) and my laptop is one of those "Driteks" (according to the info provided by the driver at /proc/driver/acerhk/info).

Well, I think the driver is not quite useful for me.

Bye

---

### Post by adrislayer on 2005-05-04
thanks for your guide, it's very usefull

I just tested now and my wifi works fine but I don't have a led either...

---

