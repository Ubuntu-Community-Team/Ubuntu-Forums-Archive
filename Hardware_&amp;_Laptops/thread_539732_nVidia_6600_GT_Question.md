---
title: "nVidia 6600 GT Question"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by oo-boon-too on 2007-08-31
Ok, So I was looking around the forum to see if there were any pre-installation tasks needed to install the driver for my nVidia 6600 GT card (Similar to the added section in xorg.conf for Ati). But what I found were ppl talking about it having problems.

I am currently installing Ubuntu 7.04 (I'm on the live CD), and I'm wondering if everything will work out fine if i have Ubuntu install the driver itself (Restricted Driver Manager option), or if I need to make any special actions. So far the card seems to be detected just fine, but only lacks the acceleration.

Any tips will be appreciated!

---

### Post by rsambuca on 2007-08-31
I have a 6600GT and haven't had a problem.  It has been a while, but I am pretty sure I just used the Restricted Drivers Manager and let it do its thing.

---

### Post by oo-boon-too on 2007-08-31
Alright cool, thanks for the reply.

Wish me luck;P

---

### Post by oo-boon-too on 2007-08-31
Hmm...well I let Ubuntu install it on its own and now when i log in it hangs. As it was installing, i clicked the little button that shows the terminal, and noticed that it was installing a driver version 96-- something, and i believe that I need version 97-- something. Anyone know how i fix it from here?

---

### Post by rsambuca on 2007-08-31
Ok, can you boot to a recovery console?  If so, just change the driver in your xorg to nv from nvidia.

To edit this via the console, enter```
sudo nano /etc/X11/xorg.conf
```Scroll down to where you see driver "nvidia" and change it to "nv".  Save, and restart X.  Then we can get the driver installed properly.

---

### Post by oo-boon-too on 2007-08-31
Alright cool thanks, I'm doing that now:)

---

### Post by oo-boon-too on 2007-08-31
Alight i am now using the nv driver.

What should I do now?

I saw something that said that I should type:

sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig --no-composite

Will that be all i need or is that just a piece an a huge puzzle?

---

### Post by rsambuca on 2007-08-31
You really don't "need" the glx-new driver, but I assume it will still work.  On my ubuntu setup I am just using the default nvidia-glx .9631 driver.

I think in hindsight, that I probably didn't use the Restricted Drivers Manager:)

Sorry about that.  Try```
sudo apt-get install linux-restricted-modules
sudo apt-get install nvidia-glx
```Then change the driver back in your xorg to nvidia and restart X.

---

### Post by oo-boon-too on 2007-08-31
Returned:
```
E: Couldn't find package linux-restricted-modules
```
When typing the first line, I ignored it and typed the next line, and will continue to edit my xorg.conf. Will that be ok?


Section should look like this?
```
Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection
```

---

### Post by rsambuca on 2007-08-31
You definitely need the restricted modules for the nvidia driver to work.  Can you go to System -> Administration - Software Sources?  Make sure that you have the "Proprietary drivers for devices (restricted)" checked.  Then do a sudo apt-get update, and then try to install it again.

---

### Post by Club17 on 2007-08-31
Me happened similar trouble when upgrading nvidia driver of 6200 TurboCache. Xserver don't recognize the new driver. I'm new in Linux, so, this command will fix this bug?

Thx!

Edit: Forget to say: I'm using Ubuntu 7.04, 'updated' with Ubuntu Studio.

---

### Post by oo-boon-too on 2007-08-31
Hmm, this is strange. I checked that it was checked (Seemed to be checked by default), then typed this:
```
katsu@katsu-desktop:~$ sudo apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release             
Hit http://us.archive.ubuntu.com feisty/main Packages               
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://security.ubuntu.com feisty-security Release
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
katsu@katsu-desktop:~$ sudo apt-get install linux-restricted-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules
katsu@katsu-desktop:~$ 

```


And here is what my sources looks like:
[http://i22.photobucket.com/albums/b346/katsuakimoto/snapshot1-1.png](http://i22.photobucket.com/albums/b346/katsuakimoto/snapshot1-1.png)

---

### Post by rsambuca on 2007-08-31
Maybe you need the version numbers or something.  In any event, just use Synaptic Package Manager to install it.  It shows up there (at least on my rig).

---

### Post by oo-boon-too on 2007-08-31
Lol it seems that i already had them, and maybe that is why it could not find them:
[http://i22.photobucket.com/albums/b346/katsuakimoto/snapshot2-1.png](http://i22.photobucket.com/albums/b346/katsuakimoto/snapshot2-1.png)

I dont need the x86_64 ones since im running 32bit right?

So I'm all set to restart?

---

### Post by rsambuca on 2007-08-31
What does it say when you type ```
uname -a
```

---

### Post by oo-boon-too on 2007-08-31
It tells me "Linux katsu-desktop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux" When i type that.

I encountered a problem:\
Sorry this is taking so long:(
When i restarted it gave me an X server error and the output said that there was an API error and that the kernel was in 9755 version of the driver but x-server  was in version 9631.

Sorry again for being so hard to work with >.<

---

### Post by rsambuca on 2007-08-31
You may as well wimp out and use envy!

[[COLOR="Red"]Link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=432056")

---

### Post by oo-boon-too on 2007-09-01
lol i just used that a few hours ago and it failed as well. It installed it and all, but after about 5 minutes my input of any kind (Keyboard, mouse) freeze and my computer goes into an all out lag-fest.

---

### Post by oo-boon-too on 2007-09-01
Can anyone help me, I just bought this card and I need to know if I should just get my money back because it won't work (Although for other people it seems to be), or if I can get it to work.

I'd rather get it to work;)

So far I can install the driver just fine, But i freeze after a minute or so.
7.04 Feisty
e-Ge-Force 6600 GT (128MB)
Logitech Keyboard
Logitech Mouse
Using "Envy" To install-------
Using Restricted Manager--|     All three ways generate this problem, So obviously there is something on my end wrong.
Using Automatix--------------

---

