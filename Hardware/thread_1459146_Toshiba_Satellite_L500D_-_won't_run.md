---
title: "Toshiba Satellite L500D - won't run"
date: 2010-04-21
forum: Hardware
---

### Post by Kung! on 2010-04-21
I found that, by disabling ACPI/APM, I was able to get the LiveCD to run, although wireless would not run.  (Not worried about that - I can easily get it working later.)

However, once installed on my laptop, Ubuntu flat out will NOT start.  I've tried all the commands (acpi=off, noacpi, etc.) and regardless of what I do, it continues to stop @ some point, displaying nothing more than a bunch of lines of code (which I can and will post later if needs be).

Anyone have any suggestions?  I do know it's an Athlon 2.10GHz chip, with 2Gb of RAM, running the RTL8192 wireless card, as well as the Mobility Radeon 4100 video card.  Will continue researching to find the problem, but in the meantime would like some advice if at all possible.

---

### Post by Kung! on 2010-04-21
Ok, an update; while I get a WHOLE bunch of text, if I add the options:

vga=771 noacpi noapm

to the mix, at least now it'll go to a blank screen.  Obviously it's still hanging somewhere, but that changes things.

I CAN say that I think it has to do with the video, because simply adding noacpi/noapm to the boot options doesn't change anything, yet adding vga=771 does.

---

### Post by dabl on 2010-04-21
Toshiba makes their own disk drives and on my NB205 it uses aggressive power management which lets the drive "fall asleep" in the absence of user activity.  I think their Windows driver gives the hdd a poke ever so often, but with Linux, if you run in terminal mode and don't touch the keyboard (like when running updates), it will appear to freeze until I tickle the touchpad or the spacebar.

---

### Post by Kung! on 2010-04-21
I should probably have been a bit clearer.

I was, and am, trying to get the installation running on my laptop.  Have been 'around the block' a few times with Ubuntu, although I rarely post, due to the vast amt of information out there.

I had troubles getting the LiveCD to run at all, but once I used

xforcevesa noacpi

it booted just fine.

I then installed, and rebooted, and attempted to boot into Ubuntu from the hard drive for the first time - no joy.  I just get a lot of text.

If I use the commands

noacpi noapm vga=771

then instead of a bunch of text, I get a blank screen; but it still goes no further.

SO, I could get the LiveCD to run, but now that it's installed I cannot get it to boot.

---

### Post by Kung! on 2010-04-22
No one else has any suggestions?  I'm trying everything I know; but so far have been unsuccessful.

---

### Post by Kung! on 2010-04-22
Well, never mind.  LOL  For some reason, while using 'noacpi' froze the system, using acpi=off makes it work just great.  :)

---

### Post by 4jrpitts on 2010-06-20
I have the same problem with a L500D.  What exactly, step-by-step, with syntax did you do.  Nothing I've tried works and I am new to ubuntu.

---

### Post by Hogosha on 2010-09-03
I know this is a dead thread but I have used ubuntu on all of my past machines up until I purchased this (L500D.) Great machine but I cannot get any linux to run on it. Any help?

---

### Post by Vigh on 2010-11-11
Sorry to break the news to you, I also have this exact laptop and thanks to toshiba they have made it as linux unfriendly as possible, you cant even update the bios due to their stupid windows only bios updater, in my opinion its either use windows/or in my case have a $500 paper-weight sitting on the table. This computer is garbage!!! On the bright side at least my toshiba M800 portege works with linux.

---

### Post by Vigh on 2010-11-11
Guys! Guys! Its a miracle, I got it working perfectly, this exact model. Unfortunately you cannot install 64-bit OS due to a poor bios that is impossible to update without a windows install. Hence 32-bit OS must be used to prevent bios loop back errors and the screen locking up and the OS locking up etc. To get wireless networking working, just download the official driver from realtek from here- 

[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

I read a forum and found it extremely amusing seeing the incompetence of the company at providing customer assistance.

Installed using an Ubuntu USB drive.

Just make sure you download the appropriate driver from realtek- may be 8191SE or 8187SE, to check which one you have sudo lshw -short look for your wireless card and note the number. Cheers. Ant.

If you unfortunately have the Realtek 8187SE- follow these steps which originally come from this thread- [http://ubuntuforums.org/showthread.php?t=314352&page=3](http://ubuntuforums.org/showthread.php?t=314352&page=3)

*NOTE* Win98 Drivers can be downloaded from Realtek instead of extracted from a motherboard CD. Just dl windows drivers and following the guide.

8187SE Realtek Driver Setup
Originally posted by jck:
OK...there is good news...

I downloaded last night and burned the Kubuntu (I'm assuming Ubuntu will be identical/similar) 7.04 Beta 32-bit desktop distro.

I now have my system fully working, with WPA-PSK (WPA Personal) on a 54Mb/s encrypted connection and I'm using the latest Firefox for Linux.

My system uses:

Asus M2N32-SLi Deluxe Wireless Edition Motherboard with the Realtek 8187 chipset

Things you need to know/have before starting this process:
- Your router's ESSID
- Your router's MAC Address on your local network
- The channel your router is using
- Your original Asus motherboard CD

I will try and step you through this. Due to differences in hardware for network cards, wireless routers, etc., in different parts of the world, I can't guarantee that this will work for everyone. I am not a Linux guru, so I probably can't answer all the questions folks might pose. I hope this helps some/all of you with the same motherboard that I have.

Steps:

1) Download and burn a CD for the 7.04 Beta Desktop distro released 23 March 2007

2) Download and burn a CD for the 7.04 Beta Alternate distro released 23 March 2007

3) Go through the installer for 7.04 Desktop distro

