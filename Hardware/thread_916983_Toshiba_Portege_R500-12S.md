---
title: "Toshiba Portege R500-12S"
date: 2008-09-11
forum: Hardware
---

### Post by escifell on 2008-09-11
Has anyone tried to install ubuntu (or any other variety of linux) on a Toshiba Portege R500-12S (the one with the solid-state memory and only weighs 0.8kg). 

If it is a non-starter, it could be an expensive mistake to purchase as I must be able to run linux.

Processor       1 x Intel® Core™2 Duo U7700, 1.33GHz, 533MHz
Chipset         Mobile Intel 945GMS Express
Cache           2MB - L2 Cache
Hard Drive      128 GB Solid State Drive - Serial ATA-150
Networking      Ethernet Fast/Gigabit
                IEEE 802.11b/g/n (draft)
                Bluetooth 2.0 EDR
RAM             2GB (installed) / 2GB (max) - DDR II SDRAM - 667 MHz
Graphics Controller     Intel GMA 950 Dynamic Video Memory Technology 3.0
Display         12.1" WXGA+ TFT (1280 x 800)

Dimensions      28.3 cm x 21.6 cm x 2.6 cm
Weight          0.8 kg

Thanks
Richard

---

### Post by msr3000 on 2008-09-29
Hi Richard,

I can see you didn't get many replies. Did you find information elsewhere? Or did you actually buy the computer and tried to install Linux yourself?

---

### Post by escifell on 2008-09-29
You are right - no replies, also not much out there on Google so I have decided to purchase one and give it a go.

I will report progress here over the next few weeks, just in case anyone is interested.

Richard

---

### Post by msr3000 on 2008-09-29
At least you can count me as highly interested. I am going to buy a laptop in the next few weeks...

And yes, there is not much on Linux and R500-12s on the internet. But Linux seems doable for other R500 versions. Let's hope the hardware isn't very different.

/Matias

---

### Post by esplinter on 2008-11-20
Hi,

I have a toshiba portege r500 with ubuntu intrepid x86_64 installed on it.

I can confirm all hardware works great under linux without any special tweaks to make it work.

acpi, vga, ethernet, wifi, audio. everything working out of the box.

---

### Post by escifell on 2008-11-24
Hi

I successfully installed Ubuntu (8.04). When the laptop arrived the 'disk' had three partitions, one small then two large: one with windows system; and one labelled data with a couple of folders/files (I did this some time ago and this is written from memory so details may not be exactly right). I created a folder called data in the windows system partition and copied these odd folders/files over. I then ran 'parted' and deleted the data partition and squeezed the system partition to give me 80Gb for linux.

I then booted from the live install CD, and installed from the desktop icon. Basically no problems though I did loop around the disk partitioning a couple of times, as I was not convinced that the default values were best. I like 3 partitions, 1 for the system, 1 for swap, and 1 for home (all partitions formated as ext3.

Everthing works OK except:
1) sound if I plug in external speakers or headphones the sound still comes out on the laptop speakers (could be a problem if you don't want your music broadcast
2) I want to use a port replicator and large screen when in the office and I have had no luck in configuring the video (though I have not given this much effort other than to note that it was not as simple as just plugging it in)
3) windows complained when I first tried to boot back to windows saying that it been damaged (too right it had). But after a 'repair' it seemed to be happy. 

Richard

---

