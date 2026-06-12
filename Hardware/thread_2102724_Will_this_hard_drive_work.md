---
title: "Will this hard drive work?"
date: 2013-01-08
forum: Hardware
---

### Post by bigb0ss on 2013-01-08
I have a Hard Drive question. Currently I am runnung Ubuntu 12.04.1 and would like to buy a portable external hard drive that will work with both my MAC and Linux based operating systems. 

I had purchased this Hard Drive for both OS, but on my Linux it did not recognize:



[http://www.walmart.com/ip/Western-Digital-My-Passport-for-Mac-1TB-Portable-Hard-Drive/21732257](http://www.walmart.com/ip/Western-Digital-My-Passport-for-Mac-1TB-Portable-Hard-Drive/21732257)


Now, I am interesting in buying: 
[http://www.walmart.com/catalog/product.do?product_id=21141706&findingMethod=rr](http://www.walmart.com/catalog/product.do?product_id=21141706&findingMethod=rr)



* If neither of these HD will work with both, which one can? Also, I am not that good with computers, I need one that will just "plug and play".


(Please Help)!!!!



Thanks

---

### Post by sudodus on 2013-01-08
My experience is that hard disk drives are easy to recognize in linux. I think that the second one, which they claim should work with Windows as well as Mac should work also with Linux. I think it's a good idea to look for USB 3 capability as well as backward compatibility to USB 2.

For external purposes I usually buy internal sata disks and an external casing with suitable properties. I want USB and esata connection. For example IcyBox and Akasa make such casings.

---

### Post by tlhIngan on 2013-01-08
> **bigb0ss said:**
> 
I had purchased this Hard Drive for both OS, but on my Linux it did not recognize:


I find it odd that Linux wouldn't recognize it. Whenever I've had something weird happen to a hard drive, Linux would be the only thing that could guarantee seeing it and fixing it if it was at all possible.

Is Linux able to use that USB port for other things?
Did you ask Linux to mount the partition on the drive?

---

### Post by bigb0ss on 2013-01-08
The chromebook in which i have has 3 USB ports, and it has recognized other thumbnails but not the Hard Drive.

---

### Post by sudodus on 2013-01-08
> **bigb0ss said:**
> The chromebook in which i have has 3 USB ports, and it has recognized other thumbnails but not the Hard Drive.
Have you checked if that drive is recognized by other computers (with any operating system: Ubuntu, Windows, MacOS)?

It does say in the specification, that it is made for Mac. So I guess that the file system is not a standard one.

Check with these terminal window commands

```
sudo fdisk -lu
``` and
```
sudo blkid
```

if you can identify your external drive!

Please post the output of those commands in a reply :-)

---

### Post by bigb0ss on 2013-01-08
I didnt buy the drive yet...i bought the western digital and returned it. Iam interested in buying the seagate

---

### Post by sudodus on 2013-01-08
> **bigb0ss said:**
> I didnt buy the drive yet...i bought the western digital and returned it. Iam interested in buying the seagate
Yes, as I wrote in post #2, that one is said to work also in Windows, and then it is very likely to work for you in Ubuntu.

---

### Post by bigb0ss on 2013-01-08
So you recommend the seagate for Ubuntu? 

* If the Seagate is not recognized by Linux, what do i do then?

---

### Post by tlhIngan on 2013-01-08
> **bigb0ss said:**
> So you recommend the seagate for Ubuntu? 

* If the Seagate is not recognized by Linux, what do i do then?
It probably will be.
If it's made to be compatible with both Mac and Windows, the interface and filesystesm, if any, are probably generic, and Linux loves generic things.

---

### Post by sudodus on 2013-01-08
> **bigb0ss said:**
> So you recommend the seagate for Ubuntu? 

* If the Seagate is not recognized by Linux, what do i do then?

If you need to be completely safe, buy the disk where you are allowed to test it and return it if it won't work, but believe me, it is ***very*** likely to work, unless there is something wrong with your Ubuntu system.

Or buy a standard internal sata disk and an external casing with suitable properties. (I want USB and esata connection.) For example IcyBox and Akasa make such casings. I have tested casings of those brands and they work with linux.

---

### Post by bigb0ss on 2013-01-08
where can i go to verify is the hard drive will work? What store can I go to and "plug it in"


Thanks

---

### Post by sudodus on 2013-01-08
> **bigb0ss said:**
> where can i go to verify is the hard drive will work? What store can I go to and "plug it in"


Thanks
Where do you live? Is there some local small computer store + repair shop? Do you have a friend/colleague who can let you test with her/his external drive, and you can get the same kind?

---

### Post by bigb0ss on 2013-01-08
nj

---

### Post by sudodus on 2013-01-09
You know, we (people helping at the Ubuntu Forums) are volunteers. We help because we like linux and we like to help. We get no money for it. So we can give no guarantee. No money back from us, if it does not work according to our tips and advice:

We give tips and advice. You solve the problem. Often it works, but not always.
--
In this case I'm almost sure that the second drive, the Seagate, will work for you. But only an idiot is 100% sure before trying.

I also gave you a tip of an internal sata drive and a casing to make it external. I have that kind of equipment myself and it works with Ubuntu 12.04 every day. So I know it works for me, but I am not 100% sure it will work for you.
--
Good luck :-)

---

