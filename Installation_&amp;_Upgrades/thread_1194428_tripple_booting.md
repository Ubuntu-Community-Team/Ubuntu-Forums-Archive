---
title: "tripple booting?"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by konnorrigby on 2009-06-22
Ok. I have an Hp computer with a 200 gb hard drive. I was looking to tri boot ubuntu, kubuntu, and windows XP. i allready have windows xp and ubuntu 9.04 dual booting on mi first hard drive and a want to put a second hard drive from mi other dell computer on mi hp computer and install kubuntu on it. so mi question is can i do this while being able to boot from a grub list. or something similer.
 
Thanks in advance.
-Konnor

---

### Post by running_rabbit07 on 2009-06-22
I only have 1 hard drive but I do have three OS. I have Ubuntu 9.04 EXT3, Ubuntu 9.04 EXT4, and the space waster that I call Windows XP. It boots fine. Grub automatically adds the necessary boot loaders to the menu. In my case it identifies the 2 different Ubuntus by showing thier hard drive designation but you shouldn't have to worry about that. Have fun.

---

### Post by konnorrigby on 2009-06-22
OK so it would work wyth 2 hard drives?
-konnor

---

### Post by running_rabbit07 on 2009-06-22
It should. I've never done that, so I can't make any promises. The operating systems treat each partition as a separate drive, so I don't see why it wouldn't work.

You said you have Ubuntu is already on your PC. Is it installed in a separate partition or inside Microsoft. I don't know if that'll make a difference but if answered it may be helpful when a more knowledgeable tech looks at the thread.

---

### Post by Polaris96 on 2009-06-22
This is a very common upgrade.  you should have no problems as long as:

1.  Make sure the jumpers on both HDDs are correctly addressed if they are IDE (big ribbon cables not scrawny ones).

2.  Make sure the BIOS setup utility queries your first HDD as the boot drive.  You can alter the BIOS settings, if necessary, by pressing DEL on startup.  You probably won't need to touch anything.

3.  Run the installer and follow the directions as they appear.  Make sure you install the new system on the new HDD.

4. Let the Grub Installer tweak out your grub settings automatically.

IF you have problems on reboot, they will likely be one of two things:

1.  You didn't get the boot priority right.  You can boot the new system but not the old one.  Go into BIOS startup and rearrange the HDDs so the original HDD boots first.

2.  The installer put grub on the wrong drive.  If this is the case, you'll get your "old" grub screen without a choice for the new OS.  you can use a text editor to grab the menu lines from the "new" menu.lst file and dump them into your otiginal /boot/grub/menu.lst

I'll be happy to walk you through either of those operations if you run into trouble.

---

### Post by konnorrigby on 2009-06-22
Ok. first i want to say thanks to both of yhu guys and also i wanto clairafi something: since i have an HP and im putting a Dell hdd on mi compuer will it work or will i have to get a special cord or something. im not reall good wyth the inside of a comuter. i know there is room for it.:-k
 
Thank you
-konnor
 
PS i dont know if this is a noobish question but what dus ide mean?

---

### Post by running_rabbit07 on 2009-06-22
The drive should work.

IDE (intelligent drive electronics) Also known as integrated drive electronics. A PC
       specification for small- to medium-sized hard drives in which the controlling
       electronics for the drive are part of the drive itself, speeding up transfer rates and
       leaving only a simple adapter (or “paddle”). IDE only supported two drives per
       system of no more than 504 megabytes each, and has been completely supplanted
       by Enhanced IDE. EIDE supports four drives of over 8 gigabytes each and more
       than doubles the transfer rate. The more common name for PATA drives. (See
       PATA.)

The above definetion was borrowed from the following manual;
CompTIA A+ Certification All-in-One Exam Guide by Mike Meyers

---

### Post by konnorrigby on 2009-06-22
thank you verry much im going to see if i can work this out in a couple days. ill let you know how it turns out.
 
Thanks
-Konnor

---

### Post by konnorrigby on 2009-06-22
Srry one last Question.
Since i have an hp And im putting a dell hdd on it will they agree wyth eachother?
and if they dont how do i fix that?

---

### Post by fugaki on 2009-06-22
as long as the jumpers are correct(IDE only) then it will recognize them both.
I have a gateway laptop with a hard drive from a toshiba in the second slot, but they were both manufactured by Western Digital, and it was plug and play.

---

### Post by konnorrigby on 2009-06-23
OK thanks. im going to tri it tomorrow and ill let yhu know it orks out.
-Konnor

---

### Post by konnorrigby on 2009-06-24
OK. So i got my computer back today. i went to look at the hard drive and it will not agree with my hp computer. so i just decided to put kubuntu on the original hdd.
 
All went well. kubuntu installed corectly. 
 
I just have a question how do i configure the grub menu? i just want it to boot up into windows first. i know its strange but i need it to because im sharing a computer and they arnt computer savi so windows is pretty native to them.

---

### Post by running_rabbit07 on 2009-06-24
Go to System> Administration>Synaptic Package Manager and search out and install StartUp-Manager. 

After it installs open it under System>Admin> amd in the Boot Options menu click on Default operating system and set it to the Windows boot loader.

 After doing this when you turn on the PC it will show the boot options but after a few seconds it will automatically load windows. 

This way you have the optin of scrolling to the _buntu of you choice when _you_ turn it on.

Tell your comrades to just let it boot when they turn it on and it will go to windows.

---

### Post by konnorrigby on 2009-06-24
thanks. but theres a problom. i cant get online with ubuntu or kubuntu. i am on dial up and i ave tried to get set up but it seems like alot of work if i can just boot into windows. therefor my question is can i download a .deb packedge to install it?

---

### Post by konnorrigby on 2009-06-24
Ok. sigh i figgured out the probloms with the hard drive. the one i was moving was an ide. and the hp was a sata. yea that was a problom.
 
so i googled it. and came up with a converter that changes ide to sereal. so im going to format my ide one and make that the slave and put ubuntu and kubuntu on it.
 
i now have a farlie good idea on what im doing now.

---

### Post by running_rabbit07 on 2009-06-25
Cool!

---

### Post by konnorrigby on 2009-06-26
Ok ive ran accross a knew problom. my old hdd was only 20gb. not gonna do meh much good. i figure ill just get a new sata hdd with more memory.
 
thanks all. you helped me alot
-konnor

---

### Post by Shazaam on 2009-06-26
See these for setting up dialup in Ubuntu...
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[https://help.ubuntu.com/9.04/internet/C/modem-identify.html](https://help.ubuntu.com/9.04/internet/C/modem-identify.html)
[https://help.ubuntu.com/9.04/internet/C/modem-connect.html](https://help.ubuntu.com/9.04/internet/C/modem-connect.html)
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

