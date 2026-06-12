---
title: "HPPavilion dv8000 install problem"
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by The Shadow on 2006-07-30
H:
 I have an HP Pavilion dv8000 with an AMD Turion64 process. I am attempting to install Ubuntu 6.06 (AMD64 version) on a second 80GB harddrive. When i boot from the CD I get a list of options for "booting from CD or Installing" "start in safe mode" "check CD for errors" "x86 memory test" or "boot from drive 1". If I select option 1, 2, or 3 I get the following error:

Kernel Panic - Not Syncing: Attempt to Kill init!"

The memory test completed with no errors.

Any suggestions?

---

### Post by The Shadow on 2006-07-30
OK. I used the acpi=off boot option and am now able to get the live CD to boot.:D 

Now the problem is that thenetwork/internet does not work. Any suggestions? :confused:

---

### Post by nrwilk on 2006-07-30
I'm sorry to say that I don't have an answer to your question.

But, I'm soon getting an HP dv8000t, and I wanted to ask you if you'd keep us posted on how well it does with ubuntu.  So, if you feel like letting us know how the machine is doing with ubuntu, please post here!

Thanks so much! :D

---

### Post by Amaranth on 2006-07-31
The hardware in the dv8000z is completely different than the hardware in the dv8000t. I have a dv8000t and when I first installed dapper I had to manually install the ipw3945 drivers then everything worked, even suspend and hibernate. I have never again been able to get those working again.

---

### Post by The Shadow on 2006-07-31
I would be glad to. So far I have had several problems; the biggest one is being a nubie. I don't know how to manually install drivers and am having difficulty with the command line. I edited the /etc/X11/xorg.conf file to try and turn off the touch pad button click and now the ssytem will not boot. I am trying to figure out how to edit the file from the recovery mode command line.

---

### Post by The Shadow on 2006-08-01
My system is up and running again, although the Wireless card is still not working. I tried installing the driver using ndiswrapper using several different versions of the driver, no joy so far. I will attempt to find the xp driver that came with the machine and see it that will solve the problem. 

Sure would like to have it working so i wouldn't have to re-boot into xp to find help and fix problems.

---

### Post by nrwilk on 2006-08-02
> **Amaranth said:**
> The hardware in the dv8000z is completely different than the hardware in the dv8000t. I have a dv8000t and when I first installed dapper I had to manually install the ipw3945 drivers then everything worked, even suspend and hibernate. I have never again been able to get those working again.

I am aware that some of the hardware is different, but some is the same.  The touchpad, etc...

I'm glad to have found another person who has tried ubuntu on a dv8000t, though.  Instead of hijacking the thread, may I PM you with some questions? :D

---

### Post by Amaranth on 2006-08-02
I don't have much to say about it. When I first installed dapper I had to manually install ipw3945 drivers then everything but the card reader and maybe the modem worked. The sound is really quiet compared to Windows, don't know why, not even Ubuntu's sound guy can fix it. I had suspend and hibernate working perfectly at one time, one day they stopped working and I've never been able to make them work again. That's all I know about it.


Edit: Oh, and the battery lasts about an hour less in Ubuntu than Windows. Luckily I have two batteries so having one only last 3 hours is ok.

---

### Post by govijay on 2006-08-28
I too have a dv8000 and the problems are just numerous.

acpi=off gets the install to work -- but no acpi functionality, so hibernate, suspend ???? -- major features for a laptop

irqpoll gets the on board ethernet to work

ATI drivers do not work period

If I could, I would return this HP laptop and pick a platform that is supported. 

Note: Battery life and HEAT!! are a major problem.

Is there a website where the latest laptops are shown to work properly with ubuntu and other major linux distributions?

Thanks

---

### Post by Amaranth on 2006-08-28
Sounds like the dv8000z is a major dud, I'm glad I got the Intel/nVidia version (dv8000t).

---

### Post by nrwilk on 2006-08-28
> **Amaranth said:**
> Sounds like the dv8000z is a major dud, I'm glad I got the Intel/nVidia version (dv8000t).

Same here.  ubuntu is working great on my dv8000t.

I'm sorry the z model isn't working out so well. :(

---

