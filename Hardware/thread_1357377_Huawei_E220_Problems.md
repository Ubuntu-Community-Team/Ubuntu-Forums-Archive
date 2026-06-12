---
title: "Huawei E220 Problems"
date: 2009-12-17
forum: Hardware
---

### Post by remush on 2009-12-17
Hi all,

I have a new installation of ubuntu 9.10 and have just tried my Virgin Huawei E220 mobile broadband device, and unfortunatly it did not work.

I get the following error message when I inserted the usb modem
------------------------------------
Unable to mount VIRGIN BROADBAND
Error mounting: mount exited wiht the exit code 32: mount:
block device /dev/sr1 is write-protected, mounting read-only
mount: /dev/sr1 alrady mounted or /media/BIRGIN
BROADBAND Busy
------------------------------------
This error message only presented itself once.

When I click
System > Preferences > Network Connections > Mobile Broadband Tab > ADD | my modem is not in the list.

I'm a beginer linux user so would appreciate some ideas as to why the modem does not work on ubuntu

---

### Post by moddie666 on 2009-12-17
Hello.

From what you psted, you can see that ubuntu tries to mount the device like a usb drive (because of an error in the Firmware). Since this is a modem that obviously cannot work.

I have found instructions on how to get it working in Karmic, however they are in German (my native language).

[http://linux.frankenberger.at/Huawei_E220.html](http://linux.frankenberger.at/Huawei_E220.html)

The simplest solution shown in there seems to be a firmware upgrade (for Huawei E220) that corrects this situation, but you may have to use windows for upgrading.

Hope that helps.

greetings
/moddie

---

### Post by garryknight on 2009-12-17
Your mobile dongle can be a broadband device or a storage device. If it's like my E220, it has a slot in the side for a micro-SD card. Ubuntu sees its storage device capability and attempts to mount it. There are utilities available that switch the dongle into broadband mode, such as ozerocdoff.

You might want to check out the vodafone-mobile-connect app which should work with your dongle provided that you know the default username, password, and APN for your provider. You can download the package and follow the instructions _**[here]("http://www.betavine.net/bvportal/resources/datacards/os/ubuntu")**_, then insert the dongle, wait a while, then run vodafone-mobile-connect and set it up and you should be good to go. The program will allow you to connect and disconnect, see upload and download usage, and also lets you send SMS messages.

---

### Post by swinb on 2009-12-17
I have an E220 on 3uk network and have had trouble getting it to work. The simplest solution that worked for me was to have the device plugged in as I booted the computer and then it seemed to recognize it as a modem. Bit of a newb myself and from looking around there are other solutions, but might be worth trying that first.

---

### Post by jjose on 2009-12-18
Hi ,

I need a veru urgent help.I am using Huawei E220 with Ubuntu 9.10.
I am trying to send AT commands to the modem and get response from the same.
I was able to obtain the same while I was using Ubuntu 7.0 (or a previous version).
I think to use AT commands the device should be configured in the right mode(flash device mode , I guess).Any idea about this problem.When I google for this I get lot of links to do the reverse of what I  want - converting to modem mode.

Can anyone hepl me with switching the modem to the right mode so that I can get response from the AT commands.

Anyone else with similar problems ?

PS: I think the network manager which helps to connect to the internet is blocking the device from responding to AT commands.


Thanks And Regards
Jose

---

### Post by uidb4056 on 2010-01-04
I have the same USB modem that worked flawlessly with previous releases but didn't work with Karmic x64 on my Lenovo W500 (kernel 2.6.31.16-generic). Found in Launchpad that this can be solved updating the firmware of modem this link will show you the way and includes a link on Launchpad with explanations ( [http://azizan.aiskosong.net/?p=458](http://azizan.aiskosong.net/?p=458) ).

I've switched to XP where the modem runs without problems, downloaded the firmware and applied it (only the firmware not the dashboard because Launchpad says is not necessary), after the update of firmware in XP I've checked if still runs on it and Yes! it still works and get as a side benefit that the connection now is at 7.2 GB instead of previous 3.6 GB.

Going back to Karmic again now at connection of the USB the internal disk is showed in desktop but , when starts the modem it was started OK but I was not able to navigate ...

Searching for a solution (apparently the problem was no DNS) I edited the wideband connection starting from terminal 'sudo nm-connection-editor' and in the Tab 'Adjusting IPV4' fill the field DNS Servers with the DNS used by XP and then this was solved.

I hope this can help

---

### Post by jdevora on 2010-01-05
Looks like a kernel problem that isn't able to reconize the E220 as a modem and as a mass strorage (with the windows drivers) at the same time 
I using  [http://www.techrecipes.net/linux/huawei-e220-on-ubuntu-9-10-karmic-koala.html](http://www.techrecipes.net/linux/huawei-e220-on-ubuntu-9-10-karmic-koala.html) as a work arround 


The open bugs for this problem:
  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)
  [https://bugs.launchpad.net/linux/+bug/464429](https://bugs.launchpad.net/linux/+bug/464429)
  [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/434477](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/434477)

---

### Post by uidb4056 on 2010-01-05
> **jdevora said:**
> Looks like a kernel problem that isn't able to reconize the E220 as a modem and as a mass strorage (with the windows drivers) at the same time 
I using  [http://www.techrecipes.net/linux/huawei-e220-on-ubuntu-9-10-karmic-koala.html](http://www.techrecipes.net/linux/huawei-e220-on-ubuntu-9-10-karmic-koala.html) as a work arround 


The open bugs for this problem:
  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)
  [https://bugs.launchpad.net/linux/+bug/464429](https://bugs.launchpad.net/linux/+bug/464429)
  [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/434477](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/434477)

If you apply the firmware update of the E220, then the mass storage is recognized and the modem works, the only problem may be you can still have is the proper DNS addresses that you can fix using my suggestion.

---

### Post by mohdshakir on 2010-07-06
The updated URL for the TechRecipes link is here:
[http://www.techrecipes.net/operatingsystem/linux/huawei-e220](http://www.techrecipes.net/operatingsystem/linux/huawei-e220)

---

