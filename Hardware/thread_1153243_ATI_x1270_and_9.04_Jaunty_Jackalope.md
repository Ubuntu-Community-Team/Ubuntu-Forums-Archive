---
title: "ATI x1270 and 9.04 Jaunty Jackalope"
date: 2009-05-08
forum: Hardware
---

### Post by Shibblet on 2009-05-08
My friend has an Averatec Laptop that has an ATI Mobile x1270 Graphics card in it.

We've looked all over the forums and followed all sorts of instructions, but we still cannot get this to work.

As soon as a graphic driver is loaded, or we turn on visual effects, the screen get a whole bunch of gaarbled or distorted images.

Can anyone help with this problem?

---

### Post by DJYoshaBYD on 2009-05-08
the ati driver (fglrx) is not supported for 9.04 at this time.. have him downgrade to 8.04 or 8.10.... then install the drivers, and then all of your visual fx will work..

I highly suggest 8.04 or 8.10, as they have largest compatibility spectrum that I have dealt with.. I have tried jaunty on everything that I have that had hardy or intrepid on, and most of it didnt work... so yeah.. no need to just upgrade to the newest, just cause its the newest... 

but yeah... even 8.10 would work great for that setup.. it should anyway.. im using it right now.. lol.. with an ati card and 3d fx... I just spun my desktop cube.. lol

---

### Post by b3ta on 2009-05-08
As for as I know ATI has stopped developing their Linux drivers for cards older than HD2000 as of the latest version of Catalyst and leaved it up to the open source community. Sad, but true :( (this is the reason I am going to order an Nvidia card in a few days)

---

### Post by DJYoshaBYD on 2009-05-08
well, Nvidia is the best anyway.. I NEVER go with ATI unless already on the pc and i have to work with it... AMD/ATI are frikkin jerks, and they are going to lose alot more market share to Nvidia from Linux users than ever before if they keep it up..

to avoid problems, everyone should just stick with nvidia.. lol...

---

### Post by Shibblet on 2009-05-08
Well, we gave Ibex a try, and got the same problem in return.  Glitched graphics... so I guess we don't know which drivers to use.

---

### Post by DJYoshaBYD on 2009-05-08
Do this on a clean install on ibex.. im using ibex, with the newest ATI driver, and installed it very very easily using the file from ATI's site..
but try Envy first

ok.. go here

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

download envyNG

run it again...

ON A CLEAN INSTALL... this will work.. it has to... ive done it with hella different ati cards, and envy 99% of the time works great.. I like to use the files from the manufactures site, though... you just have to be comfy and know hot to run programs from the command line.. which is:

```
sudo sh ./insertatifilenamehere
```

so yeah.. whatever the name of the driver file you download from ATIs site, put that RIGHT after the "./" with NO space...

thats how install it.. make sure you use capital letters.. linux is case-sensitive...

if envy doesnt work, then go to ati's site and download the new drivers for your card..

are you trying to use the 64 bit version? ati support in 64 bit linux licks ***.. lol

---

### Post by ssri on 2009-05-08
well, I wouldn't run the shell script from ATI.  I've had nothing but problems installing fglrx that way.  Try this:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually)

I've done it a number of times, and each time the Catalyst drivers work very well.  Remember to follow the instructions to the letter.

Remember to download Catalyst 9.3, as your card is not supported with 9.4.

Good luck!

---

### Post by DJYoshaBYD on 2009-05-08
wow.. thats WAAAAYYYY too much.. especially for someone starting out.. Running the shell script works perfect every single time for me.. if it doesnt work, it tells you why, then you fix it, and do it again.. its sooooooooo easy...

OR

Just use envy, and it will do everything for you...

---

### Post by Shibblet on 2009-05-08
This was an Averatec 2575 Laptop.  Ubuntu 8.10 Intrepid Ibex worked great, and so did Envy!  Mark this thread as solved!  Thanks again guys!

---

### Post by ssri on 2009-05-08
> **DJYoshaBYD said:**
> wow.. thats WAAAAYYYY too much.. especially for someone starting out.. Running the shell script works perfect every single time for me.. if it doesnt work, it tells you why, then you fix it, and do it again.. its sooooooooo easy...

OR

Just use envy, and it will do everything for you...



Ehhh, you only need to create the debs just once.  I wrote a bash script to automate the rest, along with another script that purges it whenever I want to test the latest opensource radeon drivers.  This coming from someone who started out on intrepid.

---

