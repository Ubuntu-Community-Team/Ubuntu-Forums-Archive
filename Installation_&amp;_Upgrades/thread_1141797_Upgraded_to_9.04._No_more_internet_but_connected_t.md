---
title: "Upgraded to 9.04. No more internet but connected to router!"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by vjstar on 2009-04-28
Hi guys,

I upgraded from 8.10 to 9.04 today. Everything was working fine under my 8.10 install but once I updated to 9.04, everything internet related is not working anymore.

The problem is very weird because the wireless card is detected, I can connect to my wireless network just fine, even acess my router config page but once I try to browse a 'regular' webpage with Firefox it just says page cannot be found.

I tried to connect my laptop directly with a regular rj45 cable and it still gives me the same problem: I can connect to the router/wireless network, the router is connected to the internet but I can't access the internet with my 9.04 install.

What should I do to fix that?
Let me know as soon as possible! :)
Thanks!

---

### Post by vjstar on 2009-04-28
I really don't know what is wrong. The router gives my laptop an IP just fine. The router is connected to the internet. I am 99% sure it's a problem with ubuntu 9.04!

Man, I should have tested the version with the Live CD before upgrading! Someone please help me!

Thanks!

---

### Post by mattinblack on 2009-04-29
I have a wired connection to a cable router. I can use any live linux distro and it works fine. Have been using 8.1 for ages and has been fine. I upgraded to 9.04 and suddenly no internet, no FTP. Ping works fine with domain names so its not a DNS issue. All the Dynamic settings are ok - same in all distros.

I am tearing my hair out because I dont want to lose faith in Ubuntu but to have a live distro that works and then fails on install is really rather too much. I am typing this from an ancient live fedora boot cd!

---

### Post by upchucky on 2009-04-29
have you tried to bypass the router and connect the pc to the modem directly?

if this works then it is possible the router and modem have the same address

eg: my router uses by default 192.168.0.1
    my modem uses 192.168.0.1 by default

in this case i could talk to the router, but not connect to the internet.

I changed the router to 192.168.1.1 and got connected to the net.

I have seen where an octet has on a power failure gotten changed by one digit, this also causes no pages to load.

eg: 255.255.255 268

somehow that last set got changed to 267, i corrected it and it came to life.

you will have to check the information from your isp for the proper settings, get them working without the router first, then set up the router later.

the following are sample settings from an isp to be set up in a router, and/or browser.

yours will be different, but this gives you an idea on what to look for in the router and browser.

IP Address :  	 209.222.163.183
Subnet Mask : 	255.255.255.226
Default Gateway : 	209.222.163.261
Primary DNS Server : 	209.225.163.261
Secondary DNS Server : 	216.185.243.254

---

### Post by vjstar on 2009-04-29
> **mattinblack said:**
> I have a wired connection to a cable router. I can use any live linux distro and it works fine. Have been using 8.1 for ages and has been fine. I upgraded to 9.04 and suddenly no internet, no FTP. Ping works fine with domain names so its not a DNS issue. All the Dynamic settings are ok - same in all distros.

I am tearing my hair out because I dont want to lose faith in Ubuntu but to have a live distro that works and then fails on install is really rather too much. I am typing this from an ancient live fedora boot cd!

At least I am not alone in this situation!

**upchucky**: It is not an IP problem... all the ips are looking just fine.

I have no idea what's wrong... this is incredible! I never had such problem with any linux distro!

Someone please help!

---

### Post by npast on 2009-04-29
I am beginning to hate 9.04.  Before 8.04 worked just fine. Upgraded to 9.04 on my both laptops, and suddenly a bunch of problems. 

One problem: I am connected to internet, but the network manager applet says that there are no valid active onnections found.

when I click on 'edit connections' there is no any network list. How the hell am I connected then? and what happens when I take my laptop to work ? I won't be able to connect to the wireless network there -- this is just what happened to my other laptop. (in addition that laptop now has no sound with 9.04, but had sound with 8.04) these thing just annoy the hell out of me right now. Probably I will remove 9.04 and reinstall back 8.04

---

### Post by sir_nasty on 2009-04-29
perhaps I don't get it but.... dns issue possibly?  try some traceroutes, nslookups and verify your dns settings, possibly hardcode the dns instead of letting it just resolve through the router?

post results...

---

### Post by squeaksof2006 on 2009-04-29
I "upgraded" to the new Ubuntu today.  I'm really wishing I hadn't...  My Internet won't stay connected, either!  I don't know much about computers, I got put on Linux because it was supposed to be easier, not make it impossible to get my homework done!  My volume's also been having issues...  Any ideas?:confused:  I can't go on like this!!!

---

### Post by ToPazs on 2009-04-30
Same problem here. This is weird! I can access to Google sites fine but not others.

---

### Post by sir_nasty on 2009-04-30
> **ToPazs said:**
> Same problem here. This is weird! I can access to Google sites fine but not others.


THAT is DNS for sure.....  set your computer to a static ip and put in your ISP's DNS or at least add them.

instructions on how to do that found here:


[http://ubuntuforums.org/showthread.php?t=544383](http://ubuntuforums.org/showthread.php?t=544383)

---

### Post by pkrstillrules on 2009-05-01
The following worked for me.

Check your /etc/resolv.conf file. 

The domain to search is usually separated by blank spaces. But some
bug in NetworkManager may have introduced \032(which is ascii 
equivalent of spaces) to separate the domains. Once way is to manually 
edit the file and replace \032 with blan spaces and save it. 

dns resolution would work fine after this fix. Someone needs to fix it
NetworkManager.

---

### Post by kentcvk on 2009-05-05
I was upgraded my ubuntu 8.10 to 9.04, I can't connect internet when I changed my existing Linksys wireless router to Dlink wireless router modem. the network manager show it connected to the router, but I can't access internet and I am very sure the Dlink router was connected to internet,tried to fix the ip address, same problem. After I changed it back to Linksys routers, It can access internet...but can't access the Linksys config pages...really got no idea what is the problem:confused:confused:

---

### Post by WarrenKarl on 2009-05-05
Hi,

After upgrade to 9.04 Ubuntu does not recognize that I have a wireless card.
What should I do?
Any help would be appreciated.

---

### Post by mattinblack on 2009-05-08
> **vjstar said:**
> At least I am not alone in this situation!

**upchucky**: It is not an IP problem... all the ips are looking just fine.

I have no idea what's wrong... this is incredible! I never had such problem with any linux distro!

Someone please help!

I eventually fixed it. No its not DNS or anything else like that. It is an issue that is covered in the release notes - its the NETWORK MANAGER. This is different in 9 but for some CRAZY reason when you upgrade it is not always changed and you have to install the NEW network manager manually. Only problem is you CANNOT do this without internet access to do an apt get install.

I backed up my data onto a spare drive, used a Live distro to download and burn a new install cd for 9 (remember to point the download at an actual directory on your hard drive and not the desktop) then did a clean install. Works fine. 

Phew thats that off my chest, and after I recommended [ubuntu  here!]("http://www.bukisa.com/articles/48893_why-microsoft-compute-for-free-i-show-you-how") as well.
:guitar:

---

