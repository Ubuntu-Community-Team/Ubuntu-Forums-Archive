---
title: "Can't install updates"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by Zacariah on 2009-02-19
I've just got Ubunttu, and I'm finding a lot of it rather hard..

I play a few online games, and what not, and they all need shockwave, and i found somewhere something about whine, and tried to follow the instructions and download it, but it didn't work. I keep getting heaps of messages with everything, and its getting rather annoying. Thinking of going back to windows, but i would rather stick it out, and learn abit more about this.

I have 149 updates to download/install, i click 'install updates' and get this error message

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: _cache->open() failed, please report."

Now i figured that ment, type 'dpkg --configure -a' into the terminal, (without the ' obviously) but i get another error message saying,

"dpkg: requested operation requires superuser privilages"

I really have no idea what to do, any help would be appreciated, i need a lot of help.

If you're willing to help with this, and problems i'll undoubtedly have in the future, feel free to add me to msn.
[email]zaccydapro303@hotmail.com[/email] (its a very old msn)

Thanks.

EDIT: i'm also wondering about winrar, and stuff like that.. Is there a program like winrar for linux? or will winrar work on linux?

---

### Post by Partyboi2 on 2009-02-19
>  "dpkg: requested operation requires superuser privilages" This means that you need to run the command with superuser privilages. So open a terminal (Applications>Accessories>Terminal) and do as it says but put sudo in front to gain superuser privilages.
```
sudo dpkg --configure -a
```Edit: To extract .rar files you can use  unrar or  unrar-free, see [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/FileCompression#Rar%20%28.rar%29").

---

### Post by Zacariah on 2009-02-19
Thanks, 

I got a message saying 'you have three broken packages on your system, use the broken filter to find them'

or something along those lines. Any help? not sure what the broken filter is, or where it is.

---

### Post by Partyboi2 on 2009-02-19
You can fix the broken package from a terminal by typing
```
sudo apt-get -f install
``` Or you can open Synaptic (System>Admin>Synaptic Package Manager) and go to Edit > Fix Broken Packages.

---

### Post by konqueror7 on 2009-02-19
```
sudo apt-get install -f
```

didn't see there was already a reply post...:)

---

### Post by Zacariah on 2009-02-19
So you basically have to have a good understanding of coding/python type stuff to use linux propperly?

---

### Post by Partyboi2 on 2009-02-19
> **Zacariah said:**
> So you basically have to have a good understanding of coding/python type stuff to use linux propperly?
No you don't, just time to learn something new :) 
Ubuntu offers plenty of gui tools to be able to accomplish what can be done in a terminal.
I personalty know very little about most of the programming languages.

---

### Post by Zacariah on 2009-02-19
Would you be able to help with um, getting shockwave? I don't fully understand how..

[https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

---

### Post by Partyboi2 on 2009-02-19
What part are you stuck at?

---

### Post by Zacariah on 2009-02-19
The whole thing pretty much.. 

Installing stuff on Ubuntu has got me rather stumped.

I don't have a very good patience.

I take it i need to install wine first.. How do i do that..

---

### Post by Partyboi2 on 2009-02-19
Open a terminal (Applications>Accessories>Terminal) and install the required packages (wine mozplugger) by typing
```
sudo apt-get install wine mozplugger
```
Or you can open up Synaptic Package Manager and searh for those 2 packages and install them.

---

### Post by Zacariah on 2009-02-19
Thanks alot, it worked.

Well i followed the rest of the instructions, and it worked.

Could you get windows live messenger, using whine?

---

### Post by Partyboi2 on 2009-02-19
I have never tried using windows live messenger with wine. You could always install amsn and try it.
To install open a terminal and type
```
sudo apt-get install amsn
``` Or search synaptic for amsn.

---

### Post by Zacariah on 2009-02-19
The code you use in terminal, thats python isn't it?

---

### Post by linux_tech on 2009-02-19
python is programing language used in web apps,etc. 
It is supported in ubuntu.
To access- Applications>Accessories>Terminal.Then type ```
python
```

---

### Post by Zacariah on 2009-02-20
Um .. I figured I'd just post this in the same thread, I'm trying to set up my wireless Internet, and my laptop has an inbuilt wireless driver, I assume I have to install the driver? again. (After installing ubuntu) But i put the disk in and it just says "cannot find the autorun program" or something.

Any help would be appreciated.

Thanks

---

### Post by Zacariah on 2009-02-20
I'm going to reinstall windows.

Theres to many things i can't do on ubuntu, and i don't really have any reason to have it.

Thanks for your help guys.

---

