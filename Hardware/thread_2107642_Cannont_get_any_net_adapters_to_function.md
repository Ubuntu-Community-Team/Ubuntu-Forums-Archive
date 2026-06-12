---
title: "Cannont get any net adapters to function"
date: 2013-01-22
forum: Hardware
---

### Post by Landon1976 on 2013-01-22
0     down vote          [favorite]("http://askubuntu.com/questions/246199/both-internet-adapters-cannont-be-installed-cannont-connect-to-net-cannot-comple#")            
                                     I am using Ubuntu LTS 12.4 64bit I have a WNDA3100v2 USB netgear  adapter that despite the myriad of help suggestions cannot be used unless connected to the Net to get packages  although, I downloaded some I cant install ANY beacause prerequisite issues, cant even get synaptic or any other package because it is not  included in the install .iso. My Lan wired adapter happens to be a  AR8161 Atheros that is also unsupported? so i cant use that route to repair the first adapter. AND that is second problem that needs to be fixed as well.  I have spent 2 days reading posts and downloading files and trying to use ndiswrapper with no luck (it does recognize that usb drive is inserted tho just wont turn it on) amazingliy enough the constant in this forum is "you must be connected" or simply sudo apt-get???  I concede that maybe im missing somthing... I am baffled as to how this  can be done though. I am patient and learning this is my first duel boot (both  adapters work when I boot in win 7) admittedly like most people new to  Ubuntu I am a little confused by the console commands but I seem to be  handling on my laptop which loaded Ubuntu 12.4 64bit with ease :) SO... if  anyone is willing to take the time to assist me I would be very pleased. I  should say the the atheros DID read in the terminal as AR8161 that’s  how I got the information. I am on a laptop next to the desktop i am  asking about so i can post some code if you guide me as to what info is  needed. Thank you in advance :)

---

### Post by Landon1976 on 2013-01-23
I should have named this post somthing different perhaps... (this is was my first post in these forums) I should have titled it "AR8161 Atheros/WNDA3100v2 Not working"

---