4) Reboot into 7.04 Desktop from disk drive

5) Blacklist the built-in driver by editing /etc/modprobe.d/blacklist and add the following line to the bottom:

blacklist rtl8187

then save the modification and exit your editor

6) Insert the 7.04 Alternate CD into your CD drive

7) Cancel any default actions the operating system wants to assign to the CD

Start Adept (Menu->System->Adept Manager in Kubuntu) and do Manage Repositories option under the View menu

9) In the Software Sources window, choose the 2nd tab labelled Third-Party Software and click the Add CD-Rom... button at the bottom.

10) Adept should load the repositories that are on the Alternate Distro CD, then ask you to Update your repositories list.

11) When your list refreshes, scroll down and find ndiswrapper-utils-1.9, choose to Request Install, then click the Apply Changes button to install ndiswrapper.

12) Once you have ndiswrapper on your system, exit Adept.

13) Eject your 7.04 Alternate CD, and insert your Asus motherboard CD. Cancel any defaults that the Operating System wants to assign.

14) When it mounts and displays on your desktop, right click and Open the CD.

15) Navigate to the Drivers/Wifi/WIN98 directory, and copy the Netrtuw.inf and RTL8187.sys files.

16) Navigate to your home directory and paste the files there.

17) Open a terminal window.

1 At the terminal window, do the following:

ndiswrapper -l

You should have no drivers loaded

sudo ndiswrapper -i Netrtuw.inf

This should load the driver into ndiswrapper

sudo ndiswrapper -m

You might see some kind of message...but...it didn't affect me.

sudo depmod -a

This should work fine too.

19) Now, restart your install.

20) Once you have 7.04 up, login.

21) Open a terminal window.

22) Type ifconfig and confirm that "wlan0" is there. It should be.

23) Type iwconfig and confirm "wlan0" is there too. Mine was there, but it had no ESSID, no AP Association, and the channel/frequency was wrong.

24) Type the following commands to setup your wlan0:

sudo iwconfig wlan0 essid <your router's ESSID>
sudo iwconfig wlan0 ap <your router's MAC Address>
sudo iwconfig wlan0 channel <your router's channel>

25) Type iwconfig again and look at wlan0. You should now be getting signal strength and what not. At least, I did.

25) If the previous step worked, then do this: On your taskbar, go to the KNetworkManager icon, right click it, and choose your local wireless network. This should have the same name as your ESSID.

26) At this point, it should recognize your network and the proper encryption. You should have a place to enter your WPA password. Enter the ASCII password and Apply.


Wait and watch...my network came up...and...I am typing this article from my Firefox 2.0.0.2 browser in Kubuntu 7.04 Beta using WPA-PSK.

I will try to answer questions as I can.

This is a 32 bit distro that I am using. I will try to install 64-bit 7.04 beta to see if it works any better. If it does, I will post something this weekend.

My kudos to Ubuntu/Kubuntu/Edubuntu/Xubuntu. You are the first OS I have gotten to work with this (relatively) new hardware I have. I am very appreciative and will be trying to get as much of a donation together to send to show my appreciation.

Cheers

jck

Edit: I went ahead and did a /etc/networking/interfaces file from Wieman's examples at the article here

Don't know if it helps, but it might stabilize your connection

---

### Post by Vigh on 2010-11-12
FOR REALTEK 8187 users only
also for some weird weird reason, you need to make 2 network connections, for example if your SSID is NETWORK

you need to make 2 networks connections in settings

NETWORK0 and NETWORK both with correct passphrases

for some reason you need to add an additional digit on the end of the SSID

click connect to NETWORK0 as its connecting it will fail to fully establish, then click connect to NETWORK in the network applet on the top panel, your wireless will connect every time provided you have entered correct settings for your network, but unfortunately due to a bug in the hardware, you must manually do this every time u wish to connect to the wireless broadcast

NOTE- read on to see solution to this

---

### Post by Vigh on 2010-11-16
Auto-connect issue with the wireless network was solved by setting static IP addresses, inputting subnet mask, gateway and DNS manually. I now connect to the wireless network with normal default SSID/PASSPHRASE settings and it connects automatically first time, everytime.

---

