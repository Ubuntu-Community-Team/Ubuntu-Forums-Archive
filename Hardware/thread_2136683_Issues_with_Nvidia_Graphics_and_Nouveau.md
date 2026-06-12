---
title: "Issues with Nvidia Graphics and Nouveau"
date: 2013-04-18
forum: Hardware
---

### Post by Chaori on 2013-04-18
Hi all,

I am still very new to Ubuntu and I am having a few issues, just wondering if anyone could help me out. I have had to reinstall Ubuntu completely around 10 times now because of issues installing graphics drivers and it causing parts of Ubuntu to crash and no longer load (such as Compiz and Unity) and I'm so sick of reinstalling it lol.

Could someone please explain to me the 'best' or proper way to install drivers for a Nvidia video card? The default Nouveau driver in Ubuntu 12.10 has really bad graphical glitches (exactly the same issue as [this thread]("http://ubuntuforums.org/showthread.php?t=2076002")) - however the Nouveau driver in the 13.X Beta works perfectly (I want to continue using 12.10 for the moment). 

Coming straight from Windows I assumed the best way to install the drivers for my GTX570 would be off the Nvidia website, however I am reading very conflicting views depending on what site I read. The Nvidia driver Readme tells me to add a line to modprobe.d/blacklist.conf to stop Nouveau from loading when the computer starts up (which seems like an odd way of doing it - I assume it's because it conflicts with the Nvidia driver). I did try this but when I tried to go back to the Nouveau driver by removing the file that stopped it starting it completely f**ked up Ubuntu. Another website I read said to install Jockey and download drivers through that, and that resulted in Compiz crashing and another re-install of Ubuntu. I also read that Ubuntu do not support the closed-source driver and won't offer help if you have any issues with it as it is not open-source. Does this mean I should use Nouveau? Is there any way I can fix the graphical glitches without using the Nvidia driver from their website?

I tried the suggestion in the other thread linked above (***sudo apt-get install nvidia-current***) and this seemed to install perfectly, but when I rebooted my computer I kept getting messages that Ubuntu has encountered an error, and Compiz crashes. If I reboot again Compiz simply won't load and if I try ***sudo compiz --reload*** it will throw a lot of errors at me. It will display my desktop background and the folders on my background (I can also open applications through terminal) but I simply have none of the Ubuntu GUI.

If anyone could help me get my computer working properly that would be great. At this point I am scared to try anything because it will most likely result in Compiz crashing and me having to re-install Ubuntu.

---

### Post by Chaori on 2013-04-18
Just an addition - after running the Ubuntu software update I no longer get the graphical glitches using the Nouveau driver, but the visual effects run a lot slower than they did when I had the driver installed from the Nvidia website.

---

### Post by Chaori on 2013-04-18
Reading off site [http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html](http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html)

Says to use the following:
```

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

```

However in the comments people are saying that after doing so they no longer have a HUD (the issue I get when I try to install Nvidia drivers). A user in the comments says to do the following:
```

sudo apt-get install linux-source
sudo apt-get install linux
sudo apt-get autoremove nvidia-current
sudo apt-get install xserver-xorg xserver-xorg-video-all
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo reboot
```

Could anyone confirm which one I should try? I really don't want to re-install Ubuntu again :(

---

