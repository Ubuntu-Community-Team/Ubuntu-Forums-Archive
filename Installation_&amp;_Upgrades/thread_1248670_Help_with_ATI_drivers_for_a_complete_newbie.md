---
title: "Help with ATI drivers for a complete newbie"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by Mustang.Concept on 2009-08-24
Hey all
I just installed Ubuntu which is the very first time i deal with Linux actually
Now obviously you can imagine how confused i am when i am double clicking
the drivers and received a sort of error that tells me to run it as  a Super User?...

I googled for "how to install ATI drivers with super user"
and found some "solutions" but they were like Chinese to me...

They told me to run some commands, without even mentioning where the
hell is the place to run commands at?
But i managed to find it, apparently it is called "Terminal"
cool so i went into the Terminal, copied the commands and it said "command wasnt found"

anyways... i am completly lost and the guides are... not newbie friendly
all i managed to do is to find the terminal
I have 3 drives (i cant see their labels at all so all i know is the size and content)
1 drive is the one with vista on it which is the 113.7GB drive
1 drive is 29.2GB which im not sure where he came from... but there is #RECYCLE folder in it
and 1 drive 100% empty
of and filesystem which i dont know what it is

the ATI driver is located on my ubuntu desktop

help =\

---

### Post by Jerry.S on 2009-08-24
What you can do is drag and drop the driver in to the terminal window so it loos something like this:

yourname@yourcomputername~$ you will see something like '/home/yourname/desktop/yournewdriver'

change it to look like this: yourname@yourcomputername~$ **[SIZE="3"]sudo sh[/SIZE]** '/home/yourname/desktop/yournewdriver'

Thats how I got mine to load

---

### Post by tuxxy on 2009-08-24
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by sloggerkhan on 2009-08-24
If you aren't using repo driver, first get proper dkms system dependancies, then run the driver with the build pkg ubuntu option, then click the deb files that appear.

---

### Post by Mark Phelps on 2009-08-24
> **Mustang.Concept said:**
> Hey all
I just installed Ubuntu which is the very first time i deal with Linux actually
Now obviously you can imagine how confused i am when i am double clicking
the drivers and received a sort of error that tells me to run it as  a Super User?...

One thing you need to learn about Linux is that it automatically installs the drivers for you.  If you start forcing the installation of other drivers, you are guaranteed to break your installation so that, at worst, it won't boot anymore.

So, before you do that, how about telling us what make & model ATI card you have and why you feel it necessary to install drivers when open source drivers have already been installed for you.

---

