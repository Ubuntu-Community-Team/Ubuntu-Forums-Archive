---
title: "RTL8111/8168B fix script for ubuntu"
date: 2012-03-27
forum: Hardware
---

### Post by jaybutts on 2012-03-27
Using the Network Interface Card on my motherboard the RTL8111/8168B.

 I found I had network issues dropping packets often 100% and being disconnected all the time I found that this problem has been ongoing for awhile and the kernels from 2.6 to even 3.2 load the wrong module for some reason it loads the 8169 driver module.

   I have written a script to fix it for me and for you after each upgrade. Please spread the good word :)
[COLOR=RoyalBlue]
[/COLOR] [COLOR=DeepSkyBlue]**[COLOR=RoyalBlue]How to tell if you are effected by this bug:[/COLOR]**
[/COLOR] 
[COLOR=Red][B][COLOR=RoyalBlue]If the command 

```
lspci|grep r8168
```[/COLOR][/B][/COLOR][B][COLOR=RoyalBlue]

 returns the result -

 05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)[/COLOR][/B] 
[B][COLOR=RoyalBlue][U] 
[COLOR=Red]AND[/COLOR][/U]If the command 

[/COLOR][/B]```
**[COLOR=RoyalBlue]_lsmod|egrep "r8168|r8169"_[/COLOR]**
```**[COLOR=RoyalBlue]_[COLOR=Red]ALSO[/COLOR]  _returns only the the 8169 and not the r8168 kernel module.[/COLOR]**


Below is the stable version 0.1.1 [Release Date April 1st 2012] and it is tested for upgrades and new installs on ubuntu 11.10  and 12.04 BETA.

Instructions. 

Copy the script to a new text file
Save the file as 81681fixer.sh
go in a terminal to where you saved the file
run the file with this command:

```
 chmod+x 81681fixer.sh; sudo sh ./81681fixer.sh

``````

#!/bin/bash
is8168=$(lspci|grep 8168|wc -l);
isusing8169=$(lsmod|grep 8169|wc -l);
isroot=$(whoami|grep root|wc -l);
isblacklisted=$(grep r1868 /etc/modprobe.d/blacklist.conf|wc -l);

if [ $isroot -ne 1 ];
then
echo "You are not root please run 'sudo su -' or su before running this script";echo "script must be run as root";
exit 1;
fi
echo "Checking that you are root user";
if [ $is8168 -lt 1 ];
then
echo "Your NIC is not RealTek 8168 this fix does not apply to you";
exit 1;
fi
echo "Checking that your Nic is an 8168";


#####################################
##All error checks are good lets run the script
#####################################
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms &&
cd /usr/src/ && sudo rm -fr [r8168-8.028.00.tar.bz2]("http://r8168.googlecode.com/files/r8168-8.028.00.tar.bz2;"); sudo wget [http://r8168.googlecode.com/files/r8168-8.028.00.tar.bz2; ]("http://r8168.googlecode.com/files/r8168-8.028.00.tar.bz2;")
sudo tar -xjf r8168-8.028.00.tar.bz2;
cd r8168-8.028.00/;
sudo make clean modules && sudo make install;
if [ $isblacklisted -lt 1 ];
then
echo blacklist r8169 >> /etc/modprobe.d/blacklist.conf;
fi
sudo rmmod r8169;
sudo depmod;
sudo modprobe r8168;
sudo update-initramfs -u;
echo "fix installed successfully hopefully! :)";

```

---

### Post by jaybutts on 2012-03-27
I will test this soon as I have to upgrade my kernel already and make any fixes plus add some things like ping tests and uninstall option. There could actually be syntax error as I haven't even run it once.

---

### Post by ratcheer on 2012-03-27
Great job, I hope it works!

I also hope it will soon become moot, because my ethernet connection has been doing just fine with r8169 in the kernels used by Precise.

Tim

---

### Post by jaybutts on 2012-03-27
> **ratcheer said:**
> Great job, I hope it works!

I also hope it will soon become moot, because my ethernet connection has been doing just fine with r8169 in the kernels used by Precise.

Tim Well that is good to hear :)

---

