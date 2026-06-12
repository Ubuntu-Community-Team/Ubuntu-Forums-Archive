---
title: "Still Cannot Get the Screen Resolution Right"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by lakelovers on 2006-02-16
I'm about to throw in the towel. I've tried repeatedly to correct the screen resolution and I get nowhere. It's stuck at 640. I've read many of the posts regarding screen resolution and followed many of the suggestions. I posted my xorg.conf file but got no response. When I reconfigure, which I've done many times, I have trouble getting back into "Xwindow." This time I lost my bookmarks and an important file in OpenOffice. And when the initial screen came up I got this message: Error, failed to initialize HAL! What the heck does that mean?

This is my current xorg.conf files. I'm afraid to reboot because I probably won't get back in without a lot of reconfiguring. I really hate to sound so negative but I've spent way too much time trying to get Ubuntu working correctly, which is a disappointment because I understood this was a distro that "worked." I'd appreciate it if anybody could give me an idea on how to get this straightened out.


Section "Device"
        Identifier      "Intel 3D AGP Graphics"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "ENVISION"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-130
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel 3D AGP Graphics"
        Monitor         "ENVISION"
 Device          "Intel Intel 3D AGP Graphics"
        Monitor         "ENVISION"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
       SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by heimo on 2006-02-16
What seems suspicious to me is the duplicate Monitor and Device lines in screen section. Keep the device line which match device sections identifier line. Also if you can give us the exact model of your monitor, that could help - or even better, check that the vertrefresh and horizsync lines match the values in manual of your monitor.

Some additional information:
[http://www.ubuntuforums.org/showthread.php?t=83973]("http://www.ubuntuforums.org/showthread.php?t=83973")

---

### Post by lakelovers on 2006-02-16
Thanks for your reply. The monitor model is Envision EN-710e. The duplicate lines may have happened when I copied the file to this forum. I did it in chunks and may have overlapped the copies. Also, my eyes were so tired I wasn't seeingn straight. I'll take a look at the file and delete any duplications. I am using the refresh figures from the monitor specs.

I looked at the file and there is no duplication. Here's what I get when I try to start X: XI0: fatal I0 error 104 (Connection reset by peer) on X server ":0.0 after  0 requests (0 known processed) with 0 events remaining.

I find the link you suggestg for addition information quite helpful. I tried the directions there but still not successful. By the way when I do a refigure of xorg I get a corrupted screen i.e., so of the symbols "<> []" are misplaced or duplicated < >>. Something is really whacky.

---

### Post by lakelovers on 2006-02-17
I may have gotten the xorg.conf file right but I cannot get into a session. It logs off immediatedly. I'm beginning to wonder if I have a failing hard drive. When the logged-off window appears it says:"your session only lasted less than 10 seconds. This could mean there is some installation problem or that you may be out of diskspace." In the details it says "unable to read ICEauthority."

I should have plenty of free diskspace. It's a 30 GB and Ubuntu is the only thing on it and I don't have any huge files (e.g., photos, music).

Here's the rest of the story. Before Ubuntu I ran Mandriva. I got a full disk warning on that, too, but found that my backups were going on the ext3 partition. Those were removed freeing up about 5GB. So, I was able to work for a day with no problems. Guess what, it filled right back up. Then I thought I must have a virus. Maybe I still do, but when I installed Ubuntu, I wiped the disk. 

I don't want to buy a new hard drive until I'm sure that this one is, in fact, biting the dust. How can I prove the integrety of the hard drive? I'm sure that there's a command line to show the free space on the drive; I'll try finding it.

All help is appreciated

---

### Post by heimo on 2006-02-17
How do you start X? If you're using *startx *you could probably try to launch gdm.

Make sure it's not running:
```
sudo /etc/init.d/gdm stop
```

And then start it:
```
sudo /etc/init.d/gdm start
```

This should start a login screen. Does it?

You can use *df *to check free disk space.

---

### Post by lakelovers on 2006-02-17
The screen goes black. No login screen. I used df and there's lots of free space.

---

### Post by heimo on 2006-02-17
Check your xorg.log (information on the thread linked in my first post). Also you should probably run these commands to make sure your install went fine:
```
sudo dpkg --configure -a
sudo apt-get install ubuntu-desktop
```

And if you're running 5.04, you should probably try to [upgrade to Breezy Badger]("https://wiki.ubuntu.com/BreezyUpgrade") 5.10.

---

### Post by lakelovers on 2006-02-17
I did a google serch on "ICEauthority" and which led me back to [http://ubuntuforum.org/archive/index.php/t-153.html](http://ubuntuforum.org/archive/index.php/t-153.html) there I found a post saying to try: "sudo chown <login name> /home/<login name>/.ICEauthority" and it worked. I am now back into a Ubuntu session. I'm thankful I didn't run out get a new hard drive.

One continuing problem: ** I still don't have the correct screen resolution**. I've had so much trouble trying to correct it that I'm afraid to keep trying, but I sure wish I could get it right because running in 640x480 is very ackward.

Our posts crossed one another. Okay, I think I'll upgrade to Breezy Badger. Do you think that version will recognize my monitor better?

---

### Post by heimo on 2006-02-17
[quote=lakelovers]Our posts crossed one another. Okay, I think I'll upgrade to Breezy Badger. Do you think that version will recognize my monitor better?[/quote]

I hope it would, but you never know (without trying out). Check the xorg.log and consider upgrading to Breezy. In couple months there'll be Dapper Drake 6.04 (I'm upgrading to the development version right at the moment). 

Also check 855resolution and try changing the *vesa* driver to i810
[http://ubuntuforums.org/showthread.php?t=24923](http://ubuntuforums.org/showthread.php?t=24923)

---

