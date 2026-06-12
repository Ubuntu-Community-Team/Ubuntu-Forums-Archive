---
title: "Udev rules to change USB vendor and product ID"
date: 2012-11-27
forum: Hardware
---

### Post by soccnut on 2012-11-27
I have a USB device which is unsupported in linux. However, another similar device has a driver that would work with my device. 

Can i use Udev rules to "spoof" the vendor and product ID of the device so that the driver would recognise it? What would be the rule that i need to add?

Thanks

---

### Post by varunendra on 2012-11-28
First of all, Welcome to the forums soccnut !

> **soccnut said:**
> I have a USB device which is unsupported in linux. However, another similar device has a driver that would work with my device. 

Can i use Udev rules to "spoof" the vendor and product ID of the device so that the driver would recognise it? What would be the rule that i need to add?

Thanks
What kind of device it is ? If it is a USB modem, see if this post can help you - [http://ubuntuforums.org/showpost.php?p=11899627&postcount=11](http://ubuntuforums.org/showpost.php?p=11899627&postcount=11)

I'd appreciate if you post back the details of the device, including **lsusb** output, and how it went. Of course if you need detailed help, post back the details of the problem along with output of lsusb, and hopefully, we may help finding the solution.

.

---

### Post by soccnut on 2012-11-28
Thanks for the help. I found the required driver online and installed it without any problems

---

### Post by varunendra on 2012-11-28
> **soccnut said:**
> Thanks for the help. I found the required driver online and installed it without any problems

Glad you got it solved.

It would be a great help for us all if you could tell us about the device type (modem or what..) and the link for the driver.

Also, please mark the thread as [Solved] now that it is (using **Thread Tools** at the top-right corner of the first post above). It helps both who are looking for help, and also those who are willing to help.


Thanks!

---

