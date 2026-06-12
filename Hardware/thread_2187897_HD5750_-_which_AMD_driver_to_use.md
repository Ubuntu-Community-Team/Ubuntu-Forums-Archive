---
title: "HD5750 - which AMD driver to use?"
date: 2013-11-14
forum: Hardware
---

### Post by dannyboy79 on 2013-11-14
Hi guys,
I may be purchasing a used computer from a friend and I have learned that it has a XFX AMD HD5750. I have always ran Nvidia cards by choice because of the propritary binary blobs being easier to install and perform better. Well, I am going to base my purchase decision around the feedback I get regarding which driver to use and install to use with the HD5750. Is the propritary AMD Catalyst™ 13.11 Beta V6 Driver for Linux the bst option or shall I just go with the current stable released AMD Catalyst™ 13.4 Proprietary Linux x86 Display Driver? Or is the open source driver any good? I will be using it as a daily driver but will be gaming on it now. Nothing to demanding, Serious Sam 3 BFE, Bastion, Portal, maybe even buy Metro Last Light if the HD5750 can handle it. It should be better than my current 8400GS that's for sure. 

Also, this tower I may be buying has an AMD A8-3870k APU, so would I just have to disable the onboard GFX to get the HD5750 to work or can i somehow use both or would it even be smart to run both?

Any feedback would be greatly apprecaited. Oh, I will be running Xubuntu 12.04.3 and then when the next LTS comes I will be switching to it.

---

### Post by snafu006 on 2013-11-14
Here: [http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers)

The form page is not maintain but the drivers are and they work.

---

### Post by QIII on 2013-11-14
Personally, I'm not a big fan of PPAs for graphics drivers.

Each version of Ubuntu has in its repos the most recent ATI driver at the time of the release.  That was 12.4 when 12.04 came out.  The easiest thing to do would be to just use that driver.

If you don't want to do that, you can download the driver from ATI and either:  1.  Make it into a .deb; 2.  Run the .run file raw.

The broad answer to your question is that the drivers are available and are, despite common misconceptions, quite easy to install.  I'm not sure where the "ATI's drivers are hard to install" myth comes from.

From the repo:

```
sudo apt-get install fglrx fglrx-amdcccle
```
or
```
sudo apt-get install fglrx-updates fglrx-amdcccle-updates
```

and then 

```
sudo amdconfig --initial
```
or, if there are multiple ATI cards
```
sudo amdconfig --adapter=all --initial
```

Two commands.  That's it if you install from the repo.

---

### Post by dannyboy79 on 2013-11-16
ok, well I downloaded the latest stable release of the AMD catalyst from the AMD website. unzipped it onto my desktop, chmod a+x to make it executable, then I went to tty1, I stopped lightdm, then I ran the installer using sudo ./amd_blah_blah_whateverthelongnamewas_installer.run. I accepted all the defaults during the install, then when done I issued sudo service lightdm start and I am not using the latest AMD stable driver. I did have to change the command to run the amdcccle  in admin mode to gksudo amdcccle

---

### Post by Blaqksheep on 2013-11-16
I've got an HD7770 and the proprietary drivers are head and shoulders above the open source drivers, especially with Wine.

However, your GPU has been around longer so the open source drivers might be more robust.  I've been using AMD GPUs since they were ATI but this will likely be the last I buy due to AMD's awful compatibility and support.

[EDIT]  That said, I'd stick to stable releases.

---

### Post by QIII on 2013-11-16
You will need to reboot.  Restarting lightdm isn't enough.

---

### Post by dannyboy79 on 2013-11-16
well I can assure you I didn't have to reboot, restarting lightdm worked just fine and I was able to configure using AMD catalyst and dmesg reports fglrx 12.10.5 [Mar 28 2013]

---