### Post by ahendriks on 2012-03-27
> **jaybutts said:**
> Any suggestions or modifications are welcome.

isblacklisted=$(grep r1868 /etc/modprobe.d/blacklist|wc -l);



This line should be:

```

isblacklisted=$(grep r1868 /etc/modprobe.d/blacklist.conf|wc -l);

```

Am I right?

---

### Post by jaybutts on 2012-03-27
> **ahendriks said:**
> This line should be:

```

isblacklisted=$(grep r1868 /etc/modprobe.d/blacklist.conf|wc -l);

```Am I right?
Yep, thank you, fixed that.

---

### Post by ahendriks on 2012-03-27
Okay, furthermore:

> 
if [ $is8168 -ne 1 ];
then
echo "Your NIC is not RealTek 8168 this fix does not apply to you";
exit 1;
fi
if [ $isusing8169 -ne 1 ];
then
echo "Your nic is an 8168 but its not using 8169 driver, this fix doesn't apply to you";
exit 1;
fi

You mixed up is8168 and isusing8169? You should have an 8169 card and using a 8169 to apply the fix, am I right? You check if it is a 8168(!) card and using a 8169 driver. You should have a 8169 card and a 8169 driver... ?

---

### Post by ahendriks on 2012-03-27
Shoudn't the blacklist be done earlier in the proces... I believe so... dunno for sure...

Oh yeah, very, very, very good thread! Many thx if this works!

---

### Post by jaybutts on 2012-03-27
> **ahendriks said:**
> Okay, furthermore:


You mixed up is8168 and isusing8169? You should have an 8169 card and using a 8169 to apply the fix, am I right? You check if it is a 8168(!) card and using a 8169 driver. You should have a 8169 card and a 8169 driver... ?

Yes your right, I changed the 1's to 0's, this is how I originally had it but for some reason I changed it.

---

### Post by jaybutts on 2012-03-27
> **ahendriks said:**
> Shoudn't the blacklist be done earlier in the proces... I believe so... dunno for sure...

Oh yeah, very, very, very good thread! Many thx if this works!
hmm why do you think that? If we do it early then it will have blacklisted on a failed install.

---

### Post by ahendriks on 2012-03-27
Doesn't any of the other commands (depmod/modprobe/update-initramfs) need the blacklist?

---

### Post by jaybutts on 2012-03-27
> **ahendriks said:**
> Doesn't any of the other commands (depmod/modprobe/update-initramfs) need the blacklist?

I don't think so, thats for on boot only I believe, I could be wrong because I never build modular kernel, I am a gentoo guy for desktop before I switched to ubuntu recently. These are the commands I used in order and it worked for me to fix a fresh 11.10 install. I don't see why any of them would use it at all.

---

### Post by jaybutts on 2012-03-27
Hmm actually I think your onto something because I just rebooted and it loaded both modules, I will look into this.

---

### Post by jaybutts on 2012-03-27
Ok your right again it has to be done before the other steps, I have made it so it is done after successful compilation. We will just have to deal with it adding on failed installs in the uninstall or some other way. Thanks for your help.

---

### Post by martin1969 on 2012-03-28
Thanks for your help, but still getting the same problem as shown.


```
martin@martin-GA-870A-UD3:/usr/src$ tar -xjf r8168-8.028.00.tar.bz2
tar (child): r8168-8.028.00.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

```

---

### Post by jaybutts on 2012-03-28
> **martin1969 said:**
> Thanks for your help, but still getting the same problem as shown.


```
martin@martin-GA-870A-UD3:/usr/src$ tar -xjf r8168-8.028.00.tar.bz2
tar (child): r8168-8.028.00.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

```

It looks like maybe your download is failing, probably due to the bad network drives, what is the output of:

cd /usr/src;ls

