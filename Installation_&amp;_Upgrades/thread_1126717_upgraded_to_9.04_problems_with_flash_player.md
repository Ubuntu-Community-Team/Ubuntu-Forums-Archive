---
title: "upgraded to 9.04 problems with flash player"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by redb on 2009-04-15
Flash has stopped working in both firefox and Opera.  Cannot utube or hulu.  I have been searching for ways to solve this issue for a couple of days and my patience is wearing thin.  Is anyone else having problems?  Is there a work around?

---

### Post by spiderbatdad on 2009-04-15
remove flashplugin-nonfree install adobe-flashplugin via synaptic package manager.

---

### Post by redb on 2009-04-15
I tried to uninstall the non-free...

sudo apt-get remove flashplugin-nonfree 

Reading package lists... Done

Building dependency tree 
      
Reading state information... Done

Package flashplugin-nonfree is not installed, so not removed

0 upgraded, 0 newly installed, 0 to remove and 96 not upgraded.

Before this I had installed adobe-flashplugin via synaptic package manager. Still does not work.  I have tried to install the .deb package from adobe and when that did not work I tried to install it .tar.  No luck.  This is my wifes laptop and it seems to have a hex on it.

[edit] I just installed epiphany web browser and still get the blank screen on hulu and youtube.  
I don't know what the problem is, I have no problems on my hp with x600 graphics card (besides the buggy accelerated graphics), but I have had hangups on this nvidia nVidia Corporation MCP78S [GeForce 8200]

---

### Post by gus.ke on 2009-04-16
I had the same problem, so I deleted flash player and tried to install adobe's, but there doesn't seem to be a 64-bit version.

---

### Post by redb on 2009-04-16
I solved the problem by downloading the image and making a clean install.  Everything seems to be working fine now.  Thanks.

---

### Post by brianpatrick on 2009-04-18
Hi,
spiderbatdad said to:
remove flashplugin-nonfree install adobe-flashplugin via synaptic package manager.
There is no adobe-flashplugin in the default Synaptec repos. Which repo did you find it in?

The closest thing I could find is flashplugin-installer. It had no sound. Mp3s play with Rythmbox and MPG files play fine with VLC. Neither youtube nor bbc flash video had any sound. 

Then, I installed the 64 bit flash player, libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz from Adobe. Still no sound. 

Based on how I hacked it into Suse 11.1, I installed the libflashplayer.so module in:
-rwxr-xr-x 1 root   root    9543400 2009-04-18 16:08 /usr/lib/browser-plugins/libflashplayer.so
-rwxr-xr-x 1 root   root    9543400 2009-04-18 17:33 /usr/lib/firefox-addons/plugins/libflashplayer.so
-rwxr-xr-x 1 root   root    9543400 2009-04-18 16:07 /usr/lib/firefox/libflashplayer.so

I think it might be a problem between oss and alsa sound settings. How do you tell Firefox to use one or the other. VLC had a menu option to select one or the other. They just happened to work with OSS. 

Thank you,
    BrianP

---

### Post by Vjetar on 2009-04-20
Similar problems here, flash works in FFox but youtube comes with sound and no video in Opera.

First I tried to purge flashplugin-nonfree an reinstall flashplugin-installer. No luck.

Then i did : ```
sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/opera/plugins/
```

restart Opera and youtube works fine.

---

### Post by MuddBuddha on 2009-04-20
I had the same problem and tried several forum fixes to no avail.  lastly, I just installed the other two flash(.flv) handlers from Add/Remove and flash videos began working.

Worth a shot.

---

### Post by jdorenbush on 2009-04-23
> **spiderbatdad said:**
> remove flashplugin-nonfree install adobe-flashplugin via synaptic package manager.

I too am having problems.

I don't even see the 'adobe-flashplugin' in Synaptic.

When Firefox prompts that there is missing plugins I try to run the install of Adobe Flash Player, but it says 'flashplugin-nonfree' is already installed. After checking Synaptic, I can see that it is _not_ installed.

I've uninstalled everything Flash-related to the best of my knowledge and tried to reinstall.. still no luck.

UPDATE: I just tried installing 'swfdec' and using that. That installed just fine, however it isn't work out so great. For example, in Google Analytics the flash content just continues to try and load.

---

### Post by Vjetar on 2009-04-23
@jdorenbush do you see flashplugin-installer installed in synaptic ?

---

### Post by infamousnation on 2009-04-23
Looks like there is no more adobe-flashpugin which is a real shame becasue it was the best solution for playing flash videos on my desktop.  I never had any problems with it like I had with all the other packages I tried.  I hate to install the .deb off adobe's web site because I prefer to only install things through repos but I may have to try that.  Getting 9.04 working has been more difficult that past releases, at least for me.

