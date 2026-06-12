---
title: "IBM X31 graphic driver problem (i think)"
date: 2010-01-22
forum: Hardware
---

### Post by macli on 2010-01-22
warning - i'm used to windows not linux (at all)...

I decided to install ubuntu on my old laptop (ibm x31) after trying ubuntu out on an old desktop (with success). It installed ok (used the same cd as i used on my desktop - is that a problem?), even found my wireless connection but i'm having grapich problems. The screen updates strangely and there are lines across the screen.

I have no idea how to fix this - on windows i would install an a driver but in ubuntu i'm lost.

Could anyone point me in the right direction?

Thanks,

---

### Post by myth1914 on 2010-01-22
It looks like the X31 has an ATI Radeon card (although this may differ depending on the sub-model if any).   The menu name eludes me at the moment, but look for "hardware drivers" or something close to that in the admin/pref section of the menu depending on your choice of desktops (xfce, kde, etc)

Also, look here for install notes on your particular laptop:  [http://www-cs-students.stanford.edu/~blynn//linuxthinkpadx31.html]("http://www-cs-students.stanford.edu/%7Eblynn//linuxthinkpadx31.html")

---

### Post by macli on 2010-01-22
Thanks,

yes - I have a radion mobility m6 card.

But I don't know how to change driver, and the gui is so bad that I can't use the menu (screen is not updatering). 

This is why i fear linux over windows - i have no idea how to fix this

Can anyone help?

---

### Post by myth1914 on 2010-01-22
This how-to should help get you going: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installation%20of%20the%20fglrx%20Driver%20from%20the%20Ubuntu%209.10%20Karmic%20Repositories](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installation%20of%20the%20fglrx%20Driver%20from%20the%20Ubuntu%209.10%20Karmic%20Repositories)

However, without the GUI to install the binary...  Perhaps not the best solution, but if you can get to the command line of the machine in question and run:

sudo aptitude -y install openssh-server vnc4server

Then, from another machine, install a VNC viewer like tightVNC.  Now, Either through ssh or with the terminal on the ubuntu box run:

vnc4server

which will then guide you through a simple password creation and (it's been a while) choosing which screen.  Choose the default and it should say something like you can now connect to hostname:1

From the VNC viewer on the other box, connect to <ipaddress_of_ubuntu_box>:590x where X is the number that the vnc4server provided.  hostname:1 = ipaddress:5901, hostname:2 = ipaddress:5902

This should provide you with a remotely rendered X session on the VNC viewer and allow for administration.

I know this is not elegant, but while I feel I know enough, these forums have taught me there is much to learn.  Regardless, this should work.

---

### Post by macli on 2010-01-22
Hi

Got an vnc connection but System->Administration->Hardware Drivers is empty. Now what?

Perhaps Ubuntu can't be installed om IBM X31 laptop with a ATI Mobility RADEON M6C-16h?

Thanks,

---

### Post by realzippy on 2010-01-22
...maybe this helps:

[http://swiss.ubuntuforums.org/showthread.php?t=899178](http://swiss.ubuntuforums.org/showthread.php?t=899178)

---

### Post by macli on 2010-01-22
Thanks for your answer - but its way to complicated to get this issue solved. If it can't be solved in GUI i'm lost.

Have to give up and install XP/Win 7 instead - not what I was hoping for.

Thanks

---

### Post by cenzorrll on 2010-01-22
hmm, i have an ibm x31 that i've had ubuntu on for years.  radeon no longer supports the graphic card, so i don't believe you'll be able to update the driver.  However, i'm pretty sure the generic driver ubuntu uses takes care of everything (if i recall correctly even compiz works).

try installing jaunty instead of karmic, it was the last distro I used on mine and it worked flawlessly (well, don't know about the wireless as I turned off the internal one a while back)

sadly the lines could also mean your graphics card is on it's last legs, or possibly producing too much heat (try making sure desktop effects are disabled, shutdown for a few minutes (hell, stick it in the freezer if you want) and restart to see if it does the same thing

---

### Post by realzippy on 2010-01-22
> **macli said:**
> Thanks for your answer - but its way to complicated to get this issue solved. If it can't be solved in GUI i'm lost.

Have to give up and install XP/Win 7 instead - not what I was hoping for.

Thanks

Maybe your card is supported by the old ATI driver (which,afaik,stopped
running since 9.04 Jaunty due to newer Xorg).You should google for it,
or,maybe its faster,download 8.10,install it.The ATI driver should be in the restricted drivers,if not,you could install it easily by :

[B]sudo apt-get install fglrx
[/B]

---

### Post by macli on 2010-01-23
Hi,

Just to let you now - before installing XP I decided to try 8.1 like RealZippi suggested - and it works like a charm. I go with 8.1 for now - thanks for your help.

---

### Post by realzippy on 2010-01-24
...great.Have fun...and,please mark thread as solved (Threadtools)

---

