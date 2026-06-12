---
title: "installing mac os x?"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by Ginseng727 on 2009-08-20
Brand new user to ubuntu, it is running fine, but wen i put in my Mac OS X discs, it says cant mount volume, same with my wireless internet adapters disc too (netgear WG111t) I want to run mac os x on it, but the internet adapter is for windows, what should I do?

Thanks, from a newbie

---

### Post by zarthon on 2009-08-20
First a bit of friendly advise about posting
[LIST=1]
[*]Put one or maybe two problems if they are related in a post. 
[*]It is fine to write multiple posts.
[*]Be very clear and specific about each problem. Describe what you see on the screen and any relevant technical information.
[*]These forums are about Ubuntu linux. Post other problems you are having in appropriate forums.
[/LIST]

To solve your cd-rom issues and get your netgear wg111t usb wireless network adapter working on Ubuntu follow the steps I have posted below.
Do you have a Macintosh Comptuer ?
Installing MacOS on hardware other than the hardware made by apple intended to run it ( creating a * hackintosh *) ***violates the Apple license agreement. *** Also since MacOS only supports a narrow band of hardware this is non trivial. The narrow hardware support contributes greatly to the overall stability of their platform because they can focus on that narrow band of hardware and make it work really well.
This is an Ubuntu forum.  This is not the best place to get advice for installing MacOS X. There are other places that give hackintosh device online so you could search.I can't offer any advice on this topic.
I would seriously consider getting one OS working before installing another one anyway.

_CD-ROM problem_
When you insert a cd-rom and the computer is off if it is a bootable cd like the Ubuntu install CD-ROM then your comptuer will boot from the CD into ubuntu.

When the computer is on and running Ubuntu it should appear in the menu Places->"Removable Media"

Also if you open "Computer" from Places or your desktop the icon that ordinarly will say something like "CD-RW / DVD Drive". After inserting a Disc it should display the name of the Disc.

Does this happen?
If not attach the file /etc/fstab in a response to this post.

_Getting your wireless networking card to work under ubuntu_
To make hardware work under Ubuntu you get the drivers from the distribution so you probably don't need to use your wifi driver cd-rom.

You probably just need to configure the settings for your local wifi network?  Got to System-> Preferences -> Network Connections
Click the wireless tab.
If there is already a network connection there then select it and click the "edit" button. If not click add.
enter the SSID. If you are using security like WEP or WAP then click on the security tab and fill out the form. These should be the similar to what you have on a windows comptuer configured for the same network. You can write them down from there and enter them in the form.

If you can't get it to work then post back, answer these questions and post the related system information under an NEW post with the tile "getting netgear wg111t to work on Ubuntu" and I am sure you will get plenty of help.

You have a usb wireless network adapter  netgear wg111t
Correct?

What sort of comptuer & processor?

Post with an attachment of your lspci
Go to Applications->Accessories-> Terminal
in the terminal type 
```

sudo lsusb > ~/Desktop/Ginseng727wifi.txt
sudo lsmod >> ~/Desktop/Ginseng727wifi.txt

```
The file will appear on the Desktop. You can open it to see what you are sending. It will list your usb hardware and loaded drivers.

When you go to attach and browse it will be easy to find by clicking Desktop on the left.

---

