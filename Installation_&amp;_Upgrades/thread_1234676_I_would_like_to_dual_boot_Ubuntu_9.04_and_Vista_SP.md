---
title: "I would like to dual boot Ubuntu 9.04 and Vista SP1"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by makinasvp on 2009-08-08
Hello there, I would like to have a dual boot on my computer. Right now I am running on Windows Vista Ultimate SP1, and would like to install ubuntu 9.04.
Can someone please help me on how to properly do it without any conflicts whatsoever? Please?

My computer specs are:

-AMD FX-60 Dual core processor
-Asus A8N32 SLI Deluxe mobo
-ATI HD 4870 video card


I have a single 1TB HDD, and Windows Vista is using 203GB out of 931GB, which means I have 728GB free of space.

I mostly use Windows Vista for gaming, but would like to use Ubuntu for absolutely everything else. 

Can someone please help me how to do so. I do remember trying to dual boot Ubuntu and Windows myself once, but I realyl messed it up and I didn't even have the option to choose between the 2 OS's when I would restart my computer. Please help!!  :)

PS: I've already downloaded Ubuntu 9.04 and burnt it onto a disc, so I am all set to go. What's my first step?

---

### Post by Partyboi2 on 2009-08-08
Hi, you can follow this guide through
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by makinasvp on 2009-08-08
Would this work if I would like to install Ubuntu Studio 9.04? Or just Ubuntu 9.04? Because i am very attracted to Ubuntu Studio... lol

---

### Post by mikewhatever on 2009-08-08
I figure the first step was downloading. Just follow the installation guide.
[https://help.ubuntu.com/community/GraphicalInstall?action=fullsearch&context=180&value=linkto%3A%22GraphicalInstall%22](https://help.ubuntu.com/community/GraphicalInstall?action=fullsearch&context=180&value=linkto%3A%22GraphicalInstall%22)

---

### Post by makinasvp on 2009-08-08
am i going to need a swap partition or something? I am so confused...

---

### Post by mikewhatever on 2009-08-08
> **makinasvp said:**
> am i going to need a swap partition or something? I am so confused...

Swap is usually recommended.

---

### Post by makinasvp on 2009-08-08
On PartyBoi's link they don't tell you to have a swap... I don't get it...
If I start up my computer, and want to choose whether I want to load Ubuntu or Vista, will I be able to? At this point this is my MAIN concern. Last time I have tried this, I could not launch Vista anymore and had to erase Ubuntu and reinstall Vista. I am a hardcore gamer so I cannot get rid of Vista... But would like to use Ubuntu for everything else.

---

### Post by garikaib on 2009-08-08
You can choose automatic partitioning if you have one disk. But it is prudent to partition your hard using a partitioning manager like Partion Magic.

---

### Post by makinasvp on 2009-08-08
> **garikaib said:**
> You can choose automatic partitioning if you have one disk. But it is prudent to partition your hard using a partitioning manager like Partion Magic.

Well that's the thing, I have windows vista installed and it comes with "Disk Management" which allows me to do that... Here let me take a screenshot...

[IMG]http://i26.tinypic.com/zxqc6.jpg[/IMG]

---

### Post by garikaib on 2009-08-08
A swap partion is mandatory. The rule of thumb is to have a swap partition twice the size of your RAM.

---

### Post by theozzlives on 2009-08-08
> **makinasvp said:**
> am i going to need a swap partition or something? I am so confused...

You'll need to resize your NTFS partition using Vista's tool. Yes you should have a swap 2x the amount of RAM, I also recommend a /home partition to hold your files and settings. The root (/) partition only need be about 10 GB.

---

### Post by garikaib on 2009-08-08
You say you want Windows for gaming which means you need to reserve more space for your games. Depends on your needs. If you have nothing in the volume labelled D: Just restart your computer and boot from your CD and when the partitioning option shows up delete the partition. It would normaly be shown as sdb but just double check if this is really D by looking at the size. Then choose automatic partioning.

---

### Post by Partyboi2 on 2009-08-08
> **makinasvp said:**
> On PartyBoi's link they don't tell you to have a swap... I don't get it...
If I start up my computer, and want to choose whether I want to load Ubuntu or Vista, will I be able to? At this point this is my MAIN concern. Last time I have tried this, I could not launch Vista anymore and had to erase Ubuntu and reinstall Vista. I am a hardcore gamer so I cannot get rid of Vista... But would like to use Ubuntu for everything else.
The swap is automatically created for you when you chose the "Use the largest continuous free space" option at the partitioning stage of Ubuntu.

---

### Post by makinasvp on 2009-08-08
> **Partyboi2 said:**
> The swap is automatically created for you when you chose the "Use the largest continuous free space" option at the partitioning stage of Ubuntu.

OOOOOOOOOOOH so I don't need to manually do it huh?? Just choose "Use the largest continuous free space" and it'll do it for me?
Ok so once I'm done shrinking my C drive for Ubuntu, just install it on the free space? 

Oh and Partyboi2, if I install UbuntuStudio 9.04, will it be the same process?? or is it just for Ubuntu 9.04?

---

### Post by makinasvp on 2009-08-08
Quick noob question though, how do I properly burn Ubuntu 9.04 or UbuntuStudio 9.04 onto a disc in order for it to boot when I startup my computer?

---

### Post by mikewhatever on 2009-08-08
From the look of the image name, Ubuntu studio uses a different text based installer, while the guides provided only apply to Jaunty-9.04 with the graphical installer. You will also need a swap partition with Studio, but, as said, the installer is different, and is a bit harder to use.

Edit: Burning guide [https://help.ubuntu.com/community/BurningIsoHowto?action=fullsearch&context=180&value=linkto%3A%22BurningIsoHowto%22](https://help.ubuntu.com/community/BurningIsoHowto?action=fullsearch&context=180&value=linkto%3A%22BurningIsoHowto%22)

---

### Post by Partyboi2 on 2009-08-08
You can follow [[COLOR=Blue]this[/COLOR]]("https://wiki.ubuntu.com/BurningIsoHowto") on how to burn the iso to disk. The install steps a slightly different (not my much) I think for installing Ubuntu Studio. 
Once you have installed Ubuntu you could always install the Ubuntu Studio packages as another option.

Edit:>  OOOOOOOOOOOH so I don't need to manually do it huh?? Just choose "Use the largest continuous free space" and it'll do it for me?
Correct, but make sure you use Vista to shrink down the Vista partition first as mentioned in the guide I provided.

---

### Post by theozzlives on 2009-08-08
Attached are my partitions, mind you sda1 would be NTFS on yours and you wouldn't have a /root (I have my reasons). Course I did mine manually.

---

