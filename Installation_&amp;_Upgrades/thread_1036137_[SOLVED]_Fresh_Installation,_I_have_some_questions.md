---
title: "[SOLVED] Fresh Installation, I have some questions."
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by ricardo072 on 2009-01-10
Hi all,

I'm newbie in this forum, I'm from Guadalajara Mexico, I'm C/C++/Java Developer :P... I have a fresh installation of Ubuntu WorkStation x64 ( minor hw details: Intel core 2 Cuad, NVidia GeForce 8600GT video card, 8 Gb ram and motherboard gigabyte GA-EP35-DS3L ) I already installed the NVidia video driver ver 177 and the first updates were installed (more than 200)...

I have some questions:

1) I installed compiz-fusion (Settings Manager also), and the emerald theme manager, everything looks good. I would like to know if there is some way to install a real iMac LookAndFeel (if any), with some gattgets. I don't know how to install and configure a tool called "AWM".

2) My motherboard have a 7.1 sound channels output integrated, how can I configure the sound in ubuntu ?

3) How can I install Flash?, I can't use youtube right now, i.e.

Your help is very appreciated.
Thanks a lot.
Best regards.

---

### Post by blackened on 2009-01-10
> **ricardo072 said:**
> ...3) How can I install Flash?, I can't use youtube right now, i.e....

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by ricardo072 on 2009-01-10
> **blackened said:**
> ```
sudo apt-get install flashplugin-nonfree
```
ok thx

---

### Post by skern03 on 2009-01-10
> **ricardo072 said:**
> Hi all,

I'm newbie in this forum, I'm from Guadalajara Mexico, I'm C/C++/Java Developer :P... I have a fresh installation of Ubuntu WorkStation x64 ( minor hw details: Intel core 2 Cuad, NVidia GeForce 8600GT video card, 8 Gb ram and motherboard gigabyte GA-EP35-DS3L ) I already installed the NVidia video driver ver 177 and the first updates were installed (more than 200)...

I have some questions:

1) I installed compiz-fusion (Settings Manager also), and the emerald theme manager, everything looks good. I would like to know if there is some way to install a real iMac LookAndFeel (if any), with some gattgets. I don't know how to install and configure a tool called "AWM".

2) My motherboard have a 7.1 sound channels output integrated, how can I configure the sound in ubuntu ?

3) How can I install Flash?, I can't use youtube right now, i.e.

Your help is very appreciated.
Thanks a lot.
Best regards.

Not sure about the iMac question... From what I've seen on my daughter's new Mac Book, the closest I've seen to that look (with the shelf and gadgets at the bottom) is Kubuntu 8.10. My experience with it was poor; it was buggy at best.

As for configuring sound, at the top of the Multimedia and Video Forum are two stickies. You want to follow the instructions in the second, Comprehensive Sound Problem solutions Guide.

---

### Post by ricardo072 on 2009-01-10
> **blackened said:**
> ```
sudo apt-get install flashplugin-nonfree
```

I already did this, but youtube still telling me:
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player.

any suggestion ?
Thx

---

### Post by ricardo072 on 2009-01-10
> **skern03 said:**
> Not sure about the iMac question... From what I've seen on my daughter's new Mac Book, the closest I've seen to that look (with the shelf and gadgets at the bottom) is Kubuntu 8.10. My experience with it was poor; it was buggy at best.

As for configuring sound, at the top of the Multimedia and Video Forum are two stickies. You want to follow the instructions in the second, Comprehensive Sound Problem solutions Guide.

Thanks, I will check Multimedia and Video forums.

---

### Post by avtolle on 2009-01-10
You might also want to check out the Apple Users subforum for further information and potential assistance.

---

### Post by yobird42 on 2009-01-10
if you're looking for a mac-like theme check out gnome-look.com, there are tons of mac themes for emerald. 

To install awn window manager which is the dock, go to synaptic and search for "awn". 

I'm not sure what you mean by gadgets but installing the screenlet manager might help with that. search for "screenlets" in synaptic. 

A search for "flash player" in synaptic could help as well if you're unable to install of the adobe website.

---

### Post by ricardo072 on 2009-01-10
> **yobird42 said:**
> if you're looking for a mac-like theme check out gnome-look.com, there are tons of mac themes for emerald. 

To install awn window manager which is the dock, go to synaptic and search for "awn". 

I'm not sure what you mean by gadgets but installing the screenlet manager might help with that. search for "screenlets" in synaptic.

That's right, I meant "screenlets", thanks a lot!

---

### Post by skern03 on 2009-01-10
> **ricardo072 said:**
> I already did this, but youtube still telling me:
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player.

any suggestion ?
Thx

Also at top of the Multimedia & Video forum is a sticky, Comprehensive Mutli-media and Video how-to. It cured a lot of video issues for me, including the weird javascript not enabled message. For me, it was enabled, but I still got the message. 

After I upgraded to Ubuntu 8.10, and followed the instructions in the sticky mentioned above, my video problems went away for the most part.

---

### Post by skern03 on 2009-01-10
> **yobird42 said:**
>  I'm not sure what you mean by gadgets 

OP & Yobird: My kid's Macbook refers to them as "widgets." Vista <urp> has gadgets as does Google. Anyway, they're small apps like games.

---

### Post by blackened on 2009-01-11
> **skern03 said:**
> OP & Yobird: My kid's Macbook refers to them as "widgets." Vista <urp> has gadgets as does Google. Anyway, they're small apps like games.

```
sudo apt-get install gdesklets
```
or
```
sudo apt-get install adesklets
```
or
```
sudo apt-get install screenlets
```

---

### Post by skern03 on 2009-01-11
> **blackened said:**
> ```
sudo apt-get install screenlets
```

Very cool! Thanks a million.

---

### Post by ricardo072 on 2009-01-11
I want to thank to all of you for your help...

Once I execute "sudo apt-get install screenlets", how can I configure it ?
where I can get the most common screenlets like a "Clock" or CPU Monitor ?
I need a "How-to Use"....

---

### Post by skern03 on 2009-01-11
> **ricardo072 said:**
> I want to thank to all of you for your help...

Once I execute "sudo apt-get install screenlets", how can I configure it ?
where I can get the most common screenlets like a "Clock" or CPU Monitor ?
I need a "How-to Use"....

Go to Applications, Accessories, Screenlet Manager. You'll get a window with screenlets, including clock, CPU meter, weather, and many more. Check out Sidebar - it lets you dock the screenlets.

If you want them back when you login, then from the Screenlet Manager, under Options, select Running Screenlets. Click each applet in succession, and select Auto start on login.

It's a good idea for each of the screenlets to have BOTH keep above and keep below unchecked.

---

### Post by ricardo072 on 2009-01-11
:guitar:

it seems to work,
Thanks!

---

### Post by skern03 on 2009-01-11
> **ricardo072 said:**
> :guitar:

it seems to work,
Thanks!

Great! Don't forget to mark the thread solved so others can benefit. You can do that by clicking Thread Tools, Mark as Solved.

---

### Post by ricardo072 on 2009-01-12
> **skern03 said:**
> Great! Don't forget to mark the thread solved so others can benefit. You can do that by clicking Thread Tools, Mark as Solved.

So sorry, inndeed the "Thread tools" is displaying only one option... is "Show Printable Version" What can I do ?
-------------------------------------

Never mind... i've logged in..

---

