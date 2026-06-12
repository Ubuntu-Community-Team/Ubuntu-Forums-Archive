---
title: "HELP! HDD + Ethernet problem:wrong swap drive and no ethernet detected"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by ankur.gupta.10 on 2007-07-05
hello..
i am new to linux and was installing Ubuntu 6.06 , without any help, for the first time. I thought it to be as simple as clicking 'next' 4-5 times. So i had one partition ready for it of 8 GB. But while installing it asked for the swap partition. I had no idea what it meant. So i thought for while and selected as my 30 GB drive as it didnt asked to format the drive. 

The installation started and gave an error at 15%. So i again restarted the installation. And this time i selected 'use the largest continous free space' , thinking it might work. And luckily it worked. So while i was enjoying it i realized that its not showing my HDD (didnt knew at that time anything about mounting). 

So now i went to windows and found a missing 30GB partition. And i was shocked. Then i went to 'computer management->storage->disk management' and there it was written local drive with a healthy state and '15% free'. Then assuming my data is still safe and contacted my friend (should have done that earlier).

He knew some basics in linux and told me few commands of mounting. In linux terminal, i typed them 
sudo mount /dev/sda6 /abc
sudo su
cd /abc
ls

and saw my data was safe and readable. He said i have to install ntfs-3g driver to do more. But my ethernet is also not detected so i cant access internet. i am posting it via windows. I have used the driver cd (containg linux driver) i got..it says wrong user while installing.

So .. how to get my drive a ntfs format without actually deleting anything. Also i cant access to internet. If there is some command please post it or if any alternative in windows to give it a nfts format or just any other option that could help.....PLEASE HELP..... All that 30 GB was full. I dont wanna lose that and i dont have problem of ethernet untill that partition doesnt get a format.

Thanks
Ankur Gupta

---

