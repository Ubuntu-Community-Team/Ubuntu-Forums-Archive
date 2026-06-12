---
title: "Nvidia Linux driver 550.120"
date: 2024-11-14
forum: Hardware
---

### Post by suprleg on 2024-11-14
Ubuntu 18.04, 4.15.0-213-generic, Z97 MB. Yes, I know it's older, but I can't upgrade further as it's a Team client machine with many non-duplicable stat reporting scripts. After installing the 550.120.run file, my RTX3070  and older GTX960 both go to 100% load and 100% fan speed and instantly  overheat to 90C+ as soon as my F@H client starts.
I've tried downgrading the driver by booting Ubuntu in recovery mode and  then using the root prompt to reinstall a downgraded driver. I've  updated the Nvidia driver many, many times over the years with no  issues. 
However, after trying every fix shown online, I'm still met with the initial driver install error:
ERROR: An NVIDIA kernel module 'nvidia' appears to already be loaded in your ke$
ERROR Installation has failed.
Any help would be appreciated.
Sorry if this is in the wrong sub-forum.

---

### Post by 1fallen on 2024-11-14
You only said you've updated many times before with run driver, but never mentioned if "you" ran the unistaller first, this has to be done before a down-graded version can be installed.

This has been a good method for myself but YMMV.
First you need the installation file. Then put it in your home folder, open a terminal and run:
```

sudo ~/installation_file.run --uninstall`
```

Then restart your computer and your drivers will be completely uninstalled.

Now you should be able to run the different nvidia version.

---

### Post by suprleg on 2024-11-15
When updating the Nvidia driver I've always switched to tty2 then: 
sudo service lightdm stop 
sudo service FAHClient stop
sudo apt-get remove --purge nvidia*
cd to .run file directory 
chmod +x .run file
./runfile
reboot
I don't use the ppa drivers I prefer the drivers provided by Nvidia.
At any rate, I repaired the kernel from the root recovery mode prompt, fixed several dependencies, and was able to downgrade the Nvidia driver version.
Thanks for the response.

---

