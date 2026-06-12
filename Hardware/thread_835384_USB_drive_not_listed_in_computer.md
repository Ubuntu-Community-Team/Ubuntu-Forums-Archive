---
title: "USB drive not listed in computer"
date: 2008-06-20
forum: Hardware
---

### Post by kismeras on 2008-06-20
Hey Guys,

I have an external usb hard drive plugged into my laptop. However, it is not listed in computer. Is there something that i need to do to get it to show up? Thanks.

---

### Post by kismeras on 2008-06-20
I guess i should have also said that i am using Hardy Heron on an Acer 5672 laptop. Thanks.

---

### Post by AndThenWhat on 2008-06-20
Just out of curiosity have you tried running **lsusb** in the terminal?

It would be helpful to know the output of that command.

---

### Post by AndThenWhat on 2008-06-20
One thing you could check into is 

go to **System -> Administration -> Authorizations**

and make sure that **Mount Filesystems From Removable Drives** is authorized for your user.

---

### Post by kismeras on 2008-06-20
Here is the output from lsusb,

Bus 005 Device 003: ID 046d:0892 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 001: ID 0000:0000

I would have posted it originally, but i didn't know about it. Thanks. I went to Authorizations and gave myself permission. I'm going to restart now to see if that worked. Will keep you posted.

---

### Post by kismeras on 2008-06-23
I used a couple of thumb drives and they worked fine. I'm guessing the HDD did not show up because it is formated in ntfs. If that's the case, can i make it so that it will show up?

---

