---
title: "Want to install Ubuntu"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by Krish002 on 2009-01-23
hello Friends,
i am using windows from last 10 yrs.
now i want to use Linux based operating system and i hav heard tht ubuntu is best for new users. 

i have already odered the DVD and got it via post.....
but befor installing i want some help bcoz i am very new user for it..........
actually i am afraid for unavailibility of drivers for ubuntu 
kindly tell me my system is compatible for ubuntu and how can i get drivers for my hardware my config is:

MOBO:ASUS Commando
CPU: ITEL C2D E6300 1.83 Ghz
RAM: Corsair TWIN2X2048-6400C4
GPU: Sapphire HD3870 DDR3 512MB
PSU: Cooler Master 500W
HDD: WD SATA 500GB(win XP is installed)
     and Samsung SATA 160GB(want to install ubuntu)

i have two drive, one drive has WIN XP and on another i want to install UBUNTU so kindly guide me for it how can i do tht,

any help will be widely appreciated.

---

### Post by Pumalite on 2009-01-23
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
Use the Alternate CD

---

### Post by Alnico on 2009-01-23
Before you start installing, ensure that you run a scandisk and disk defrag in Windows. Then back up all critical data.

Now try putting the Ubuntu Live CD and booting your PC from it. (You may need to enable booting from a CD in your BIOS if not already enabled)

Looking at your hardware, other than your graphics card, which may need separate drivers to be downloaded, all hardware should work perfectly.

After you run the Live CD, do the following:

1. Plug in a thumb drive & iPod - test and see if it works
2. Plug in a bluetooth dongle - see if the icon appears
3. Check the existing partitions (if you can view them). On the menubar, click **Places**, and then navigate to **Removal media**.
4. If you have any printers, scanners, or webcams, make sure they are Linux compatible. HP printers & scanners are generally Linux-compatible through HPLIP.
5. Check your internet connection.
6. Check your supported screen resolution


If everything is fine, look for the **Install** icon on the desktop. Go through the installation wizard screens, and then select your second disk to install Ubuntu when partitioning. 10 GB should be enough for you at the moment. (The more the better -- I have set it at 18 GB, which is more than enough for me).

One thing to remember; when partitioning, you need to set a swap space. Make sure you set it to twice the amount of RAM you have. If you have 2+ GB RAM, you can set the swap space equal to the amount of RAM. Since you have a lot of hard disk space, doubling the existing RAM won't be too costly for you. Note that once you set the swap space, that space on the hard disk is unavailable for data storage.

Installation shouldn't take you more than 10 minutes.

Note that there are several Ubuntu options available for installation. 
1. By desktop manager type (Ubuntu, Kubuntu, Edubuntu)
2. By bit (i386 - 32 bit & amd64 - 64 bit)
3. By functional type: (desktop vs server)

I would recommend that you go in for Ubuntu Intrepid Ibex (8.10) Desktop edition. The amd64 (x64) version should work fine on your hardware. I would recommend you use this version.

---

### Post by Sef on 2009-01-23
>  i have two drive, one drive has WIN XP and on another i want to install UBUNTU so kindly guide me for it how can i do tht,

Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by Krish002 on 2009-01-24
thanx friend ur help is widelly appreciated

i will sure try the suggestions provide by you guys. 
thank you,
sef, alnico, pumalite

one more quary i hav

my another HDD(samsung 160GB) i hav already prepare a portion(NTFS 30GB) for ubuntu can i directlly install ubuntu in it....
or i hv to repartition whole HDD again.............?

---

### Post by russu52 on 2009-01-24
direct ubuntu to install into that partition and to use it all. ubuntu will do the rest

---

### Post by Krish002 on 2009-01-26
thank you guys i didnt know tht in ubuntu forums one can get reply and help so soon and proper............thanx russu.........

alnico according to your suggestion i had try live CD

i can hear the sound and my resolutions are also higher but visual effect are not working so i think ubuntu require my graphics driver.

i can also see my two network connection but due to lack of my knowledge in ubuntu i cannot make internet connection.

in windows following things i m doing for setup my internet.

1) in the properties of local area connection i m giving the IP,DNS all those thing provided by my internet service provider

2) then i created the new connection (i do following in this)
  - connect to the internet
  - setup my connection manually
  - connect using a broadband connection tht require username   and password

kindly help me out how to configure internet in UBUNTU.........
 
and tell me if i hv to install my graphics driver then how can i do tht.

all ur warming support and helps are appreciated.

---

### Post by russu52 on 2009-01-26
for internet connection:

right click netwrok icon on top panel
select edit connections
on new window, click on dsl tab (last one on your right)
click add
on new window, type username, password.
give name to your service.
check box "connect automatically"
type your admin password and enable permanent store (allways allow) in keyring.

click on network icon
click on your service in drop-down list.
bingo!

hope it works for you

---

