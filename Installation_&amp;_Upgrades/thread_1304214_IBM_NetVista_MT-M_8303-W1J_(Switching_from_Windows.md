---
title: "IBM NetVista MT-M 8303-W1J (Switching from Windows to Ubuntu)"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Shahnawaz on 2009-10-29
Hi,
I'm intending to migrate to Linux Ubuntu from Windows XP Service Pack 3.
Here are my System details:

Processor: 
Pentium (R) 4 CPU 1.70 GHz 
(ACPI\GENUINEINTEL_-_X86_FAMILY_15_MODEL_1\_0

512 MB of RAM

Network Adapter:
Intel(R) PRO/1000 MT Network Connection

Onboard audio:
Integrated PCI AC'97
ADI 1981A CODEC
SoundMAX 3.0 with SPX

Webcam
A4 TECH PC Camera V

Display Adapter
Intel (R) 82845G/GL/GE/PE/GV Graphics Controller

Disk Drive:
ST3802110 A   (I guess it's my hard disk, and it's 80 GB)

DVD/CD-ROM:
SONY CD-RW CRX320EE

Printer:
HP PSC 1402

I want to know, if I install Ubuntu, will my all hardware work well and supported by Ubuntu OS?
If Ubuntu, won't automatically detect and install drivers for my Network Adapter, I won't be able to connect to internet. So if I have to download drivers from web, can you tell me where to download? so I may download and keep a copy of them in my data traveler USB device.

Will I be able to use my webcam in the messengers like MSN, Yahoo and Skype with my friends using Windows?

I have 4 partitions on my Disk, 3 are NTFS and one is FAT32
Can I just delete the C partition, and create a new one instead of it to use Ubuntu?
OR should I delete all the partitions? back up all the data of all the partitions? and then create all new partitions for Ubuntu?

And Can I install Ubuntu from a USB data traveler (Kingston) ? Because my CD writer isn't working properly.

Thanks in advance for your help.

Shahnawaz Jamot

---

### Post by Mark Phelps on 2009-10-29
> **Shahnawaz said:**
>  ... I want to know, if I install Ubuntu, will my all hardware work well and supported by Ubuntu OS? 
Boot from the LiveCD and try it out. That way, you will be able to tell how well it detects your hardware and installs the correct drivers.  

> If Ubuntu, won't automatically detect and install drivers for my Network Adapter, I won't be able to connect to internet. So if I have to download drivers from web, can you tell me where to download? so I may download and keep a copy of them in my data traveler USB device.
It's generally a bad idea to ask a long list of questions in a single post because those of us who respond tend to read the thread title -- and will miss the details buried in the post.  Better solution is to do the following: (1) search the forum for threads dealing with your specific make and model hardware, (2) look in the PROPER forums (i.e., Networking for networking, Video for video, etc.), only if you can't find anything, then start a thread for your specific problem -- again, in the proper forum.
>  Will I be able to use my webcam in the messengers like MSN, Yahoo and Skype with my friends using Windows?  These are notorious problems.  As above, search the forums first, then, post threads for each of them.
> 
I have 4 partitions on my Disk, 3 are NTFS and one is FAT32
Can I just delete the C partition, and create a new one instead of it to use Ubuntu? OR should I delete all the partitions? back up all the data of all the partitions? and then create all new partitions for Ubuntu?
Don't know what's IN your partitions, but generally, in MS Windows, "C" partitions contain the OS. So, if that's true on your box, deleting it will remove any possibility of dual-booting.

You will need two partitions for Ubuntu -- swap needs a partition. With four primary already on your drive, deleting one partition will require that you create an Extended partition in it's place and create the two Linux partitions inside it.

> And Can I install Ubuntu from a USB data traveler (Kingston) ? Because my CD writer isn't working properly.

Yes, as above, search the forums on this topic and you will find threads and tutorials for installing from USB drive.

---

### Post by Shahnawaz on 2009-11-01
Hi Mark, thanks for the help.
I just read your reply now.
Sorry for asking all those questions in a single forum.
I tried Live CD and I could access to internet. Sound and Video worked too. Webcam also working and haven't tried HP printer yet.
I deleted all the partitions, and installed Ubuntu on entire disk. So I guess ubuntu by default made 2 partitions.
I installed Ubuntu from the CD.
I'm just having a problem to install Emesene 1.5-1, I posted it in a new thread.
Thanks again.
Have a nice day.

---

