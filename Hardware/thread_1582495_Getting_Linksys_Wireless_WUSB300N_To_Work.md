---
title: "Getting Linksys Wireless WUSB300N To Work"
date: 2010-09-26
forum: Hardware
---

### Post by Llama Drama on 2010-09-26
Hello, I'm new to ubuntu, and don't know much... but I just recently installed it on my PC. Now, I'm trying to get my WUSB300N wireless usb adapter to work for me so I can go on the internet. I already tried using this method posted a while back > Welcome to the Ubuntu Community! 

You don't need to put that tar file in /opt/ndis. Just put that WUSB300N.tar file in your home directory somewhere, say in Public. Then at the command line, navigate to your public folder and untar the file:
Code:
cd ~/Public
tar xvf WUSB300N.tar
Un-tarring that file will create a "Drivers" directory in the Public folder with your Windows drivers. You need to make sure you have both the ndiswrapper-common and the ndiswrapper-utils-1.9 installed to use ndiswrapper:
Code:
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
After that, just install the Windows driver:
Code:
cd ~/Public/Drivers
sudo ndiswrapper -i netmw245.inf
sudo modprobe ndiswrapper
After that, open up your network manager and see if you can find any networks, and try connecting to them. Let me know if you have any problems with the directions above. but it didn't work. Whenever I go to connect, it just keeps saying its connecting and never ends. Also when I go to click on the wireless icon at the top bar, it freezes me up and I have to manually shut down. What should I do? I installed ndiswrapper-common and ndiswrapper-utils 1.9, I'm running ubuntu 10.04 Lucid Lynx.

---

### Post by Llama Drama on 2010-09-26
I forgot to mention it keeps freezing now everytime I startup and it doesn't connect. The time updates but everything else is frozen...:confused:

---

