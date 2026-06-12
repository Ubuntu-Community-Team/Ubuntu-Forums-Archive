---
title: "Trying to get my internal WiFi card working"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by Cyber Akuma on 2008-04-12
I have a Toshiba Satellite A215-S7413 Laptop, according to Vista's device manager my WiFi hardware is a Realtek RTL8187B. However, it appears to internally be wired through the USB bus instead of the PCI bus. I am running Ubuntu 7.10.

Anyway, a few months ago I had tried using a linux-based driver somebody wrote, but after talking with posters here for a while, I was unable to get it to work, that thread is located here:

[http://ubuntuforums.org/showthread.php?t=680579](http://ubuntuforums.org/showthread.php?t=680579)

So now I am trying to go through ndiswrapper.

I found the drivers here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

It seems to be the only chipset on that page that does not have Linux drivers, lucky me :mad:

Anyway, I tried the Windows 98, Windows 2000, Windows XP 32, and Windows XP 64 (this is  64 bit version of Linux I installed).

All of them gave me the same error, the driver was installed but it thought the hardware was not present. ndiswrapper couldn't even use the vista drivers.

I remember hearing someone tell me that ndiswrapper is broken in 7.10 but I am not sure how true this is.

Does anyone have any advice on what I can do?

---

### Post by Tom--d on 2008-04-12
[http://ubuntuforums.org/showthread.php?t=708605&highlight=rtl8187b]("http://ubuntuforums.org/showthread.php?t=708605&highlight=rtl8187b")

This might answer your question :) 

With 64bit, use the 64bit driver.

---

### Post by Cyber Akuma on 2008-04-12
Thanks, i'll try that, however, I have a question.

In that post, you say to use the Windows98 drivers, however, in this post you say to use 64bit drivers.

64 bit drivers only exist for Windows XP and Vista.

---

### Post by Adreniline on 2008-04-12
Though I went through the trouble of finding the proper drivers for my card (Broadcom) - it still uses ndiswrapper (Downloaded Version 1.52) for my wireless card.

My drivers are installed, but the hardware is not recognized when I turn on my computer.  One thing that must be done each time after the computer turns on is the following commands:
> sudo modprobe ndiswrapper
sudo iwlist scanning

That command activates my wireless card and then scans for networks (it will output a long list of networks that are available).

I am then able to connect to my wireless network.

Maybe that will help you activate your wireless card.  You may also want to set it to 'always on' in the bios.

---

### Post by Tom--d on 2008-04-12
> **Cyber Akuma said:**
> Thanks, i'll try that, however, I have a question.

In that post, you say to use the Windows98 drivers, however, in this post you say to use 64bit drivers.

64 bit drivers only exist for Windows XP and Vista.

Try it with all of them as you are using 64bit and I don't know what will happen is you use the 32bit win98 driver. 

Try the 98 driver first and then do the same with the XP 64bit and if they dont work. Try the Vista64bit one. If they dont work. I dont know :S

---

### Post by Tom--d on 2008-04-12
> **Adreniline said:**
> Though I went through the trouble of finding the proper drivers for my card (Broadcom) - it still uses ndiswrapper (Downloaded Version 1.52) for my wireless card.

My drivers are installed, but the hardware is not recognized when I turn on my computer.  One thing that must be done each time after the computer turns on is the following commands:


That command activates my wireless card and then scans for networks (it will output a long list of networks that are available).

I am then able to connect to my wireless network.

He has a Realtek chip set. The driver for it is RTL8187B but for some reason, realtek only made the driver to recognise the ID: 8189 and others. But not ID: 8179 which is in Toshiba laptops (Which i have and now made it work :) )

---

### Post by Adreniline on 2008-04-12
I know.  I was talking about commands for ndiswrapper to turn the card on (should the drivers be installed properly).

I guess I misunderstood his first post.  I confused 'not present' with 'not working'.

---

### Post by Tom--d on 2008-04-12
> **Adreniline said:**
> I know.  I was talking about commands for ndiswrapper to turn the card on (should the drivers be installed properly).

I guess I misunderstood his first post.  I confused 'not present' with 'not working'.

I see :)

Yeah.. RTL8187B is annoying to set up but when it works. Its good :)

---

### Post by Cyber Akuma on 2008-04-12
Ok, I checked in Windows Vista first and my hardware ID is listed as 8197 so I tried adding that %RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200 line to the 64bit XP drivers.

Ndiswrapper listed the hardware as present and I saw a Wireless Settings avaliable.

Now heres the annoying part....

It can see every wifi network around me EXCEPT mine!

I enabled broadcasting and tried disabling my MAC filters and any security, it could see the networks of others around me but not my own. Every other WiFi enabled device and computer I have in my house (including this laptop while running Vista) can connect fine even when broadcasting is off and MAC filters and WEP security is enabled.