try download  this file and putting it in /usr/src
[http://r8168.googlecode.com/files/r8168-8.028.00.tar.bz2]("http://r8168.googlecode.com/files/r8168-8.028.00.tar.bz2;")

---

### Post by jaybutts on 2012-03-28
Ok well I had some good testing opportunities today and found some bugs. I will be updating the script asap.

---

### Post by martin1969 on 2012-03-28
cd /usr/src;ls  

gives

linux-headers-3.0.0-12          linux-headers-3.0.0-17
linux-headers-3.0.0-12-generic  linux-headers-3.0.0-17-generic
linux-headers-3.0.0-16          nvidia-current-280.13
linux-headers-3.0.0-16-generic

When i try to extract to usr/src  it says i don't have enough permissions. All the r8168 files sre in the directory. The r8169 appears to be disabled but still next to the r8168 file in the same directory.

---

### Post by jaybutts on 2012-03-28
> **martin1969 said:**
> cd /usr/src;ls  

gives

linux-headers-3.0.0-12          linux-headers-3.0.0-17
linux-headers-3.0.0-12-generic  linux-headers-3.0.0-17-generic
linux-headers-3.0.0-16          nvidia-current-280.13
linux-headers-3.0.0-16-generic

When i try to extract to usr/src  it says i don't have enough permissions. All the r8168 files sre in the directory. The r8169 appears to be disabled but still next to the r8168 file in the same directory.

It looks like you are not root, type sudo su - 

This will give you a root shell, then run the script again. Make sure you are using latest version posted on first page because I have done updates periodically. I will solve for this error you experienced. Thank you for your feedback.

---

### Post by jaybutts on 2012-03-28
Ok I have made a lot of fixes on the original script to call it complete as it has been tested on multiple machines and by several people and all errors are resolved. I have posted that version to the OP, We will call this version 0.1, I wanted to finish 0.2 TEST today but it doesn't look like I will complete it. I will release this version soon which contains update, install, and remove options and better error checking w/ documentation and instructions.

I also need to work out the error martin experienced above. I think I can just have everything run as sudo so that you can just run the script with sudo like normal but currently you must run it from a real root shell and not sudo. Sorry I didn't think of that because I am a sys admin for a living I run around with root always.

---

### Post by fabiodasoghe on 2012-03-30
I tried this script and it cannot find the file /etc/init.d/functions
I get this output (my system is in italian language):

./fix-network.sh: riga 2: /etc/init.d/functions: File o directory non esistente
./fix-network.sh: riga 13: echo_success: comando non trovato
Checking that you are root user
./fix-network.sh: riga 19: echo_success: comando non trovato
Checking that your Nic is an 8168

I commented out the executing part after the checking...

EDIT: I decided to ignore this little error and execute your script. Now the network is working good!!! Great script, thank you so much!!

Hope they will fix this in the main distro/repository, is very very annoying...

---

### Post by jaybutts on 2012-04-01
> **fabiodasoghe said:**
> I tried this script and it cannot find the file /etc/init.d/functions
I get this output (my system is in italian language):

./fix-network.sh: riga 2: /etc/init.d/functions: File o directory non esistente
./fix-network.sh: riga 13: echo_success: comando non trovato
Checking that you are root user
./fix-network.sh: riga 19: echo_success: comando non trovato
Checking that your Nic is an 8168

I commented out the executing part after the checking...

EDIT: I decided to ignore this little error and execute your script. Now the network is working good!!! Great script, thank you so much!!

Hope they will fix this in the main distro/repository, is very very annoying...

On ubuntu you didn't have /etc/init.d/functions? Sorry if thats not in the main ubuntu, its on most distros and I added that after the ubuntu test where done, I just went ahead and removed it, it was only for the pretty green [OK] messages.

Thanks a lot for your feedback.

---

### Post by jaybutts on 2012-04-01
Ok just did a dist-upgrade to 12.04 and test my script 0.1 stable, worked flawlessly :)

Next kernel upgrade I will test and release beta 0.2

The problem is still there for my nic after an upgrade to the current version 12.04 after an upgrade from 11.10

---

### Post by ratcheer on 2012-04-01
> **jaybutts said:**
> 
The problem is still there for my nic after an upgrade to the current version 12.10 after an upgrade from 11.10

My 12.04 system is running well with the standard r8169 driver. Knock on wood.

I still have to install the Ralink rt3562sta driver for my wireless card, though.

Tim

---

### Post by jaybutts on 2012-04-02
> **ratcheer said:**
> My 12.04 system is running well with the standard r8169 driver. Knock on wood.

I still have to install the Ralink rt3562sta driver for my wireless card, though.

