---
title: "Does anyone use this in a production environment?"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by breauxlg on 2009-09-03
I had a server with windows small business server 2003 installed on it that ran for 5 years without me ever having to reload it. I bought a new server with windows server 2008, so I decided to load Ubuntu on the old server (which never gave me any trouble.) I followed one of the perfect server tutorials and got it up and running. 

I was really excited to get this done and was telling everyone about how fast the setup was and how everything, including my Epson All-in-one just worked.

I saw the ispconfig tutorial and decided to add that to my server. It killed the server and I found out after posting a question on the forums that the entire ispconfig install tutorial must be followed, although that was not made clear on the tutorial. 

I started again from scratch and got the server up and running again, reloaded my content again, and got the web and mail server running again. This is a straight Ubuntu-only install, not dual boot, or anything like that. 

I had a power outage, the battery backup ran down and when power came back on, I went to boot my servers, and the iSeries came up fine, the Windows 2008 server came up fine and the Ubuntu server could not find grub - not that it was obvious - at the time it just would not boot. It took some research to find out the grub was missing. I have been through several questions on the forum that were like mine, but none of the has worked. It appears that the disk configuration is hosed. 

I followed one of the backup tutorials that I found on the forums, but it backs up the system onto the same hard disk that the system is on. I tried to find a backup that would let me save to my secondary hard drive and couldn't find a way to mount that hard drive, much less backup to it. 

I guess I have a few of questions: 

Is there anything comparable to the disk management function on Windows server for mounting additional hard drives?

Is there an imaging program that will let me make a copy of my primary hard drive that can either be booted, or easily restored?

Am I wasting my time trying to get this to work? Is 9.04 stable enough to actually try to use in a production environment?

I am at the point of having to reload once more, I guess. I'm not nearly as excited as I was the first time I loaded the system. I guess I'll have to reload the web sites and email domains, etc.

I would really like to get an idea of how to NOT have to reload when problems like this arise. This will probably be the last time I try this.

Sorry to sound so down, but this has taken a lot more of my time than I expected. I'm no genius, but I've got a degree in Computer Science and have been making my living developing software since 1977 and have had my own company since 1982 and I can't get this to work. I can see a lot of potential, but have not been able to tap the potential for myself. 

By the way, my goal is to setup a web and mail server and create a drupal website for a non-profit organization to let Christian bands and Christian venue's connect via searchable criteria. i.e. A heavy metal Christian band will play for free within a 100 mile radius of their home town. A progressive church 50 miles away wants a band to come to their facility to provide alternative-style Christian music to their youth group. If they were both users of my website, I would like for them to be able to find each other easily. 

Thanks in advance for any advice.
Lynn

---

### Post by tgalati4 on 2009-09-03
That's a lot of stuff for one post.

Was there a reason for not running apcupsd to shut down the server cleanly during battery use?

Sounds like a RAID controller or hard disk issue.  Old servers have wear issues.  Unless you have installed new drives and cleaned the machine out, I would expect no reliability.

Hard drive failure rises after 3-5 years of continuous use according to Google's research.  And they go through a lot of hard drives.

sudo cp /dev/sda /dev/sdb will make a workable image on a second hard drive that is similar size.  You can also use dd if you need a bit-by-bit image.

I'm not familiar with Windows disk management.  In linux, drives are mounted with a simple mount command.  They are automatically mounted with an entry in /etc/fstab.

One question per post will streamline your journey into linux.

Just curious, in your five years of Server 2003 use, how many times did you have to reboot it?

---

### Post by falconindy on 2009-09-03
> **breauxlg said:**
> Am I wasting my time trying to get this to work? Is 9.04 stable enough to actually try to use in a production environment?
If you're looking for absolute stability for a production server go with 8.04, which is the latest LTS release of Ubuntu. You'll see mixed reviews on these forums about system stability with 9.04. I won't hypothesize about the possible correlation between stability and user proficiency. ;)

Also, if you're not already, you should be using the server edition of Ubuntu or at least recompiling the kernel with the server modules.

---

### Post by breauxlg on 2009-09-03
Sorry about the length of the post.

The reason for not shutting down the servers cleanly was that I was 330 miles away when the power failed. 

I put two new hard drives in before starting this project. I'm aware of the fact that "things with moving parts" rank right behind power supplies in the weakest link department. 

"sudo cp /dev/sda /dev/sdb will make a workable image on a second hard drive that is similar size. You can also use dd if you need a bit-by-bit image." 
Thank you very, very much. That is exactly what I needed to know. I must have been searching on the wrong terms, because I really did try to find that. 

