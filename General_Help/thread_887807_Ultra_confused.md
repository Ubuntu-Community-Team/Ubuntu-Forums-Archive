---
title: "Ultra confused"
date: 2008-08-12
forum: General Help
---

### Post by scoleshill on 2008-08-12
Hey all,

Since I've installed Hardy, I'm having more and more problems completely frustrate me and being new to Linux, I have no idea what to do.

1. I can't remove files from the trash bin. I could put them into the trash bin, but I can't  remove them to move them anywhere. 

2. The power icon on the top right corner has turned into a 'freeze everything forever' button. Once I click it to turn off the computer, nothing happens and all I can do is move the mouse around. 

3. I can't reinstall Ubuntu to start from scratch because the reinstall fails. It lists a lot of numbers that continuously count up and they all say 'SQUASHFS ERROR'.

I'm running a Centrino 1.7ghz, 100gb hd with 1gb of ram. Any help would be super appreciated.

---

### Post by Kralizec on 2008-08-12
1. I'm not quite sure what you're problem is, I may be able to help with more information.

2. I don't know how to fix the shutdown button, but you can run ```
sudo shutdown -P now
``` or ```
sudo poweroff
``` you can shutdown your computer, and ```
sudo reboot
``` restarts your computer.

3. If the reinstall is failing and you're receiving that many errors, you may want to check the disk for errors using the option in the live disk's menu.

I hope this helped some.

---

### Post by alzie on 2008-08-12
Check and see if you have gnome-power-manager installed. (its in synaptic)

When you click the red power button it seems to want to check with the power manager and if its not there it will wait a looong time for a response.  I uninstalled it as it seems to be more of a laptop thing but I ended up reinstalling it to get rid af the wait when shutting down.

I hope this helps

---

### Post by colobix on 2008-08-12
If you click one the power on/off button on your PC. Now you will b able to choose log out, change user, shut down etc.
A quick and nice way if you use a laptop. Now you can delete the power off icon from your panel.

But to me it seems like u got more then one simple problem with your linux. I suggest you format your pc and reinstall it again. SInce you are familiar with windows, I suggest you install windows and just run the linux live version for a few weeks.

---

### Post by lukjad on 2008-08-12
To remove trash files in Hardy Heron, sometimes you need to run this command.

Go to Application->Accessories->Terminal and type:

> sudo rm -r ~/.local/share/Trash/files/

---

### Post by linux_tech on 2008-08-12
If you click the power button (red button, far- right side) and it does nothing, it likely has something to do with power management. 

Can you click on System-> Quit?

Is this a laptop? 

Check to see if power management is disabled or not. System->Preferences->Sessions->Power Manager 
You may need to reboot also  
When you reboot go into your bios and check your power management settings there also.

---

