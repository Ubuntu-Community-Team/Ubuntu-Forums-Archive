---
title: "Using external usb disk as extra partition"
date: 2015-03-12
forum: Hardware
---

### Post by joo7 on 2015-03-12
I searched a lot on the internet but have not find an exact match for this question, so please excuse me if any doubt is stupid.


  So, I have Linux 32-bit installed on my computer and I'm running  out of space because my original disk is small. I have an external usb  disk with 300Gb (and a Sata that is only lacking an eclosure to be fully functional) and so I was thinking of connecting it/them to the computer  and put it to function as another partition where I can install  programs.


  My questions are:
  
[LIST=1]
[*]Can I do this easily? Is this a question of just mounting the external drive to a folder?
[*]What happens when I disconnect and then connect again the usb storage disk, won't I have troubles with the previously installed programs?
[*]Does the usb disk need to be formatted and/or does one need to put a linux OS in the disk?
[*]If the answer to "can I install programs to the external usb" is  yes, when I execute the programs from that mounted partition i.e. the  external usb drive, are they going to be slower? And does the answer  depend on whether the drive is a USB 2.0 or USB 3.0 (or eSata)?
[/LIST]

---

### Post by sudodus on 2015-03-12
> **joo7 said:**
> I searched a lot on the internet but have not find an exact match for this question, so please excuse me if any doubt is stupid.


  So, I have Linux 32-bit installed on my computer and I'm running  out of space because my original disk is small. I have an external usb  disk with 300Gb (and a Sata that is only lacking an eclosure to be fully functional) and so I was thinking of connecting it/them to the computer  and put it to function as another partition where I can install  programs.


  My questions are:
  
[LIST=1]
[*]Can I do this easily? Is this a question of just mounting the external drive to a folder? 
[*]What happens when I disconnect and then connect again the usb storage disk, won't I have troubles with the previously installed programs? 
[*]Does the usb disk need to be formatted and/or does one need to put a linux OS in the disk? 
[*]If the answer to "can I install programs to the external usb" is  yes, when I execute the programs from that mounted partition i.e. the  external usb drive, are they going to be slower? And does the answer  depend on whether the drive is a USB 2.0 or USB 3.0 (or eSata)? 
[/LIST]


1. For data files, yes. For programs, no.

2. You should always unmount the partition(s) on the disk before unplugging it. It is a bad idea to install programs in an external disk.

3. If you have only linux in the computer, use a linux file system 'format to a linux file system' for example ext4. If you dual boot with Windows, use the file system NTFS for easy access from both operating systems.

4. You can have the whole linux operating system on an external disk or even a USB pendrive, and the speed depends a lot on the transfer speed of the protocol and on the hardware (pendrive flash, disk, SSD, ...). eSATA and USB 3 are fast, USB 2 slow and USB 1.1 very slow.

See also these links

 			 			[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389") 				

  			 			[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858") 				

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by joo7 on 2015-03-13
Thank you very much for the answer.

So, like you said many times it's a bad idea to install programs to external disks (can you tell me why btw?) . But the main purpose of me using an external disk was that I need to install a couple of heavy programs that occupy 40+ Gb.
If I can't (or shouldn't) do that, what other way do I have to install these heavy programs alongside my nearly-full computer?

---

### Post by sudodus on 2015-03-13
Programs should be available not only when you want to run them, but also when the system finds new program packages and wants to update/upgrade them.

Linux programs are usually rather small and occupy not too much space. But your programs are certainly different, and you can always make an exception. Sometimes the executable part can be small and in the system partition, and heavy data files or data bases can be put somewhere else. It might be easy or hard to reconfigure that.

Are we talking about native linux programs or Windows programs that you run via Wine (or similar)?

It makes a big difference what kind of external connection you have. eSATA and USB3 are fast, while USB2 is slow, not good if you need to manage huge amounts of data.

It is even possible to boot a whole linux system from an external drive (a separate system from that in the internal drive). It works well with eSATA and USB 3 for me. And a basic linux system is often less than 4 GB, and works well in a 8 GB pendrive or disk. So in your case maybe it is easiest with a separate linux system including your heavy programs in an external disk.

See this link [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by joo7 on 2015-03-13
The programs I'm talking about are Xilinx programs (that can be for Windows or Linux), Vivado, Vivado HLS and SDK which occupy a large amount of data.

I'm now testing with a 8Gb pen drive to install just one of those programs there and see if I'll have any trouble when running the program. So far it's taking a looott of time just to install the program in the usb, but as you said, it's a simple 2.0 connection.

That link you sent is going to be my final solution if this doesn't work.

---