When I disabled roaming mode and tried to configure it manually, I could see two networks listed, somebody else's and a blank one with no name (No idea if this is mine that it's seeing or not).

Any idea why this is happening?

---

### Post by Tom--d on 2008-04-12
That was the problem I had. 

If you know your SSID and your encryption (if you dont have any, leave it blank) and Connection Settings as Automatic Configurations (DHCP)

Then it should connect, to make sure... open Network tools ( System > Admin > Network Tools) and on Devices go to Network device and click the one which is yours (Most likely wlan0) and check the IP of it. If they are not there.. reboot and try then. (it will automatically connect to your wireless within boot. Thats if the wireless drivers worked)

Free Roam just doesnt want to work. It lists the networks but doesn't connect to them.

---

### Post by Cyber Akuma on 2008-04-12
Free roam shouldent work anyway since I use WEP encryption though, plus I have a static IP.

I tried manually setting everything up, but I still got no connection.

One thing confuses me though, I am not sure if I should choose WEP hex or WEP ASCII, and if I should use my passphrause or KEY (I am assuming I should use WEP HEX and my KEY, but that didnt work).

---

### Post by Tom--d on 2008-04-12
The only way to find out is try all of them.

Also, is you SSID hidden?

---

### Post by Adreniline on 2008-04-12
Remember, Hex is 0 through F, so if you use any characters from G - Z, it's going to be ASCII

---

### Post by Tom--d on 2008-04-12
> **Adreniline said:**
> Remember, Hex is 0 through F, so if you use any characters from G - Z, it's going to be ASCII

Ah, never knew that. Thank you :)

---

### Post by Cyber Akuma on 2008-04-12
> **Adreniline said:**
> Remember, Hex is 0 through F, so if you use any characters from G - Z, it's going to be ASCII

I am well aware of that.

My passcode is a jumble of random alphanumeric characters but the keys it generated are all HEX.

Am I supposed to choose WEP ASCII and use the passkey or WEP HEX and use the key?

Also, I tried rebooting, now WiFi no longer appears under my network settings, even though the ndiswrapper gui still shows the driver as installed and the hardware as present.

---

### Post by Tom--d on 2008-04-12
> **Cyber Akuma said:**
> I am well aware of that.

My passcode is a jumble of random alphanumeric characters but the keys it generated are all HEX.

Am I supposed to choose WEP ASCII and use the passkey or WEP HEX and use the key?

Also, I tried rebooting, now WiFi no longer appears under my network settings, even though the ndiswrapper gui still shows the driver as installed and the hardware as present.

It should run at boot. There is a command for this. I will search for it.

---

### Post by Tom--d on 2008-04-12
add "ndiswrapper" to your /etc/modules file,
Code:

```
sudo gedit /etc/modules
```

remember to save the file.

That will load up ndiswrapper at boot.

---

### Post by Cyber Akuma on 2008-04-16
Sorry for not replying for the last few days.

Ok, here is where things get...... confusing.

When I first installed the drives, as I said, Ubuntu added a wireless option under my network settings, and I could see everyone's network, except my own, so the drivers were obviously working.

I tried installing drivers for my sound card, and edited my modules file to include ndiswrapper.

This is where things started to go bad.

At first my laptop would not boot into Ubuntu, it would hang at a black screen before the login screen.

After rebooting it worked, and I could see Wireless settings in the network manager, but if I dared to try to touch it, Ubuntu would basically go crazy. Nothing would work anymore, any application I try to open, it could say its opening it on the taskbar then nothing would happen, I coulden't even re-open the network settings, I coulden't even open the menu to shutdown or reboot my system and was forced to do a hard shutdown by holding down the power button.

After this what worked and what didnt in Ubuntu was hit-and-miss. Sometimes I coudlent even get the network manager to load (it would appear blank with no devices listed) and sometimes I could get as far as going into my wireless settings but when it tried to apply the changes I made it would go crazy again.

After rebooting, as long as I did not enter the network settings everything would work fine, it was only when I go into my network settings that it did this.

Soon, it would stop booting at all, it just hanged at a black screen before the GUI appears so I could enter my login info.

I rebooted into recovery mode and used VI (barely, I could never get the hang of that pp) to comment out ndiswrapper from my modules file, and Ubuntu booted fine.

I tried the Windows98 drivers (which are only avaliable as 32 bit) this time and commented ndiswrapper back, Ubuntu rebooted fine but wireless did not appear in my network settings.

I tried to re-install the 64 bit XP drivers but with these installed and ndiswrapper enabled in modules Ubuntu would no longer boot into the GUI.

Do you have any advice?

---

