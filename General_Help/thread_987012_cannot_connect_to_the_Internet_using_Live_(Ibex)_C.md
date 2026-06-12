---
title: "cannot connect to the Internet using Live (Ibex) CD"
date: 2008-11-19
forum: General Help
---

### Post by sadicote on 2008-11-19
I would not have posted a new topic, but I searched this forum exhaustively for a solution to my problem...

When I use the live CD, i get a "No Network Connection". When i try to edit the Network properties and put my IP address,etc. in the IPv4 fields, the OK button remains grayed out...

I am a first time user and have no idea of the command line, etc. and couldn't understand much from the resources that i could find.

It is my ambition to be able to use Linux, and the Linux console like a pro, and i have all the time in the world...

A reply would be greatly appreciated

---

### Post by tseligkas on 2008-11-19
First, the user interface of the 8.10 (Intrepid Ibex) network configuration window is different from previous releases, that's why you probably haven't found relevant issues in other posts.

The only way I have managed to replicate your problem (OK button disabled) is to have missing information from the IPv4 addresses field entry. You have to specify those in the window address, subnet mask & gateway.

For example, if you have the following, IP address: 192.168.1.2, netmask:255.255.255.0 & gateway: 192.168.1.1 you should complete the following:

```
Address      |    Netmask    |   Gateway
--------------------------------------------
192.168.1.2          24        192.168.1.1

```After you complete these, clicking OK should restore networking. If not, you may have to restart networking. I would tell you to restart your PC but you are using liveCD, so try to open a terminal and issue the following command:

```
sudo /etc/init.d/networking restart
```Let us know how it works out...

---

### Post by sadicote on 2008-11-19
Thank you for getting back to me so quickly; tried editing the eth 0 settings and put 24 instead of 255.255.255.0, "OK" button still remained grayed out, so I opened a terminal and typed out the command you provided, got a 'Reconfiguration Started' and 'OK' in the terminal, but the OK button on the editing eth 0 menu did not turn green:confused:

---

### Post by sadicote on 2008-11-20
Same problem even after dual boot installation.

---

### Post by tseligkas on 2008-11-25
Sorry for the late reply.

I did a little search for you. I found **[this]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/273205")**. Also, check if there is something you miss-typed or entered wrong in other tabs.

You can provide a screenshot of the said problem to us if you want (hit the PrtScn button of your keyboard).

---

### Post by sadicote on 2008-12-03
Hi, I have uploaded my screenshot as advised. The problem persists even after I have typed out the complete IP address and clicking Add. OK button remains grayed out, as soon as i have typed out address and clicked add, it shows a blank, same with Netmask and Gateway. Also, what do i put in 'Search Domains'

---

### Post by deadowl on 2008-12-03
You're supposed to click add and then type your IP address and subnet mask out on the list thing.

---

### Post by sadicote on 2008-12-03
> **deadowl said:**
> You're supposed to click add and then type your IP address and subnet mask out on the list thing.

I did, i clicked add and then typed out my address, then clicked add again to type the Netmask, and the previously typed address field showed a blank....

---

### Post by sadicote on 2008-12-03
Sorry to be a pest, but maybe my screenshot of the 'sudo /etc/init.d/networking restart' command output will be of some help...

---

### Post by deadowl on 2008-12-03
> **sadicote said:**
> I did, i clicked add and then typed out my address, then clicked add again to type the Netmask, and the previously typed address field showed a blank....

You don't click add a second time for the netmask, you click to the right of the IP address field, below where it says "netmask" across the top.

---

### Post by sadicote on 2008-12-03
Sorry, that was incredibly stupid of me, but still no-go..also, i have no idea what to put in Search Domains

---

### Post by deadowl on 2008-12-03
Are you migrating from a different operating system in which the internet connection worked?

---

### Post by sadicote on 2008-12-03
No, I have dual boot installed with Wubi

---

### Post by tseligkas on 2008-12-03
1st: The first screenshot you attached in thread is bad. It doesn't show the addresses table, hence the confusion of deadowl. The last screenshot seems correct.

2nd: The /etc/init.d/networking restart command line output is reasonable. Since you haven't managed to configure fixed IP address it tries using DHCP to bind an address for you.

3rd: Remove/clear the IP addresses from and close any open Network Connections windows. From a terminal sudo open the /etc/network/interfaces file. Delete auto eth0 and iface eth0 lines and type the following:

```
iface eth0 inet static
address 192.168.19.123
netmask 255.255.255.0
gateway 192.168.19.1

auto eth0
```Then issue a sudo /etc/init.d/networking restart and see if it works. If it doesn't post the output here.

4th: You don't need to type search domains.

---

### Post by sadicote on 2008-12-03
You are really having to spoon feed me on this one,i know..my acquaintance with PC's, let alone Linux, is just about a year and a half old.

---

### Post by deadowl on 2008-12-03
Fell asleep. Does the internet work under Windows?
If it does, start up using Windows, and when your start menu is up and everything, do the following:
Open the start menu
Select Run
Type "cmd" in the bar (less quotes) and press enter
Type ipconfig in the command prompt and press enter
Post the output here.

---

### Post by sadicote on 2008-12-03
:D Me too, and booted in Ubuntu as soon as i got up, and there it was, "network connected", more beautiful words were never written. And yes, i did go to ipconfig and checked, the values are as i wrote them, thanks, and my apologies to tseligkas for posting without rebooting first.:D

---

