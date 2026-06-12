---
title: "Direction Explanation"
date: 2008-10-28
forum: General Help
---

### Post by sunkssss on 2008-10-28
Hello all...

I'm trying to follow a guide somebody posted (thread is now closed) but am having trouble understanding some of the terminology. Could somebody explain steps 8+9 to a noob?

> Newly installed Ubuntu 7.10 Desktop edition.
Wanted to install Nvidia 2-GeForce 8600 GT Drivers.
Downloaded driver from: [http://www.nvidia.com/object/linux_d...100.14.19.html](http://www.nvidia.com/object/linux_d...100.14.19.html)
Solution that worked out for me.
1. Log-in as normal user.
2. Then go to Terminal and type ‘apt-get install build-essential’.
3. Wait until it returns the prompt and no errors displayed.
4. Then press (without quotes) ‘Ctrl+Alt+F1’.
5. Screen will flicker and you will see command line.
6. Log-in as root.
7. Stop X-Server by ‘sudo /etc/init.d/gdm stop’.
8. Now cd to the location where the Nvidia driver is.
9. And run it as ‘sh driver-name’
10. It will ask to accept. Accept it.
11. Then it will say that no precompiled kernel found etc. and would you like it to download from ‘ftp…’
12. Say yes… and it should successfully begin the installation.
13. When finished type on the prompt ‘sudo /etc/init.d/gdm restart’.
14. For a moment you should see nvidia logo. It means you are successful.

---

### Post by FAJALOU on 2008-10-28
so you will want to change directory (cd) to where the driver is being stored.  so for example, if you save it on your desktop, it the command will be ```
cd ~/Desktop/<folder where the script is stored> 
```
Then you will want to start the driver name   so type in ```
 sh <name of driver> 
```  Of course, enabling the drivers through System>Administration>Hardware Drivers is always recommended.

---

### Post by alienprdkt on 2008-10-28
cd is change directory, so in terminal type
#cd /path-to-driver
#sh driver-name
(sh maybe a typo for su, if doesn't work try typing su)

---

### Post by sunkssss on 2008-10-28
Thank you very much for the clarification. I have tried enabling the restricted drivers, but performance was less than satisfactory.

---

### Post by sunkssss on 2008-10-28
Now I've run the command you gave me, but it's telling me that no such folder or file exists. I put the .run file in a folder named 'Driver' and typed the command as cd ~/desktop/driver but it's not working. Did I misunderstand you?

---

### Post by jerome1232 on 2008-10-28
I'm going to go ahead and nitpick but those instructions never made the file executable, and you will have to run the program as root to get it installed.

edit: seeing as you posted before I completed this, either your in the wrong folder, or it's because the file isn't executable try chmoding it as in my example. Make sure you answer yes to the last question about editing your xorg.conf

```
#after you have stopped the xserver and cd to where the file is
chmod +x name-of-intaller.run
sudo ./name-of-installer.run
```


If all goes to the pits and you can't get into a gui this command should get you back
```
ctrl+alt+f1
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```

---

### Post by sunkssss on 2008-10-28
I'm positive I'm in the right directory. It's in a folder titled 'Driver' on my desktop, so the path should be /desktop/driver

I suppose the file may not be executable, could you explain what you mean by chmodding it? For example I attempted chmod +x nvidia-linux-x86-100.14.19-pkg1.run but it still says 'No such file or directory"

Could there be an issue because I'm using 7.10 amd64?

---

### Post by jerome1232 on 2008-10-28
Ok I think what is happening is Linux is case sensitive so, Desktop is different from desktop, and NVIDIA-blah-blah.run is different from nvidia-blah-blah.run (you get me)

so the path should be 'Desktop/Driver'

```
cd Desktop/Driver
```

I know when you download nvidia drivers by default they start off with cap letters.

Auto-completion is your friend when in a terminal, hit tab once and if your command can be completed for you, if you hit tab twice rabidly in succsession it will list possible completions.

chmod changes the permissions of files, in Linux a file must be given permission to execute, it's not dictated by what the extension is.
chmod +x *filenamehere* is the command to give a file execute permissions.

---

### Post by sunkssss on 2008-10-28
Ah, case sensitive. That was the issue. 

But the point is moot, since it turns out the driver is intended for x86 platforms but I'm running x-86_64. Darn.

---

### Post by jerome1232 on 2008-10-28
Lol that's fine they have a 64 bit version on their website.

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) make sure you tell it 'linux 64-bit'

---

### Post by sunkssss on 2008-10-28
So it's telling me that I need to be logged in as root, but when I sudo -i and type my password, then attempt to run the same command cd ~/Desktop/driver it tries to go to /root/Desktop/driver when it should be /home/sunkssss/Desktop/driver

What's going on?

---

### Post by jerome1232 on 2008-10-28
Long explantion:

When you type sudo -i you become root, and your automatically taken to roots home directory, /root. In which the folder Desktop may exist but the subfolder Driver certanly doesn't. When logged into root you need to type the full path instead of the relevant path

```
cd /home/youruserhere/Desktop/Driver
```

Short answer:

Don't use sudo -i just preface the commands you need to run as root with sudo. That way your working directory doesn't get changed on you :)

