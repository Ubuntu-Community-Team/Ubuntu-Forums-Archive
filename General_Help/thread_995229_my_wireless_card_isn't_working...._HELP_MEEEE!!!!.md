---
title: "my wireless card isn't working.... HELP MEEEE!!!!"
date: 2008-11-27
forum: General Help
---

### Post by Nitrozzy7 on 2008-11-27
I have a problem with my wireless card. I've got an acer 5715z it runs only on ubuntu 8.04 and it's updated. I am new to the system and I sometimes get a feeling that the man who made Ubuntu wants to get me mad... First how can I make the screen be bright when I boot in? 2nd is there an easy way to run .bin files? 3rd is there an easy way to download .flv videos from youtube? 4th can I play games like SimCity4 NFS:Most Wanted Flight Simulator 2004 on Ubuntu? Oh! I almost forgot... How on earth my wireless card is going to work. It's an Atheros 802.11b/g WLAN, the system seems to know that and although I've searched through everything I haven't come up with a solution. And one last thing how can I remove ubuntu and install windows xp if I want to? :confused:

---

### Post by HermanAB on 2008-11-27
You can install ndiswrapper with a Windows Xp driver.

See this:
[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)


There are no shortage of howto guides on this one.  Look at the stickies in the network forum.

Cheers,

Herman

---

### Post by wildbillkelso on 2008-11-27
Hi.

With regard to running windows games in Ubuntu have a look at [http://www.winehq.org/](http://www.winehq.org/) but unfortunately FS2004 will not work. You can install wine by going to the synaptic package manager and searching for and installing wine. Then go to [http://www.winehq.org/site/download](http://www.winehq.org/site/download) and get the Ubuntu update. Good instructions here on how to get it. First though you should check out [http://appdb.winehq.org/](http://appdb.winehq.org/) to see how the games and applications you would like will run under Wine in Linux.

Hope this helps.

Best regards.

Tim

---

### Post by wildbillkelso on 2008-11-27
And if you would realy like to remove Ubuntu from a dual boot setup I deleted the Ubuntu partition with Gparted and resized the NTFS partition. Then put the xp disk in. click on repair windows and when loaded type MBRFIX and reboot it will scan your drives. Grub will be gone and XP will boot normally. If you have got rid of windows completely just boot from the XP CD and follow the instructions. Please persevere with Linux though. We are all learning!

Hope this helps to.

Cheers.

Tim

---

### Post by frankleeee on 2008-11-27
[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)
Is a great downloader.

---

