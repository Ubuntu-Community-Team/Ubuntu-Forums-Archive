---
title: "Not quite computer smart enough"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by onexmadxdisaster on 2009-09-12
I am and always have been a windows person. I ordered a laptop with ubuntu, under the assumption from what i have heard that ubuntu is fairly similar to windows, with little differences. and I was also told I would be able to install a windows emulator called WINE if I needed windows compatible programs (which I DO, for school).

Essentially, I like ubuntu. I am just not familiar enough with it yet to be fully commited to it. I am getting an older dell desktop computer and installing ubuntu to further familiarize myself with it before I dedicate my laptop to it.

My laptop is a nice dell mini 9. I upgraded the memory and harddrive with the money i saved by getting ubuntu. Solid State Drive too, nice and quiet. Love the little thing.

I have found WINE in the add remove programs menu, but for some reason the check box is a darker gray and I cannot click it. It simply wont let me install it, along with a couple other useful sounding programs like gparted. Not too happy about now, and not too happy that I cant figure it out on my own.

I need XP on my laptop for school. I KNOW it is compatible (vista is too but it isnt that great and would tremendously slow the little guy down).I went and got myself an XP cd, code and all. Everytime I put it in my external cd drive, it loads, comes up with a box asking if I want to run the CD, and I click yes, but then it does nothing. when I click inside the folder for the CD, the auto run says there is no program to run it with. 

Can ANYBODY help me? also put it in plain english, laimans terms please. i am slow to pick up on the new names, like terminal not command prompt! I am computer smart, just not quite enough to figure this stuff out. 

Thanks!

---

### Post by Bucky Ball on 2009-09-12
What programs do you need to use for school?

---

### Post by steveneddy on 2009-09-13
Personally I would install [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") 3.0 from the web site and install XP in [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") and use XP inside Ubuntu.

That's what all of the cool kids are doing.

---

### Post by onexmadxdisaster on 2009-09-13
For a computer class I need to buy and install microsoft office 7, and I need to download a couple accounting programs. Not to mention I would love to have my itunes and limewire (I know its bad) back.

---

### Post by Bucky Ball on 2009-09-13
I suggest you dual-boot with Windows and no, Ubuntu is not like Windows with a few little differences. This is a common myth.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Open Office would probably cover anything you needed to do in MS Office 7, including saving files in a compatible format for Windows. Educational Institutions often mislead students and staff they HAVE to use an MS product, probably because they have so much cash tied up in the deal and back patting exercise.

---

### Post by onexmadxdisaster on 2009-09-13
No, I cannot just use open office. I need microsoft office 7, the computer class is teaching me about how to use that program. Not just a matter of wanting office 7, but it is a required class. I can choose to use the school computers, but I would much rather use my laptop, so that I can do this stuff at home, not on campus.

---

### Post by onexmadxdisaster on 2009-09-13
Checking into virtual box now. Anyone have any idea why I cant download wine? someone mentioned to me once that SSD might have something to do with it. anyone able to correct or agree with this?

---

### Post by onexmadxdisaster on 2009-09-13
While installing virtual box, a little box pops up saying :disk space low, 100% of partition is in use. ??? problem? Then it said compilation failed. idk if it installed or not. I wish someone could do all this for me...

---

### Post by lisati on 2009-09-13
As has been pointed out, Ubuntu is different in many ways to Windows. Don't be too hasty to drop Ubuntu: some of your Windows skills can be adapted to Ubuntu - for example, "point and click" is fairly universal across operating systems with a graphical interface.

Open Office has already been mentioned as a possible alternative to MS Office in some circumstances.

*Some* software for Windows can be used with Ubuntu with the help of a program called "[Wine]("https://help.ubuntu.com/community/Wine")" - it might be worth checking if MS Office 7 can be run with Wine (a legal copy, of course!)

Good luck!

---

### Post by j.bell730 on 2009-09-13
Try this [link]("apt:wine"). If there is an error, post it.

---

### Post by themusicalduck on 2009-09-13
What size is your ssd drive? Certainly looks like you're low on space. Wine and virtualbox are both large programs. This would also cause problems if you wanted to dual boot with Windows and Ubuntu because two operating system with software installed is gonna take up a lot of space.

Also virtualbox will need extra ram, power and disk space because you'll need to install and run windows inside of Ubuntu. 1Gig of ram is probably minimum needed to do it.

Try looking in places > computer. Right click on filesystem, click properties and see what space is left.

Since it sounds like you're doing a very windows-centric course, I think Ubuntu might be a bit of a hassle. It's still worth using for other non-windows tasks though.

---

### Post by presence1960 on 2009-09-13
so we all can see exactly what you have on your lappie do this:

Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by onexmadxdisaster on 2009-09-13
My packing slip says...
2GB, DDR2, 533MHz, 1 Dimm
and
16GB Solid State Drive   (mini-card module/PATA)
Mini OS powered by Ubuntu   8.04.1

Since this troubleshooting experience, my laptop is acting funny. closing web browsers by itself, not letting me click stuff, etc. I now have to be on my sisters desktop to even post here because when i go to login on my laptop, when i click submit, it just clears the password entry field and does nothing. What the heck?!

---

### Post by onexmadxdisaster on 2009-09-13
I would have said screen shots would be easier, but I guess doing these little things has messed up my laptop. virtual box is on my menu but doesnt function, how do I take it off/uninstall?

---

### Post by j.bell730 on 2009-09-13
```
sudo apt-get purge virtualbox
```

---