edit
I installed the .deb from adobe's web site and it seems to be working perfect.  I can confirm flashplugin-installer did not work for me.

---

### Post by jdorenbush on 2009-04-23
> **Vjetar said:**
> @jdorenbush do you see flashplugin-installer installed in synaptic ?

Nope :(

---

### Post by miig on 2009-04-24
I had the same issue after a dist upgrade ( 8.10 -> 9.04)
And Firefox was telling me that the flash player wasn't installed, where synaptic was telling the opposite.

What worked for me was :

uninstalling flashplugin
```
sudo apt-get remove flashplugin-installer
```


then reinstalling it
```
sudo apt-get install flashplugin-installer
```

---

### Post by Vjetar on 2009-04-24
> **jdorenbush said:**
> Nope :(

So install it. It will download adobe flash plugin from Adobe site.

@infamousnation: flashplugin-installer wil download and install flash plugin from Adobe site. I works fine in Firefox, but Opera need tweak i mentioned before.

---

### Post by kramthegram on 2009-04-24
I'm reporting the same problem. No flash in 9.04 on a core 2 duo. Can't install anything from adobe as it's 32 bit and I've tried all the package suggestions so far. Any additional help would be appreciated, thanks.

---

### Post by nealaustin on 2009-04-24
> **miig said:**
> I had the same issue after a dist upgrade ( 8.10 -> 9.04)
And Firefox was telling me that the flash player wasn't installed, where synaptic was telling the opposite.

What worked for me was :

uninstalling flashplugin
```
sudo apt-get remove flashplugin-installer
```


then reinstalling it
```
sudo apt-get install flashplugin-installer
```

I also had the same problem but had tried in my frustration to install the ubuntu version. What fixed mine was: the above mentioned [code]uninsta... then I went into the synaptic package manager andtook out the Ubuntu version with it's extra pack. Rebooted and then the above [code]insta... . After a new Reboot it works perfectly. I find that one of the best tests for functionality is _rtl-now.rtl.de _ . If Flash works there it will work anywhere. :D

---

### Post by nealaustin on 2009-04-24
One other thing. I had the packaged file from Adobe sitting on my desktop. I'm not sure if Apt had used it or not. The package name is: libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz It appears to be an Alpha version.

---

### Post by jdorenbush on 2009-04-24
> **miig said:**
> I had the same issue after a dist upgrade ( 8.10 -> 9.04)
And Firefox was telling me that the flash player wasn't installed, where synaptic was telling the opposite.

What worked for me was :

uninstalling flashplugin
```
sudo apt-get remove flashplugin-installer
```


then reinstalling it
```
sudo apt-get install flashplugin-installer
```

I did that. Install went smoothly. Video seems to be playing fine.

Thanks.

---

### Post by Ozdemon on 2009-04-25
> **miig said:**
> I had the same issue after a dist upgrade ( 8.10 -> 9.04)
And Firefox was telling me that the flash player wasn't installed, where synaptic was telling the opposite.

What worked for me was :

uninstalling flashplugin
```
sudo apt-get remove flashplugin-installer
```


then reinstalling it
```
sudo apt-get install flashplugin-installer
```
Well, I don't understand how, but this instantly solved my problem of no video in Firefox.

---

### Post by _sleeper on 2009-04-25
i removed flushplugin-nonfree and installed adobe-flashplugin and it worked instantly.

---

### Post by Bill_in_SD on 2009-04-25
It seems like if you have any flash player installed before the upgrade then when adobe-flash is installed things like hulu.com stop working.

I uninstalled all flash players except adobe and it worked.  If you are using synaptic, make sure you check to see if gnash is intalled - it did not show up when my search string was 'flash'.

So, my last step was simply removing gnash and now everything works in Firefox.

Good luck-

---

### Post by jdorenbush on 2009-04-25
Strange... now Flash is messed up again. All I get is a white box where the Flash content should be.

---

### Post by neubert500 on 2009-04-26
Removing GNASH fixed my firefox problem also. THANKS!:P

---

### Post by freifliege on 2009-04-26
removing swfdec-mozilla and installing the player from the adobe website solved the problem for me.

---

### Post by mevdschee on 2009-04-29
This worked for me:

sudo dpkg --purge flashplugin-nonfree
sudo dpkg --purge flashplugin-installer
sudo apt-get install flashplugin-installer

---

### Post by manifoldronin on 2009-05-02
> **Vjetar said:**
> 

```
sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/opera/plugins/
```

restart Opera and youtube works fine.

Thanks. That worked for me, too, with a minor difference:
```
sudo ln -s /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/opera/plugins/
```

---

