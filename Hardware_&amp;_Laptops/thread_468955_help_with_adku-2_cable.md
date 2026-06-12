---
title: "help with adku-2 cable??"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by ninjaprawn on 2007-06-09
hi!!

i have had to reinstall win xp back onto my pc, after loving 3 months without it!!! the reason for this is because i cant get my nokia 7610 working thru the dku-2 cable it came with!!!!

how do i get my pictures off the phone?????? it is s60! if anyone knows what other phone it is like, that would be a start, i dont mind experimenting!!!!!!

i started with gnokii, ive installed the gnapplet.sis on my phone,now understand i should use cobex!

i installed cobex thru apt-get!!!! any advice would speed up this process, i cant find any where that explains any commands or any thing about how to use cobex! im kind of getting lost in a sea of google pages that even tho have cobex in them, dont actually relate to cobex 1 bit! for example, how can i get pictures off, what im guessing from what i have read is the path of the mmc card, e:/nokia/images????? i think thats the path anyway!?!

thanks!

---

### Post by ninjaprawn on 2007-06-09
i figured it out, if anyone reads this thread with the same problem;

run;
sudo apt-get install openobex-apps

first, then
sudo apt-get install obexftp

Set UDEV permissions
- Open a terminal and type lsusb.
- Look for a line similar to this:
Bus 001 Device 005: ID 0421:0428 Nokia Mobile Phones
- In this example, 0421 is the VendorID, while 0428 is the ProductID.
- Add the following line to /etc/udev/rules.d/40-permissions.rules in Ubuntu:
BUS=="usb", SYSFS{idVendor}=="VendorID", SYSFS{idProduct}=="ProductID", GROUP="plugdev", USER="yourUserName"
- Replace VendorID, ProductID and yourUserName with the correct values.

Listing directories:
(Run command as normal user with Ubuntu and as root with everything else)

CODE

$ obexftp -u 1 -l
-u 1 connects to interface 1, while -l will list directories and files in the root directory.

Downloading files
Let's say we want to get 011.mp3 from the Music files directory:
CODE

$ obexftp -u 1 -c 'Music files' -g 011.mp3

To upload file.txt from Desktop to Documents directory on the phone:
CODE

$ obexftp -u 1 -c 'Documents' -p path/to/Desktop/file.txt

the downloaded files went to my 'home folder'. also i put the files i wanted to get off my phone just on the mmc, not in a folder!!

this worked with a nokia 7610!!!!!!!!

i got this all from;
[http://news.softpedia.com/news/Access-Your-Mobile-Phone-Through-USB-Cable-46486.shtml](http://news.softpedia.com/news/Access-Your-Mobile-Phone-Through-USB-Cable-46486.shtml)

---

### Post by wingnux on 2007-06-26
THANK YOU VEEEEEEEEEERY MUCH!!! =)

I wish I could batch-download all files at once instead of typing each file name but that's ok ;)

Thanks again! :D

---

