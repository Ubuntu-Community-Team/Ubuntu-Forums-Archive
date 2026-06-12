---
title: "How to check if the webcam on my laptop is working or not?"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by bopmatic on 2008-03-13
Generally speaking, how to check if the webcam on my laptop is working or not? Thanks.

---

### Post by |{urse on 2008-03-13
i usually check mine with xawtv or 

sudo apt-get install amsn 

amsn has all that too

---

### Post by YldGuy on 2008-03-13
make sure you have the cam drivers installed first. I used camorama to check initially.. camorama is not that good but atleast i came to know that drivers were installed... my cam works well with skype though.

---

### Post by daengbo on 2008-03-13
The easiest way to check that it's working properly without installing anything is to run gstreamer-properties from ALT-F2 or the terminal. On the "Video" tab, look for the "Default Input" section and click "test." You should see the webcam's video output.

Cheers

---

### Post by bopmatic on 2008-03-13
> **|{urse said:**
> i usually check mine with xawtv or 

sudo apt-get install amsn 

amsn has all that too

Thanks for the tips guys and I don't think it's reading the built-in webcam on my laptop. I tried Camerama and aMSN. Both returned saying I didn't have my viewcam plugged in!!

So what can be done next?

---

### Post by egglestn on 2008-03-13
TBH we probably need a bit more information,
like for example, the make and model of laptop, which type of cam it has etc.

 BUT I found this thread extremely helpful, and I now have a working webcam

[http://ubuntuforums.org/showthread.php?t=482967](http://ubuntuforums.org/showthread.php?t=482967)

HTH

---

### Post by Limbic on 2008-03-13
What kind of computer is it?  I've got an HP dv2715nr that comes with a webcam.  I didn't have any luck with Camorama, but Cheese (it's in the repositories) detected it just fine and works great.  I'd give Cheese a try before you do any more experimentation with drivers.

I'd try either the 'lsusb' or 'lspci' commands to see if your webcam shows up first, though.

---

### Post by YldGuy on 2008-03-13
yup.. do a lsusb.. check if the camera is detected. mine showed up as syntek and i had to install drivers for syntek. Once it was done, everything was perfect.

---

### Post by bopmatic on 2008-03-14
> **YldGuy said:**
> yup.. do a lsusb.. check if the camera is detected. mine showed up as syntek and i had to install drivers for syntek. Once it was done, everything was perfect.


I did 'lsusb' in terminal and the results were as follow:

Bus 005 Device 002: ID eb1a:2750 eMPIA Technology, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 

I did a search on eMPIA Techology and looks like the viewcam on my laptop is using their usb model 2750 viewcam. 

How do I install the driver on Ubuntu 7.10?

My laptop is a Centralfield. It's sold in Hong Kong as a 'built to order' type, similar to Dell. I tried sudo apt-get install Cheese but it returned saying, "couldn't find package Cheese"!! 

Any ideal guys? Thanks!

---

### Post by YldGuy on 2008-03-14
i googled for eMPIA technology... their site showed up video capture devices.. so i guess thats your webcam. you need to find the driver for this.

check this discussion here: [http://ubuntuforums.org/printthread.php?t=369881](http://ubuntuforums.org/printthread.php?t=369881)

does that help?

---

### Post by bopmatic on 2008-03-14
> **YldGuy said:**
> i googled for eMPIA technology... their site showed up video capture devices.. so i guess thats your webcam. you need to find the driver for this.

check this discussion here: [http://ubuntuforums.org/printthread.php?t=369881](http://ubuntuforums.org/printthread.php?t=369881)

does that help?

Thanks for the help. However, checked on the link and the steps on compiling the driver looked kind of complicated to me! I will look at it again later and see if I feel like doing it. 

Thanks again, much appreciated!

---

