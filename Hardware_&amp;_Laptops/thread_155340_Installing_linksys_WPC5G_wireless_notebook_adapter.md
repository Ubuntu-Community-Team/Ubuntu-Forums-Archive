---
title: "Installing linksys WPC5G wireless notebook adapter"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by Swalchy on 2006-04-04
tried following the instructions at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) to install ndiswrapper in order to install the drivers need for the card (which I've already got from..somehwere I can't be bothered finding the link for)

Managed to get down to "make"

and then it says something about not finding kernel etc, so now I'm compete stuck as to what I'm supposed to be doing.

I''m a complete noob to linux, never mind ubuntu, so please, be gentle :P

---

### Post by kurgan78 on 2006-04-05
Assuming you have a wired connection on this laptop...

Go to [http://www.linksys.com](http://www.linksys.com), click on Support and then Downloads. Select the correct **Windows** driver for your card. Check the version by looking at the label on the backside of the adapter card.

Extract the downloaded ZIP file you downloaded from linksys.com to a folder in your home folder or your desktop. Open a terminal and go to that directory and find the subfolder that has LSBCMNDS.INF in it, change to that directory, and type in:
```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i lsbcmnds.inf
sudo ndiswrapper -m
```

If the apt-get doesn't work, edit /etc/apt/sources.list and uncomment the universe lines.

Now load the ndiswrapper module
```
sudo modprobe ndiswrapper
```

Verify driver and hardware present
```
sudo ndiswrapper -l
```

Type "iwconfig" and you should see a wlan0 wireless device.

Now add ndiswrapper to /etc/modules
```
sudo sh -c 'echo "ndiswrapper" >> /etc/modules'
```


From here you should be able to use the GUI tools to configure your wireless network. Look on your KDE or Gnome applications menu to find system settings for networking or wireless networking.

The alternative is to edit more /etc files.

---

### Post by Swalchy on 2006-04-05
right, managed to get to the "sudo modprobe ndiswrapper" stage, but it gave me this error:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Perhaps I must say this is a **wireless** connection i'm using, using a wireless network card.

---

### Post by kurgan78 on 2006-04-07
Did you download the source and compile or did you "sudo apt-get install ndiswrapper-utils"? Your original post indicated your were compiling from source. I had no trouble making ndiswrapper work by installing the one from the universe repository.

---

### Post by Swalchy on 2006-04-07
I downloaded the source to my windows PC and then copied it to my Ubuntu Laptop, and now you've confused me using the word compile... sorry :(

---