"I'm not familiar with Windows disk management. In linux, drives are mounted with a simple mount command. They are automatically mounted with an entry in /etc/fstab."
Can you point me to a good reference book or document that will explain how linux recognizes the drive, the naming conventions and a description of the mount commands? It seems as though there are gazillions of references and I have no clue as to which one would be most useful to me. 


"Just curious, in your five years of Server 2003 use, how many times did you have to reboot it?"
I kind of figured I'd get some of the old Linux vs. Windows smackdown type of response, but no offense intended. In fact I rebooted the Windows Server very infrequently, but then I was just using it as a file/web/mail server. Also, I really, really hate Windows as well as Microsoft, but I have been able to do what I need to do, albeit after jumping through many unnecessary (to me) hoops. 

I do very much appreciate the time you folks contribute to these forums. 
Thanks,
Lynn

---

### Post by breauxlg on 2009-09-03
"If you're looking for absolute stability for a production server go with 8.04, which is the latest LTS release of Ubuntu. You'll see mixed reviews on these forums about system stability with 9.04. I won't hypothesize about the possible correlation between stability and user proficiency. "
Thanks for that info. I was not aware the there could be that much difference, but I'll definitely go with 8.04, because I know there is a correlation between stability and user proficiency, and I am not by any means proficient.

"Also, if you're not already, you should be using the server edition of Ubuntu or at least recompiling the kernel with the server modules. "
I loaded the server version, but I really, really need the graphical interface because of my ignorance of command line usage, so I added the GUI (Gnome?) over the server. When the instructions called for me to use vi, I started a terminal session, ran nautilus with the sudo prefix and just browsed to the file and then opened it with the text editor. I did see after I installed that way, that I maybe should have installed the desktop version and then added the server components. Do you know if that's the case? 
Again, thanks.

---

### Post by falconindy on 2009-09-03
Get used to the `man` command (and `man mount` in this case). It's short for manual, and will give you plenty of information about any command you're wary about running. In general, the naming convention is [designation]d[sequential letter][partition number]. So, hda3 refers to the 3rd partition on the first found hard drive. sdd2 would generally refer to a scsi, or sata, device. In this case we're looking at the 2nd partition on the 4th found hard drive.

You can see the setup of your hard drives with `sudo fdisk -l`. It'll also appear in your /etc/fstab file, however you may see UUID's instead of the '/dev/sda1' sort of format. UUIDs can be used interchangably, and obtained using `sudo vol_id /dev/sda1`. Any time you make changes to your /etc/fstab, you can coerce the updates with `sudo mount -a`. Be **extremely** careful with your /etc/fstab and be sure to go slowly and make backups if you're concerned.

Adding Gnome over the server version is definitely the way to go, imo. The other way I can think of accomplishing it would involve recompiling your kernel after installing the desktop edition. A little more complicated for a beginner and less fun... or more fun, depending on your point of view!

Editorial remarks: Windows servers have historically been fairly stable as long as you play nice with them. I have a suspicion that people who admin Linux servers are more "gentle" than those who adminster Windows servers because of the culture surrounding the two operating systems (heavy generalizations here). I played network admin to a small network of a dozen or so servers and for the most part, they were rock solid. However, the application servers almost always had problems and I'm sure it's because of the programs and data they stored, **not** the operating system. My 2 domain controllers ran flawlessly for months at a time and we even had a Windows 2000 Advanced Server box emulating a Unisys mainframe (supporting a small bank). In my 2 years there, that machine was only rebooted 3 times and one of those was a shutdown to replace a drive in the RAID-10 array, and the other two were for tape drive failures.

lol... man mount...

---

### Post by breauxlg on 2009-09-03
Roger on the "playing nice." My personal servers and pc's have been very, very reliable, but I don't put ANYTHING on them that I don't absolutely need to do my job. I only a year ago replaced an IBM laptop running Windows 2000 as my primary work pc. I bought a Lenovo and zapped the hard drive, loaded a clean copy of XP Pro, and that's what I primarily use. I have Vista Ultimate loaded on a PC in case I have a customer call that's using one, but I have very few applications on it. My workhorses are still XP Pro. I imagine that when I get Ubuntu 8.04 loaded and running, I'll have very few problems with it either.

---

### Post by tgalati4 on 2009-09-04
Hook up a cable (USB, serial, ethernet) to your UPS so that your server will shutdown automatically when there is a long power outage.  That way you can be in Hawaii and still have your hardware protected.

There are lots of tutorials.  A google search on "ubuntu tutorials" will provide an afternoon of reading.

One helpful collection:

[The Psycho Cat]("http://www.psychocats.net/ubuntu/index")

---

### Post by breauxlg on 2009-11-26
Thanks for all the replies. I've been running 8.04 LTS for a while now and it's wprking very well.

---

