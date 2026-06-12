---
title: "Nvidia GeForce 410M driver for Ubuntu 10.04 on Sony Vaio VPCEH25EN"
date: 2012-01-18
forum: Hardware
---

### Post by akhil520c on 2012-01-18
Hi,

I purchased this laptop 2 days ago, it has the Nvidia GeForce 410M GPU. After I installed Ubuntu and all the updates, its not detected this graphics card, so my screen resolution is stuck at 800X600, and I'm not able to change the screen brightness using the function keys or under System -> Power Management. Could anyone provide me a solution for both these issues? Even System -> Administration -> Hardware Drivers gives me the message that there were no proprietary drivers found for my system.  I installed the Nvidia closed-source driver from the Nvidia site, but I was not happy with the display quality. So, I reformatted and reinstalled Ubuntu. Would any open-source driver work? I prefer not to install closed-source drivers, because it complicates things, and I'm not the geeky type. I'd rather prefer solutions from Ubuntu, that are simple to perform, and that just work. 

Thanks,
akhil520c

---

### Post by jerrrys on 2012-01-20
I do not run this card, but you may find a solution for video driver here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Nvidia+GeForce+410&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Nvidia+GeForce+410&sa=Search&cof=FORID:9)

---

### Post by Lekensteyn on 2012-01-21
The GT 410M is a NVIDIA card with Optimus technology. To get those cards to work, see [http://askubuntu.com/a/36936/6969](http://askubuntu.com/a/36936/6969)

---

### Post by akhil520c on 2012-01-23
Thanks for the replies, jerrrys and Lekensteyn.

I'll look at my options, considering the information you have made available to me :-)

Thanks again,
akhil520c

---

### Post by akhil520c on 2012-01-25
Lekensteyn: 

Before I go ahead with any of this, I had one simple question:

I'm not really keen, as of now, to use the Nvidia card on this laptop, at all, firstly, because I don't need the extra graphics performance, and secondly, because I want the best battery back-up I can get.

As you had mentioned on askubuntu: 
> @JorgeCastro Bumblebee is only necessary  if you want to use the nvidia card. If you don't install the nvidia  driver, the Intel card will function fine. – [Lekensteyn]("http://askubuntu.com/users/6969/lekensteyn") Oct 22 '11 at 15:58

I'm now doing a fresh install of Ubuntu 10.04.01 LTS. Could you please guide me on how to proceed, so that I can just get the integrated Intel graphics to work, with native resolution ( 1366X768 ), and how I can permanently disable the Nvidia GPU (I checked in the BIOS, there's no such option here). Because, the last time I installed 10.04, it apparently didn't even detect the integrated Intel graphics, as I didn't get the native resolution, only 800X600. 

Thanks,
akhil520c

Thanks,
akhil520c

---

### Post by akhil520c on 2012-01-25
Hi,

I did a fresh install of 10.04, and I get the following output for the lspci command:

```
lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Device 1055 (rev a1)
```Does this mean that the integrated Intel graphics have been disabled by default on my system? Is there any way I can activate it back? (there's no setting for it in the BIOS). If not, does this mean that I'm forced to use the nVidia controller, whether I like it or not? If this is the case, am I then a good candidate to install Bumblebee? 

Thanks,
akhil520c

---

### Post by akhil520c on 2012-01-26
Hi,

Just an update:

I installed bumblebee as per the instructions on [http://askubuntu.com/a/36936/6969](http://askubuntu.com/a/36936/6969), but after a restart, didn't find any change, as the screen resolution was still 800X600, etc, and when I ran the "optirun" command, I got the error "The Bumblebee daemon has not been started yet or the socket path..." On running "bumblebeed" (bumblebee daemon?), I got the output:

[ERROR] No Optimus system detected, quitting.

So apparently, I don't have an Optimus system in the first place?

So now, I'm gonna go ahead and uninstall bumblebee.

akhil520c

---

### Post by Lekensteyn on 2012-02-11
> **akhil520c said:**
> Lekensteyn: 

Before I go ahead with any of this, I had one simple question:

I'm not really keen, as of now, to use the Nvidia card on this laptop, at all, firstly, because I don't need the extra graphics performance, and secondly, because I want the best battery back-up I can get.

As you had mentioned on askubuntu: 
I'm now doing a fresh install of Ubuntu 10.04.01 LTS. Could you please guide me on how to proceed, so that I can just get the integrated Intel graphics to work, with native resolution ( 1366X768 ), and how I can permanently disable the Nvidia GPU (I checked in the BIOS, there's no such option here). Because, the last time I installed 10.04, it apparently didn't even detect the integrated Intel graphics, as I didn't get the native resolution, only 800X600. 

Thanks,
akhil520c

Thanks,
akhil520c
Even if you do not need to use the nvidia card, Bumblebee still has added advantages: it disabled the nvidia card to save power. It looks like the Optimus settings are disabled (in BIOS?)

Since you've uninstalled Bumblebee, please run the next commands to make the system autodecide which GL libraries to use.

```

for arch in x86_64-linux-gnu i386-linux-gnu; do
    update-alternatives --force --auto ${arch}_gl_conf 2>/dev/null
done

# versions before Oneiric without multiarch
update-alternatives --force --auto gl_conf 2>/dev/null

```
Check your BIOS for an Discrete/Optimus/Integrated mode. If possible, report your machine at [https://bugs.launchpad.net/lpbugreporter/+bug/752542](https://bugs.launchpad.net/lpbugreporter/+bug/752542)

---

### Post by coffeecat on 2012-02-11
> **Lekensteyn said:**
> The GT 410M is a NVIDIA card with Optimus technology. To get those cards to work, see [http://askubuntu.com/a/36936/6969](http://askubuntu.com/a/36936/6969)

If I read that link correctly, it refers to Optimus variants of the 410M card, which would imply that there are non-Optimus variants.

> **akhil520c said:**
> I got the output:

[ERROR] No Optimus system detected, quitting.

So apparently, I don't have an Optimus system in the first place?

@akhil520c, I have a GeForce 410M in my Vaio VPCEJ and I do not have Optimus. I can get the native screen resolution with the proprietary nvidia driver in both Oneiric/11.10 and Precise/12.04. I very much doubt that you will be able to solve this with 10.04. The GeForce410M is too new and the xserver version in 10.04 is too old.

I have also found a fix for the screen brightness Fn key problem which works just fine in 12.04, but I haven't tried this in 11.10. I don't suggest that you install 12.04 just yet as it's still in alpha (unless you are an experienced user), but you will certainly be able to get the proper screen resolution in 11.10 and the fix for the Fn keys may work as well. If you want more details or help with this, post back.

---

### Post by Starks on 2012-02-11
Looks like you don't have Optimus

---

