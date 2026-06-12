---
title: "Brightness Control problem  MacBookPro9-2/Ringtail"
date: 2015-03-13
forum: Hardware
---

### Post by Pasley on 2015-03-13
Hi! I'm kinda new here. I've looked over the forums, but i can't seem to find a problem with my set-up. Can anyone offer any assistance.

**_Problem_**

Host: MacBook Pro 9,2/Ringtail
Os: Ubuntu 14.04.2 LTS \n \l (mac os has been wiped)

Cannot control brightness eventhough brightness pop-up dispays when brightness button has been pressed.
keyboard backlight works properly.
volume works properly.
disc eject works properly.

I've looked up similar problems, but I've only been able to find references for older systems.

I don't know where to begin on a newer system. I have had mint dual booted on here once, and it was able to control the brightness. However straight ubuntu is the os i want to use.

Please, someone, help!

---

### Post by Hulk_Joshua on 2015-03-13
Run the command below in terminal to know what video card is used for the backlight/brightness: ls /sys/class/backlight/ [[IMG]http://itsfoss.itsfoss.netdna-cdn.com/wp-content/uploads/2014/03/Screenshot-from-2014-03-20-220414.png[/IMG]]("http://itsfoss.itsfoss.netdna-cdn.com/wp-content/uploads/2014/03/Screenshot-from-2014-03-20-220414.png") As you can see, the output for me  is dell_backlight and intel_backlight. An indicator that the graphics  card in use is Intel. Another way to find out the graphics card would be  to go in **System Settings->Details->Graphics**. You can see the graphic card in use. If your graphics card is Intel, you can proceed with the fix below. [h=2]Fix brightness control issue with Intel card in Ubuntu 14.04 and Linux Mint 17:[/h] Open a terminal and create the following configuration file, if it does not exist: sudo touch /usr/share/X11/xorg.conf.d/20-intel.conf Now we need to edit this file. You can use any editor be it a terminal one or graphical. sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf Add the following lines to this file: [INDENT] Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection [/INDENT] Save it. Log out and log in back. The brightness control should be working through function keys now: [[IMG]http://itsfoss.itsfoss.netdna-cdn.com/wp-content/uploads/2014/03/Brightness_control_Ubuntu.jpeg[/IMG]]("http://itsfoss.itsfoss.netdna-cdn.com/wp-content/uploads/2014/03/Brightness_control_Ubuntu.jpeg")

---

### Post by Pasley on 2015-03-13
Oh my jesus thank you!

---

### Post by Pasley on 2015-03-13
Would you mind telling me what's going on there? I'm trying to learn more about linux, so any insight would help alot.

---

