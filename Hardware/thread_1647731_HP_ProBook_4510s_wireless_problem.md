---
title: "HP ProBook 4510s wireless problem"
date: 2010-12-17
forum: Hardware
---

### Post by WlaadDyaab on 2010-12-17
Hi

I know that there are some problems that have been solved on this forum, related to this Broadcom wireless card problem as soon as Ubuntu is installed

I decided to change to Kubuntu a couple of days ago but I wasn't successful at all in figuring out how to solve the wireless headache at the beginning

I decided to change back to Ubuntu 10.10

I already had the wireless issue solved since I done an upgrade from Ubuntu 10.04 LTS to Ubuntu 10.10 when it first came out. But now it's simply hard to solve with Ubuntu 10.10

I downloaded Ubuntu 10.10 and I'm currently exhausted from doing a lot of research on this forum and on other forums, links, you name it (before I posted this Thread)

I'm stuck with a Laptop that can't get away from Ethernet cable

Can someone please help. If you're going to give me Terminal commands, please, I repeat please (kindly) could you give it to me in it's details because I'm still new to Linux and I find it hard when someone tells me to do things I can't fully understand...much appreciated

Thanks

---

### Post by WlaadDyaab on 2010-12-19
[Solved]


Finally it's solved

Just for the information of people and newbie's like myself

I solved this problem by:

Step 1:

- Getting a blank Re-wrightable CD (it has 700 MB free space)
- If you have a Linux distribution (Ubuntu or Windows (But I'm using Ubuntu)) on one of your other computer - 1. Insert blank CD. 2. Download Ubuntu from Ubuntu.com (on there it shows all steps VERY nicely and easy).

Step 2:

(Assuming you want Ubuntu only)

Note: There is a way to make Microsoft Windows run as an Application on Linux/Ubuntu. And also another way of having both Windows and Ubuntu/Linux run on the same computer (it's called "Dual-boot")

When you restart computer (with ISO CD inserted (ISO means a CD that has an operating system installed on it)) you will get Ubuntu doing it's procedures

Note: I also inserted Netgear Wireless-N USB Adapter WN111

- Choose to erase whole disk

- Then continue with rest of the installation (it's easy and strait forward, no need to panic)

Step 3

- I clicked on the icon at the top, that searches for wireless connection (the icon that looks like two monitors, next to the Bluetooth or Sound or Envelope icons)

- I made sure that there were names of wireless routers

- I took off the Netgear wireless USB adapter

Step 4

- Click on System - Administration - Update Manager

- Click on Install Updates (note: they normally are around 200 MB)

- Type your password and press Enter

Note: As I was looking around on the forums, I noticed that there was a problem with one of the Firefox Plugins that was causing wireless disconnection

Also

After I repeatedly installed Ubuntu because the wireless card (the on-board wireless card in my HP ProBook 4510s..it's a Broadcom make/module) never seemed to work on it, I found out that when I go to Additional Drivers (System - Administration - Additional Drivers) and install it's driver, that my wireless card actually stops working

So when the Additional Drivers icon pops up (next to the wireless connection icon (the two monitor icon)) and says that there are some restricted updates available I IGNORE IT!!

Also

Make sure that the default Internet browser (the main Internet browser) is not Firefox

- Click on Applications - Ubuntu Software Centre

- In Ubuntu Software Centre click on Internet - Web Browsers - (and choose which one you want (I chose Chromium)), and then click install

Note: For the next step, I don't know if it's the right way, or best way

- To make the your Internet browser the default browser, click on System - Preferences - Preferred Applications

- In Preferred Applications, under "Web Browser" choose (in my case) Chromium

And just to be on the safe side in order to not choose Firefox by accident, I right-clicked on Firefox on the top (the panel) and chose "Remove from Panel"

And enjoy surfing the Net :)

---

