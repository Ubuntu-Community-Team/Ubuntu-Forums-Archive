---
title: "Installing Linux on a laptop"
date: 2009-02-18
forum: Hardware
---

### Post by CommandoGuard on 2009-02-18
I intend to purchase the [MSI EX400]("http://asia.msi.com.tw/index.php?func=newsdesc&news_no=653") laptop. It has an Intel Core2 Duo processor and an ATI Mobility Radeon HD3450 graphic card. Do you think I'll have any problem installing Ubuntu (specifically, Intrepid Ibex) on the laptop?

---

### Post by cmay on 2009-02-18
run the live cd to find out. i used a usb stick wiht a live version i made from a utility called unetbootin to try out my new laptop before i ordered it. it turned out to be better than i expected when it was installed. the video and sound i could not anything should be wrong wiht but it could not find the webcam when running the live usb stick that has do with the gsttreamer plugins that are not on the live cd so when i got home and installed intrepid ibex on it everything just worked out of the box. 

if however it seems that sound is not working and network cant be detected (not wireless as it can be tricky to see at first if it works or not) and other stuff whihc should be working right out of the box and dont  then i would think about googling for the hardware compatibilty on the laptop based on the specs. 

hope you find a answer to this.

---

### Post by binbash on 2009-02-18
you will have wireless problems if that is atheros chipset(it does not write the chipset but other msi notebooks have atheros) but it is easy to fix

---

### Post by stchman on 2009-02-18
> **CommandoGuard said:**
> I intend to purchase the [MSI EX400]("http://asia.msi.com.tw/index.php?func=newsdesc&news_no=653") laptop. It has an Intel Core2 Duo processor and an ATI Mobility Radeon HD3450 graphic card. Do you think I'll have any problem installing Ubuntu (specifically, Intrepid Ibex) on the laptop?

If you intent to buy a laptop to run Linux on then go to the Ubuntu laptop wiki.

[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

There are many entries for laptops that folks have tested.

Also take a look at the hardware specs on the laptop.

I would recommend the following:

Intel chipset
Intel or Nvidia video
Intel or Atheros wireless

If it looks like Intel plays well with Linux.... it does.

Avoid Broadcom, ATI, Creative X-Fi as they are Linux unfriendly.

---

### Post by Ailis on 2009-02-19
I got my MSI EX400 yesterday, and have not been able to successfully install linux. I've tried both ubuntu (both 32-bit and 64-bit) and opensuse, but I run into the same problem each time. I boot from the cd/dvd and the first menu shows up fine. But when i choose 'install' I can hear the optical drive speeding up and then subside. The ubuntu install just halts with a black screen. Nothing more shows up. For the suse install it first says that it's loading the kernel before a progress bar shows up that doesn't move an inch. No activity from the hard drive or the optical drive. I also tried to run the live cd of suse from within vista and it too froze after loading the kernel. 

I've reinstalled windows vista without any problem (both business and enterprise). I've tried to reformat the whole hard drive and repartioning it (in vista) and I've tried to update the BIOS. I have no clue whatsoever where to go from here. I'm googling for my life here. :p

If anyone has any bright ideas, I'd appreciate it. If I make any progress on my own I'll let you know. I cannot understand why it doesn't work.


Ailis

---

