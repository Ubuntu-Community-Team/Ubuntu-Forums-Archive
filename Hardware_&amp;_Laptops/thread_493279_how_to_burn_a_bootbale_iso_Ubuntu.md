---
title: "how to burn a bootbale iso Ubuntu ?"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by retro_killa on 2007-07-05
i just wiped out windows vista & now i am running ubuntu Ubuntu 6.06 on my acer aspire 9300 laptop. 

i am very very new to useing linux and the chnage over is really hard right now because i do nto know anything about linux all i know is it is faster then vista so far.

so my question is how or where can i get a program that will allow me to make/burn bootable     .iso ? 

step by step please also the reason i want to make a bootable isco is so i can try linspire

---

### Post by coffeecat on 2007-07-05
It's much easier than in Windows. You need either K3b or Gnomebaker. Look in the Synaptic Package Manager.

K3b is a KDE application. In my view it's better than Gnomebaker, but if you're running Ubuntu/gnome, it will bring in a lot of KDE dependencies.

Once you've installed either, look for 'burn CD image' (or burn DVD image) in the Tools menu in K3b or on the toolbar in Gnomebaker.

**Edit:** If you're new to Linux and want to try distros that have live CDs from which you can also install (should you so wish), have a look for Ubuntu 7.04 (Feisty) :wink:, PCLinuxOS and Mepis.

---

### Post by retro_killa on 2007-07-05
> **coffeecat said:**
> It's much easier than in Windows. You need either K3b or Gnomebaker. Look in the Synaptic Package Manager.

K3b is a KDE application. In my view it's better than Gnomebaker, but if you're running Ubuntu/gnome, it will bring in a lot of KDE dependencies.

Once you've installed either, look for 'burn CD image' (or burn DVD image) in the Tools menu in K3b or on the toolbar in Gnomebaker.

**Edit:** If you're new to Linux and want to try distros that have live CDs from which you can also install (should you so wish), have a look for Ubuntu 7.04 (Feisty) :wink:, PCLinuxOS and Mepis.

i am so so so n00bish i do nto even knwo how to install this or what link d/l from there site please help

---

### Post by retro_killa on 2007-07-05
i found this & it works ;) 

Open a terminal window and type in:
sudo apt-get install k3d
or
sudo apt-get install gnomebaker:popcorn:

---

### Post by coffeecat on 2007-07-05
> **retro_killa said:**
> i am so so so n00bish i do nto even knwo how to install this or what link d/l from there site please help

Assuming you're using Ubuntu/gnome and not Kubuntu or one of the other Ubuntu variants...

From the main menu, go to System > Administration > Synaptic Package Manager. You'll be prompted for a password - that's the same password as you use to log in, but as the first created user it will give you administrator privileges which are needed for installing applications.

Press the search button in the Synaptic window, and put 'k3b' in the search field.  Find k3b in the list, right-click on it and mark it for installation. It will almost certainly open another window asking you to approve a large number of dependencies. Click the 'Mark' button. Now click on the Apply button. Before it downloads anything it will tell you the total size of download. If you're happy with that, click Apply. If not, click Cancel.

If you clicked Apply, all the necessary packages will be downloaded and installed automatically. Then you'll find the app K3b in the Applications > Sound & Video menu. I'm assuming here that you've got broadband. If you're on dialup the download will be far too big. 

If you cancelled, wanting gnomebaker instead, go to the Edit menu in Synaptic and choose undo (to deselect K3b and its dependencies). Then go through the same procedure as before, but search for and install gnomebaker.

Once you've got used to it, downloading and installing applications in most Linux distros - certainly in Ubuntu - is much easier than in Windows.

Good luck.

---

### Post by coffeecat on 2007-07-05
> **retro_killa said:**
> i found this & it works ;) 

Open a terminal window and type in:
sudo apt-get install k3d
or
sudo apt-get install gnomebaker:popcorn:

Well done. You've found the terminal way to do what I've just described as the GUI way.

And there's more. :) Have a look at Applications > Add/Remove. Not as powerful as Synaptic, but much more user-friendly if you want to see what types of applications are available in the repos.

---

### Post by bigken on 2007-07-05
in ubuntu if you have an iso just right click it and select burn or write to disc 

to create an iso from a cd just right click and select copy disc

---

### Post by retro_killa on 2007-07-05
> **coffeecat said:**
> Well done. You've found the terminal way to do what I've just described as the GUI way.

And there's more. :) Have a look at Applications > Add/Remove. Not as powerful as Synaptic, but much more user-friendly if you want to see what types of applications are available in the repos.

i am d/l freespire from there site to see if it will be more user freindly for me. 

any ideas for a super user n00bish linux os ? because i really want to make the chage over for a windows user to a linux lover ;) 


also thx for the help guys & gals

---

### Post by odinb on 2007-07-05
> **retro_killa said:**
> 
any ideas for a super user n00bish linux os ? because i really want to make the chage over for a windows user to a linux lover ;) 


Choose Kubuntu, the GUI is very windows-alike, did the move myself less than a week ago myself, and it is addictive...

Already fighting with my second machine....

---

### Post by retro_killa on 2007-07-05
> **odinb said:**
> Choose Kubuntu, the GUI is very windows-alike, did the move myself less than a week ago myself, and it is addictive...

Already fighting with my second machine....



what makes it easy to use ? explain

---

### Post by odinb on 2007-07-05
It installs easily on most hardware. (It does not like broadcom chipset on your WLAN-adapter, and does not like the nVidia Go 6100 on my second laptop.)

It installs faster than XP.

All the usual applications come pre-installed (like open-office).

The packet manager lets you install missing applications and keep the OS and applications up to date easily and fast.

KDE looks similar to the desktop you are used to from Windows.

To find applications, you can use: [http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)

To find compatible laptop HW, you can use: [http://www.linux-laptop.net/](http://www.linux-laptop.net/)

If you want a media-version you can install MythTV.

It is blazing-fast compared to Vista on the same HW....

---