Tim

ah ok, tbh I didn't even attempt to let it run, I mean it is the wrong driver after all.

---

### Post by ratcheer on 2012-04-02
> **jaybutts said:**
> ah ok, tbh I didn't even attempt to let it run, I mean it is the wrong driver after all.

No, the entire time it has supposed to have been the right driver. The Linux kernel includes this driver with the intent of it working for these cards. I have seen comments in the kernel change logs to the effect that this or that was being fixed to work for the 8168 cards. This has been going on for several years, at least since 2007.

On Arch Linux, the r8169 worked with a couple of 3.1.x kernels, but in later revisions, it stopped working again. But so far, it has worked for me in all 3.2.x kernels I have used.

This has been a major pain for us, but I am hoping it will finally be gone.

Tim

---

### Post by martin1969 on 2012-04-03
Ive tried everything in this thread in multiple different ways and nothing works, is the r8169 driver now the one to go with?

I have r8169 blacklisted, but r8168 doesnt appear in the blacklist file.

I have r8168 in the directory and it says it is being used when i ask in the terminal which driver is being used.

Has someone sorted this out can you post the command line so i can try and rectify.

Cheers

---

### Post by ratcheer on 2012-04-03
Ok, in the terminal, run "sudo lspci -v". Post the output (just the section for the ethernet device). Near the bottom, there should be a line that says "Kernel driver in use: r8168".

Tim

---

### Post by martin1969 on 2012-04-04
THanks, here is the output and it says r8168 in use.



```
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 49
    I/O ports at 9e00 [size=256]
    Memory at fd8ff000 (64-bit, prefetchable) [size=4K]
    Memory at fd8f8000 (64-bit, prefetchable) [size=16K]
    [virtual] Expansion ROM at fd800000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
    Capabilities: [cc] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 03-00-00-00-68-4c-e0-00
    Kernel driver in use: r8168
    Kernel modules: r8168

```

---

### Post by ratcheer on 2012-04-04
Well, that is good. So, I am having trouble understanding why you don't have a connection.

I don't know what desktop environment and network control you are using. If you are using Unity and Network Manager, do you have a Network Manager icon at the top right of your screen? Is Enable Networking checked? If it is, is there a "Wired connection 1"? If yes to that, is there a Connect item under it?

It is hard to help you troubleshoot without being able to see everything. :confused:

Tim

---

### Post by martin1969 on 2012-04-05
I have wired connection 1 when i click on connect to wireless 1 the authentication box appears with my correct password in and i click connect and it then tries to connect without success before putting the authentication box up again, at which point i press connect and the process repeats.

This problem only happens with my PC, using the unity desktop.

I have connected my laptop to the same wired connection with no problem. 

I have wireless on the PC, when i try the connect to wired the wireless emblem stays on and starts pulsing as if it is searching for a wireless connection which it is not. In the past when i have switched to a wired connection from a wireless connection the symbol changed to a pair of arrows. This no longer happens.

In the drop down menu when i click the wireless symbol the wired connection 1 is highlighted but there is no connection symbol under it. I usually just click the wired connection symbol 1 and i am sure in the past this is all i have done.

---

### Post by martin1969 on 2012-04-09
It is fixed.

I updated to the latest ubuntu 11.10 OS version and the wired connection was fine. I updated to the latest kernal with no problems, and i am using the r8169 driver with no problems.

---

### Post by Vanish00 on 2012-04-09
I found this to be a great thread along with the post in thread

[http://ubuntuforums.org/showthread.php?t=1865436#postmenu_11372287]("http://ubuntuforums.org/showthread.php?t=1865436")
by Wildmann39

I mostly followed your script step by step. I did run into issues with blacklisting
I got permission denied even with using sudo, not sure why.
```
echo blacklist r8169 >> /etc/modprobe.d/blacklist.conf;
```

This worked for me to make the change.
```
echo 'blacklist r8169' | sudo tee -a /etc/modprobe.d/blacklist.conf
```


Thank you, glad to have the internet back to normal!!!

---

### Post by jaybutts on 2013-01-10
Thanks, this has been fixed since 12.04 release so haven't touched it since.

---

