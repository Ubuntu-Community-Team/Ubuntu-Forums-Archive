---
title: "Hey !! help me as fast as you can ...please..."
date: 2010-02-02
forum: Hardware
---

### Post by pandeylavakesh on 2010-02-02
Hey !! folk ..
I am very upset due to a random error that crept in my system. What happend actually was that my system hanged up, I waited for a while and after that I SWITCHED OFF my laptop using POWER BUTTON. When I started by pressing power button then it is now showing the following message :

*Starting web server apache2
*Checking battery state ......done
*Swap: waiting for UUID = 8f0dfbcb-cd0f-4bdf-b257-37498f6a558.

After this, nothing happens. I left the system as it is for around half an hours thinking that perhaps it needs some time to recover but in vain. I would like to tell you that I am using UBUNTU 9.10 . I have tried my level best to give maximum required information but if you still need something to sort out this problem then you are welcome.One more thing : I am also having WINDOWS 7 installed in my laptop along with UBUNTU.
When I started UBUNTU in recovery mode I reached up to the Terminal like activities, where I was supposed to write some commands to do anything. So again I presses CTRL+ALT+DEL to restart and then it gets Started. But when I again Restarted the same problem persists. In a nutshell, I can say that after the RECOVERY MODE it is getting started, when I am Shutting it down then also it is getting started but whenever I am RESTARTING it after a fresh start the same error is again coming.
I would be grateful to you if you will suggest me some remedial activity for my system. 

Thanks [:smile:]

---

### Post by zwaardmeester on 2010-02-02
Try this: boot with an Ubuntu Live CD (or Live USB) and wait till it's finished loading. Go to "Places" and look for a disk which has the "etc" folder on it. This 'disk' is the partition of your harddrive where Ubuntu is on. Copy (or remember) the mount location of this partition, and open a terminal. The mount location will be something like /media/1EF49BF85CEF30C4 or something more readable. For now i will use this name, replace it with ur own one. 

**_Step 1_**
First backup the file /media/.../etc/fstab:
```
sudo cp /media/1EF49BF85CEF30C4/etc/fstab /media/1EF49BF85CEF30C4/etc/fstab_backup
```

_**Step 2**_
What you will do now is update the UUID of the swap partition in this file called 'fstab'. The correct ID you can find by issuing
```
sudo blkid
```
Look for the line with TYPE="swap", copy the UUID. 

_**Step 3**_
Open the fstab file by
```
gksudo gedit /media/1EF49BF85CEF30C4/etc/fstab
```
Look for the line
```
UUID=3da911ea-795d-4f5e-a5bf-51037496c9e3 none            swap    sw   
```

**_Step 4_**
Replace the UUID with the one found in step 2. Save the file and reboot normally (i.e. without live CD)

Did this help?

---

