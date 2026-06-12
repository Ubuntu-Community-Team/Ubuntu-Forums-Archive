---
title: "Bios problem?"
date: 2013-11-05
forum: Hardware
---

### Post by leif-perjus on 2013-11-05
Hello!
I'm running XUbuntu on my Asus eee pc (1015PED) 
i was trying to upgrade rom from shipped 1Gb to 4Gb, but the Asus computer don't handle more than 2Gb !!!

Now are all dead, only power led came on when start and the HD led light up for 1/2 sec or less then go off.
ater that only power led are on and nothing hapend.....
I think something happent to bios, are there somthing to do??

Greatfur in advance for any help.

Greetings from Leffep

---

### Post by varunendra on 2013-11-06
Hello leif-perjus, Welcome to the forums ! :)

It is always a good idea to provide a link to a page that shows exactly the specs of your system. I searched for it and two pages show two different types of RAM -
[http://www.cnet.com/laptops/asus-eee-pc-seashell/4505-3121_7-34168005.html](http://www.cnet.com/laptops/asus-eee-pc-seashell/4505-3121_7-34168005.html) says it has a 1 GB DDR2 **667 MHz** RAM
[http://www.pcworld.com/product/664588/eee-pc-1015ped-pu17-bu-10-1-netbook-atom-n475-1-83-ghz-blue.html](http://www.pcworld.com/product/664588/eee-pc-1015ped-pu17-bu-10-1-netbook-atom-n475-1-83-ghz-blue.html) says it has a 1GB DDR3 **1333 MHz** RAM

Which one is yours?

And how did you try to upgrade? Did you make sure the RAM is of same specs as supported by your netbook's slot (frequence, voltage)?
Was it a single module of 4GB or 2x2GB modules?
What did you do with the stock RAM module that came with it?

Can you access the BIOS settings?

Try inserting the original module and make sure it is properly seated. If it is under warranty, it is probably the best idea to take it to the service center to do the upgrade/fix.

---

### Post by leif-perjus on 2013-11-06
> **varunendra said:**
> Hello leif-perjus, Welcome to the forums ! :)

It is always a good idea to provide a link to a page that shows exactly the specs of your system. I searched for it and two pages show two different types of RAM -
[http://www.cnet.com/laptops/asus-eee-pc-seashell/4505-3121_7-34168005.html](http://www.cnet.com/laptops/asus-eee-pc-seashell/4505-3121_7-34168005.html) says it has a 1 GB DDR2 **667 MHz** RAM
[http://www.pcworld.com/product/664588/eee-pc-1015ped-pu17-bu-10-1-netbook-atom-n475-1-83-ghz-blue.html](http://www.pcworld.com/product/664588/eee-pc-1015ped-pu17-bu-10-1-netbook-atom-n475-1-83-ghz-blue.html) says it has a 1GB DDR3 **1333 MHz** RAM

Which one is yours?

And how did you try to upgrade? Did you make sure the RAM is of same specs as supported by your netbook's slot (frequence, voltage)?
Was it a single module of 4GB or 2x2GB modules?
What did you do with the stock RAM module that came with it?

Can you access the BIOS settings?

Try inserting the original module and make sure it is properly seated. If it is under warranty, it is probably the best idea to take it to the service center to do the upgrade/fix.

Hello and thanks for answer and greetings!
Mine are similar to this: [http://www.cnet.com/laptops/asus-eee-pc-seashell/4505-3121_7-34168005.html](http://www.cnet.com/laptops/asus-eee-pc-seashell/4505-3121_7-34168005.html) says it has a 1 GB DDR2 **667 MHz** RAM but my original memory module are: DDRIII 1GB-1333 SSY3128M8-EDJED
and the one i upgrade to are: 4GB DDR3-1600 CL9  204-PIN SODIMM 1.5v

Both are 204 pin and fitted as the should. After uppgrade nothing hapent exept the power led light go on. After waiting some minutes i hold powerbutton so it shut down, change to original memory (1GB) again but when power on nothing hapent, screen black all the time, only power led light.

I open up computer and disconnected the 3V battery (Right under touchpad) for 30 minutes then connected the battery, assembled computer and try again, NO success. Still all black exept power led.

Also try F1 F2 F3............ together with power on but Nothing..... so cant access the BIOS. No HD activity when power on.

ASUS Type 1015PED-PIK006S Date: 2012-01-10    Got it second-hand so maby no warranty

What to do ???  Give to grandchildren to play with??

Grateful to all help .... !!!!

---

### Post by sudodus on 2013-11-06
I think your 4GB RAM card does not fit logically. Put the old 1GB RAM card back and run the computer with Xubuntu. Check the memory specs with

```
sudo lshw -class memory -sanitize > lshw.txt
```

and post the content of the file **[FONT=courier new]lshw.txt[/FONT]**. Mark that text and click on the ***#*** icon at the top of the editing window to put it within code tags. This will help us decide what kind of memory card you should use.

---

### Post by leif-perjus on 2013-11-06
> **sudodus said:**
> I think your 4GB RAM card does not fit logically. Put the old 1GB RAM card back and run the computer with Xubuntu. Check the memory specs with

```
sudo lshw -class memory -sanitize > lshw.txt
```

and post the content of the file **[FONT=courier new]lshw.txt[/FONT]**. Mark that text and click on the ***#*** icon at the top of the editing window to put it within code tags. This will help us decide what kind of memory card you should use.

Hi sudodus !
Sorry i can't, because the computer dont start anymore and my other laptop don't have the same DDR3 memory.
:(

---

### Post by sudodus on 2013-11-06
What happens if you put the old 1 GB RAM card back to the computer (and remove the 4GB RAM card)? Is something damaged?

---

### Post by leif-perjus on 2013-11-06
> **sudodus said:**
> What happens if you put the old 1 GB RAM card back to the computer (and remove the 4GB RAM card)? Is something damaged?

If i put ori memorycard back, still dead computer, only power led lighting steady
I'm petty sure something happen to bios

I disconnect the 3V battery in 30 minutes, but with no success.

Is there any way to reset the bios in a dead computer ??

---

### Post by varunendra on 2013-11-06
Might sound funny, but I read in a (totally unrelated) review that the BIOS of a particular Dell model needed about 24 hrs to get totally reset. So you may try that as another attempt on resetting the BIOS.

I don't think a 1.5V RAM module has the potential to do any physical damage to the board, so it is most probably just the BIOS confusion.
Also, double check that you have *properly* seated the original module, there is no lose contact.

---

### Post by leif-perjus on 2013-11-07
Ok tnx for all help so fare, i'll disconnected the 3V battery now, and hope on success after 24 hour or more..........

---

### Post by leif-perjus on 2013-11-11
> **leif-perjus said:**
> Ok tnx for all help so fare, i'll disconnected the 3V battery now, and hope on success after 24 hour or more..........

No, no change I assemble the computer again after 38h disconnected backup- and working-batteries 
I'm go to computer repair tomorrow, see what they can do.......  :confused:

---

### Post by varunendra on 2013-11-11
> **leif-perjus said:**
> I'm go to computer repair tomorrow, see what they can do.......

Perhaps the best idea at the moment.. :|

---

### Post by sudodus on 2013-11-11
Could there have been a discharge pulse of static electricity, that has damaged some component in the computer?

---

### Post by Yellow Pasque on 2013-11-11
You should try hitting F9 (once) when the system comes on to see if you can start Recovery Mode.

Also, if you have the Intel NM10 chipset (you probably do), the maximum RAM is 4GB, but only in a 2x2GB configuration. A 4GB stick won't work.

---

### Post by leif-perjus on 2013-11-13
> **sudodus said:**
> Could there have been a discharge pulse of static electricity, that has damaged some component in the computer?

Today i got the computer back from repair company. The can not repair the Asus eee, they think same as you Sudodus. 
So i need a new motherboard !!

Someone have a eee (1015PED) with broken screen or keyboard... but the motherboard are ok, i'm interested to buy... !

---

### Post by sudodus on 2013-11-13
It's a good idea to ask here, and check some web sites where second hand computers are sold, for example Blocket. There are also several companies selling second hand revamped computers at reasonable prices.

---

