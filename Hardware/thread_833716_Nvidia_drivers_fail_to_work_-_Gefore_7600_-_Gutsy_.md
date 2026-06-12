---
title: "Nvidia drivers fail to work - Gefore 7600 - Gutsy Gibbon"
date: 2008-06-18
forum: Hardware
---

### Post by Fireman_DJ on 2008-06-18
This problem is one pain in the ****. I've tried just about everything I've found on the net with no luck.

My Ubuntu history goes like this. I started with 7.04 and a Geforce 6600. I updated to 7.10. I then installed a new vid card (the current Geforce 7600) which only needed a slight config change.
This all worked fine and Ubuntu was running my biggest game, Enemy Territory (plus others like AA 2.6 etc).
I upgraded to 8.04 and thats when I lost my video drivers.

From there I tried a lot of things. I did a clean install of 8.04.

I've since done a clean install of 7.04 and upgraded it to 7.10, the last install I had 3D working in. However, I'm not able to get the Nvidia drivers working.

I use the restricted driver manager to install the nvidia drivers from a clean install. I restart and am given a low resolution mode warning.
I use Envy, same thing. I install the Nvdia drivers by hand, same thing.

The best I've been able to achive is having the Nvidia driver installed, started up with the Nvidia bootscreen sreen showing. Ubuntu loaded normally and at full res. But I was unable to use any 3D functions. And I don't even know how I managed to get that installed.

Help, please. I may sound desperate, but thats because I am.
I've not been able to play ET for about 2 months (ie, since a few days after 8.04 was released). I've tried to fix it, given up and then tried again and so on during this time. I'm pretty good with computers but am still learning the in's and out's of linux.

Cheers, DJ.
```
dj@main:~$ lspci |grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GT (rev a2)
dj@main:~$ uname -a
Linux main 2.6.22-14-386 #1 Tue Feb 12 07:12:19 UTC 2008 i686 GNU/Linux

```

---

### Post by hariprs on 2008-06-18
Hi,

1. Download latest driver from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

2. Press Alt+F2 after login to Ubuntu

3. Again login to CLI

4. Terminate GDM
$ sudo killall gdm

5. Run the downloaded driver
$ sudo sh <Driver name>

6. Restart the system

It should work now...

---

### Post by Fireman_DJ on 2008-06-18
> **hariprs said:**
> Hi,

1. Download latest driver from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

2. Press Alt+F2 after login to Ubuntu

3. Again login to CLI

4. Terminate GDM
$ sudo killall gdm

5. Run the downloaded driver
$ sudo sh <Driver name>

6. Restart the system

It should work now...

Is this the same thing as you just said? Because thats what I meant when I said I installed the Nvidia drivers by hand.

```
Alt+F1
<login>
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-<version>.run
sudo reboot
```

This was done after I had uninstalled the drivers from the previous failed attempts.

I also redownloaded the drivers from that page you gave about a week ago with the same results.

I've tried editing my xorg.conf by hand to add little snippets that have helped others (like Option "AllowGLXWithComposite" "True" and more), configuring it with "sudo dpkg-reconfigure xserver-xorg" and even deleting it (after backing it up of course).

I've tried just about every thing I've found on these forums. Installing and running the -386 kernel rather then the generic (which was the default install), every different step-by-step install guide.
 I've even tried turning the PC on it's side, holding a empty cup and standing on one foot while booting the PC up to see it it made a difference (well, not really, but you get the idea).

---

