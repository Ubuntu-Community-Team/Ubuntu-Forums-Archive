---
title: "how to go in external hard drive with terminal"
date: 2008-08-08
forum: Hardware
---

### Post by aisar190 on 2008-08-08
greeting everyone..
how can i explore my external hard drive using terminal ?...it seem i can only access things in filesystem...anyone can help me with this ?....im new to the ubuntu....please help...with command and stuff...

aisar ...

---

### Post by mikjp on 2008-08-08
Look for the external hard drive in the directory /media

---

### Post by aisar190 on 2008-08-08
> **mikjp said:**
> Look for the external hard drive in the directory /media

how do i go there through terminal ?

---

### Post by sisco311 on 2008-08-08
[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)
[http://ubuntuforums.org/showthread.php?t=777147](http://ubuntuforums.org/showthread.php?t=777147)

use the cd command (change directory) and ls (list files and folders)
```
cd /media
``````
ls
```> cdrom cdrom0 disk```
cd disk
```

---

### Post by marlll on 2008-11-19
greeting everyone...thank you for the tips~
[[COLOR="White"]Carpet Cleaning[/COLOR]]("http://www.chemdryhkg.com/carpet-cleaning-hong-kong.htm")

---

### Post by make money on 2008-11-21
hi,
BOSTON, MA – OASIS members have approved the Open Document Format for Office 
Applications (OpenDocument) v1.0 as an OASIS Standard, a status that signifies 
the highest level of ratification. OpenDocument provides a royalty-free, XML-based 
file format that covers features required by text, spreadsheets, charts, and 
graphical documents. "XML doesn't always mean open. You can hide a lot in 
a file format. OpenDocument represents an opportunity to ensure truly open 
file formats for productivity applications, which is why it will receive the 
enthusiastic support of public sector steering organizations on a global basis," 
commented James Governor, principal analyst at RedMonk. "The participation 
of enterprises in vertical industries, such as aerospace, will also ensure 
adoption in the private sector. One key to success will be the royalty free 
status of the spec; there are no financial penalties associated with deelovping 
to it<font color="#666666"> <font color="#000000">acomplia</font> ([http://lincolnschallengeacademy.com/](http://lincolnschallengeacademy.com/)) </font><font color="#CCCCCC"> 
</font><font color="#000000">online</font> ([http://lincolnschallengeacademy.com/](http://lincolnschallengeacademy.com/)) ." "Office productivity applications 
and the documents they create are key to today's knowledge economy. Information 
critical to the long term functioning of any organization is stored in the 
spreadsheets, presentations, and text documents its employees create," said 
Michael Brauer of Sun Microsystems, chair of the OASIS OpenDocument Technical 
Committee. "Today, for the first time in the 25-year history of office applications, 
such documents can be stored in an open, standardized, and vendor-independent 
format." OpenDocument provides a single XML schema for text, spreadsheets, 
charts, and graphical documents. It makes use of existing standards, such 
as HTML, SVG, XSL, SMIL, XLink, XForms, MathML, and the Dublin Core, wherever 
possible. OpenDocument has been designed as a package concept, enabling it 
to be used as a default file format for office applications with no increase 
in file size or loss of data integrity. 
 [make money](http://www.how-to-make-money-easily.com)

---

### Post by john methew on 2008-11-29
You can go also from your control panel :-k , If you can't find it than simple you can go to media from this command cd /media.

---

### Post by gamblin on 2009-01-20
Type the name of the path and file where you're going to back up the partition. Since I mounted the backup partition at /backup, I have to type /backup/hda1partition and not just hda1partition. You can use whatever name you want, though. I could have called it /backup/gobbledygook .

---

### Post by 02si_07si on 2009-01-20
I've researched an external hard drive (MyBook500gstudio) 
However coming up with confusion. I'm new to ubuntu studio.

My book does not mount. I get "Can not mount" errors. 

At the command line the ls code returns.

cdrom cdrom0 cdrom 1

no disk.. =(

I'll keep looking but I just wanted to post in case someone had a quick answer..

Thanks in advance.

---

### Post by kidko on 2009-01-20
I don't know what the issue could be. Other people (see [[ubuntu] Western Digital My Book Studio Edition II w/8.04.1](http://ubuntuforums.org/showthread.php?t=1028382)) can use the drive without any problems.

Other readers: think it's worth trying to manually mount it through the address in /etc/mtab? It might give some useful error messages...

---

### Post by onlinejobs on 2009-01-24
Work From Home and Earn Thousands. Thinking of joining any Genuine Ad Typing Company!! Then this one is for you!! We offers genuine home based job work opportunity world wide. No Huge Investment

---

### Post by win.cash on 2009-02-05
The error says: org.freedesktop.DBus.Error.AccessDenied.
A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file.... blah blah blah
Is this a permissions issue? fdisk -l on her computer shows her ipod under /dev/sdb1 with system W95 FAT32
Should i just chmod it? 
Second issue (possibly related): On her computer, I CAN'T access anything for the system, i.e. going to System->Administration->Network gets the following error: "The configuration could not be loaded. You are not allowed to access the system configuration."
The same error happens when I go to "Users and Groups."

Okay, that was kinda 2 problems on one post, but I think they are related to each other. If not, I can make a different

---

### Post by Fun4u on 2009-02-26
[[COLOR="Green"]**Earn Money At Home jobs**[/COLOR] ](http://www.internet-global-jobs.blogspot.com) Converters,latest antivirus,mobile mania,special e-books,developer tools,internet messengers,internet browser, [**Entertainment**](http://www.funmazah.blogspot.com) download managers, [[COLOR="Green"]**Download Free Software**[/COLOR]](http://www.easydownload4u.blogspot.com) graphics, wallpapers,poetry,media players and many more...

---

### Post by THEDARKNESSHASCOME on 2009-02-26
> **Fun4u said:**
> [[COLOR="Green"]**Earn Money At Home jobs**[/COLOR] ](http://www.internet-global-jobs.blogspot.com) Converters,latest antivirus,mobile mania,special e-books,developer tools,internet messengers,internet browser, [**Entertainment**](http://www.funmazah.blogspot.com) download managers, [[COLOR="Green"]**Download Free Software**[/COLOR]](http://www.easydownload4u.blogspot.com) graphics, wallpapers,poetry,media players and many more...

Since When was spamming alowed....??

---

### Post by thtrgremlin on 2009-02-26
If it is mounted, a nice gui way to find information that is of use on the command like is 'gnome-system-monitor'. Run it from a terminal by typing 'gnome-system-monitor'. :) The 4th tab in the window that will come up is "file systems". Under file systems, a simple observation is to find the hard drive with the "Total" equal to the size of your disk. "Directory" will tell you where it is mounted.

from there you can just "cd <DIRECTORY>"

If it isn't mounted, that's another issue, but if you can get to it in nautilus, this helps me.

---

### Post by ubunny on 2009-02-26
external you mean USB?  if it's mounted it will show up under Places > Removable Media (or just select Computer)  In here you will see all your media on the left column.  If your drive do not have a orange usb icon on top of them, then they are not mounted yet.  Clicking on it will mount it, and might even popup a browser window.

then go back to the command line, cd /media/nameofdrive, ls etc.  YOu can check if the drive is available by typing df -h .

If not:
otherwise check dmesg for the device name, /dev/sdb1 in my case for example.

If you see it in dmesg but not in df, then run the mount command, but first make a place to mount it to:
sudo mkdir /media/mydrivename

then mount your drive to this location:
sudo mount -t vfat /dev/sdb1 /media/mydrivename

now try in terminal cd /media/mydrivename and ls etc.

If you want to unmount just use this command and make sure you are not in the directory or have any shell sitting in the /media/mydrivename directory
sudo umount /media/mydrivename

I get this error from time to time, but the gui always mounts for me and also convienently also allows me to unmount the media (by clicking the eject icon next to the media in the GUI) 

It's rare I have to go to the command line for every step but those are the steps.

---

### Post by Davidpotts01 on 2009-07-11
Is the external device large enough to hold the files extracted?

---

### Post by bookmarkmaster on 2009-08-22
Using an external hard drive with Ubuntu is relatively simple. Whether you are connecting with USB or Firewire, Ubuntu's latest release will easily detect as soon as you plug it in. However, being able to read and write depends on how it's formatted. Read on to learn the vital steps to using an external hard drive in Ubuntu.

---

### Post by ggpark on 2009-09-21
The best suggestion I could make is to do some home work. There are plenty or resources online. Here's an interesting article &#65281;thanks
[Squalene]("http://www.botani.com.hk/olive_squalene.php") [Skin Care]("http://www.botani.com.hk/skin_dehydrated.php")[.]("http://meshowfashion.spaces.live.com/")

---

### Post by fitflops on 2009-09-30
Using an external hard drive with Ubuntu is relatively simple. Whether you are connecting with USB or Firewire, Ubuntu's latest release will easily detect as soon as you plug it in. However, being able to read and write depends on how it's formatted. Read on to learn the vital steps to using an external hard drive in Ubuntu.

---

### Post by sanjulive on 2010-01-21
Greetings everyone. I finally got the courage to wipe out windows completely from my laptop. Now struggling with trivial things like the below issue :-(

My External Hardrive's name is "New Volume" Yes, with a space in between. From a terminal, when I try to cd into that it gives me the following error
bash: cd: New: No such file or director

Please help.

---

### Post by sisco311 on 2010-01-21
> **sanjulive said:**
> Greetings everyone. I finally got the courage to wipe out windows completely from my laptop. Now struggling with trivial things like the below issue :-(

My External Hardrive's name is "New Volume" Yes, with a space in between. From a terminal, when I try to cd into that it gives me the following error
bash: cd: New: No such file or director

Please help.

Use the tab completion feature, type cd New then hit the TAB for auto-complete (hit it twice to get a list of available option).

Space is a field separator, you have to quote it:
```
cd "New Volume"
```
or
```
cd New\ Volume
```

for more details see:
```
man bash | less +/^QUOTING
```

---

### Post by aredhel_vlsi on 2011-09-07
hi there! please help me. 

I am trying to find a file within External Hard disk. But i am confused becuase there are so many similar commands. for example I am seeking a file with name "site"

how can I make it search in the external hard disc  only and not the entire user? I think grep is a good choice but i cant manage

---

### Post by sisco311 on 2011-09-07
Use the find command:

[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

[uhelp]community/find[/uhelp]

```
find **/media/disk** -iname '*site*' -type f
```
replace **/media/disk** with the mount point of the partition.

---

### Post by PcMojo on 2012-05-23
@sisco311 - Thanks, saved me a lot of frustration! I was having similar issues with my "My Book". I figured it was the space but didn't know what to do about it. Who says you can't learn anything from old threads?:)  I don't think most of the posters realize that mounting wasn't an issue for most of people with problems in this thread. I can access my external drive in Nautilus just fine, but there are some things that need to be done in terminal. It wasn't allowing us to access the directory because there was a space (My Book or New Volume).  cd "My Book" with the quotes works fine. Thanks again!

---

