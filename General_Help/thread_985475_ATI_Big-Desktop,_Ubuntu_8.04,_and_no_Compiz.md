---
title: "ATI Big-Desktop, Ubuntu 8.04, and no Compiz"
date: 2008-11-17
forum: General Help
---

### Post by Rohan Kapoor on 2008-11-17
Hello,

I have a Compaq Presario v2000 computer running Ubuntu 8.04. In additional I have an external 17" CRT monitor. I have followed the instructions here: [http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804](http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804), for the ATI Radeon Xpress 200M graphics card in my notebook. My problem is this: with two monitors hooked up Compiz just refuses to run saying:

```
rohan@Rohan-Laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5955 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x768) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 

```

I really love Compiz and would be very happy if this could be run. I would prefer not to upgrade to 8.10 but will if I have too. 

Thanks to this great community for their ongoing help and support!

Also is the attached of the Compiz Check Tool:```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) y

 Your resolution is 2560x768 but the maximum 3D texture size that your
 graphics card is capable of is 2048x2048. Thus Compiz will not be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again). 
```

---

### Post by Rohan Kapoor on 2008-11-18
Bump. Guys I really need help with Compiz. Can someone offer any advice?

---

### Post by loomsen on 2008-11-18
[color=red]
ADVICE:
> 
Your resolution is 2560x768 but the maximum 3D texture size that your
 graphics card is capable of is 2048x2048.

[/color]

2048/2=1024

So obviously you will have to set your screens up with a resolution of 1024x768...

---

### Post by Rohan Kapoor on 2008-11-18
But that switches back to clone displays!

---

### Post by loomsen on 2008-11-18
Well then most likely this is what's actually configured in your xorg.conf, if anything at all... Your X server will look like you set it up in your xorg.

---

### Post by Rohan Kapoor on 2008-11-18
> **loomsen said:**
> Well then most likely this is what's actually configured in your xorg.conf, if anything at all... Your X server will look like you set it up in your xorg.
So there is no way to have this Big Desktop and Compiz?

---

### Post by vandorjw on 2008-11-18
> Your resolution is 2560x768 but the maximum 3D texture size that your
 graphics card is capable of is 2048x2048.

Buy a new Graphics Card?

nVidia 9800 GTX is capable of; Max Resolution (external) 2560 x 1600

Cheers - CC7

I am not sure if you can increase your max resolution using software only...

---

### Post by Rohan Kapoor on 2008-11-18
You may have noticed this is a laptop. No videocard replacement options!

---

### Post by nanotube on 2008-11-24
hey
check out this launchpad thread, here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519)

it seems that if it really is a hardware limitation, you might also make it work by changing colordepth to 16 from 24, but keeping your resolution the same.

i am on a laptop with ati radeon 9000 myself, using ubuntu intrepid, running with two screens combined resolution of 3520 x 1200, and running into the "maximum 3D texture size (2048): Failed" problem as well. 

i'll try changing the depth to 16, and see if that enables compiz for me.

(and by the way, if i run compiz with skip_checks, it does start, but the right half of the screen is all garbled, so in my case it does look like a hardware, or at least video driver, limitation).

---

### Post by Rohan Kapoor on 2009-10-07
Hate to bump old threads but was just wondering if anyone was able to get this working on 9.04?

---

