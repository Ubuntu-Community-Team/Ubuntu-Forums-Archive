---
title: "Stamina/Speed switch on Vaio SZ Series"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by bazzard on 2007-11-08
Hi

I'm using a Sony VAIO SZ3HP laptop under gusty 7.10

I have nearly got everything working apart from a couple of things.

I want to get the stamina/speed switch working which allows switching between the two different graphics modes available. There seems to be a solution to this here under the video heading: [http://ariel.vardi.free.fr/ariel//vaiosz.html](http://ariel.vardi.free.fr/ariel//vaiosz.html)

However, because I'm a n00b to linux, I don't know where to start to get the switch working using the explanation on that site. Would someone please break it down for me step by step for a n00b, It would be much appreciated.

Also, if anyone knows how to get the built-in mic and line-in jack working, help would be appreciated.

Cheers.

---

### Post by Daelyn on 2007-11-08
> **bazzard said:**
> Hi

I'm using a Sony VAIO SZ3HP laptop under gusty 7.10

I have nearly got everything working apart from a couple of things.

I want to get the stamina/speed switch working which allows switching between the two different graphics modes available. There seems to be a solution to this here under the video heading: [http://ariel.vardi.free.fr/ariel//vaiosz.html](http://ariel.vardi.free.fr/ariel//vaiosz.html)

However, because I'm a n00b to linux, I don't know where to start to get the switch working using the explanation on that site. Would someone please break it down for me step by step for a n00b, It would be much appreciated.

Also, if anyone knows how to get the built-in mic and line-in jack working, help would be appreciated.

Cheers.

No offence, but, I would suggest you look around a little in HOW-TO's and familiarize yourself with the linux systems and the basic commands needed to edit configuration files etc.

This is not something a "green to linux" should do. It is a bit advanced stuff.

First tip: read some HOW-TO's and familiarize with the system.
Second: DO NOT USE THE XORGS provided on that site. They will not work out of the box.
Third: look at this link to get a very good functional switcher:
[http://ubuntuforums.org/showthread.php?p=2614800#post2614800](http://ubuntuforums.org/showthread.php?p=2614800#post2614800)

If you do not know what the commands, in the description/guide provided above, does, I encurage you to NOT attempt this. It could mess up your system alot.

---

### Post by bazzard on 2007-11-08
OK, thanks for the advice.

---

### Post by bazzard on 2007-12-01
I'd still like someone to explain to me how I can set up the speed/stamina switch please.

---

### Post by Daelyn on 2007-12-01
> **bazzard said:**
> I'd still like someone to explain to me how I can set up the speed/stamina switch please.

Read my post above and follow the instructions and you'll succeed.

---

### Post by steeef on 2008-01-04
The linked script worked great, but I've recently installed the Nvidia beta drivers (169.07, I believe), and they've changed enough that not all of the same libraries are where this particular script expects them to be. Is there a simple fix to get this working again?

---

### Post by steeef on 2008-03-23
After getting the script to work on a few different versions of the NVIDIA drivers, I figured it was worth posting my solution here. The only things that need changing with more recent drivers are the initial symlinks, which I've listed here (these are for version 169.12, but should be similar with future versions):

```

sudo ln -sf /etc/init.d/xorg_conf /etc/rc2.d/S12xorg_conf
sudo ln -sf /usr/lib/libGL.so.1 /usr/lib/libGL.so
sudo ln -sf /usr/lib/libGL.so.169.12 /usr/lib/libGL.so.1.nvidia
sudo ln -sf /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/xorg/modules/libglx.so.mesa
sudo ln -sf /usr/lib/xorg/modules/extensions/libglx.so.169.12 /usr/lib/xorg/modules/libglx.so.nvidia

```

You'll notice that I left out the line for /usr/lib/nvidia/libGL.so.1.2.xlibmesa, but this file doesn't seem to exist (nor does the nvidia directory), and leaving it out didn't prevent me from switching between the two cards successfully.

I hope this helps someone. I really like the ability to switch between the two cards seamlessly. Now if I can just figure out how to get the brightness controls working...

---

