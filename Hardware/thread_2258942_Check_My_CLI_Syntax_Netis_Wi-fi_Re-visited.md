---
title: "Check My CLI Syntax: Netis Wi-fi Re-visited"
date: 2014-12-31
forum: Hardware
---

### Post by Kurt_Alan on 2014-12-31
I am starting a new thread on an old problem that got buried, meaning many views, no solution, thread took a turn but, alas, no more views.

Can you find an error in my syntax? These are the directions from Netis Tech Support:

1,  unzip  XXX.zip    ——unzip files
   2,  cd  XXX          ——enter in unzip files
3      3,  sudo chmod +x ./install.sh ——provide the executable permissions for install.sh
   4,  sudo sh install.sh  ——compile driver
4&#65292;     5,  lsmod | grep name(adapter chip name) ——check if driver install successfully

Confirmation of numbers 1 and 3.  #4 is the critical command to execute driver compile but I am not getting it right: ```
 lucas@lucas-desktop:~$ cd /home/lucas/Desktop/rtl8812AU_8821AU_linux_v4.2.0_6952.20130315/
lucas@lucas-desktop:~/Desktop/rtl8812AU_8821AU_linux_v4.2.0_6952.20130315$  sudo sh install.sh
[sudo] password for lucas: 
sh: 0: Can't open install.sh
 
```

Can you suggest an alternative? What am I doing wrong?

---

### Post by schragge on 2014-12-31
First, I don't see the third step, i.e
```
chmod +x install.sh
```
Note that sudo is not needed for this step. OTOH, the way you call it doesn't require the file to have executable permissions.

The 4th step fails because there's no file named *install.sh* in there. The instructions you got are probably for an older version of the driver. What there *is* however is a Makefile. So the usual command sequence
```

make
sudo make install

```
should work. But don't rush to do it yet! I urge you to try commands from [this recipe]("http://askubuntu.com/a/491267") first.

---

### Post by Kurt_Alan on 2015-01-01
@schragge


Thank you for the most wonderful New Year's gift! After more than 20 hours trying to solve my problem, you gave me the solution: ```
sudo apt-get install build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd rtl8812au
make
sudo make install
sudo modprobe 8812au 
``` Well, OK, it was from askubuntu but you are the one who found it! My Ethernet Cat5 is UNplugged and I am up and running on my new wi-fi -- in less than five minutes!

Therefore, thread "solved"!

---

