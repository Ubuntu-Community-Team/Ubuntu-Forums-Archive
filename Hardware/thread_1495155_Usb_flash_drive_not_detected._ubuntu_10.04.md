---
title: "Usb flash drive not detected. ubuntu 10.04"
date: 2010-05-27
forum: Hardware
---

### Post by marcio123 on 2010-05-27
Hi,

I have a problem with all kinds of usb memory drives. 

When I plug it in it isn't mounted and it doesn't appear in /dev 

the only place when I can see that it is plugged is "lsusb" which shows 


Bus 002 Device 018: ID 0d49:7450 Maxtor 


Please write what should I do.

---

### Post by romunov on 2010-06-14
I'm having a similar problem. I've noticed this happened when I upgraded to 10.04. I'm also experiencing problems with suspend, second hard drive... But that's for another post. :)

---

### Post by atulkakrana on 2010-06-30
Same problem here...It was working well on Ubuntu 10.04 before installing updates

---

### Post by saeed_alzubaidi on 2010-07-17
I have the same problem

---

### Post by AltomineUK on 2010-07-17
Hello,

Check the '/media' directory.          External filesystems are usually mounted there...

---

### Post by marcio123 on 2010-07-18
If they are not shown in /dev they cannot be mounted

---

### Post by AltomineUK on 2010-07-18
> **marcio123 said:**
> If they are not shown in /dev they cannot be mounted

Well they are normally mounted in both places normally and I forgot where the control panel that controls mounting is kept =(

---

### Post by rajeshgheware on 2010-08-15
I face the same issue.  In dmesg log I can see usb ports detected however whenenver I plug any usb flash drive, it is not detected.
See this bug FYI:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614351](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614351)
Visit this link and click on "This affects me"

---

### Post by woodyg on 2010-10-04
Hi everyone,
have you managed to sort out your problems? I have a case of USB memories not being detected, and I don't really know where to look for the problem. The lsusb command mentioned earlier gives me

[I]Bus 002 Device 003: ID 17ef:4810 Lenovo 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

so nothing in there. Where do I go from here?
[/I]

---

### Post by ajcookie on 2010-11-15
Anyone get a solution to this one, I've got the same problem.

---

### Post by thanigaivelan19 on 2011-08-08
Hi,

USB Flash drive is not detecting in Ubuntu 11.04. 

when i used **lsusb **commandBus 002 Device 002: ID 15d9:0a4c Trust International B.V. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubPlease help me

Thanks

Thanigaivelan

---

### Post by hitman2k9 on 2011-09-16
Same problem here . Its shows up at the lsusb but not in /dev/ . Facing this after some updates previously it was working.
[http://paste.ubuntu.com/690662/](http://paste.ubuntu.com/690662/)

---

### Post by warfie on 2011-10-18
I have the same problem... this is a very old and well known problem... still no solution????

---

### Post by woodyg on 2011-10-18
> **warfie said:**
> I have the same problem... this is a very old and well known problem... still no solution????

Which Ubuntu version are you running? At the moment I'm running 11.04 on the laptop that is having problems with detecting USB...

---

### Post by warfie on 2011-10-19
> **woodyg said:**
> Which Ubuntu version are you running? At the moment I'm running 11.04 on the laptop that is having problems with detecting USB...

Sorry, I should have said which release.... 10.04 LTS on four machines, 2 desktops and 2 laptops. All have the same problem.

---

### Post by Rebelli0us on 2011-10-22
Same problem here. What must be very embarrassing for Ubuntu is that my Windows Guest OS in Virtualbox can see the flash drive just fine!

---

### Post by boazjones on 2011-11-30
Shouldn't we consider the manner in which Linux views Objects?

I mean, "everything is a file" - right?"

My flash drive reads as a file within the "Media" folder. It is recognized as a "flash drive" - shown by USB Flash Drive Icon; but do to the organizational paradigm in Linux, it still retains its nature as a directory.

That's not so bad - is it?

---

