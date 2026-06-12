---
title: "Acer Aspire 5315 fan script not working"
date: 2017-10-01
forum: Hardware
---

### Post by rgonzalez3894 on 2017-10-01
Hello everyone, 

My 2007 acer aspire 5315 recently had windows vista removed and lubuntu installed so it runs much faster.

However, the fan that cools the interior was not working, so I checked on ubuntu forums and it seems like someone made a bash script
called acer_fancontrol in the following link:

[https://ubuntuforums.org/showthread.php?t=1748521](https://ubuntuforums.org/showthread.php?t=1748521)

I followed all the steps but the fan still does not turn on when the computer is running. 

I would appreciate any help, thanks.

---

### Post by Kirboosy on 2017-10-02
Let me be the first to welcome you to the forums! :)

I also read in that thread that a BIOS update fixed another users issue. Have you tried to update your BIOS?

Also which line did you un-comment for your system?

What version of Lubuntu did you install? 32 or 64 Bit?

Hope that helps!
~Caboose

---

### Post by rgonzalez3894 on 2017-10-02
Hi there, 

I have a 32 bit system with 1 GB RAM so I uncommented the line underneath the one that says 1 GB RAM. 

I installed the 32 bit lubuntu and I have not updated the bios which I am not certain it is possible since most people say that it could only be done through windows OS. Is it possible to get a virtual machine with windows vista and then proceed to update the bios or would that not have an effect on my actual bios?

---

### Post by Kirboosy on 2017-10-02
I believe your issue is the script is written for 64 bit systems and you are on 32 bit.

Try manually running the script and see if it gives you an error.

---

### Post by rgonzalez3894 on 2017-10-02
[FONT=Calibri,Helvetica,sans-serif][SIZE=3][COLOR=black][FONT=Calibri]after typing 
acer_fancontrol 
into the command line, I get a bunch of lines reading something like the following message:

 
 
 /usr/bin/acer_ancontrol: 133:  /usr/bin/acer_fancontrol: Cannot fork
 /usr/bin/acer_fancontrol: 169: [: Illegal number:

[/FONT][/COLOR][/SIZE][/FONT]

---

### Post by rgonzalez3894 on 2017-10-02
is it possible to edit the script to work on a 32 bit system?

---

### Post by mörgæs on 2017-10-02
> **rgonzalez3894 said:**
> ...since most people say that it could only be done through windows OS.

Most people could be wrong. If you run a Freedos live boot you might be able to upgrade from here.

---

### Post by Kirboosy on 2017-10-02
> **mörgæs said:**
> Most people could be wrong. If you run a Freedos live boot you might be able to upgrade from here.

+1 

I have personally used FreeDOS on systems to upgrade the BIOS and I haven't had any issues. However the systems I upgraded on were Asus, and Dell so your mileage may very.

Also it might be easier to just install 64 bit on the system rather than try to rewrite a script.

---

### Post by rgonzalez3894 on 2017-10-02
how do I get a 64 bit, new processor perhaps?

---

### Post by Kirboosy on 2017-10-02
From what I have read your computer already supports 64 bit. You just need to download a 64 bit version of LUbuntu

If you were running 16.04 you can download that from: [https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS](https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS)

~Caboose

---

### Post by rgonzalez3894 on 2017-10-02
I checked through the terminal my system's specs and it is a 32 bit system.

---

### Post by Kirboosy on 2017-10-03
> **rgonzalez3894 said:**
> I checked through the terminal my system's specs and it is a 32 bit system.

You will have to completely reinstall Ubuntu on the system. There isn't a way to upgrade from 32 bit to 64 bit. The only way is to reinstall your system completely. Make sure you backup all your data.

---

### Post by mörgæs on 2017-10-03
> **rgonzalez3894 said:**
> I checked through the terminal my system's specs and it is a 32 bit system.

How did you check? Please post the output of **lscpu** in CODE tags.

---

### Post by rgonzalez3894 on 2017-10-03
> **mörgæs said:**
> How did you check? Please post the output of **lscpu** in CODE tags.

Hi I used the command 

cat /proc/cpuinfo

and 

arch

both showed outputted i686 which is a 32 bit.

---

### Post by rgonzalez3894 on 2017-10-03
> **Caboose885 said:**
> You will have to completely reinstall Ubuntu on the system. There isn't a way to upgrade from 32 bit to 64 bit. The only way is to reinstall your system completely. Make sure you backup all your data.

So does the bit of the system depend on the OS and not on the physical limitations of the cpu?

---

### Post by Kirboosy on 2017-10-03
> **rgonzalez3894 said:**
> So does the bit of the system depend on the OS and not on the physical limitations of the cpu?
From what I read on the [Acer website]("https://www.acer.com/ac/en/US/content/support-product/50;-;Aspire+5315") they have Windows Vista 64 Bit drivers for your laptop. That would lead me to believe that the processor does support the 64bit instruction set.

---

### Post by rgonzalez3894 on 2017-10-03
> **Caboose885 said:**
> You will have to completely reinstall Ubuntu on the system. There isn't a way to upgrade from 32 bit to 64 bit. The only way is to reinstall your system completely. Make sure you backup all your data.

I may just reinstall the 64 bit version of lubuntu because it says on the website that PCs older than 2007 are usually not 64 bit compatible and I got the acer aspire in 2007 so it most likely will accept the 64 bit lubuntu. However, is the bit of the system the cause of the issue with running the fan script?

---

### Post by Kirboosy on 2017-10-03
> **rgonzalez3894 said:**
> However, is the bit of the system the cause of the issue with running the fan script?

I believe it is part of the problem. I think a BIOS update will be the best solution, but it won't hurt you to upgrade lUbuntu to 64 bit. 

Keep in mind that the script you are trying to use was written in 2008 so there might be slight issues with the script as kernels and utilities change.

---

### Post by rgonzalez3894 on 2017-10-07
> **Caboose885 said:**
> I believe it is part of the problem. I think a BIOS update will be the best solution, but it won't hurt you to upgrade lUbuntu to 64 bit. 

Keep in mind that the script you are trying to use was written in 2008 so there might be slight issues with the script as kernels and utilities change.

Hi I upgraded the laptop to the 64 bit lubuntu and reinstalled the acer_fancontrol files, and the fan actually worked for the first 3 times that I rebooted the laptop

However, after a shutdown and restart, the fan does not come on anymore.

---

### Post by mörgæs on 2017-10-08
Please copy ```
sudo lshw -sanitize > lshw.txt
``` to the terminal, run it and post lshw.txt in CODE tags.

---