### Post by Yellow Pasque on 2013-01-23
Well, you can install the wireless backports package, (grab it using Windows or an updated LiveCD/USB where your adapter works out of the box). [http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller/210466#210466](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller/210466#210466)
You'll have to figure out which version matches your kernel: [https://launchpad.net/ubuntu/precise/+search?text=linux-backports-modules-cw](https://launchpad.net/ubuntu/precise/+search?text=linux-backports-modules-cw)

It would really be easier to use Ubuntu 12.10 for such new hardware..

---

### Post by Landon1976 on 2013-01-25
> **Temüjin said:**
> Well, you can install the wireless backports package, (grab it using Windows or an updated LiveCD/USB where your adapter works out of the box). [http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller/210466#210466](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller/210466#210466)
You'll have to figure out which version matches your kernel: [https://launchpad.net/ubuntu/precise/+search?text=linux-backports-modules-cw](https://launchpad.net/ubuntu/precise/+search?text=linux-backports-modules-cw)

It would really be easier to use Ubuntu 12.10 for such new hardware..
I will look into the live cd option you suggested. Thank you for the idea :) as for the 12.10, I considered upgrading however all the 12.10 users are experiencing the same hardship that I am.  I am all most exhausted with attempts (but still motivated) also i ordered a new USB wireless adapter that i researched on the supported hardware and bought one ($18.99) that users claim works out of the box on 12.4 LTS.  I am embarased that it came to that however I dont want to abandon Ubuntu before i even get a chance to use it on my desktop.

---

### Post by Landon1976 on 2013-01-25
> **Temüjin said:**
> Well, you can install the wireless backports package, (grab it using Windows or an updated LiveCD/USB where your adapter works out of the box). [http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller/210466#210466](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller/210466#210466)
You'll have to figure out which version matches your kernel: [https://launchpad.net/ubuntu/precise/+search?text=linux-backports-modules-cw](https://launchpad.net/ubuntu/precise/+search?text=linux-backports-modules-cw)

It would really be easier to use Ubuntu 12.10 for such new hardware..
ok great. This may work for me. I found out that my Kernel is "3.2.0-29-generic" however on the page you linked (thank btw for the link, very convenient) i see these choices... [linux-backports-modules-cw-3.3-3.2.0-29-generic]("https://launchpad.net/ubuntu/precise/+package/linux-backports-modules-cw-3.3-3.2.0-29-generic"):,          [linux-backports-modules-cw-3.4-3.2.0-29-generic]("https://launchpad.net/ubuntu/precise/+package/linux-backports-modules-cw-3.4-3.2.0-29-generic"):,[linux-backports-modules-cw-3.3-3.2.0-29-generic-pae]("https://launchpad.net/ubuntu/precise/+package/linux-backports-modules-cw-3.3-3.2.0-29-generic-pae"):[linux-backports-modules-cw-3.4-3.2.0-29-generic-pae]("https://launchpad.net/ubuntu/precise/+package/linux-backports-modules-cw-3.4-3.2.0-29-generic-pae"): and here is my next question. What is the first number and how do I know which to use? all 4 of these have my kernel number included but 3.3 or 3.4? Also, two of the choices are followed by "pae" cn=ant wait to hear back from you. [Temüjin]("http://ubuntuforums.org/member.php?u=327594")

---

### Post by Yellow Pasque on 2013-01-25
You want this package then: [https://launchpad.net/ubuntu/precise/+package/linux-backports-modules-cw-3.4-3.2.0-29-generic](https://launchpad.net/ubuntu/precise/+package/linux-backports-modules-cw-3.4-3.2.0-29-generic)
Once you have net connection, you install the linux-backports-modules-cw-3.4-generic package so that when you upgrade kernel, appropriate wireless package is automatically pulled.

---

### Post by Landon1976 on 2013-02-01
Ok first, let me say thank you for your help so far.  I am tugging on your sleeve once again and hoping that you have some patience left for me. I am using the temporary net adapter that i bought with this install now and the kernel was upgraded
( uname -a  :   3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux )

Still the WNDA3100v2 does not work.

I looked for the backports you suggested with the new kernel and I see this message "WARNING: the "linux-backports-modules-cw-3.4-3.2.0-37-generic-pae" package was deleted from this repository"

I now have ndiswrapper installed and will continue to search the forums for a driver that works with 64bit OS. If you still have some more advice for me I am open ears.

---

### Post by Landon1976 on 2013-02-08
Ndiswrapper loads the correct driver based on the device code and the devices shows up and the connection is configurable however it never connects to the network. After my passkey is entered it just attempts connection for about 3 minutes then asks aagin for network key :( 
I feel like i put so much effort into this issue i am frustrated. Its been weeks. I even bought a new adapter for temp use but i have to swap adapters depending on which boot choice i make. Really feels like a Poor solution I shouldn’t even use that word. I am still viewing this post for suggestions if anyone has got this adapter working please leave me a note . 
I know a lot of you 32bit users are working with it fine but again im using Ubuntu 12.4LTS 64bit and i cannot use my Netgear WNDA3100v2. for those of you wondering why I am using that adapter it is because I also have the netgear N600 router with duel bands  to match these adapters. I also use the same adapters in 2 other computers. furthermore do not expect to connect to the second band under Ubuntu (it doesn’t even show the second band when displaying list of networks).  I would be happy if i could just connect the one band to my encrypted network.

PS for now I have given up on my second problem in my original post. Ubuntu does not work with my internal Atheros LAN card embeded in my asus motherboard P8H77-v when connected via cable :( I happen to have the 2 devices that do not function with Ubuntu. It is a challenge to overcome but ill focus on the wireless now and continue using the Buffalo adapter i bought as a temporary solution

---

