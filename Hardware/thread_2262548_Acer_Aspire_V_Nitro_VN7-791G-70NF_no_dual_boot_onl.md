---
title: "Acer Aspire V Nitro VN7-791G-70NF no dual boot only Ubuntu"
date: 2015-01-25
forum: Hardware
---

### Post by motar2 on 2015-01-25
I am ready to purchase this laptop and will like to know if anyone has info regarding compatibility.    I read some reviews were the users are very happy as far as hardware compatibility, but also read some questions about some issues if you only want to run Ubuntu and not dual boot.  It seems the there are some problems with the UEFI and Windows 8.1.  I will appreciate any help.

---

### Post by weatherman2 on 2015-01-25
My Acer AO756h has UEFI and dual boots Windows 8 and Ubuntu 12.04.  However, I never managed to get Grub to boot Windows.  Instead, I hit the F12 key when restarting or starting the computer, and then I can choose either Windows 8 or Ubuntu.  I rarely boot into Windows at all, though.

Of course, that Acer you are considering may differ from mine.

At worst, you could install Windows in a virtual machine (like Virtualbox) within Ubuntu.  But you'd need a Windows license - product key - to do so, and I'm guessing you can't use your Windows 8.1 license from the laptop itself (no more product key labels) unless someone has figured out how to have the virtual machine Windows see your UEFI/BIOS to know it is licensed without entering in a product key.  If you have say an older Windows 7 computer laying around with a readable product key sticker on the bottom, you should be able to install Windows 7 in a virtual machine with that key, if you can live with Windows 7 not Windows 8.1.    I find it more convenient to start up a virtual machine anyway instead of re-booting just to do some Windows task, but not everything in Windows will work in a virtual machine.

---

### Post by motar2 on 2015-01-26
Thanks for the info  weatherman2, I have been off win for over 8 years, so I don't really use it at all, seems that the linux community was right all along when the criticizes the hardware lock to Win MS.          It just seems to me not quite right, that we purchase a PC and are force to use a specific OS, the PC specs are suppose to be and open specification standard.    Well not much we can do, apart from some hacking the software or hardware.

---

### Post by motar2 on 2015-01-28
I just like to let people know that I am a very happy chap this morning. :-)

The above laptop works great with Ubuntu, no need to keep win8.1.

After lots of reading about UEFI, (did not want to end up with a brick) particularly this explanation from a blog.
[https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

Decide to go ahead and wipe win 8.1 completly, and set my Ubuntu as I usually do with 3 partitions, swap, system and home, in this case also needed a new UEFI partition, which the installer will warn you about if you forget.
The system so far works  really well as far as my needs are concern.
So if you have a new Acer laptop and want to wipe win 8.1, you should have no problems, you do need to disable secure boot, but that’s about it.
Fantastic work the Ubuntu developers, thanks a lot for you work.

---

### Post by risto-mononen on 2015-02-22
Thanks for the info motar2! I am planning to buy the same and wanted to check beforehand.

---

### Post by Khisanth_ on 2015-04-05
Hi, I just want to share that I have managed to run my windows in VirtualBox. 
Just make a copy of windows drive:
sudo dd if=/dev/sda of=/media/ubuntu/data/dd_sda.img
convert it to VirtualBox hdd:
VBoxManage convertfromraw /media/ubuntu/data/dd_sda.img /media/ubuntu/data/Win8.vdi
And then create VirtualBox machine using Win8.vdi drive

That's it.

PS
I have deleted the original Windows partitions but kept dd_sda.img as a backup.

---

### Post by Johan_Wikman on 2015-08-08
Did you have to do anything specific to get the wifi working? I just installed Ubuntu 15.04 and everything else but for wifi seems to work.

---

### Post by Marco_Cestonaro on 2015-10-17
Same Problem here... any news on that? (Bluetooth and wifi doesn't work [qualcomm atheros ar5bwb222 wireless network adapter seems to not work with ubuntu])

---

### Post by tonip2 on 2016-04-18
I guess both Johan and Marco have fixed the issue, but just in case and since I got here looking for a sollution to the same problem, you can try this:

[http://askubuntu.com/questions/66142...s-168c003e-dev]("http://askubuntu.com/questions/661424/ubuntu-14-04-wireless-not-working-no-network-interface-atheros-168c003e-dev")

---

