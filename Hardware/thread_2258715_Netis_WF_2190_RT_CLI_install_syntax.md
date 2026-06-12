---
title: "Netis WF 2190 RT: CLI install syntax"
date: 2014-12-29
forum: Hardware
---

### Post by Kurt_Alan on 2014-12-29
When I do ```
 lsusb 
``` I get ```
Bus 003 Device 006: ID 0bda:8812 Realtek Semiconductor Corp.  
``` So I can see that my Netis USB adapter is recognized.

I have the choice of compile or install.  My choice is install.  I have the install.sh file.  Inside of this script I can see referenced 8192cu which I assume is the Realtek wi-fi driver. I don't know if this driver will be fetched from the internet or if it is already included in my install packet.

The Netis readme has lots of documentation on compiling and configuration but not one word on installation. The website recommends the Linux utility hardinfo.  Their tech support offers same advice. As far as I know, hardinfo has no install function but provides system information only.  Maybe hardinfo has some system information I need relevant to this driver install?

I need to take a stab at this problem.  I have all the parts, hardware and software, under my nose.  What would be the CLI syntax for installing this driver?

---

### Post by Frogs Hair on 2014-12-30
Support question, moved to*** Hardware.***

---

### Post by Kurt_Alan on 2014-12-30
I am still working on this problem.  I did some reading on procedures for running an install.sh  That included making it executable.
Then I sequestered my install.sh to Downloads along with my folder that includes the driver.  Then I pointed the install.sh to this folder: ```
  lucas@lucas-desktop:~/Downloads$ sudo ./install.sh rtl8812AU_8821AU_linux_v4.2.0_6952.20130315/
[sudo] password for lucas: 
```


The first thing I don't understand about the output is that it says that I must untar my tarball.  However, I have already done so. Isn't rt.click "extract" in the GUI the same as "untar" in CLI? There may be other errors but I'm thinking that If I can solve this one, some of the others may be solved too.
How can I resolve the untar issue? See following: ```
 ##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
./install.sh: line 17: cd: driver: No such file or directory
Decompress the driver source tar ball:
	
tar: Old option 'f' requires an argument.
Try 'tar --help' or 'tar --usage' for more information.
install.sh
rtl8812AU_8821AU_linux_v4.2.0_6952.20130315
./install.sh: line 25: cd: install.sh: Not a directory
Authentication requested [root] for make clean:
make: *** No rule to make target `clean'.  Stop.
Authentication requested [root] for make driver:
make: *** No targets specified and no makefile found.  Stop.
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
 
```

Just as a point of information, when I look at the contents of install.sh, it looks like these are the same steps that would be used to compile the driver manually, so does that mean that an install.sh script such as this is just a script that automates compiling that would otherwise be manual?

But, again, the main problem is: Why do I have to decompress the tarball if I have already extracted it?
Thanks for any help or suggestions. I'm itching to mark one Netis thread "solved."

---

### Post by Kurt_Alan on 2015-01-01
OP:

Solution by schragge: ```
sudo apt-get install build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd rtl8812au
make
sudo make install
sudo modprobe 8812au 
```

---

### Post by berlinblue on 2015-10-17
I just wanted to add the following to this topic: this method worked **PERFECTLY** for me!! 
Many thanks to those involved, presenting this solution! 

I got it instantly working with: **Linux Mint 17.2 Cinnamon 64-bit**.

Here's what I did / happened (as kind of a newbie to Linux):
[LIST=1]
[*]I plugged in the "netis WF2190" Wireless USB Dongle
[*]I opened a terminal and copy-pasted (Control + Shift + V) exactly the lines of code (and hit enter after each line), below "Solution by Schragge" (I didn't do anything more!)
[*]Then: A folder with the name "rtl8812au" was created in my Documents folder.
[*]And in meantime, the wireless adapter got recognized and started working: the wireless network got available (where it wasn't before).
[*]Finally, I deleted the "rtl8812au" folder from my Documents, as I don't want it to live there.
[/LIST]
**Many thanks again! **
Hope this might be of help, to any other "newbie". 

> **Kurt_Alan said:**
> OP:

Solution by schragge: ```
sudo apt-get install build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd rtl8812au
make
sudo make install
sudo modprobe 8812au 
```

---

