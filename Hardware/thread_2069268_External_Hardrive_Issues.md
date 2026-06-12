---
title: "External Hardrive Issues"
date: 2012-10-10
forum: Hardware
---

### Post by rjk42 on 2012-10-10
I recently post this at western digital and decided to post it here because Ubuntu was able to get me farther with solving my issue.

I used the live USB version of Ubuntu 12.04.1 desktop.

--
I was going through my files in my 500gig "My Passport", which was hooked up to my laptop.  As I was taking the computer off my lap and onto the table, when the external drive slipped off the laptop and hit the table while still hooked in.  Soon afterwards, the laptop would prompt me asking to format the drive, which I choose no.  It was still accessible but when I performed a chkdsk, it came up with some errors.  The chkdsk stated "The disk does not have enough space to replace bad clusters", so I went in and deleted a backup image of 127gig I created before with no issues.

After I deleted the 127gig back up image, the drive ran fine.  I could access all the files that I needed but the computer still displayed a prompt to format the drive.  I read through the chkdsk report and noticed it reported errors in a folder I created for a backup of some software I purchased.  It was just an executable file with the necessary files for installation.

-->> 
"detected in file 93237 of name \BDSPRM\3rdParty\DirectX\APR200~1.CAB.
Read failure with status 0xc000000e at offset 0x116d0ec000 for 0x10000 bytes.
Read failure with status 0xc000000e at offset 0x116d0ec000 for 0x1000 bytes.
The disk does not have enough space to replace bad clusters"

So I thought that by deleting the folder "BDSPRM", that would free up more space and help get rid of issues when I run the chkdsk again.  But after doing so, the computer will not open the drive at all.  It will recognize it and now will only assign a specific letter instead of displaying "My Passport F:” It also hangs up my system.  My computer cannot shut down when the drive is connected through USB.  

I tried to access it through a live USB Linux - Ubuntu.  When the Linux is up and running, it would recognize the drive and name it "My Passport" where Windows 7 could not.  I would click on the drive and I would receive an error stating it could not be mounted because it is being accessed through another application.  I continued to wait and click and eventually was able to access all my files again.  I was transferring some of the files to a folder I created to backup what is on "My Passport" but did not finish due to work.  I figure it would work again and I can continue at another time.

So now, when I boot up the live Linux, like before, I cannot access my drive but it shows up as "My Passport".  Eventually it will allow me to right click it and select properties, which it will display the used and free space appropriately but now I cannot get in there to copy out the files before.  I'm not sure what to do now but it seems as though using Linux is my best chance.  I'm very limited when it comes to Linux so I'm not sure what steps I can take to try to recover the drive.  My laptop runs Windows 7.

Thanks in advance 

---

I'm not knowledgeable with linux but would like to start.  Are there any steps to take to help with my issue using linux?  I want to access the drive and back up everything before I do a complete format.

Thanks!!

I also attached the chkdsk report.

---

