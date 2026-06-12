---
title: "My Ubuntu is all screwed up!"
date: 2008-11-25
forum: General Help
---

### Post by iampriteshdesai on 2008-11-25
I installed Ubuntu today and tried to install Nvidia drivers using old .deb files there were 3 files one was of 7 mb other was of 5 mb. The installation went succesfully. But after restarting Ubuntu said it was going into safe graphics mode. I choosed the option of restore previous configuration. On restarting I get the login screen. After filling in my password and name I get the sound but nothing else. Only a brown colour like that of Ubuntu Forums. I used the old drivers from my kubuntu installation. they were only 1 day old.
__________________

---

### Post by decard_pain on 2008-11-25
well theres your problem..old.deb packages of nvidia drives will not work with the latest kernals.
you should have installed the driver using system->administration->hardware drivers.

you will need to remove that package and do the instalation of the driver as i've writen above..
hope this helps

---

### Post by iampriteshdesai on 2008-11-25
Those old debs were downloaded only one day ago in kubuntu

---

### Post by modemthug on 2008-11-25
Quick morning bump

---

### Post by heatblazer on 2008-11-25
My mom`s pc has nVidia GeForce 3 Ti and she is using ubuntu 8.04LTS. I just wanted to test the upgrade but it told me that my vga is too old for the drivers, so I cancelled. Just go and get newer vga. There are plenty for few bucks.

---

### Post by iampriteshdesai on 2008-11-25
> **heatblazer said:**
> My mom`s pc has nVidia GeForce 3 Ti and she is using ubuntu 8.04LTS. I just wanted to test the upgrade but it told me that my vga is too old for the drivers, so I cancelled. Just go and get newer vga. There are plenty for few bucks.

But I cannot even acess the desktop, there is nothing after the login screen. After answering proper password I get only a blank screen with brown color. no desktop

---

### Post by Coreigh on 2008-11-25
Which Ubuntu are you using? Ubuntu or Kubuntu? They aren't interchangeable.

You will need to remove the .deb's you installed and start over.
```
sudo dpkg --remove --purge <package.deb>
```
For each one you installed. (remove and purge may be redundant)

Then use the Hardware manger to install the correct nVidia drivers. In Ubuntu it is System >> Administration >> Hardware Drivers. You may also need to be sure 3-rd party sources are enabled for synaptic. System >> Administration >> Software and Sources. (Again this is Ubuntu)

To remove the packages, and hopefully restore the desktop to a basic display you can use an alternate tty. With the machine booted up press Ctrl+Alt+F2 this should take you to a terminal screen with only a login prompt. Type your user name and press enter, it asks for password, type the password but NOTE you will not see anything type, no dots or stars it just stays blank. Press enter and you should have a command prompt that looks like a terminal window. Remove your packages and then reboot.
```
sudo reboot now
```

---

### Post by iampriteshdesai on 2008-11-25
I tried but get some conflicts error. Then i installed dselect and uninstalled nvidia packages which i could find still gettin the same problem.
Nothing except the sound and the brown skin.
guess this is the last day on Ubuntu for me...

---

### Post by Coreigh on 2008-11-25
If the login screen looks normal the you know that the setup works and it is just improperly configured. Try using Ctrl+Alt+Plus ( Ctrl Alt + ) (Or Ctrl Alt - ) to scroll through different screen resolutions. You may be able to get to one where you can see the Application Menu and then access the Screen Resolution applet. (System >> Preferences >> Screen Resolution).

Also is there a mouse cursor in the login screen or after you have logged in?

---

### Post by mozkill on 2008-11-25
Once you get your Ubuntu configured you should always back up your configuration using CloneZilla  .   This will protect you from having to do a whole re-install.

---

### Post by iampriteshdesai on 2008-11-25
Yes I do get the mouse but the desktop doesnt load, There isn't any applications menu. Even Alt+F2 doesnt work.

---

### Post by iampriteshdesai on 2008-11-25
I'll try clonezilla later.

---

### Post by Arup on 2008-11-26
Hi Pritesh,

Nice to see you here, do you have Intel graphics on your system, specifically the G31 and above series? I have the same issue, after logging off and re-logging, the screen goes blank, I attribute this to the Intel xorg.

---

