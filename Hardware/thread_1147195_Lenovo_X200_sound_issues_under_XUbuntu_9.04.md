---
title: "Lenovo X200 sound issues under XUbuntu 9.04"
date: 2009-05-03
forum: Hardware
---

### Post by itsmine on 2009-05-03
I am using XUbuntu 9.04 with ext4 file system on my lenovo X200 notebook. However, there are two issues which are very annoying me.

First, the sound is mute by default, even I turn it on, it will mute automatically every time after reboot.

Second, the buttons of increasing and decreasing the sound volume are out of function. I must control the sound volume through the software.

Thanks for anyone who helps!

---

### Post by lhs2miler on 2009-05-05
Really new to ubuntu and I can't help.  I had a static issue soon after my install.....and I reinstalled and it works again.  I won't stick with this if the sound cuts off....let me know if you find out any solution.

---

### Post by itsmine on 2009-05-29
The problem is solved basically, although the sound control on the keyboard still does not work.

Please refer to this page: [https://answers.launchpad.net/ubuntu/+question/68564](https://answers.launchpad.net/ubuntu/+question/68564)

Thanks CyrusCT for providing the solution.

##### WORK-AROUND FOR AUDIO PROBLEM #####

1.) Manually adjust the mixer settings to something that is a good default for your audio needs. These settings will be loaded every time you restart your computer.

2.) Change the file permissions for /var/lib/alsa/asound.state to enable read/write access for the group/others (open the folder in Thunar, then right-click the file, select properties, and go to the Permissions tab). If you don't do this, then the next step will give you a permission denied error.

3.) Open up a terminal and enter the command "alsactl store" (without the quotes). This stores your mixer settings in /var/lib/alsa/asound.state for later use.

4.) From The Xubuntu/Xfce menu, go to Settings and open Sessions and Startup. Go to the Application Autostart tab and click the Add button.

5.) Enter the command "alsactl restore" (without the quotes) and the name and description of your choice. This causes the "alsactl restore" command to automatically run when you start your computer. The command restores you mixer settings from /var/lib/alsa/asound.state where you saved them earlier.

---

### Post by phoenixlipo on 2009-05-29
Hello,

I am considering installing a linux distro' on my X31, but I am unsure as to what is the best, even if there is a 'best'. I will be initially dual -booting it with Windows XP Pro SP3. My choices are Ubuntu, Xubuntu, and maybe Puppy Linux, but I think I get the impression that final option might be too basic. Although I'm not a Windows hater, I think I can decide what I want on an OS, without being saddled with a load of bloat I don't want - hence Linux. My main wish is to have faster, cleaner system that I configure to my needs without worrying about cocking up everything if I decide to remove certain applications I don't want or need, ala Windows! Your thoughts would be appreciated.

X31 2672 1GB RAM 40GB HDD X3 Ultrabase

thanks,

---

### Post by lhs2miler on 2009-05-29
> **itsmine said:**
> I am using XUbuntu 9.04 with ext4 file system on my lenovo X200 notebook. However, there are two issues which are very annoying me.

First, the sound is mute by default, even I turn it on, it will mute automatically every time after reboot.

Second, the buttons of increasing and decreasing the sound volume are out of function. I must control the sound volume through the software.

Thanks for anyone who helps!



Sorry, no help yet.....but my sound worked great after reinstalling.  I'm not sure what's up, but I don't think this issue effects most with the x200.  Doubt any difference between my tablet and your notebook.

---

### Post by James Paige on 2009-06-12
I have an X200. Sound playback seems fine, but I get a lot of clicks and static when I record sound from my microphone (which works well on another computer). Has anybody else had recording problems on this model?

---

