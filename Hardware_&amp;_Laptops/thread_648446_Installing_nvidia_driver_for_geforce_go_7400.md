---
title: "Installing nvidia driver for geforce go 7400"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by mrbubbles on 2007-12-23
I'm a NEW user of ubunut (and linux - second day much turmoil so far) and i need to know how to install the driver for my nVidia geforce go 7400 on my hp pavilion dv5220us.

I'd really appreciate any help anyone can give.  Thanks!

:popcorn:

---

### Post by mrbubbles on 2007-12-23
I know how to get to the terminal, but using it... well, that's a different story.  I'm unsure of the file system, commands, etc. and how to get the drivers installed seems pretty complicated to a windows user :)

i just need some step-by-step code instructions.

Thanks!

---

### Post by logos34 on 2007-12-23
>system>admin>restricted driver manager>enable 

may need to get restricted-modules pkg

sudo apt-get install linux-restricted-modules-`uname -r`

Or are there issues I'm unaware of using the nvidia-glx-new with the go 7400?

---

### Post by mrbubbles on 2007-12-23
logos, thank you for your reply.

i've tried installing the nvidia-glx-new package and it has some trouble.  I've created a launcher with the code"

sudo "gnome-open %u"

but it tells me "Error: Dependency is not satisfiable: nvidia-glx"

i've also tried installing a different driver/package through the same launcher that I got from the nvidia website, it's name is NVIDIA-Linux-x86-1.0-8756-pkg1.run.  apparently the terminal has a hard time understanding the character coding (as per the error that's atop the popup window).

:(

---

### Post by mrbubbles on 2007-12-23
i'm assuming my restricted driver manager is working - the wireless adapter in my computer is enabled through this (which is why I can post :))

---

### Post by logos34 on 2007-12-23
what happens when you run 

sudo nvidia-settings

?

---

### Post by mrbubbles on 2007-12-23
i ran 

sudo nvidia-settings

and it said "command not found"](*,)](*,)

---

### Post by logos34 on 2007-12-23
then the restricted driver is not working because not installed (and network card driver is something separate).

> 
i've tried installing the nvidia-glx-new package and it has some trouble. I've created a launcher with the code"

sudo "gnome-open %u"

but it tells me "Error: Dependency is not satisfiable: nvidia-glx"

i've also tried installing a different driver/package through the same launcher that I got from the nvidia website, it's name is NVIDIA-Linux-x86-1.0-8756-pkg1.run. apparently the terminal has a hard time understanding the character coding (as per the error that's atop the popup window).


Why don't you try installing it again--maybe the dependencies problem will resolve itself:

backup xorg first:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo apt-get install nvidia-glx-new

then

sudo nvidia-glx-config enable

ctrl+alt+backspace 

to restart desktop or reboot

If x server fails to load on restart, at the prompt simply restore backup xorg.conf:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by mrbubbles on 2007-12-23
backed up xorg like you said (it didn't say anything after i pressed enter, but it didn't give me any kind of message to make me think it didn't work :))

i tried installing nvidia-glx-new again, and this is what it said:
"Package nvidia-glx-new is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package nvidia-glx-new has no installation candidate"

*whew*

something i'm missing?

---

### Post by mrbubbles on 2007-12-23
just a thought - is there a specific PLACE that the installation files need to be in?  i've got them on the desktop, but should they be in \home?  or \home\luke?

---

### Post by logos34 on 2007-12-23
> **mrbubbles said:**
> backed up xorg like you said (it didn't say anything after i pressed enter, but it didn't give me any kind of message to make me think it didn't work :))

you can always check if it's there with

**ls** /etc/X11/xorg*

> i tried installing nvidia-glx-new again, and this is what it said:
"Package nvidia-glx-new is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package nvidia-glx-new has no installation candidate"

Do you have all the repositories enabled?

system>admin.>software sources

check main, multiverse, universe and **restricted**

then try to fetch it again:

sudo apt-get update

sudo apt-get install nvidia-glx-new

---

### Post by mrbubbles on 2007-12-23
I didn't have the repositories enabled... that's something new for me :)  When I installed ubuntu, my internet wasn't working so I guess it wasn't able to enable them then.  It's downloading stuff currently.  I'll give an update when I've tried installing the driver again.=D>

---

### Post by mrbubbles on 2007-12-23
woo hoo!  seems to be working.  :guitar: the terminal is downloading the necessary files.  just wondering if there's something i need to do with the driver that nvidia (on their website) told me i needed to get: NVIDIA-Linux-x86-1.0-8765-pkg1-run

---

### Post by mrbubbles on 2007-12-23
We're goin' places!  It's installed, but when I entered "sudo nvidia-settings" the popup said that i wasn't using the x driver, and that i needed to edit my config file by typing in "sudo nvidia-xconfig" 

i did this, and it told me where the backup was saved.  

the file says that both my monitor and video cards are "generic"  is there something i need to type in that's different or do in the system>admin>screens & graphics utility?

---

### Post by logos34 on 2007-12-23
Now go to restricted drivers manager--is it checked/enabled?.  Reboot

---

### Post by mrbubbles on 2007-12-23
hmmm... not even on the list

for some reason, in screens & graphics, ubuntu still thinks the card is an intel 945, but now it's using the nvidia driver

---

### Post by mrbubbles on 2007-12-27
it's working!  thanks logos, you're great.

:guitar:

---

### Post by logos34 on 2007-12-27
you're welcome!  Mark as 'solved' and enjoy 'buntu!

---

### Post by Q4-percy on 2007-12-27
Yeah hey, I'm having the same problem. Everything is happening the same as above. I have an AMD 3500 64 bit w/ a GeForce 8600 nVidia. I'm a rather newB. Thanks,

---