---

### Post by jerome1232 on 2008-10-28
Maybe a better explanation, pwd returns you current directory

```
jeremy@direbane:~$ pwd
/home/jeremy
jeremy@direbane:~$ sudo -i
root@direbane:~# pwd
/root
root@direbane:~# exit
logout
jeremy@direbane:~$ pwd
/home/jeremy
```

---

### Post by sunkssss on 2008-10-28
Oh man, this is absolutely beautiful. I got it to work! Thank you so much for your help (Jeremy?)! Now if I can only get sound working  (see [http://ubuntuforums.org/showthread.php?p=6047943#post6047943](http://ubuntuforums.org/showthread.php?p=6047943#post6047943)) I will be set for years to come... I haven't felt this good about linux in a long time, so perhaps I'll even order a separate soundcard for my system if I can't get my integrated audio working. Thanks a lot!

---

### Post by sunkssss on 2008-10-28
Actually, there is one last thing. Somewhere during this process something happened to my GRUB menu, and it now shows  Ubuntu 7.10, kernel 2.6.22-15-generic (with a recovery below) BUt it also shows another Ubuntu 7.10 except this is kernel 2.6.22-**14**-generic (with recovery below) and then finally my XP Professional. This doesn't really make any sense to me, is this normal? I'm pretty sure it wasn't there before, however I may be mistaken.

---

### Post by sunkssss on 2008-10-28
Meh, upon reboot I'm only able to enter low-graphics mode. This might not be right after all. Maybe I should take a break, it's now 3 o'clock and I've got class at 8:30.

---

### Post by jerome1232 on 2008-10-28
Actually it's perfectly normal, basically whenever you get a kernel upgrade the system keeps the old ones around in case the new kernel breaks something, this way you can always fall back to your old kernel that works. I usually just leave them there, at the very least keep 2 to 3 kernels. They only use up a few megabytes a piece.

edit: Did you upgrade the kernel after you installed that nvidia driver? With nvidia's drivers you have to re build the driver after kernel updates, just stop the xserver and run their installer on the first boot into a new kernel like you did the first time.

---

### Post by sunkssss on 2008-10-28
Oh, that makes sense I suppose. So it doesn't matter which kernel I choose to start in? 

Also, could the reason Ubuntu keeps running in low-grpahics mode be because I let NVIDIA edit my x configuration automatically as opposed to manually? How would I know how to configure it?

---

### Post by jerome1232 on 2008-10-28
> **sunkssss said:**
> Oh, that makes sense I suppose. So it doesn't matter which kernel I choose to start in? 

Also, could the reason Ubuntu keeps running in low-grpahics mode be because I let NVIDIA edit my x configuration automatically as opposed to manually? How would I know how to configure it?

I think it's because you got a kernel update, with nvidia's installer you have to rebuild the driver when the kernel get's updated. If it fails again try using nvidia-xconfig and then rebooting
```
sudo nvidia-xconfig
```

Out of curiosity did you every try using envyng to install the latest drivers? It's much easier and doesn't have this particular draw back (rebuilding the driver every kernel upgrade) If you want to try it first uninstall the driver and return xorg to a default config

Steps to get rid of nvidia's driver, restore xorg to defaults, and use envyng to install the latest driver,
```
sudo ./nvidia-installer.run --uninstall
sudo dpkg-reconfigure -phigh xserver-xorg
#reboot
sudo apt-get install envyng-gtk
sudo envyng -g
# or if that didn't work right
sudo envyng -t
```

---

### Post by sunkssss on 2008-10-28
is that period before the /nvidia-installer.run --uninstall supposed to be there? the command is not being found.

nevermind, i was forgetting /Desktop/driver

actually, I just can't get it to work. Tomorrow I'll probably reinstall Gutsy and just try using ENVY per your advice. I've just had bad experience with ENVY, but perhaps that's because I was using it in Hardy and Intrepid.

This process has taught me a few things though, and every little bit helps, so thanks for your time.

---

