---
title: "Wimax USB Shuttle Modem Driver not supported!"
date: 2010-11-11
forum: Hardware
---

### Post by 1R3N1CU5 on 2010-11-11
Hello, I'm new to this forum & not sure if this is the right section for such an issue. 

I've used Ubuntu for quite a long time, & at this point I've recently bought a new Wimax usb "Shuttle" modem as released by the provider "Qubee". At first when I bought it, I didn't realise the possibility that it might not be supported in Linux since every hardware I ever owned always worked perfectly on Linux. Therefore, at this point I'm quite disappointed & I'm not sure as to what steps I can take to solve the problem. 

When plugged in, the USB modem does not automatically power up. There's a particular driver that comes built in on the modem which has to be installed on a windows machine. Only through that software, the modem powers on & is usable. I did talk to a technical person from Qubee & they told me that Qubee currently support Mac & Windows version only & that they might develop one for Linux but that is uncertain.

If I didn't have this problem, I would have never switched to Windows except for the gaming part....& because of this problem I'm rarely able to use Linux these days :(

---

### Post by 1R3N1CU5 on 2010-11-26
Sorry guys, but doesn't anyone know of any solution to my problem? :[

---

### Post by ampc on 2010-12-28
I am having same problem...

I am working to find out the solution through virtual machine.

The idea is to run XP's virtual machine in linux and share internet betwenn virtual machine and linux..

But you will have to wait,

I will reply you soon.

Regards,
Abdul Mannan

---

### Post by 1R3N1CU5 on 2011-01-12
Thnx for replying...I thought no one would ever reply :(

Anyway, I know it can be run on linux through XP virtual box....but it is quite resource intensive & not ideal for running on laptops, etc.

Pls let me know if you find any solution, thanks!

---

### Post by ampc on 2011-01-13
Well... I am currently using internet in ubuntu through virtual machine method...
I will certainly inform you when I find a direct way to run internet in ubuntu...

---

### Post by KaYnemO on 2011-01-25
I am not sure this will help, but this is what I've done to get the wimax samsung "yota" jingle to work:

1. install madwimax from repositories:
```
sudo apt-get install madwimax
```
2. create a new file with rules:
```
sudo gedit /etc/udev/rules.d/60-madwimax.rules
```
3. insert the following code into the file and save:
```
# udev rules file for madwimax  supported devices
SUBSYSTEM!="usb|usb_device",  GOTO="madwimax_rules_end"
ACTION!="add", GOTO="madwimax_rules_end"

ATTR{idVendor}=="04e8",  ATTR{idProduct}=="6761", RUN+="//sbin/madwimax -qd  --exact-device=$attr{busnum}/$attr{devnum}"
ATTR{idVendor}=="04e9",  ATTR{idProduct}=="6761", RUN+="//sbin/madwimax -qd  --exact-device=$attr{busnum}/$attr{devnum}"
LABEL="madwimax_rules_end"
```
4. just in case - reboot.

If all works well the jingle should be detected automatically and it will initiate in a few seconds after you insert it.

Hope this helps.

---

