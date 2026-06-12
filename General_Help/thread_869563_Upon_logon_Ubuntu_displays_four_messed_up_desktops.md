---
title: "Upon logon Ubuntu displays four messed up desktops. (pic included)"
date: 2008-07-24
forum: General Help
---

### Post by ESC201 on 2008-07-24
Hi all, I recently upgraded my entire system. (Motherboard, processor, ram, etc) And when I boot up Ubuntu, it displays everything perfectly, including the logon screen. However, once I log on my desktop looks like the photo below. As you can imagine, this makes my box pretty much unusable. I assume this is because of my new motherboard where I am using the integrated graphics card and I am using the same monitor as I did before I upgraded everything and I never had an issue there.
My new motherboard is an Intel DG35EC [( http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3797456&CatId=3691 )]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3797456&CatId=3691")
and my monitor is a Samsung 906BW.  
I've spent hours on Google to no avail. Any help/knowledge/a point in the right direction would be awesome. Thanks! :)

This is what my desktop looks like...
[IMG]http://img.photobucket.com/albums/v326/skrtyuin578/DSC02611Small.jpg[/IMG]

---

### Post by tamoneya on 2008-07-24
is there any difference if you try switching between the DVI and VGA or VGA and DVI.

PS: I just ordered this board.  I was thinking it would be well supported because its made by intel.  I hope im not wrong.

---

### Post by ESC201 on 2008-07-25
I was using VGA because I don't have another DVI cord lying around however, I took one my other computer and I now see a 'normal' desktop but Ubuntu still won't let me set my monitor to the correct resolution. So I still assume that I'm in need of a driver.

---

### Post by tom66 on 2008-07-25
Does it boot well from a live CD? If so, it might need a reinstall/configuration.

---

### Post by tamoneya on 2008-07-25
not exactly the same error but i think if you follow the same line of reasoning here you may get some helpful results: [http://ubuntuforums.org/showthread.php?t=669386](http://ubuntuforums.org/showthread.php?t=669386)

It uses the same graphics chipset as your motherboard: Intel GMA X3500.

---

### Post by ESC201 on 2008-07-26
I booted up from the live cd and it detected my display properly so I copied the xorg.conf file to a flash drive and then booted up again from my hard drive and Ubuntu detected my monitor perfectly and I now have the correct resolution. :) How that happened, I have no idea. The only thing that still isn't correct is that I can not enable the pretty desktop effects which is somewhat annoying to me. Any ideas with that issue?

---

### Post by MatthewPlanchard on 2008-07-26
As far as enabling compiz goes, have you tried going into Menu-System-Hardware Drivers and making sure all the drivers (restricted included) are checked?

---

### Post by ESC201 on 2008-07-26
It's probably bad if I don't have a Hardware Drivers menu, huh?

[IMG]http://img.photobucket.com/albums/v326/skrtyuin578/Screenshot.png[/IMG]

or I'm blind.

---

### Post by rossjman1 on 2008-07-26
you can enable the Hardware drivers menu by going to the Menu Editor (System > Prefs > Main Menu) and going down to the administration menu and making sure that hardware drivers is checked.

---

### Post by ESC201 on 2008-07-26
> **rossjman1 said:**
> you can enable the Hardware drivers menu by going to the Menu Editor (System > Prefs > Main Menu) and going down to the administration menu and making sure that hardware drivers is checked.

When I try to check hardware drivers it immediately unchecks itself.

---

### Post by rossjman1 on 2008-07-26
> **ESC201 said:**
> When I try to check hardware drivers it immediately unchecks itself.
How odd. Try typing this in the terminal and report any errors.
```

sudo /usr/bin/jockey-gtk

```

---

### Post by ESC201 on 2008-07-26
The hardware drivers window opened however there is nothing listed in there and it says "No proprietary drivers are in use on this system."

---

### Post by hrod beraht on 2008-07-29
> **tamoneya said:**
> PS: I just ordered this board.  I was thinking it would be well supported because its made by intel.  I hope im not wrong.

Nope, you're not wrong. Intel rules with Linux. I have the same motherboard (DG35EC) and Ubuntu installed on it like a dream. From nothing to a fully functioning system in like 20 minutes. It even correctly set my 1920x1200 monitor resolution.

> **ESC201 said:**
> The only thing that still isn't correct is that I can not enable the pretty desktop effects which is somewhat annoying to me. Any ideas with that issue?

So *None* is the only thing you can check on the System --> Preferences --> Appearance --> Visual Effects tab?

Bob

---

### Post by ESC201 on 2008-08-03
> 

So *None* is the only thing you can check on the System --> Preferences --> Appearance --> Visual Effects tab?

Bob

Yes that's correct however a few days ago I was having some pretty bad issues with grub so I made a backup of my personal data and reinstalled Ubuntu. From there I was able to enable desktop effects. Go figure.

Thanks everyone for all your help. :)

---

