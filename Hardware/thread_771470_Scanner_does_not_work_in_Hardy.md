---
title: "Scanner does not work in Hardy"
date: 2008-04-27
forum: Hardware
---

### Post by typefaze on 2008-04-27
Hi
I'm running Hardy and trying to get a Canon LiDE 35 scanner to work.
It works when I run it as root (sudo xsane) but not when I run it as a regular user. So it looks like a permission problem.

$ sane-find-scanner returns the following:
found USB scanner (vendor=0x04a9, product=0x2213, chip=GL841?) at libusb:004:012

while
$ sudo sane-find-scanner returns
found USB scanner (vendor=0x04a9 [Canon], product=0x2213 [CanoScan], chip=GL841) at libusb:004:012

$ sudo scanimage -L returns
device `genesys:libusb:004:012' is a Canon LiDE 35/40/50 flatbed scanner

Running $ scanimage -L as regular user will not work.

My regular user is member of group 'scanner', and I suspect I have to do some changes in some device files.
But I'm pretty new to linux, and honestly have no clue where to look or how to find out which device-file is used.

Anyone who can guide me?

---

### Post by Doombringer on 2008-04-30
Same here. Works as sudo and only detects my integrated screen Webcam if I run it as a regular user.

---

### Post by SumnerBoy on 2008-05-01
I am in the same boat - can't access my scanner using the saned:scanner user/group, only root seems to work.

---

### Post by Doombringer on 2008-05-12
I think I have found a solution.

Go to System -> Administration -> Users and groups, click unlock, select your username, click Properties, go to tab "User Privileges" and hit Use Scanners. It seems like it is unchecked by default. Anyways, it was for me.

Hope it helped.

---

### Post by SumnerBoy on 2008-05-15
I am running the server edition of Ubuntu so this tip doesn't apply to me. Can anyone tell me how to acheive this without a GUI?

---

### Post by mandyfester on 2008-05-16
Hello

I have more or less the same problems. I configured saned to be accessible over my network from my Ubuntu Server Hardy using the page
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

The command scanimage -L on the server works. I get:
device `pixma:04A91712' is a CANON Canon PIXMA MP530 multi-function peripheral

So I guess it works

If I try and connect over the network with a client using xsane I always get the message:
[saned] init: access by host ::ffff:192.168.0.11 denied

Any suggestions are welcome.

Thanks

Andy

---

### Post by mandyfester on 2008-05-17
The reason I was getting access denied was because I had added
192.168.0.0/24

to /etc/saned.d/saned.conf

Adding specific client ip addresses got me past the access denied but as this thread says I can only work with xsane if I run the saned as root.

---

