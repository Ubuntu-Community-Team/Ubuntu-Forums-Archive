---
title: "Turning on Wireless Card"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by motlive on 2006-12-20
Hi All, 

First time ubuntu user trying to get my advent 7096 to take Ubuntu and have my wireless card enabled. 

This laptop has a little button on it to turn the card on, in windows you can turn it on during the splash screen, but ubuntu doesnt recognise the button, but it does know the other 2 are for the browser and email :S

I followed the installation guide here:
[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

my card is:

Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 43)

I have done this twice now, and every time the machine will not boot correctly afterwards, when I take the splash screen off, and ctrl-alt-del to kill the processes it then boots to the login prompt, but I cant do anything else from there. It wont login to the desktop, and i have tried to edit etc/networking/interfaces to remove the lines about wlan0 but it says i dont have rights, and when i use sudo -i it just hangs again. 

Anyone got any ideas or guides that i could have a shifty at?

Cheers

Apologies for this being so long.

---

### Post by bhajee on 2007-10-06
I have the same problem!! Did you find a solution please?

---

### Post by motlive on 2007-10-08
If I remember correctly I did manage to get it working, I have to use some obscure drivers i found. 

I saved them somewhere incase i needed them again, i broke my ubuntu installation and didnt go back to it. 

I will try and dig them out for you....

---

### Post by slanbarn on 2007-11-08
GAH!!! this is my problem to!!!!

I have installed the drivers using ndiswrapper, but cant get the button to work!
Actually, i didnt even know the two other buttons workedm until i read this post, why not the wireless button?

please if someone knows ow to make the button work, i would gladly kiss you feet for a week:)

edit: I have an Advent 7105

---

### Post by slanbarn on 2007-11-08
To input some informatin of my own

On my Advent 7105, the program 'xev' caputers and recognise the two other buttons(browser and email), but the wireless button, it just dont seem to know its there... no reaction... 

well, hope it can tell someone something :)

---

### Post by slanbarn on 2007-11-08
Hi guys!

I solved it, for me atleast...

As I said, I have a Advent 7105, and the Marvell Libertas wireless network card.

I used ndiswrapper to install the windows driver, and it worked.

When I tried with a newer driver, not 3.1.x.x.x something, but 3.2.x.x. someting, the button works ! :) it enables the wireless card!

for me atleast.....

i followed this ndiswrapper guide: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and the driver i used, i downloaded from: [http://www.ecs.com.tw/ECSWebSite/Downloads/ProductsDetail_Download.aspx?detailid=562&DetailName=Driver&DetailDesc=&CategoryID=3&MenuID=6&LanID=9](http://www.ecs.com.tw/ECSWebSite/Downloads/ProductsDetail_Download.aspx?detailid=562&DetailName=Driver&DetailDesc=&CategoryID=3&MenuID=6&LanID=9)

hmm, offcourse, that ECS-site is for the 7105 model, but it sounds like it is the same wireless card as the thread-creator has...

and from this compressed archive, i used the .inf in the win2000 and xp folder...

hope it will work for you guys to!!

---

