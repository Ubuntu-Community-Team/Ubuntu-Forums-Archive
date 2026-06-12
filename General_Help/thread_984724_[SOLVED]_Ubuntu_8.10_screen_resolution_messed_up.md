---
title: "[SOLVED] Ubuntu 8.10 screen resolution messed up"
date: 2008-11-16
forum: General Help
---

### Post by samrohde on 2008-11-16
I booted my computer and my screen resolution is messed up throughout the entire computer including GRUB and the entire GUI. It took off half a task bar thickness(12 pixels) all the way around. I tried going into System > Preferences > Screen Resolution and I tried every resolution but all of them were the same. I am using an Olevia 232v 32" wide screen TV/Monitor connecting the computer to the TV with a VGA cable. My computer's Video/Graphics card is an Intel Graphics Media Accelerator 950, the computer processor is an Intel Celeron Processor 420. I don't know if the CPU is a 32 or a 64 bit, but I am running the 32 bit Ubuntu version. I tried booting into recovery mode and I went to xfix but it didn't fix the problem. How can I fix this problem? I have never had this problem before, until I upgraded to Ubuntu 8.10 from 8.04. I'm new to Ubuntu so be specific. Thanks.:)

---

### Post by Marcus Derekus on 2008-11-16
Open /etc/X11/xorg.conf as root like so:

```

sudo gedit /etc/X11/xorg.conf

```

Then go to the **Section "screen"** line and add the following code:

```

Section "Screen"
	Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        SubSection "Display"
                **Modes      "1020x758"**
        EndSubSection
EndSection

```

If SubSections does not exist create it and add the code exactly as it is
Dont forget to EndSubSection

If it does exist dont change any thing else. Just add the part in bold.

BTW replace **"1020x758"** with whatever resolution you are wanting

Please post results

---

### Post by samrohde on 2008-11-16
> **Marcus Derekus said:**
> Open /etc/X11/xorg.conf as root like so:

```

sudo gedit /etc/X11/xorg.conf

```

Then go to the **Section "screen"** line and add the following code:

```

Section "Screen"
	Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        SubSection "Display"
                **Modes      "1020x758"**
        EndSubSection
EndSection

```

If SubSections does not exist create it and add the code exactly as it is
Dont forget to EndSubSection

If it does exist dont change any thing else. Just add the part in bold.

BTW replace **"1020x758"** with whatever resolution you are wanting

Please post results

I tried it and I still have the same problem. I followed the code exactly, I saved the file, closed everything and I rebooted.

---

### Post by Marcus Derekus on 2008-11-16
Now try setting your resolution through System>preferences>screen resolution

BTW remember the resolution i gave was just an example

---

### Post by samrohde on 2008-11-16
> **Marcus Derekus said:**
> Now try setting your resolution through System>preferences>screen resolution

BTW remember the resolution i gave was just an example

Okay, I did and the new resolution I put in isn't there. However, I tried the other resolutions and even though the screen resolution changes I still am missing half a task bar thickness all the way around. It's the weirdest thing I have ever seen. I have attached some pictures of what it looks like.

---

### Post by sama_j on 2008-11-16
I had this same problem. Changing the refresh rate fixed it for me.
I hope it's as easy for You :)

---

### Post by SunnyRabbiera on 2008-11-16
I just with you didnt have to manually edit xorg like this, I mean yes people were having issues with displayconfig-gtk but someone can mess things up by editing xorg manually as well.

---

### Post by Marcus Derekus on 2008-11-17
just adding resolution modes won't hurt anything. (besides you can always run xfix under recovery mode if something goes wrong or even better backup xorg.conf before any changes)

but i do know that changing refresh rate does work sometimes.

also you could try going to System>Administration>Hardware Drivers and enable you graphics card (if you didn't already)

---

### Post by samrohde on 2008-11-17
> **Marcus Derekus said:**
> just adding resolution modes won't hurt anything. (besides you can always run xfix under recovery mode if something goes wrong or even better backup xorg.conf before any changes)

but i do know that changing refresh rate does work sometimes.

also you could try going to System>Administration>Hardware Drivers and enable you graphics card (if you didn't already)

I went to Hardware Drivers to enable my graphics card and the list is empty. There are no drivers. Could that be the problem? If so, where can I get the right driver?

---

### Post by Marius Derekus on 2008-11-17
That can probably be fixed by changing your monitor settings (you should have some buttons on your monitor, some that expand the screen height and width). Hope it helps.

---

### Post by Marcus Derekus on 2008-11-17
Hmm you could check [http://downloadcenter.intel.com](http://downloadcenter.intel.com) (they do distribute some linux drivers), 

check synaptic package manager, 

or perhaps [http://packages.ubuntu.com](http://packages.ubuntu.com) (post if the site seems confusing and i'll help out)

Remember though this might not fix your problem.

btw did you try ajusting refresh rate

also 

Marcus Derekus is a different person then Marius Derekus

just telling you so you dont get confused

---

### Post by samrohde on 2008-11-17
> **Marius Derekus said:**
> That can probably be fixed by changing your monitor settings (you should have some buttons on your monitor, some that expand the screen height and width). Hope it helps.

Wow, I feel really stupid, lol:). I went into my monitor settings and there was a setting that is called "crop" and it was turned on. So I turned it off and what do you know, I can see the entire computer screen. The problem is fixed. I use my TV as my computer monitor also, so at some Point I guess around the same time I upgraded, the crop was turned on. I can't believe it was that simple. I guess the most difficult problems have some of the simplest solutions. Thank you to everyone for all of you help. I have had a cropped computer screen for about 2 weeks now, I have been searching for the solution all this time when it was right in front of my face!:lolflag:

---

### Post by Marcus Derekus on 2008-11-17
Lol! We all do it!

---

### Post by roshanjose on 2008-11-17
hey even i have the same set of problems as mentioned above but expanding the screen by using the monitor settings button is just a temporary solution..it does strain your eyes. get something better.....we r in need of a good solution

---

### Post by Marius Derekus on 2008-11-17
Sorry, didn't know it strained your eyes

---

### Post by samrohde on 2008-11-17
> **roshanjose said:**
> hey even i have the same set of problems as mentioned above but expanding the screen by using the monitor settings button is just a temporary solution..it does strain your eyes. get something better.....we r in need of a good solution

I didn't expand the screen, I shrunk it with the monitor settings.

---

